---
title: Практическое руководство. Отмена цикла Parallel.For или Parallel.ForEach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: d29137127dd47844f8f08d3ac689cf2827d9efe2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288229"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="b56dc-102">Практическое руководство. Отмена цикла Parallel.For или Parallel.ForEach</span><span class="sxs-lookup"><span data-stu-id="b56dc-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="b56dc-103">Метод <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> и <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> поддерживают отмену с применением маркеров отмены.</span><span class="sxs-lookup"><span data-stu-id="b56dc-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="b56dc-104">Дополнительные сведения о механизмах отмены в целом см. в [этой статье](../threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="b56dc-104">For more information about cancellation in general, see [Cancellation](../threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="b56dc-105">В параллельном цикле <xref:System.Threading.CancellationToken> передается в методу через параметр <xref:System.Threading.Tasks.ParallelOptions>, и этот параллельный вызов заключен в блок try-catch.</span><span class="sxs-lookup"><span data-stu-id="b56dc-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b56dc-106">Пример</span><span class="sxs-lookup"><span data-stu-id="b56dc-106">Example</span></span>  
 <span data-ttu-id="b56dc-107">Следующий пример демонстрирует, как отменить вызов <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b56dc-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b56dc-108">Этот же подход вы можете применить и к вызову <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b56dc-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="b56dc-109">Если маркер, сообщающий об отмене, совпадает с указанным в экземпляре <xref:System.Threading.Tasks.ParallelOptions>маркером, то параллельный цикл создаст для отмены одно исключение <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="b56dc-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="b56dc-110">Если отмена вызвана другим маркером, цикл создаст исключение <xref:System.AggregateException> и вложит в него <xref:System.OperationCanceledException> в качестве значения InnerException.</span><span class="sxs-lookup"><span data-stu-id="b56dc-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b56dc-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b56dc-111">See also</span></span>

- [<span data-ttu-id="b56dc-112">Параллелизм данных</span><span class="sxs-lookup"><span data-stu-id="b56dc-112">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="b56dc-113">Лямбда-выражения в PLINQ и TPL</span><span class="sxs-lookup"><span data-stu-id="b56dc-113">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
