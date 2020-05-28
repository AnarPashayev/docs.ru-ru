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
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="6f1cc-102">Практическое руководство. Публикация метаданных для службы с использованием файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="6f1cc-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="6f1cc-103">Это один из двух инструкций, демонстрирующих публикацию метаданных для службы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6f1cc-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="6f1cc-104">Существуют два способа указать, как служба должна публиковать метаданные: с помощью файла конфигурации и с помощью кода.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="6f1cc-105">В этом разделе показано, как публиковать метаданные для службы с помощью файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="6f1cc-106">В этом разделе показано, как опубликовать метаданные незащищенным образом.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="6f1cc-107">Любой клиент может получить метаданные из службы.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="6f1cc-108">Если требуется безопасная публикация метаданных в службе, см. раздел [Настраиваемая конечная точка безопасных метаданных](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="6f1cc-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="6f1cc-109">Дополнительные сведения о публикации метаданных в коде см. в разделе [инструкции. Публикация метаданных для службы с помощью кода](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="6f1cc-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="6f1cc-110">Публикация метаданных позволяет клиентам извлекать метаданные с помощью запроса WS-Transfer GET или запроса HTTP/GET, используя строку запроса `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="6f1cc-111">Чтобы убедиться в том, что код работает, создайте базовую службу WCF.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="6f1cc-112">Для упрощения в следующем коде представлена несложная резидентная служба.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
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
  
 <span data-ttu-id="6f1cc-113">Эта служба представляет собой резидентную службу, настраиваемую посредством файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="6f1cc-114">Отправной точкой будет служить следующий файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-114">The following configuration file serves as a starting point.</span></span>  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="6f1cc-115">Публикация метаданных для службы WCF с помощью файла конфигурации приложения</span><span class="sxs-lookup"><span data-stu-id="6f1cc-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="6f1cc-116">В файле App.config после закрывающего элемента `</services>`.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="6f1cc-117">В элемент `<behaviors>` добавьте элемент `<serviceBehaviors>`.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="6f1cc-118">Добавьте элемент `<behavior>``<serviceBehaviors>` элемента .</span><span class="sxs-lookup"><span data-stu-id="6f1cc-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="6f1cc-119">Добавьте элемент `<serviceMetadata>` в элемент `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="6f1cc-120">Задайте атрибуту `httpGetEnabled` значение `true`, а атрибуту `policyVersion` значение Policy15.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="6f1cc-121">`httpGetEnabled` позволяет службе отвечать на запросы метаданных, переданные с помощью запроса HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="6f1cc-122">`policyVersion` сообщает службе, что формируемые метаданные должны соответствовать спецификации WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="6f1cc-123">Добавьте атрибут `behaviorConfiguration` элементу `<service>``name`, добавленного на шаге 1, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
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
  
6. <span data-ttu-id="6f1cc-124">Добавьте один или несколько элементов `<endpoint>`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
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
  
7. <span data-ttu-id="6f1cc-125">В конечных точках метаданных, добавленных на предыдущем шаге, присвойте атрибуту `binding` одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="6f1cc-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="6f1cc-126">`mexHttpBinding` для публикации по HTTP;</span><span class="sxs-lookup"><span data-stu-id="6f1cc-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="6f1cc-127">`mexHttpsBinding` для публикации по HTTPS;</span><span class="sxs-lookup"><span data-stu-id="6f1cc-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="6f1cc-128">`mexNamedPipeBinding` для публикации по именованному каналу;</span><span class="sxs-lookup"><span data-stu-id="6f1cc-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="6f1cc-129">`mexTcpBinding` для публикации по TCP.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="6f1cc-130">В конечных точках метаданных, добавленных на предыдущем шаге, задайте для адреса одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="6f1cc-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="6f1cc-131">пустую строку, чтобы использовать в качестве точки публикации базовый адрес ведущего приложения, если базовый адрес совпадает с привязкой метаданных;</span><span class="sxs-lookup"><span data-stu-id="6f1cc-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="6f1cc-132">относительный адрес, если ведущее приложение имеет базовый адрес;</span><span class="sxs-lookup"><span data-stu-id="6f1cc-132">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="6f1cc-133">абсолютный адрес.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="6f1cc-134">Скомпилируйте и запустите консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="6f1cc-135">С помощью Internet Explorer перейдите к базовому адресу службы ( `http://localhost:8001/MetadataSample` в этом примере) и убедитесь, что публикация метаданных включена.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-135">Use Internet Explorer to browse to the base address of the service (`http://localhost:8001/MetadataSample` in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="6f1cc-136">В противном случае вверху страницы отображается сообщение "Публикация метаданных для этой службы в настоящее время отключена".</span><span class="sxs-lookup"><span data-stu-id="6f1cc-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="6f1cc-137">Использование конечных точек по умолчанию</span><span class="sxs-lookup"><span data-stu-id="6f1cc-137">To use default endpoints</span></span>  
  
1. <span data-ttu-id="6f1cc-138">Чтобы настроить метаданные в службе, которая использует конечные точки по умолчанию, укажите <xref:System.ServiceModel.Description.ServiceMetadataBehavior> в файле конфигурации, как показано в предыдущем примере, но не указывайте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="6f1cc-139">Файл конфигурации будет иметь следующий вид.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-139">The configuration file would then look like this.</span></span>  
  
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
  
     <span data-ttu-id="6f1cc-140">Поскольку служба имеет <xref:System.ServiceModel.Description.ServiceMetadataBehavior> со свойством `httpGetEnabled`, установленным в значение `true`, то для службы включена публикация метаданных, а поскольку конечные точки не были добавлены явно, среда выполнения добавляет конечные точки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="6f1cc-141">Дополнительные сведения о конечных точках по умолчанию, привязках и режимах работы см. в разделах [Упрощенная конфигурация](../../../../docs/framework/wcf/simplified-configuration.md) и [Упрощенная конфигурация служб WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6f1cc-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f1cc-142">Пример</span><span class="sxs-lookup"><span data-stu-id="6f1cc-142">Example</span></span>  
 <span data-ttu-id="6f1cc-143">В следующем примере кода показана реализация базовой службы WCF и файла конфигурации, который публикует метаданные для службы.</span><span class="sxs-lookup"><span data-stu-id="6f1cc-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f1cc-144">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6f1cc-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="6f1cc-145">Практическое руководство. Размещение службы WCF в управляемом приложении</span><span class="sxs-lookup"><span data-stu-id="6f1cc-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="6f1cc-146">Резидентное размещение</span><span class="sxs-lookup"><span data-stu-id="6f1cc-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="6f1cc-147">Общие сведения об архитектуре метаданных</span><span class="sxs-lookup"><span data-stu-id="6f1cc-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="6f1cc-148">Использование метаданных</span><span class="sxs-lookup"><span data-stu-id="6f1cc-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="6f1cc-149">Практическое руководство. Публикация метаданных для службы с использованием кода</span><span class="sxs-lookup"><span data-stu-id="6f1cc-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
