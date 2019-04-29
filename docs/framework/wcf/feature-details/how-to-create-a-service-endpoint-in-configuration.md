---
title: Практическое руководство. Создание конечной точки службы в конфигурации
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 63a40576b805952197cec5af2f89a5dc4b5d3545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787651"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="eaa0a-102">Практическое руководство. Создание конечной точки службы в конфигурации</span><span class="sxs-lookup"><span data-stu-id="eaa0a-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="eaa0a-103">Конечные точки предоставляют клиентам доступ к функциональным возможностям, предлагаемым службой Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="eaa0a-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="eaa0a-104">Можно определить одну или несколько конечных точек для службы, используя сочетание относительных и абсолютных адресов конечных точек. Если же не определять конечные точки службы, среда выполнения автоматически создаст несколько точек по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="eaa0a-105">В этом разделе показано, как добавить конечные точки, используя файл конфигурации, который содержит и относительные, и абсолютные адреса.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaa0a-106">Пример</span><span class="sxs-lookup"><span data-stu-id="eaa0a-106">Example</span></span>  
 <span data-ttu-id="eaa0a-107">Представленная ниже конфигурация службы задает базовый адрес и пять конечных точек.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced  
         in .NET Framework 4. -->  
      <service  
          name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="eaa0a-108">Пример</span><span class="sxs-lookup"><span data-stu-id="eaa0a-108">Example</span></span>  
 <span data-ttu-id="eaa0a-109">Базовый адрес задается с помощью элемента `add` в каталоге service/host/baseAddresses, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="eaa0a-110">Пример</span><span class="sxs-lookup"><span data-stu-id="eaa0a-110">Example</span></span>  
 <span data-ttu-id="eaa0a-111">В первом определении конечной точки, показанном в следующем образце, задается относительный адрес. Это означает, что адрес конечной точки представляет собой сочетание базового и относительного адресов, соответствующее правилам формирования универсального кода ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="eaa0a-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="eaa0a-112">Относительный адрес пустой (""), поэтому адрес конечной точки совпадает с базовым адресом.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="eaa0a-113">Фактический адрес конечной точки `http://localhost:8000/servicemodelsamples/service`.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="eaa0a-114">Пример</span><span class="sxs-lookup"><span data-stu-id="eaa0a-114">Example</span></span>  
 <span data-ttu-id="eaa0a-115">Во втором определении конечной точки также задается относительный адрес, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="eaa0a-116">Относительный адрес, "test", присоединяется к базовому адресу.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="eaa0a-117">Фактический адрес конечной точки `http://localhost:8000/servicemodelsamples/service/test`.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="eaa0a-118">Пример</span><span class="sxs-lookup"><span data-stu-id="eaa0a-118">Example</span></span>  
 <span data-ttu-id="eaa0a-119">В третьем определении конечной точки задается абсолютный адрес, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="eaa0a-120">Базовый адрес не играет никакой роли в этом адресе.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-120">The base address plays no role in the address.</span></span> <span data-ttu-id="eaa0a-121">Фактический адрес конечной точки `http://localhost:8001/hello/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="eaa0a-122">Пример</span><span class="sxs-lookup"><span data-stu-id="eaa0a-122">Example</span></span>  
 <span data-ttu-id="eaa0a-123">В четвертом определении конечной точки задаются абсолютный адрес и другой транспорт - TCP.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="eaa0a-124">Базовый адрес не играет никакой роли в этом адресе.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-124">The base address plays no role in the address.</span></span> <span data-ttu-id="eaa0a-125">Фактический адрес конечной точки — net.tcp://localhost:9000/servicemodelsamples/service.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="eaa0a-126">Пример</span><span class="sxs-lookup"><span data-stu-id="eaa0a-126">Example</span></span>  
 <span data-ttu-id="eaa0a-127">Чтобы использовать конечные точки по умолчанию, предоставляемые средой выполнения, не указывайте конечные точки службы ни в коде, ни в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="eaa0a-128">В этом примере среда выполнения при открытии службы создает конечные точки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="eaa0a-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="eaa0a-129">Дополнительные сведения о конечных точках по умолчанию, привязках и режимах работы см. в разделах [Упрощенная конфигурация](../../../../docs/framework/wcf/simplified-configuration.md) и [Упрощенная конфигурация служб WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="eaa0a-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```
