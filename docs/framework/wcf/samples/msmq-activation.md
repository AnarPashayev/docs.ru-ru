---
title: Активация MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: d83759f321abe7fa7e39202daadd4ceda82d8f23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051485"
---
# <a name="msmq-activation"></a>Активация MSMQ
Этот образец демонстрирует размещение приложений в службе активации Windows (WAS), которые считываются из очереди сообщений. В этом примере используется `netMsmqBinding` и основан на [Двусторонняя связь](../../../../docs/framework/wcf/samples/two-way-communication.md) образца. В данном случае служба представляет собой приложение, размещенное на веб-сервере, а клиент - резидентное приложение, выводящее данные в окно консоли для наблюдения за состоянием размещенных заказов на покупку.  
  
> [!NOTE]
>  Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.  
  
> [!NOTE]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  \<InstallDrive>:\WF_WCF_Samples  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех WCF и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  \<Диск_установки >: \Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.  
  
 Служба активации Windows (WAS), новый механизм активации процессов для [!INCLUDE[lserver](../../../../includes/lserver-md.md)], предоставляет компоненты, подобные IIS, ранее доступные только приложениям, работающим на базе протокола HTTP, для приложений, использующих протоколы, отличные от HTTP. Windows Communication Foundation (WCF) использует интерфейс адаптера прослушивателя для передачи запросов на активацию, полученных через протоколы отличные от HTTP, поддерживаемые WCF, таких как TCP, именованные каналы и MSMQ. Функциональность для получения запросов по протоколам, отличным от HTTP, размещена в управляемых службах Windows, выполняемых в файле SMSvcHost.exe.  
  
 Служба адаптера прослушивателя Net.Msmq (NetMsmqActivator) активирует приложения в очереди на основании очереди сообщений.  
  
 Клиент отправляет службе заказы на покупку из области транзакции. Служба получает заказы в транзакцию и обрабатывает их. После этого служба возвращает клиенту состояние заказа. Для двустороннего взаимодействия и клиент, и служба используют очереди для заказов на покупку и состояний заказов.  
  
 Контракт службы `IOrderProcessor` определяет односторонние операции службы, работающие с очередями. Операция службы использует конечную точку ответа для отправки клиенту состояний заказов. Адрес конечной точки ответа - это универсальный код ресурса (URI) очереди, служащий для отправки клиенту состояний заказов. Приложение, обрабатывающее заказы, реализует этот контракт.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 Контракт ответа для отправки состояния заказа задается клиентом. Клиент реализует контракт состояния заказа. Служба использует созданного клиента этого контракта для отправки состояния заказа клиенту.  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 Операция службы обрабатывает отправленный заказ на покупку. Объект <xref:System.ServiceModel.OperationBehaviorAttribute> применяется к операции службы, чтобы задать автоматическое зачисление в транзакцию, которая используется для получения сообщения из очереди, и автоматическое завершение транзакции после завершения операции службы. Класс `Orders` инкапсулирует функцию обработки заказа. В данном случае он добавляет заказ на покупку в словарь. Транзакция, в которую зачислена операция службы, доступна операциям в классе `Orders`.  
  
 Операция службы, помимо обработки отправленного заказа на покупку, возвращает клиенту состояние заказа.  
  
```csharp  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
        Console.WriteLine("Sending back order status information");  
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
        // please note that the same transaction that is used to dequeue purchase order is used  
        // to send back order status  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.OrderStatus(po.PONumber, po.Status);  
            scope.Complete();  
        }  
    }
}
```  
  
 Используемая клиентом привязка задается при помощи файла конфигурации.  
  
 Имя очереди MSMQ задается в разделе appSettings файла конфигурации. Конечная точка службы определяется в разделе System.serviceModel файла конфигурации.  
  
> [!NOTE]
>  Правила адресации несколько различаются для имени очереди MSMQ и адреса конечной точки. В имени очереди MSMQ для определения локального компьютера используется точка (.), а в пути в качестве разделителей используются символы обратной косой черты. Адрес конечной точки WCF указывает net.msmq: схему, используется имя «localhost» для локального компьютера и используются символы косой черты в пути. Для чтения очереди, размещенной на удаленном компьютере, «.» и «localhost» следует заменить именем удаленного компьютера.  
  
 Для размещения кода службы в WAS используется файл с именем, соответствующем имени класса и расширением SVC.  
  
 Файл Service.svc содержит директиву для создания `OrderProcessorService`.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 Файл Service.svc также содержит директиву сборки для проверки загрузки System.Transactions.dll.  
  
