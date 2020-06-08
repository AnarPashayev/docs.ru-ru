---
title: Практическое руководство. Использование объекта SpinWait для реализации двухэтапной операции ожидания
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: 4b2bc79a7b652c34334d5a78d9c9af328993ff44
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279210"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="d3fad-102">Практическое руководство. Использование объекта SpinWait для реализации двухэтапной операции ожидания</span><span class="sxs-lookup"><span data-stu-id="d3fad-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="d3fad-103">В примере ниже показано, как использовать объект <xref:System.Threading.SpinWait?displayProperty=nameWithType> для реализации двухэтапной операции ожидания.</span><span class="sxs-lookup"><span data-stu-id="d3fad-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="d3fad-104">На первом этапе объект синхронизации `Latch` выполняет несколько циклов, в которых проверяет доступность блокировки.</span><span class="sxs-lookup"><span data-stu-id="d3fad-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="d3fad-105">На втором этапе, если блокировка стала доступной, метод `Wait` возвращается, не вызывая <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> для ожидания. В противном случае `Wait` выполняет операцию ожидания.</span><span class="sxs-lookup"><span data-stu-id="d3fad-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3fad-106">Пример</span><span class="sxs-lookup"><span data-stu-id="d3fad-106">Example</span></span>  
 <span data-ttu-id="d3fad-107">Этот пример содержит простейшую реализацию примитива синхронизации с кратковременной блокировкой.</span><span class="sxs-lookup"><span data-stu-id="d3fad-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="d3fad-108">Вы можете применить такую структуру данных, если время ожидания должно быть очень коротким.</span><span class="sxs-lookup"><span data-stu-id="d3fad-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="d3fad-109">Этот пример приведен только в качестве демонстрации.</span><span class="sxs-lookup"><span data-stu-id="d3fad-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="d3fad-110">Если для вашей программы нужна функция кратковременной блокировки, мы рекомендуем применить <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d3fad-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="d3fad-111">Кратковременная блокировка использует объект <xref:System.Threading.SpinWait>, чтобы оставаться в цикле ожидания, пока очередной вызов `SpinOnce` не вынудит <xref:System.Threading.SpinWait> приостановить процесс и освободить временной интервал потока.</span><span class="sxs-lookup"><span data-stu-id="d3fad-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="d3fad-112">В этот момент кратковременная блокировка осуществляет переключение контекста, вызвав <xref:System.Threading.WaitHandle.WaitOne%2A> для <xref:System.Threading.ManualResetEvent>, которому передает значение оставшегося времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="d3fad-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="d3fad-113">Выходные данные журнала позволят понять, как часто кратковременная блокировка позволяет повысить производительность, реализуя блокировку без использования <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="d3fad-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3fad-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d3fad-114">See also</span></span>

- [<span data-ttu-id="d3fad-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="d3fad-115">SpinWait</span></span>](spinwait.md)
- [<span data-ttu-id="d3fad-116">Объекты и функциональные возможности работы с потоками</span><span class="sxs-lookup"><span data-stu-id="d3fad-116">Threading Objects and Features</span></span>](threading-objects-and-features.md)
