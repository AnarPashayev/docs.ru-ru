---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: cd7e97559458a4415399488b0fdb96a850033c44
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59294838"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="18f4b-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="18f4b-102">NetNamedPipeBinding</span></span>
<span data-ttu-id="18f4b-103">В этом образце показана привязка `netNamedPipeBinding`, обеспечивающая обмен данными между процессами одного компьютера.</span><span class="sxs-lookup"><span data-stu-id="18f4b-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="18f4b-104">Использование именованных каналов для обмена данными между компьютерами не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="18f4b-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="18f4b-105">Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md) службы калькулятора.</span><span class="sxs-lookup"><span data-stu-id="18f4b-105">This sample is based on The [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="18f4b-106">В этом образце служба является резидентной.</span><span class="sxs-lookup"><span data-stu-id="18f4b-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="18f4b-107">И клиент, и служба являются консольными приложениями.</span><span class="sxs-lookup"><span data-stu-id="18f4b-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18f4b-108">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="18f4b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="18f4b-109">Привязка задается в файлах конфигурации для клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="18f4b-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="18f4b-110">Тип привязки задается в `binding` атрибут [ \<конечной точки >](../../configure-apps/file-schema/wcf/endpoint-element.md) или [ \<конечной точки > из \<клиента >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) элемента, как показано на Следующий пример конфигурации:</span><span class="sxs-lookup"><span data-stu-id="18f4b-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="18f4b-111">В предыдущем примере показано, как настроить конечную точку для использования привязки `netNamedPipeBinding` с параметрами по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="18f4b-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="18f4b-112">Чтобы настроить привязку `netNamedPipeBinding` и изменить некоторые ее параметры, необходимо определить конфигурацию привязки.</span><span class="sxs-lookup"><span data-stu-id="18f4b-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="18f4b-113">Конечная точка должна ссылаться на конфигурацию привязки по имени с атрибутом `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="18f4b-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="18f4b-114">В этом образце конфигурация привязки называется `Binding1` и имеет следующее определение.</span><span class="sxs-lookup"><span data-stu-id="18f4b-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"   
             maxConnections="10"   
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 <span data-ttu-id="18f4b-115">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="18f4b-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="18f4b-116">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="18f4b-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="18f4b-117">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="18f4b-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="18f4b-118">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18f4b-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="18f4b-119">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18f4b-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="18f4b-120">Чтобы выполнить образец на одном компьютере, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18f4b-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="18f4b-121">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="18f4b-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="18f4b-122">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="18f4b-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="18f4b-123">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="18f4b-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18f4b-124">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="18f4b-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
