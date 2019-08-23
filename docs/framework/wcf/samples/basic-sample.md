---
title: Базовый образец
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: d227b3ac64108901b8280ac7887adc30b0fab13e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915453"
---
# <a name="basic-sample"></a><span data-ttu-id="04c0e-102">Базовый образец</span><span class="sxs-lookup"><span data-stu-id="04c0e-102">Basic Sample</span></span>
<span data-ttu-id="04c0e-103">В этом образце показано, как сделать службу обнаруживаемой, а также как искать и вызывать обнаруживаемую службу.</span><span class="sxs-lookup"><span data-stu-id="04c0e-103">This sample shows how to make a service discoverable and how to search for and call a discoverable service.</span></span> <span data-ttu-id="04c0e-104">Этот образец состоит из двух проектов: службы и клиента.</span><span class="sxs-lookup"><span data-stu-id="04c0e-104">This sample is composed of two projects: service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="04c0e-105">Этот образец реализует возможность обнаружения в коде.</span><span class="sxs-lookup"><span data-stu-id="04c0e-105">This sample implements discovery in code.</span></span>  <span data-ttu-id="04c0e-106">Пример, в котором реализуется обнаружение в конфигурации, см. в разделе [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span><span class="sxs-lookup"><span data-stu-id="04c0e-106">For a sample that implements discovery in configuration, see [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).</span></span>  
  
## <a name="service"></a><span data-ttu-id="04c0e-107">Служба</span><span class="sxs-lookup"><span data-stu-id="04c0e-107">Service</span></span>  
 <span data-ttu-id="04c0e-108">Это простая реализация службы калькулятора.</span><span class="sxs-lookup"><span data-stu-id="04c0e-108">This is a simple calculator service implementation.</span></span> <span data-ttu-id="04c0e-109">Код обнаружения можно найти в `Main`, где к узлу службы добавляется <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> и добавляется <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="04c0e-109">The discovery related code can be found in `Main` where a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is added to the service host and a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is added as shown in the following code.</span></span>  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new   
      WSHttpBinding(), String.Empty);  
  
    // Make the service discoverable over UDP multicast  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a><span data-ttu-id="04c0e-110">Клиент</span><span class="sxs-lookup"><span data-stu-id="04c0e-110">Client</span></span>  
 <span data-ttu-id="04c0e-111">Клиент использует <xref:System.ServiceModel.Discovery.DynamicEndpoint> для определения местоположения службы.</span><span class="sxs-lookup"><span data-stu-id="04c0e-111">The client uses a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to locate the service.</span></span> <span data-ttu-id="04c0e-112">Стандартная конечная точка <xref:System.ServiceModel.Discovery.DynamicEndpoint> вычисляет конечную точку службы, когда открывается клиент.</span><span class="sxs-lookup"><span data-stu-id="04c0e-112">The <xref:System.ServiceModel.Discovery.DynamicEndpoint>, a standard endpoint, resolves the endpoint of the service when the client is opened.</span></span> <span data-ttu-id="04c0e-113">В этом случае <xref:System.ServiceModel.Discovery.DynamicEndpoint> ищет службу на основе контракта службы.</span><span class="sxs-lookup"><span data-stu-id="04c0e-113">In this case, the <xref:System.ServiceModel.Discovery.DynamicEndpoint> looks for the service based on the service contract.</span></span> <span data-ttu-id="04c0e-114">Конечная точка <xref:System.ServiceModel.Discovery.DynamicEndpoint> ведет поиск по <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="04c0e-114">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> conducts the search over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> by default.</span></span> <span data-ttu-id="04c0e-115">Когда конечная точка службы найдена, клиент подключается к этой службе по заданной привязке.</span><span class="sxs-lookup"><span data-stu-id="04c0e-115">Once it locates a service endpoint, the client connects to that service over the specified binding.</span></span>  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 <span data-ttu-id="04c0e-116">Клиент определяет метод `InvokeCalculatorService`, который использует класс <xref:System.ServiceModel.Discovery.DiscoveryClient> для поиска служб.</span><span class="sxs-lookup"><span data-stu-id="04c0e-116">The client defines a method called `InvokeCalculatorService` that uses the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to search for services.</span></span> <span data-ttu-id="04c0e-117">Класс <xref:System.ServiceModel.Discovery.DynamicEndpoint> наследует от класса <xref:System.ServiceModel.Description.ServiceEndpoint>, чтобы он мог быть передан в метод `InvokeCalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="04c0e-117">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> inherits from <xref:System.ServiceModel.Description.ServiceEndpoint>, so it can be passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="04c0e-118">В примере затем используется конечная точка <xref:System.ServiceModel.Discovery.DynamicEndpoint> для создания экземпляра `CalculatorServiceClient` и вызываются различные операции службы калькулятора.</span><span class="sxs-lookup"><span data-stu-id="04c0e-118">The example then uses the <xref:System.ServiceModel.Discovery.DynamicEndpoint> to create an instance of `CalculatorServiceClient` and calls the various operations of the calculator service.</span></span>  
  
```csharp  
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)  
{  
   // Create a client  
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);  
  
   Console.WriteLine("Invoking CalculatorService");  
   Console.WriteLine();  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Subtract service operation.  
   result = client.Subtract(value1, value2);  
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Multiply service operation.  
   result = client.Multiply(value1, value2);  
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Divide service operation.  
   result = client.Divide(value1, value2);  
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
   Console.WriteLine();  
  
   //Closing the client gracefully closes the connection and cleans up resources  
   client.Close();  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="04c0e-119">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="04c0e-119">To use this sample</span></span>  
  
1. <span data-ttu-id="04c0e-120">В этом образце используются конечные точки HTTP, и для работы этого образца необходимо добавить соответствующие списки управления доступом по URL-адресу.</span><span class="sxs-lookup"><span data-stu-id="04c0e-120">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="04c0e-121">Дополнительные сведения см. в разделе [Настройка HTTP и HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="04c0e-121">For more information, see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="04c0e-122">Нужные списки управления доступом будут добавлены после выполнения следующей команды с повышенными привилегиями.</span><span class="sxs-lookup"><span data-stu-id="04c0e-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="04c0e-123">Если команда не работает, следует указать домен и имя пользователя в следующих аргументах.</span><span class="sxs-lookup"><span data-stu-id="04c0e-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="04c0e-124">С помощью Visual Studio 2012 откройте файл Basic. sln и создайте пример.</span><span class="sxs-lookup"><span data-stu-id="04c0e-124">Using Visual Studio 2012, open the Basic.sln and build the sample.</span></span>  
  
3. <span data-ttu-id="04c0e-125">Запустите приложение service.exe.</span><span class="sxs-lookup"><span data-stu-id="04c0e-125">Run the service.exe application.</span></span>  
  
4. <span data-ttu-id="04c0e-126">После запуска службы запустите client.exe.</span><span class="sxs-lookup"><span data-stu-id="04c0e-126">After the service has started, run the client.exe.</span></span>  
  
5. <span data-ttu-id="04c0e-127">Заметьте, что клиенту удалось найти службу, не зная ее адреса.</span><span class="sxs-lookup"><span data-stu-id="04c0e-127">Observe that the client was able to find the service without knowing its address.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="04c0e-128">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="04c0e-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="04c0e-129">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="04c0e-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="04c0e-130">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] и примеры.</span><span class="sxs-lookup"><span data-stu-id="04c0e-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="04c0e-131">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="04c0e-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
