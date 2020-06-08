---
title: Практическое руководство. Задание параметров слияния в PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: 84667fa1fbe2966c580d9c6d32e52ed686af7bb3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288125"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="55f1c-102">Практическое руководство. Задание параметров слияния в PLINQ</span><span class="sxs-lookup"><span data-stu-id="55f1c-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="55f1c-103">Этот пример демонстрирует, как указать параметры слияния, которые будут применяться ко всем последующим операторам в запросе PLINQ.</span><span class="sxs-lookup"><span data-stu-id="55f1c-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="55f1c-104">Параметры слияния не обязательно указывать явным образом, но иногда это может повысить производительность.</span><span class="sxs-lookup"><span data-stu-id="55f1c-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="55f1c-105">Дополнительные сведения о параметрах слияния см. в разделе [Параметры слияния в PLINQ](merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="55f1c-105">For more information about merge options, see [Merge Options in PLINQ](merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="55f1c-106">Этот пример предназначен для демонстрации использования и может выполняться не быстрее аналогичного последовательного запроса LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="55f1c-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="55f1c-107">Дополнительные сведения см. в статье [Общее представление об ускорении выполнения в PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="55f1c-107">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55f1c-108">Пример</span><span class="sxs-lookup"><span data-stu-id="55f1c-108">Example</span></span>  
 <span data-ttu-id="55f1c-109">Следующий пример демонстрирует поведение параметров слияния в простом сценарии, в котором ресурсоемкая функция применяется к каждому элементу неупорядоченного источника.</span><span class="sxs-lookup"><span data-stu-id="55f1c-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="55f1c-110">В случаях, если вариант <xref:System.Linq.ParallelMergeOptions.AutoBuffered> приводит к нежелательной задержке перед получением первого элемента, попробуйте вариант <xref:System.Linq.ParallelMergeOptions.NotBuffered>, чтобы получать результаты быстрее и спокойнее.</span><span class="sxs-lookup"><span data-stu-id="55f1c-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f1c-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="55f1c-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="55f1c-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="55f1c-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