```svc  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 Клиент создает область транзакции. Связь со службой происходит в области транзакции, поэтому она обрабатывается как единый модуль, в котором либо все сообщения отправляются успешно, либо не отправляется ни одного. Транзакция фиксируется вызовом метода `Complete` для области транзакции.  
  
```csharp  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
    // Open the ServiceHostBase to create listeners and start listening   
    // for order status messages.  
    serviceHost.Open();  
  
    // Create a proxy with given client endpoint configuration  
    OrderProcessorClient client = new OrderProcessorClient();  
  
    // Create the purchase order  
    PurchaseOrder po = new PurchaseOrder();  
    po.CustomerId = "somecustomer.com";  
    po.PONumber = Guid.NewGuid().ToString();  
  
    PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
    lineItem1.ProductId = "Blue Widget";  
    lineItem1.Quantity = 54;  
    lineItem1.UnitCost = 29.99F;  
  
    PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
    lineItem2.ProductId = "Red Widget";  
    lineItem2.Quantity = 890;  
    lineItem2.UnitCost = 45.89F;  
  
    po.orderLineItems = new PurchaseOrderLineItem[2];  
    po.orderLineItems[0] = lineItem1;  
    po.orderLineItems[1] = lineItem2;  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new   
        TransactionScope(TransactionScopeOption.Required))  
    {  
        // Make a queued call to submit the purchase order  
        client.SubmitPurchaseOrder(po,   
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Closing the client gracefully closes the connection and cleans up   
    //resources  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHostBase to shutdown the service.  
    serviceHost.Close();  
    }  
```  
  
 Код клиента реализует контракт `IOrderStatus` для получения от службы состояния заказа. В данном случае он выводит состояние заказа.  
  
```csharp  
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ",   
                                         poNumber , status);  
    }  
}  
```  
  
 Очередь состояний заказов создается в методе `Main`. Конфигурация клиента включает конфигурацию службы состояния заказов, размещающую службу состояния заказов, как показано в следующем образце конфигурации.  
  
```xml  
<appSettings>  
    <!-- use appSetting to configure MSMQ queue name -->  
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />  
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />  
  </appSettings>  
  
<system.serviceModel>  
  
    <services>  
      <service   
         name="Microsoft.ServiceModel.Samples.OrderStatusService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"   
                binding="netMsmqBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
    </client>  
  
  </system.serviceModel>  
```  
  
 При выполнении образца действия клиента и службы отображаются в окнах консоли как сервера, так и клиента. Можно видеть, как сервер получает сообщения от клиента. Нажмите клавишу ВВОД в каждом окне консоли, чтобы завершить работу сервера и клиента.  
  
 Клиент отображает сведения о состоянии заказа, отправленные сервером.  
  
```console  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1. Убедитесь, что установлены службы [!INCLUDE[iisver](../../../../includes/iisver-md.md)], которые необходимы для активации WAS.  
  
2. Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md). Кроме того необходимо установить компоненты не HTTP Активация WCF:  
  
    1. В меню **Пуск** выберите **Панель управления**.  
  
    2. Выберите **программы и компоненты**.  
  
    3. Нажмите кнопку **Включение или отключение компонентов Windows**.  
  
    4. В разделе **ׁגמהךא**, нажмите кнопку **добавить компоненты**.  
  
    5. Разверните **Microsoft .NET Framework 3.0** узел и проверьте **не-HTTP активация Windows Communication Foundation** функции.  
  
3. Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Запустите клиента, выполнив файл client.exe в окне командной строки. Этим создается очередь и в нее отсылается сообщение. Оставьте клиента запущенным, чтобы увидеть результат считывания сообщения службой.  
  
5. Служба активации MSMQ по умолчанию работает как сетевая служба. Поэтому очередь, используемая для активации приложения, должна иметь разрешения на получение и просмотр сетевой службой. Это можно сделать при помощи консоли управления (MMC) очередью сообщений:  
  
    1. Из **запустить** меню, щелкните **запуска**, затем введите `Compmgmt.msc` и нажмите клавишу ВВОД.  
  
    2. В разделе **служб и приложений**, разверните **Message Queuing**.  
  
    3. Нажмите кнопку **частные очереди**.  
  
    4. Щелкните правой кнопкой мыши очередь (servicemodelsamples/Service.svc) и выберите **свойства**.  
  
    5. На **безопасности** щелкните **добавить** и предоставить считывания и получения разрешений для сетевой службы.  
  
