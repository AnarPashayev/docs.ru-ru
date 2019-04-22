---
title: Предложение From (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: b18ef2f291e20d8a150972a980ba063377b0bc3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839617"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="dbdc7-102">Предложение From (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbdc7-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="dbdc7-103">Указывает один или несколько переменных диапазона и набор для запроса.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbdc7-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dbdc7-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="dbdc7-105">Части</span><span class="sxs-lookup"><span data-stu-id="dbdc7-105">Parts</span></span>  
  
|<span data-ttu-id="dbdc7-106">Термин</span><span class="sxs-lookup"><span data-stu-id="dbdc7-106">Term</span></span>|<span data-ttu-id="dbdc7-107">Определение</span><span class="sxs-lookup"><span data-stu-id="dbdc7-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="dbdc7-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-108">Required.</span></span> <span data-ttu-id="dbdc7-109">Объект *переменная диапазона* используется для итерации по элементам коллекции.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="dbdc7-110">Переменная диапазона используется для обращения к каждому элементу `collection` как запрос проходит по `collection`.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="dbdc7-111">Должен быть перечислимым типом.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="dbdc7-112">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-112">Optional.</span></span> <span data-ttu-id="dbdc7-113">Тип параметра `element`.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-113">The type of `element`.</span></span> <span data-ttu-id="dbdc7-114">Если не `type` указан, тип `element` выводится из `collection`.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="dbdc7-115">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-115">Required.</span></span> <span data-ttu-id="dbdc7-116">Относится к коллекции, должны запрашиваться.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="dbdc7-117">Должен быть перечислимым типом.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbdc7-118">Примечания</span><span class="sxs-lookup"><span data-stu-id="dbdc7-118">Remarks</span></span>  
 <span data-ttu-id="dbdc7-119">`From` Предложение используется для определения источника данных для запроса и переменные, которые используются для ссылки на элемент в исходной коллекции.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="dbdc7-120">Эти переменные называются *переменные диапазона*.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-120">These variables are called *range variables*.</span></span> <span data-ttu-id="dbdc7-121">`From` Предложение является обязательным для запроса, за исключением случаев `Aggregate` предложение используется для определения запросов, что возвращает только агрегированные результаты.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="dbdc7-122">Дополнительные сведения см. в разделе [предложение Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="dbdc7-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="dbdc7-123">Можно указать несколько `From` предложения в запросе для идентификации нескольких коллекций для объединения.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="dbdc7-124">При указании нескольких коллекций, они воспринимаются независимо друг от друга, или вы можете объединить их, если они связаны.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="dbdc7-125">Объединение коллекций неявно с помощью `Select` предложения, или явно с помощью `Join` или `Group Join` предложения.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="dbdc7-126">Кроме того, можно указать несколько переменных диапазона и коллекций в одном `From` предложение, с каждой связанной переменной диапазона и коллекций, разделенных запятыми от других.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="dbdc7-127">В следующем примере кода показаны оба варианта синтаксиса для `From` предложение.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="dbdc7-128">`From` Предложение определяет область запроса, который аналогичен рамки `For` цикла.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="dbdc7-129">Таким образом, каждый `element` переменной диапазона в области запроса должен иметь уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="dbdc7-130">Поскольку можно указать несколько `From` предложения запроса, последующие `From` предложения могут ссылаться на переменные диапазона в `From` предложения, или они могут ссылаться на переменную диапазона в предыдущем `From` предложение.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="dbdc7-131">Например, в следующем примере показано вложенный `From` предложение, где коллекция во втором предложении основана на свойстве переменной диапазона в первом предложении.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="dbdc7-132">Каждый `From` предложение может следовать любое сочетание дополнительных предложений запроса для уточнения запроса.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="dbdc7-133">Можно уточнить запрос следующим образом:</span><span class="sxs-lookup"><span data-stu-id="dbdc7-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="dbdc7-134">Объединить несколько коллекций неявно с помощью `From` и `Select` предложения, или явно с помощью `Join` или `Group Join` предложения.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="dbdc7-135">Используйте `Where` предложение для фильтрации результатов запроса.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="dbdc7-136">Отсортировать результаты с помощью `Order By` предложение.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="dbdc7-137">Группировать аналогичные результаты с помощью `Group By` предложение.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="dbdc7-138">Используйте `Aggregate` предложение для идентификации агрегатных функций для вычисления результата всего запроса.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="dbdc7-139">Используйте `Let` предложение для представления переменной итерации, значение которого определяется с помощью выражения, а не коллекция.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="dbdc7-140">Используйте `Distinct` предложение, чтобы игнорировать повторяющиеся результаты запроса.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="dbdc7-141">Определения частей результат для возврата с помощью `Skip`, `Take`, `Skip While`, и `Take While` предложения.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbdc7-142">Пример</span><span class="sxs-lookup"><span data-stu-id="dbdc7-142">Example</span></span>  
 <span data-ttu-id="dbdc7-143">В следующем запросе используется выражение `From` предложение для объявления переменной диапазона `cust` для каждого `Customer` объекта в `customers` коллекции.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="dbdc7-144">`Where` Предложение использует переменную диапазона для ограничения выходных данных клиентов из заданной области.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="dbdc7-145">`For Each` Цикл имя компании для каждого клиента в результатах запроса.</span><span class="sxs-lookup"><span data-stu-id="dbdc7-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="dbdc7-146">См. также</span><span class="sxs-lookup"><span data-stu-id="dbdc7-146">See also</span></span>

- [<span data-ttu-id="dbdc7-147">Запросы</span><span class="sxs-lookup"><span data-stu-id="dbdc7-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- <span data-ttu-id="dbdc7-148">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbdc7-148">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="dbdc7-149">Оператор For Each...Next</span><span class="sxs-lookup"><span data-stu-id="dbdc7-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="dbdc7-150">Оператор For...Next</span><span class="sxs-lookup"><span data-stu-id="dbdc7-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="dbdc7-151">Предложение Select</span><span class="sxs-lookup"><span data-stu-id="dbdc7-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="dbdc7-152">Предложения Where</span><span class="sxs-lookup"><span data-stu-id="dbdc7-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="dbdc7-153">Предложение Aggregate</span><span class="sxs-lookup"><span data-stu-id="dbdc7-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="dbdc7-154">Предложение Distinct</span><span class="sxs-lookup"><span data-stu-id="dbdc7-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="dbdc7-155">Предложение Join</span><span class="sxs-lookup"><span data-stu-id="dbdc7-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="dbdc7-156">Предложение Group Join</span><span class="sxs-lookup"><span data-stu-id="dbdc7-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="dbdc7-157">Предложение Order By</span><span class="sxs-lookup"><span data-stu-id="dbdc7-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="dbdc7-158">Предложение Let</span><span class="sxs-lookup"><span data-stu-id="dbdc7-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="dbdc7-159">Предложение Skip</span><span class="sxs-lookup"><span data-stu-id="dbdc7-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="dbdc7-160">Предложение Take</span><span class="sxs-lookup"><span data-stu-id="dbdc7-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="dbdc7-161">Предложение Skip While</span><span class="sxs-lookup"><span data-stu-id="dbdc7-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="dbdc7-162">Предложение Take While</span><span class="sxs-lookup"><span data-stu-id="dbdc7-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
