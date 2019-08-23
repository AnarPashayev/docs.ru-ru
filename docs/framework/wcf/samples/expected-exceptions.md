---
title: Ожидаемые исключения
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 7611b070df31b7a0997a94c07594716ee264af5e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961599"
---
# <a name="expected-exceptions"></a><span data-ttu-id="49eb2-102">Ожидаемые исключения</span><span class="sxs-lookup"><span data-stu-id="49eb2-102">Expected Exceptions</span></span>
<span data-ttu-id="49eb2-103">В этом образце показано, как перехватывать ожидаемые исключения при использовании типизированного клиента.</span><span class="sxs-lookup"><span data-stu-id="49eb2-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="49eb2-104">Этот образец основан на [Начало работы](../../../../docs/framework/wcf/samples/getting-started-sample.md) , который реализует службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="49eb2-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="49eb2-105">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="49eb2-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49eb2-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="49eb2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="49eb2-107">В этом образце показано кэширование и обработка ожидаемых исключений двух типов, которые должны обрабатываться правильно работающими программами: `TimeoutException` и `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="49eb2-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="49eb2-108">Исключения, вызванные методами связи в клиенте Windows Communication Foundation (WCF), являются ожидаемыми или непредвиденными.</span><span class="sxs-lookup"><span data-stu-id="49eb2-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="49eb2-109">Неожиданные исключения включают разрушительный сбой, например `OutOfMemoryException`, и ошибки программирования, например `ArgumentNullException` или `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="49eb2-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="49eb2-110">Обычно не существует удобного способа решения непредвиденных ошибок, поэтому обычно не следует перехватывать их при вызове метода связи клиента WCF.</span><span class="sxs-lookup"><span data-stu-id="49eb2-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="49eb2-111">Ожидаемые исключения из методов связи в клиенте WCF `TimeoutException`включают `CommunicationException`, `CommunicationException`и любой производный класс.</span><span class="sxs-lookup"><span data-stu-id="49eb2-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="49eb2-112">Они указывают на проблему во время обмена данными, которая может быть безопасно обработана путем прерывания работы клиента WCF и сообщения об ошибке связи.</span><span class="sxs-lookup"><span data-stu-id="49eb2-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="49eb2-113">Поскольку внешние факторы могут вызывать появление таких ошибок в любом приложении, правильно разработанные приложения должны перехватывать эти исключения и предпринимать соответствующие восстановительные меры.</span><span class="sxs-lookup"><span data-stu-id="49eb2-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="49eb2-114">Имеется несколько классов, производных от `CommunicationException`, которые могут создаваться клиентом.</span><span class="sxs-lookup"><span data-stu-id="49eb2-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="49eb2-115">В некоторых случаях приложение может также перехватывать определенные исключения, чтобы выполнять специальную обработку, и обрабатывать оставшиеся исключения как исключения типа `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="49eb2-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="49eb2-116">Чтобы реализовать это, необходимо в первую очередь перехватывать более узкие виды исключений, а лишь затем перехватывать исключение `CommunicationException` в более позднем предложении catch.</span><span class="sxs-lookup"><span data-stu-id="49eb2-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="49eb2-117">Код, вызывающий методы взаимодействия, должен перехватывать исключения `TimeoutException` и `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="49eb2-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="49eb2-118">Один из способов обработки таких ошибок заключается в прерывании работы клиента и создании сообщения о сбое взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="49eb2-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp   
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="49eb2-119">Если происходит ожидаемое исключение, клиент может стать или не стать непригодным к использованию в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="49eb2-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="49eb2-120">Чтобы определить, можно ли использовать клиент, проверьте, что свойство `State` имеет значение `CommunicationState`.Opened.</span><span class="sxs-lookup"><span data-stu-id="49eb2-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="49eb2-121">Если свойство имеет значение Opened, клиент можно использовать.</span><span class="sxs-lookup"><span data-stu-id="49eb2-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="49eb2-122">В противном случае необходимо прервать работу клиента и освободить все ссылки на него.</span><span class="sxs-lookup"><span data-stu-id="49eb2-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="49eb2-123">Можно заметить, что клиенты с сеансом невозможно использовать после возникновения исключения, а клиенты без сеансов использовать после исключения можно.</span><span class="sxs-lookup"><span data-stu-id="49eb2-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="49eb2-124">Однако это не является универсальным правилом, поэтому если требуется продолжать использовать клиент после исключения, приложение должно проверить значение свойства `State`, чтобы убедиться, что клиент еще открыт.</span><span class="sxs-lookup"><span data-stu-id="49eb2-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="49eb2-125">При выполнении образца ответы и исключения операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="49eb2-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="49eb2-126">Клиентский процесс выполняет два сценария, каждый из которых пытается выполнить операцию `Add`, а затем операцию `Divide`.</span><span class="sxs-lookup"><span data-stu-id="49eb2-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="49eb2-127">Первый сценарий имитирует сбой в работе сети путем прерывания работы клиента перед вызовом `Divide`.</span><span class="sxs-lookup"><span data-stu-id="49eb2-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="49eb2-128">Второй сценарий вызывает возникновение таймаута путем задания слишком короткого времени ожидания завершения метода.</span><span class="sxs-lookup"><span data-stu-id="49eb2-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="49eb2-129">Ниже представлен ожидаемый результат выполнения клиентского процесса.</span><span class="sxs-lookup"><span data-stu-id="49eb2-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="49eb2-130">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="49eb2-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="49eb2-131">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49eb2-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="49eb2-132">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49eb2-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="49eb2-133">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49eb2-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="49eb2-134">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="49eb2-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="49eb2-135">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="49eb2-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="49eb2-136">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] и примеры.</span><span class="sxs-lookup"><span data-stu-id="49eb2-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="49eb2-137">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="49eb2-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
