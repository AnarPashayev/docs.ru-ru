---
title: dangerousThreadingAPI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46b0add67fc6bc139ef02e09190670870749d4c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218307"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="6e987-102">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="6e987-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="6e987-103">Помощник по отладке управляемого кода `dangerousThreadingAPI` (MDA) активируется, если метод <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> вызывается не для текущего потока.</span><span class="sxs-lookup"><span data-stu-id="6e987-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6e987-104">Симптомы</span><span class="sxs-lookup"><span data-stu-id="6e987-104">Symptoms</span></span>  
 <span data-ttu-id="6e987-105">Приложение не отвечает или зависает на неопределенное время.</span><span class="sxs-lookup"><span data-stu-id="6e987-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="6e987-106">Данные системы или приложения могут остаться в непредсказуемом состоянии на какое-то время или даже после завершения работы приложения.</span><span class="sxs-lookup"><span data-stu-id="6e987-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="6e987-107">Некоторые операции не завершаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="6e987-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="6e987-108">Из-за случайного характера возникновения этой проблемы ее симптомы могут быть самыми разными.</span><span class="sxs-lookup"><span data-stu-id="6e987-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6e987-109">Причина</span><span class="sxs-lookup"><span data-stu-id="6e987-109">Cause</span></span>  
 <span data-ttu-id="6e987-110">Поток асинхронно приостанавливается другим потоком, использующим метод <xref:System.Threading.Thread.Suspend%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e987-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="6e987-111">Определить, безопасно ли приостанавливать другой поток, который в текущий момент времени может выполнять другие операции, невозможно.</span><span class="sxs-lookup"><span data-stu-id="6e987-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="6e987-112">Приостановка потока может привести к повреждению данных или нарушению инвариантов.</span><span class="sxs-lookup"><span data-stu-id="6e987-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="6e987-113">Если поток приостанавливается и впоследствии не возобновляется с помощью метода <xref:System.Threading.Thread.Resume%2A>, приложение может зависнуть на неопределенное время, что может привести к повреждению его данных.</span><span class="sxs-lookup"><span data-stu-id="6e987-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="6e987-114">Эти методы помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="6e987-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="6e987-115">Если целевой поток удерживает примитивы синхронизации, они остаются в этом состоянии на протяжении всего времени приостановки.</span><span class="sxs-lookup"><span data-stu-id="6e987-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="6e987-116">Это может привести к взаимоблокировкам в тех случаях, когда другой поток, например поток, выполняющий <xref:System.Threading.Thread.Suspend%2A>, пытается получить блокировку примитива.</span><span class="sxs-lookup"><span data-stu-id="6e987-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="6e987-117">В этой ситуации проблема проявляется в виде взаимоблокировки.</span><span class="sxs-lookup"><span data-stu-id="6e987-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6e987-118">Решение</span><span class="sxs-lookup"><span data-stu-id="6e987-118">Resolution</span></span>  
 <span data-ttu-id="6e987-119">По возможности не используйте в коде методы <xref:System.Threading.Thread.Suspend%2A> и <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e987-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="6e987-120">Чтобы обеспечить взаимодействие между потоками, используйте примитивы синхронизации, например <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex> или оператор `lock` C#.</span><span class="sxs-lookup"><span data-stu-id="6e987-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="6e987-121">Если эти методы все же необходимо использовать, постарайтесь свести к минимуму продолжительность приостановки потока и объем кода, выполняемого в это время.</span><span class="sxs-lookup"><span data-stu-id="6e987-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6e987-122">Влияние на среду выполнения</span><span class="sxs-lookup"><span data-stu-id="6e987-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="6e987-123">Этот помощник отладки управляемого кода не оказывает никакого влияния на среду CLR.</span><span class="sxs-lookup"><span data-stu-id="6e987-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="6e987-124">Он только сообщает сведения о небезопасных потоковых операциях.</span><span class="sxs-lookup"><span data-stu-id="6e987-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6e987-125">Вывод</span><span class="sxs-lookup"><span data-stu-id="6e987-125">Output</span></span>  
 <span data-ttu-id="6e987-126">Этот помощник идентифицирует небезопасный потоковый метод, который стал причиной его активации.</span><span class="sxs-lookup"><span data-stu-id="6e987-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6e987-127">Параметр Configuration</span><span class="sxs-lookup"><span data-stu-id="6e987-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="6e987-128">Пример</span><span class="sxs-lookup"><span data-stu-id="6e987-128">Example</span></span>  
 <span data-ttu-id="6e987-129">В следующем примере кода демонстрируется вызов метода <xref:System.Threading.Thread.Suspend%2A>, в результате которого активируется помощник `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="6e987-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();   
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e987-130">См. также</span><span class="sxs-lookup"><span data-stu-id="6e987-130">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="6e987-131">Диагностика ошибок посредством помощников по отладке управляемого кода</span><span class="sxs-lookup"><span data-stu-id="6e987-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="6e987-132">Оператор lock</span><span class="sxs-lookup"><span data-stu-id="6e987-132">lock Statement</span></span>](~/docs/csharp/language-reference/keywords/lock-statement.md)
