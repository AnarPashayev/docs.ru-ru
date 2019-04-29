---
title: Маршрутизация по телу сообщения
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: b8a3f7785d7d59d8ad85d6dddde7fd6a04a12d63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787560"
---
# <a name="route-by-body"></a><span data-ttu-id="2d309-102">Маршрутизация по телу сообщения</span><span class="sxs-lookup"><span data-stu-id="2d309-102">Route by Body</span></span>
<span data-ttu-id="2d309-103">В этом образце показано, как реализовать службу, которая принимает объекты сообщений с действием SOAP.</span><span class="sxs-lookup"><span data-stu-id="2d309-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="2d309-104">Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md) , реализующем службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="2d309-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="2d309-105">Служба реализует одну операцию `Calculate`, которая принимает параметр запроса <xref:System.ServiceModel.Channels.Message> и возвращает ответ <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="2d309-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="2d309-106">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="2d309-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d309-107">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="2d309-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2d309-108">Этот образец демонстрирует диспетчеризацию сообщений на основе содержимого тела сообщения.</span><span class="sxs-lookup"><span data-stu-id="2d309-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="2d309-109">Встроенный механизм диспетчеризации модели службы Windows Communication Foundation (WCF) сообщение зависит от сообщения действия.</span><span class="sxs-lookup"><span data-stu-id="2d309-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="2d309-110">Однако есть много существующих веб-служб, которые для всех своих операций определяют параметр Action="".</span><span class="sxs-lookup"><span data-stu-id="2d309-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="2d309-111">Невозможно построить службу на основе кода WSDL, когда диспетчеризация сообщений запросов осуществляется на основе параметра Action.</span><span class="sxs-lookup"><span data-stu-id="2d309-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="2d309-112">В этом образце показан контракт службы, основанный на коде WSDL (код WSDL содержится в файле Service.wsdl, который входит в этот образец).</span><span class="sxs-lookup"><span data-stu-id="2d309-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="2d309-113">Контракт службы-Calculator, подобной той, используемых в [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2d309-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="2d309-114">Однако контракт `[OperationContract]` задает для всех операций `Action=""`.</span><span class="sxs-lookup"><span data-stu-id="2d309-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="2d309-115">Чтобы при таком контракте можно было распределять сообщения между операциями, службе требуется пользовательское поведение диспетчеризации `DispatchByBodyBehavior`.</span><span class="sxs-lookup"><span data-stu-id="2d309-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="2d309-116">Это поведение отправки инициализирует `DispatchByBodyElementOperationSelector` пользовательский селектор операций с таблицей имен операций, обозначенных с помощью значений QName соответствующих элементов оболочек.</span><span class="sxs-lookup"><span data-stu-id="2d309-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="2d309-117">Операция `DispatchByBodyElementOperationSelector` проверяет начальный тег первого дочернего элемента Body и выбирает операцию, используя упомянутую ранее таблицу.</span><span class="sxs-lookup"><span data-stu-id="2d309-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="2d309-118">Клиент использует прокси-сервера, автоматически создается из кода WSDL, экспортированного службой с помощью [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2d309-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="2d309-119">Тот факт, что параметры Action всех операций пусты, не влияет на клиентский код, не считая параметров Action автоматически созданного прокси.</span><span class="sxs-lookup"><span data-stu-id="2d309-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="2d309-120">Клиентский код выполняет несколько вычислений.</span><span class="sxs-lookup"><span data-stu-id="2d309-120">The client code performs several calculations.</span></span> <span data-ttu-id="2d309-121">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="2d309-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2d309-122">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="2d309-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2d309-123">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="2d309-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2d309-124">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d309-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2d309-125">Чтобы построить решение, следуйте инструкциям в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d309-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2d309-126">Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d309-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2d309-127">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="2d309-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2d309-128">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="2d309-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2d309-129">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="2d309-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2d309-130">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="2d309-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
