---
title: Практическое руководство. Добавление и удаление отдельных элементов коллекции BlockingCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: 3f4270d2ec71421bad8974a3e5cd8f1d65db3b74
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711302"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="d8150-102">Практическое руководство. Добавление и удаление отдельных элементов коллекции BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="d8150-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="d8150-103">В этом примере показано, как добавлять и удалять элементы <xref:System.Collections.Concurrent.BlockingCollection%601> с блокировкой и без блокировки.</span><span class="sxs-lookup"><span data-stu-id="d8150-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="d8150-104">Дополнительные сведения о <xref:System.Collections.Concurrent.BlockingCollection%601> см. в разделе [Общие сведения о коллекции BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d8150-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="d8150-105">Пример перечисления коллекции <xref:System.Collections.Concurrent.BlockingCollection%601>, пока она не станет пустой и никакие элементы не будут добавляться, см. в разделе [Практическое руководство. Использование оператора ForEach для удаления элементов в коллекции BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span><span class="sxs-lookup"><span data-stu-id="d8150-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="d8150-106">Пример</span><span class="sxs-lookup"><span data-stu-id="d8150-106">Example</span></span>  
 <span data-ttu-id="d8150-107">В первом примере показано, как добавлять и удалять элементы так, чтобы операции блокировались, если коллекция временно пуста (при извлечении) или достигает максимальной емкости (при добавлении), или если заданное время ожидания истекло.</span><span class="sxs-lookup"><span data-stu-id="d8150-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="d8150-108">Обратите внимание, что блокирование при максимальной заполненности доступно, только если BlockingCollection создана с указанием максимальной емкости в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="d8150-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="d8150-109">Пример</span><span class="sxs-lookup"><span data-stu-id="d8150-109">Example</span></span>  
 <span data-ttu-id="d8150-110">Во втором примере показано, как добавлять и извлекать элементы без блокирования операций.</span><span class="sxs-lookup"><span data-stu-id="d8150-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="d8150-111">Если истекло время ожидания, отсутствуют элементы или достигнута максимальная емкость ограниченной коллекции, то операция <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> или <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> возвращает значение false.</span><span class="sxs-lookup"><span data-stu-id="d8150-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="d8150-112">Это позволяет потоку некоторое время выполнять другие полезные действия, чтобы позднее повторить попытку получить или добавить элемент, которая ранее завершилась неудачей.</span><span class="sxs-lookup"><span data-stu-id="d8150-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="d8150-113">Программа также демонстрирует, как реализовать отмену при доступе к <xref:System.Collections.Concurrent.BlockingCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="d8150-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="d8150-114">См. также</span><span class="sxs-lookup"><span data-stu-id="d8150-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="d8150-115">Общие сведения о коллекции BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="d8150-115">BlockingCollection Overview</span></span>](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)
