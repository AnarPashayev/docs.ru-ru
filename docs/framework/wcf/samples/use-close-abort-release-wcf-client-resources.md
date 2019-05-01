---
title: Использование Close и Abort для освобождения ресурсов клиента WCF
description: Dispose может завершиться ошибкой и вызывать исключения при сбое сети. Что может вызвать нежелательное поведение. Вместо этого используйте Close и Abort для освобождения ресурсов клиента, при сбое сети.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 58f828d9cd85806f5f04c349a7de18828ab5f6f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007582"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="2c16a-105">Close и Abort освобождение ресурсов безопасно в том случае, когда были удалены сетевых подключений</span><span class="sxs-lookup"><span data-stu-id="2c16a-105">Close and Abort release resources safely when network connections have dropped</span></span>

<span data-ttu-id="2c16a-106">Этот пример демонстрирует применение `Close` и `Abort` методы для очистки ресурсов при использовании типизированного клиента.</span><span class="sxs-lookup"><span data-stu-id="2c16a-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="2c16a-107">`using` Инструкция вызывает исключения, если сетевое подключение не является надежной.</span><span class="sxs-lookup"><span data-stu-id="2c16a-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="2c16a-108">Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md) , реализующем службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="2c16a-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="2c16a-109">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="2c16a-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="2c16a-110">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="2c16a-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="2c16a-111">В этом образце показаны две общие проблемы, которые могут возникнуть при использовании оператора "using" в C# с типизированными клиентами, а также код, который правильно выполняет очистку после исключений.</span><span class="sxs-lookup"><span data-stu-id="2c16a-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>

<span data-ttu-id="2c16a-112">Оператор "using" в C# приводит к вызову метода `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="2c16a-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="2c16a-113">Этот метод эквивалентен методу `Close`(), который может выдавать исключения при возникновении сетевой ошибки.</span><span class="sxs-lookup"><span data-stu-id="2c16a-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="2c16a-114">Поскольку вызов метода `Dispose`() выполняется неявно в закрывающей круглой скобке блока "using", этот источник исключений, скорее всего, останется незамеченным как теми, кто пишет код, так и теми, кто его считывает.</span><span class="sxs-lookup"><span data-stu-id="2c16a-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="2c16a-115">Он представляет собой потенциальный источник ошибок приложения.</span><span class="sxs-lookup"><span data-stu-id="2c16a-115">This represents a potential source of application errors.</span></span>

<span data-ttu-id="2c16a-116">Первая проблема, показанная в методе `DemonstrateProblemUsingCanThrow`, заключается в том, что закрывающая круглая скобка выдает исключение, а код после закрывающей круглой скобки не выполняет следующее.</span><span class="sxs-lookup"><span data-stu-id="2c16a-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

<span data-ttu-id="2c16a-117">Даже если ничего в блоке "using" не выдает исключения или все исключения в блоке "using" перехватываются, `Console.WriteLine` может не произойти, поскольку неявный вызов метода `Dispose`() в закрывающей круглой скобке может выдать исключение.</span><span class="sxs-lookup"><span data-stu-id="2c16a-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.WriteLine` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>

<span data-ttu-id="2c16a-118">Вторая проблема, показанная в методе `DemonstrateProblemUsingCanThrowAndMask`, представляет собой еще одно последствие использования закрывающей круглой скобки, выдающей исключение.</span><span class="sxs-lookup"><span data-stu-id="2c16a-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

<span data-ttu-id="2c16a-119">Поскольку метод `Dispose`() происходит в блоке "finally", исключение `ApplicationException` никогда не видно за пределами блока "using", если метод `Dispose`() выполняется с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="2c16a-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="2c16a-120">Если внешний код должен знать, когда происходит исключение `ApplicationException`, конструкция "using" может стать причиной возникновения проблем, маскируя это исключение.</span><span class="sxs-lookup"><span data-stu-id="2c16a-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>

<span data-ttu-id="2c16a-121">Наконец, в этом образце показано, как правильно выполнить очистку, если исключения происходят в `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="2c16a-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="2c16a-122">При этом используется блок try/catch для сообщения об ошибках и вызова метода `Abort`.</span><span class="sxs-lookup"><span data-stu-id="2c16a-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="2c16a-123">См. в разделе [ожидается исключения](../../../../docs/framework/wcf/samples/expected-exceptions.md) Дополнительные сведения о перехвате исключений из вызовов клиента.</span><span class="sxs-lookup"><span data-stu-id="2c16a-123">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>

```csharp
try
{
    ...
    client.Close();
}
catch (CommunicationException e)
{
    ...
    client.Abort();
}
catch (TimeoutException e)
{
    ...
    client.Abort();
}
catch (Exception e)
{
    ...
    client.Abort();
    throw;
}
```

> [!NOTE]
> <span data-ttu-id="2c16a-124">С помощью инструкции и ServiceHost: Большинство резидентных приложений чуть более размещения службы, а метод ServiceHost.Close редко выдает исключение, поэтому такие приложения могут безопасно использовать с помощью инструкции с ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="2c16a-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="2c16a-125">Однако необходимо помнить, что метод ServiceHost.Close может выдать исключение `CommunicationException`, поэтому если приложение продолжает работать после закрытия ServiceHost, следует избегать использования оператора "using" и следовать шаблону, указанному ранее.</span><span class="sxs-lookup"><span data-stu-id="2c16a-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>

<span data-ttu-id="2c16a-126">При выполнении образца ответы и исключения операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="2c16a-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>

<span data-ttu-id="2c16a-127">Клиентский процесс выполняет три сценария, каждый из которых пытается вызвать метод `Divide`.</span><span class="sxs-lookup"><span data-stu-id="2c16a-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="2c16a-128">В первом сценарии показан код, пропущенный из-за исключения, выданного методом `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="2c16a-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="2c16a-129">Во втором сценарии показано важное исключение с маской из-за исключения, выданного методом `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="2c16a-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="2c16a-130">В третьем сценарии показана правильная очистка.</span><span class="sxs-lookup"><span data-stu-id="2c16a-130">The third scenario demonstrates correct clean up.</span></span>

<span data-ttu-id="2c16a-131">Ниже представлен ожидаемый результат выполнения клиентского процесса.</span><span class="sxs-lookup"><span data-stu-id="2c16a-131">The expected output from the client process is:</span></span>

```
=
= Demonstrating problem:  closing brace of using statement can throw.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.
=
Got System.ServiceModel.CommunicationException from Divide.
Got System.ServiceModel.Security.MessageSecurityException
=
= Demonstrating cleanup with Exceptions.
=
Calling client.Add(0.0, 0.0);
        client.Add(0.0, 0.0); returned 0
Calling client.Divide(0.0, 0.0);
Got System.ServiceModel.CommunicationException from Divide.

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2c16a-132">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="2c16a-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2c16a-133">Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2c16a-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="2c16a-134">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2c16a-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="2c16a-135">Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2c16a-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c16a-136">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="2c16a-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2c16a-137">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="2c16a-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2c16a-138">Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="2c16a-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c16a-139">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="2c16a-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
