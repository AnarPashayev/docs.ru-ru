---
title: Помощник по отладке управляемого кода fatalExecutionEngineError
ms.date: 03/30/2017
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87094532a52d8f6309998486375ef4eb33b07f20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189395"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="b3c50-102">Помощник по отладке управляемого кода fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="b3c50-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="b3c50-103">Помощник по отладке управляемого кода `fatalExecutionEngineError` (MDA) активируется при обнаружении неустранимой ошибки в общеязыковой среде выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="b3c50-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="b3c50-104">В этом случае процесс завершается.</span><span class="sxs-lookup"><span data-stu-id="b3c50-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b3c50-105">Симптомы</span><span class="sxs-lookup"><span data-stu-id="b3c50-105">Symptoms</span></span>  
 <span data-ttu-id="b3c50-106">Непредвиденное завершение процесса.</span><span class="sxs-lookup"><span data-stu-id="b3c50-106">Unexpected process termination.</span></span> <span data-ttu-id="b3c50-107">Другие признаки определить невозможно, поскольку сбой среды CLR может происходить по самым разным причинам.</span><span class="sxs-lookup"><span data-stu-id="b3c50-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b3c50-108">Причина</span><span class="sxs-lookup"><span data-stu-id="b3c50-108">Cause</span></span>  
 <span data-ttu-id="b3c50-109">Неустранимое повреждение среды CLR.</span><span class="sxs-lookup"><span data-stu-id="b3c50-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="b3c50-110">Чаще всего это вызвано повреждением данных, которое может быть связано с целым рядом проблем, таких как вызовы некорректных функций вызова неуправляемого кода и передача недопустимых данных в среду CLR.</span><span class="sxs-lookup"><span data-stu-id="b3c50-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b3c50-111">Решение</span><span class="sxs-lookup"><span data-stu-id="b3c50-111">Resolution</span></span>  
 <span data-ttu-id="b3c50-112">Чтобы определить причины проблемы, попробуйте включить другие помощники по отладке управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="b3c50-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="b3c50-113">При диагностике вам могут помочь следующие помощники по отладке управляемого кода:</span><span class="sxs-lookup"><span data-stu-id="b3c50-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="b3c50-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="b3c50-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="b3c50-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="b3c50-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="b3c50-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="b3c50-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="b3c50-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="b3c50-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="b3c50-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="b3c50-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="b3c50-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="b3c50-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="b3c50-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="b3c50-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="b3c50-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="b3c50-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="b3c50-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="b3c50-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="b3c50-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="b3c50-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="b3c50-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="b3c50-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="b3c50-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="b3c50-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b3c50-126">Влияние на среду выполнения</span><span class="sxs-lookup"><span data-stu-id="b3c50-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="b3c50-127">Этот помощник по отладке управляемого кода не оказывает влияния на поведение среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="b3c50-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b3c50-128">Вывод</span><span class="sxs-lookup"><span data-stu-id="b3c50-128">Output</span></span>  
 <span data-ttu-id="b3c50-129">Адрес функции среды CLR, которая стала причиной неустранимой ошибки, идентификатор потока, в котором произошла ошибка, а также код самой ошибки.</span><span class="sxs-lookup"><span data-stu-id="b3c50-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b3c50-130">Параметр Configuration</span><span class="sxs-lookup"><span data-stu-id="b3c50-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3c50-131">См. также</span><span class="sxs-lookup"><span data-stu-id="b3c50-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="b3c50-132">Диагностика ошибок посредством управляемых помощников по отладке</span><span class="sxs-lookup"><span data-stu-id="b3c50-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
