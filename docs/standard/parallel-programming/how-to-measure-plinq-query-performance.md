---
title: Практическое руководство. Измерение производительности запросов PLINQ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 43f83a34531b853d108785052f637d9568c45280
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826883"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="76720-102">Практическое руководство. Измерение производительности запросов PLINQ</span><span class="sxs-lookup"><span data-stu-id="76720-102">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="76720-103">В этом примере показано, как использовать класс <xref:System.Diagnostics.Stopwatch> для измерения времени, необходимого для выполнения запроса PLINQ.</span><span class="sxs-lookup"><span data-stu-id="76720-103">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76720-104">Пример</span><span class="sxs-lookup"><span data-stu-id="76720-104">Example</span></span>  
 <span data-ttu-id="76720-105">В этом примере для измерения времени, необходимого для выполнения запроса, используется пустой цикл `foreach` (`For Each` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="76720-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="76720-106">На практике цикл обычно содержит дополнительные этапы обработки, увеличивающие общее время выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="76720-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="76720-107">Обратите внимание, что секундомер запускается только перед началом цикла, так как именно в это время начинается выполнение запроса.</span><span class="sxs-lookup"><span data-stu-id="76720-107">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="76720-108">Если вам требуется более точное измерение, вместо `ElapsedMilliseconds` можно использовать свойство `ElapsedTicks`.</span><span class="sxs-lookup"><span data-stu-id="76720-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="76720-109">Общее время выполнения служит полезным показателем в экспериментах с реализациями запроса, но не всегда раскрывает общую картину.</span><span class="sxs-lookup"><span data-stu-id="76720-109">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="76720-110">Более глубокое и полное представление о взаимодействии потоков запроса друг с другом и с другими запущенными процессами можно получить, используя [визуализатор параллелизма](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="76720-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76720-111">См. также</span><span class="sxs-lookup"><span data-stu-id="76720-111">See also</span></span>

- [<span data-ttu-id="76720-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="76720-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