6. Настройка службы активации Windows (WAS) для поддержки активации MSMQ.  
  
     Для удобства следующие действия выполняются в пакетном файле AddMsmqSiteBinding.cmd, расположенном в каталоге образца.  
  
    1. Для поддержки активации net.msmq сначала необходимо привязать веб-узел по умолчанию к протоколу net.msmq. Это можно сделать программой appcmd.exe, которая устанавливается в наборе средств управления [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. В командной строке с повышенными привилегиями (с правами администратора) выполните следующую команду.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Эта команда представляет собой одну строку текста.  
  
         Эта команда добавляет для веб-узел по умолчанию привязку net.msmq.  
  
    2. Хотя все приложения на узле имеют общую привязку net.msmq, включать поддержку net.msmq можно для каждого приложения отдельно. Чтобы включить net.msmq для приложения /servicemodelsamples, выполните следующую команду из командной строки с повышенными привилегиями.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  Эта команда представляет собой одну строку текста.  
  
         Эта команда позволяет приложению/servicemodelsamples, осуществлять доступ к `http://localhost/servicemodelsamples` и `net.msmq://localhost/servicemodelsamples`.
  
7. Убедитесь, что включена служба активации MSMQ, если это не было сделано ранее. Из **запустить** меню, щелкните **запуска**и тип `Services.msc`. Найдите в списке служб для **адаптера прослушивателя Net.Msmq**. Щелкните правой кнопкой мыши и выберите **свойства**. Задайте **тип запуска** для **автоматического**, нажмите кнопку **применить** и нажмите кнопку **запустить** кнопки. Этот шаг необходимо проделать всего один раз перед первым использованием службы адаптера прослушивателя Net.Msmq.  
  
8. Чтобы запустить образец в конфигурации с одной или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Кроме того, можно изменить код на клиенте, который отправляет заказ на покупку, для отражения имени компьютера и URI очереди при отправке заказа на покупку. Используйте следующий код:  
  
    ```csharp  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. Удалите привязку узла net.msmq, добавленную ранее для данного образца.  
  
     Для удобства следующие действия выполняются в пакетном файле RemoveMsmqSiteBinding.cmd, расположенном в каталоге с образцом.  
  
    1. Удалите net.msmq из списка включенных протоколов, выполнив следующую команду из командной строки с повышенными привилегиями.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Эта команда представляет собой одну строку текста.  
  
    2. Удалите привязку узла net.msmq, выполнив следующую команду из командной строки с повышенными привилегиями.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Эта команда представляет собой одну строку текста.  
  
    > [!WARNING]
    >  После выполнения пакетного файла DefaultAppPool вернется к использованию .NET Framework версии 2.0.  
  
 По умолчанию с транспортом привязки `netMsmqBinding` безопасность включена. Тип безопасности транспорта определяется двумя свойствами: `MsmqAuthenticationMode` и `MsmqProtectionLevel`. По умолчанию устанавливается режим проверки подлинности `Windows` и уровень защиты `Sign`. Чтобы служба MSMQ обеспечивала возможности проверки подлинности и подписывания, она должна входить в домен. Если запустить этот пример на компьютере, который не является частью домена, будет получена следующая ошибка: «User's internal message queuing сертификата не существует».  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Выполнение образца на компьютере, входящем в рабочую группу  
  
1. Если компьютер не входит в домен, отключите безопасность транспорта, задав для режима проверки подлинности и уровня защиты значение None, как показано в следующем образце конфигурации.  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2. Перед выполнением образца измените конфигурацию как сервера, так и клиента.  
  
    > [!NOTE]
    >  Установка для `security mode` значения `None` эквивалентна присвоению свойствам `MsmqAuthenticationMode`, `MsmqProtectionLevel` и безопасности `Message` значения `None`.  
  
3. Для включения активации на компьютере, входящем в рабочую группу, и служба активации, и рабочий процесс должны быть запущены в определенной учетной записи пользователя (должна быть одинаковой для обоих), а очередь должна иметь ACL для определенной учетной записи пользователя.  
  
     Изменение удостоверения, с которым выполняется рабочий процесс.  
  
    1. Запустите файл Inetmgr.exe.  
  
    2. В разделе **пулы приложений**, щелкните правой кнопкой мыши **AppPool** (обычно **DefaultAppPool**) и выберите **значение по умолчанию пула приложений...** .  
  
    3. Измените свойства удостоверения для использования определенной учетной записи пользователя.  
  
     Изменение удостоверения, с которым выполняется служба активации.  
  
    1. Запустите файл Services.msc.  
  
    2. Щелкните правой кнопкой мыши **адаптер Net.MsmqListener**и выберите **свойства**.  
  
4. Изменение учетной записи в **входа** вкладки.  
  
5. В рабочей группе служба должна выполняться с маркером неограниченного доступа. Для этого запустите в командном окне следующее:  
  
    ```console  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a>См. также

- [Образцы размещения AppFabric и сохраняемости](https://go.microsoft.com/fwlink/?LinkId=193961)
