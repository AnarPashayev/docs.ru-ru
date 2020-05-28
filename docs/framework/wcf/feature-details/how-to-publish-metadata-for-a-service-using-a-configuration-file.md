---
title: Практическое руководство. Публикация метаданных для службы с использованием файла конфигурации
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 179ccf97ce4f5e2aa3e132db7e77c93259d5e4ac
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144946"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Практическое руководство. Публикация метаданных для службы с использованием файла конфигурации
Это один из двух инструкций, демонстрирующих публикацию метаданных для службы Windows Communication Foundation (WCF). Существуют два способа указать, как служба должна публиковать метаданные: с помощью файла конфигурации и с помощью кода. В этом разделе показано, как публиковать метаданные для службы с помощью файла конфигурации.  
  
> [!CAUTION]
> В этом разделе показано, как опубликовать метаданные незащищенным образом. Любой клиент может получить метаданные из службы. Если требуется безопасная публикация метаданных в службе, см. раздел [Настраиваемая конечная точка безопасных метаданных](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Дополнительные сведения о публикации метаданных в коде см. в разделе [инструкции. Публикация метаданных для службы с помощью кода](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Публикация метаданных позволяет клиентам извлекать метаданные с помощью запроса WS-Transfer GET или запроса HTTP/GET, используя строку запроса `?wsdl`. Чтобы убедиться в том, что код работает, создайте базовую службу WCF. Для упрощения в следующем коде представлена несложная резидентная служба.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 Эта служба представляет собой резидентную службу, настраиваемую посредством файла конфигурации. Отправной точкой будет служить следующий файл конфигурации.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Публикация метаданных для службы WCF с помощью файла конфигурации приложения  
  
1. В файле App.config после закрывающего элемента `</services>`.  

2. В элемент `<behaviors>` добавьте элемент `<serviceBehaviors>`.  

3. Добавьте элемент `<behavior>``<serviceBehaviors>` элемента .  

4. Добавьте элемент `<serviceMetadata>` в элемент `<behavior>`. Задайте атрибуту `httpGetEnabled` значение `true`, а атрибуту `policyVersion` значение Policy15. `httpGetEnabled` позволяет службе отвечать на запросы метаданных, переданные с помощью запроса HTTP GET. `policyVersion` сообщает службе, что формируемые метаданные должны соответствовать спецификации WS-Policy 1.5.  

5. Добавьте атрибут `behaviorConfiguration` элементу `<service>``name`, добавленного на шаге 1, как показано в следующем примере кода.  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6. Добавьте один или несколько элементов `<endpoint>`, как показано в следующем примере кода.  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7. В конечных точках метаданных, добавленных на предыдущем шаге, присвойте атрибуту `binding` одно из следующих значений:  
  
    - `mexHttpBinding` для публикации по HTTP;  
  
    - `mexHttpsBinding` для публикации по HTTPS;  
  
    - `mexNamedPipeBinding` для публикации по именованному каналу;  
  
    - `mexTcpBinding` для публикации по TCP.  
  
8. В конечных точках метаданных, добавленных на предыдущем шаге, задайте для адреса одно из следующих значений:  
  
    - пустую строку, чтобы использовать в качестве точки публикации базовый адрес ведущего приложения, если базовый адрес совпадает с привязкой метаданных;  
  
    - относительный адрес, если ведущее приложение имеет базовый адрес;  
  
    - абсолютный адрес.  
  
9. Скомпилируйте и запустите консольное приложение.  
  
10. С помощью Internet Explorer перейдите к базовому адресу службы ( `http://localhost:8001/MetadataSample` в этом примере) и убедитесь, что публикация метаданных включена. В противном случае вверху страницы отображается сообщение "Публикация метаданных для этой службы в настоящее время отключена".  
  
### <a name="to-use-default-endpoints"></a>Использование конечных точек по умолчанию  
  
1. Чтобы настроить метаданные в службе, которая использует конечные точки по умолчанию, укажите <xref:System.ServiceModel.Description.ServiceMetadataBehavior> в файле конфигурации, как показано в предыдущем примере, но не указывайте конечные точки. Файл конфигурации будет иметь следующий вид.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Поскольку служба имеет <xref:System.ServiceModel.Description.ServiceMetadataBehavior> со свойством `httpGetEnabled`, установленным в значение `true`, то для службы включена публикация метаданных, а поскольку конечные точки не были добавлены явно, среда выполнения добавляет конечные точки по умолчанию. Дополнительные сведения о конечных точках по умолчанию, привязках и режимах работы см. в разделах [Упрощенная конфигурация](../../../../docs/framework/wcf/simplified-configuration.md) и [Упрощенная конфигурация служб WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода показана реализация базовой службы WCF и файла конфигурации, который публикует метаданные для службы.  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Практическое руководство. Размещение службы WCF в управляемом приложении](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Резидентное размещение](../../../../docs/framework/wcf/samples/self-host.md)
- [Общие сведения об архитектуре метаданных](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Использование метаданных](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Практическое руководство. Публикация метаданных для службы с использованием кода](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
