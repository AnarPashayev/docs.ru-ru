---
title: Практическое руководство. Синхронизация параллельных операций с барьером
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
ms.openlocfilehash: 33098878764c2f8a8c1f83a122028da40b984243
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137974"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="6615d-102">Практическое руководство. Синхронизация параллельных операций с барьером</span><span class="sxs-lookup"><span data-stu-id="6615d-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="6615d-103">В следующем примере показано, как синхронизировать параллельные задачи с помощью объекта <xref:System.Threading.Barrier>.</span><span class="sxs-lookup"><span data-stu-id="6615d-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6615d-104">Пример</span><span class="sxs-lookup"><span data-stu-id="6615d-104">Example</span></span>  
 <span data-ttu-id="6615d-105">Следующая программа подсчитывает количество итераций (или этапов), необходимых для того, чтобы каждый из двух потоков одновременно нашел свое частичное решение, используя алгоритм перемешивания слов.</span><span class="sxs-lookup"><span data-stu-id="6615d-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="6615d-106">В каждом потоке перемешиваются свои слова, а затем операция барьера после этапа сравнивает два результата и проверяет, правильно ли собрано полное предложение.</span><span class="sxs-lookup"><span data-stu-id="6615d-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="6615d-107">Объект <xref:System.Threading.Barrier> приостанавливает параллельное выполнение отдельных задач, пока все задачи не достигнут этого барьера.</span><span class="sxs-lookup"><span data-stu-id="6615d-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="6615d-108">Это полезно в тех случаях, когда параллельная операция имеет четко определенные этапы, по каждому из которых требуется синхронизация между задачами.</span><span class="sxs-lookup"><span data-stu-id="6615d-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="6615d-109">В нашем примере операция осуществляется в два этапа.</span><span class="sxs-lookup"><span data-stu-id="6615d-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="6615d-110">На первом этапе каждая задача заполняет данными свой сегмент буфера.</span><span class="sxs-lookup"><span data-stu-id="6615d-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="6615d-111">Каждая задача, которая завершает заполнение своего сегмента, сообщает барьеру о готовности и переходит в режим ожидания.</span><span class="sxs-lookup"><span data-stu-id="6615d-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="6615d-112">Когда все задачи отправят барьеру сигналы, блокировка снимается и начинается второй этап.</span><span class="sxs-lookup"><span data-stu-id="6615d-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="6615d-113">Этот барьер нужен для того, чтобы каждая задача на втором этапе получила доступ ко всем данным, созданным до этого момента.</span><span class="sxs-lookup"><span data-stu-id="6615d-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="6615d-114">Без этого барьера первая задача, выполнившая свою работу, может начать чтение из буферов, которые еще не заполнены другими задачами.</span><span class="sxs-lookup"><span data-stu-id="6615d-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="6615d-115">Этот подход позволяет синхронизировать любое количество этапов.</span><span class="sxs-lookup"><span data-stu-id="6615d-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6615d-116">См. также</span><span class="sxs-lookup"><span data-stu-id="6615d-116">See also</span></span>

- [<span data-ttu-id="6615d-117">Структуры данных для параллельного программирования</span><span class="sxs-lookup"><span data-stu-id="6615d-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
