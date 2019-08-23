---
title: Поведение отладки службы
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 75c53d567e3f16310f9623b416279decb6bee541
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964558"
---
# <a name="service-debug-behavior"></a>Поведение отладки службы
В этом образце показано, как могут настраиваться параметры поведения отладки службы. Образец основан на [Начало работы](../../../../docs/framework/wcf/samples/getting-started-sample.md), который реализует `ICalculator` контракт службы. Этот образец явно определяет поведение отладки службы в файле конфигурации. Это также можно выполнить императивно в коде.  
  
 В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.  
  
> [!NOTE]
> Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.  
  
 Файл Web.config для сервера определяет поведение отладки службы для включения страницы справки и обработки исключений, как показано в следующем образце.  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 serviceDebug > — это элемент конфигурации, позволяющий изменять свойства поведения при отладке службы. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) Пользователь может изменять это поведение для достижения следующих целей.  
  
- Это позволяет службе возвращать любое исключение, вызванное кодом приложения, даже если это исключение не объявлено с помощью атрибута <xref:System.ServiceModel.FaultContractAttribute>. Для этого необходимо присвоить параметру `includeExceptionDetailInFaults` значение `true`. Этот параметр полезен при отладке в тех случаях, когда сервер создает непредвиденное исключение.  
  
    > [!IMPORTANT]
    >  Включать этот параметр в производственной среде небезопасно. В непредвиденном исключении сервера может содержаться информация, не предназначенная для клиента, поэтому присвоение параметру `includeExceptionDetailsInFaults` значения `true` может привести к утечке информации.  
  
- > ServiceDebug также позволяет пользователю включать или отключать страницу справки. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) Каждая служба может предоставлять страницу справки, которая содержит данные о службе, включая сведения о конечной точке для получения WSDL для службы. Эту возможность можно включить, присвоив параметру `httpHelpPageEnabled` значение `true`. Это позволяет возвращать страницу справки в ответ на запрос GET к базовому адресу службы. Этот адрес можно изменить, задав другой атрибут `httpHelpPageUrl`. Можно сделать этот процесс безопасным, если использовать транспорт HTTPS вместо HTTP. Для этого необходимо задать `httpsHelpPageEnabled` и `httpsHelpPageUrl`.  
  
 При выполнении примера запросы и ответы операций отображаются в окне консоли клиента. Первые три операции (сложение, вычитание и умножение) должны выполняться успешно. Последняя операция (деление) завершается неудачей - выдается исключение в результате деления на ноль.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1. Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] и примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
