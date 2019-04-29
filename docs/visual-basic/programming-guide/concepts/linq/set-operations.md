---
title: Операции с множествами (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 59ab09607462c762758e6a246ec218a92e01f5de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786883"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="3947a-102">Операции с множествами (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3947a-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="3947a-103">Операции над множествами в LINQ — это операции запросов, результирующие наборы которых основываются на наличии или отсутствии эквивалентных элементов в одной или другой коллекции (или наборе).</span><span class="sxs-lookup"><span data-stu-id="3947a-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="3947a-104">Методы стандартных операторов запросов, которые выполняют операции над множествами, перечислены в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="3947a-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3947a-105">Методы</span><span class="sxs-lookup"><span data-stu-id="3947a-105">Methods</span></span>  
  
|<span data-ttu-id="3947a-106">Имя метода</span><span class="sxs-lookup"><span data-stu-id="3947a-106">Method Name</span></span>|<span data-ttu-id="3947a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="3947a-107">Description</span></span>|<span data-ttu-id="3947a-108">Синтаксис выражений запросов Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3947a-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="3947a-109">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="3947a-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="3947a-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="3947a-110">Distinct</span></span>|<span data-ttu-id="3947a-111">Удаляет повторяющиеся значения из коллекции.</span><span class="sxs-lookup"><span data-stu-id="3947a-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3947a-112">Исключения</span><span class="sxs-lookup"><span data-stu-id="3947a-112">Except</span></span>|<span data-ttu-id="3947a-113">Возвращает разность множеств, т. е. элементы одной коллекции, которые отсутствуют во второй.</span><span class="sxs-lookup"><span data-stu-id="3947a-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="3947a-114">Неприменимо.</span><span class="sxs-lookup"><span data-stu-id="3947a-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3947a-115">Пересечение</span><span class="sxs-lookup"><span data-stu-id="3947a-115">Intersect</span></span>|<span data-ttu-id="3947a-116">Возвращает пересечение множеств, т. е. элементы, присутствующие в каждой из двух коллекций.</span><span class="sxs-lookup"><span data-stu-id="3947a-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="3947a-117">Неприменимо.</span><span class="sxs-lookup"><span data-stu-id="3947a-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3947a-118">Объединение</span><span class="sxs-lookup"><span data-stu-id="3947a-118">Union</span></span>|<span data-ttu-id="3947a-119">Возвращает объединение множеств, т. е. уникальные элементы, присутствующие в одной из двух коллекций.</span><span class="sxs-lookup"><span data-stu-id="3947a-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="3947a-120">Неприменимо.</span><span class="sxs-lookup"><span data-stu-id="3947a-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="3947a-121">Сравнение операций над множествами</span><span class="sxs-lookup"><span data-stu-id="3947a-121">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="3947a-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="3947a-122">Distinct</span></span>  
 <span data-ttu-id="3947a-123">На следующем рисунке показано поведение метода <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> применительно к последовательности символов.</span><span class="sxs-lookup"><span data-stu-id="3947a-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="3947a-124">Возвращаемая последовательность содержит уникальные элементы из входной последовательности.</span><span class="sxs-lookup"><span data-stu-id="3947a-124">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![График, демонстрирующий поведение Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a><span data-ttu-id="3947a-126">Исключения</span><span class="sxs-lookup"><span data-stu-id="3947a-126">Except</span></span>  
 <span data-ttu-id="3947a-127">На следующем рисунке показано поведение <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3947a-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3947a-128">Возвращаемая последовательность содержит только те элементы из первой входной последовательности, которых нет во второй.</span><span class="sxs-lookup"><span data-stu-id="3947a-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="3947a-129">![Рисунок, показывающий действие Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Показывает поведение исключения.")</span><span class="sxs-lookup"><span data-stu-id="3947a-129">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="3947a-130">Пересечение</span><span class="sxs-lookup"><span data-stu-id="3947a-130">Intersect</span></span>  
 <span data-ttu-id="3947a-131">На следующем рисунке показано поведение <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3947a-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3947a-132">Возвращаемая последовательность содержит элементы, общие для обеих входных последовательностей.</span><span class="sxs-lookup"><span data-stu-id="3947a-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![График, отображающий пересечение двух последовательностей.](./media/set-operations/intersection-two-sequences.png)    
### <a name="union"></a><span data-ttu-id="3947a-134">Объединение</span><span class="sxs-lookup"><span data-stu-id="3947a-134">Union</span></span>  
 <span data-ttu-id="3947a-135">На следующем рисунке показана операция объединения двух последовательностей символов.</span><span class="sxs-lookup"><span data-stu-id="3947a-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="3947a-136">Возвращаемая последовательность содержит уникальные элементы из обеих входных последовательностей.</span><span class="sxs-lookup"><span data-stu-id="3947a-136">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![График, показывающий объединение двух последовательностей.](./media/set-operations/union-operation-two-sequences.png)    
## <a name="query-expression-syntax-example"></a><span data-ttu-id="3947a-138">Пример синтаксиса выражения запроса</span><span class="sxs-lookup"><span data-stu-id="3947a-138">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="3947a-139">В следующем примере используется `Distinct` предложение в запросе LINQ для возврата уникальных чисел из списка целых чисел.</span><span class="sxs-lookup"><span data-stu-id="3947a-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 [!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3947a-140">См. также</span><span class="sxs-lookup"><span data-stu-id="3947a-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="3947a-141">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3947a-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="3947a-142">Предложение Distinct</span><span class="sxs-lookup"><span data-stu-id="3947a-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="3947a-143">Практическое руководство. Объединение и сравнение коллекций строк (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3947a-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="3947a-144">Практическое руководство. Нахождение разности множеств между двумя списками (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3947a-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
