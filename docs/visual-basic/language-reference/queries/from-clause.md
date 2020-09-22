---
title: Предложение From
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
ms.openlocfilehash: 120ba6da11bffc3a0e81873d1fd606633724723d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875250"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="8bbdc-102">Предложение From (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bbdc-102">From Clause (Visual Basic)</span></span>

<span data-ttu-id="8bbdc-103">Указывает одну или несколько переменных диапазона и коллекцию для запроса.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bbdc-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8bbdc-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="8bbdc-105">Компоненты</span><span class="sxs-lookup"><span data-stu-id="8bbdc-105">Parts</span></span>  
  
|<span data-ttu-id="8bbdc-106">Термин</span><span class="sxs-lookup"><span data-stu-id="8bbdc-106">Term</span></span>|<span data-ttu-id="8bbdc-107">Определение</span><span class="sxs-lookup"><span data-stu-id="8bbdc-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="8bbdc-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-108">Required.</span></span> <span data-ttu-id="8bbdc-109">*Переменная диапазона* , используемая для прохода по элементам коллекции.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="8bbdc-110">Переменная диапазона используется для ссылки на каждый элемент в, `collection` когда запрос выполняет итерацию по `collection` .</span><span class="sxs-lookup"><span data-stu-id="8bbdc-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="8bbdc-111">Должен быть перечислимым типом.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="8bbdc-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-112">Optional.</span></span> <span data-ttu-id="8bbdc-113">Тип параметра `element`.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-113">The type of `element`.</span></span> <span data-ttu-id="8bbdc-114">Если не `type` указано, тип `element` выводится из `collection` .</span><span class="sxs-lookup"><span data-stu-id="8bbdc-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="8bbdc-115">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-115">Required.</span></span> <span data-ttu-id="8bbdc-116">Ссылается на коллекцию, к которой выполняется запрос.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="8bbdc-117">Должен быть перечислимым типом.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bbdc-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="8bbdc-118">Remarks</span></span>  

 <span data-ttu-id="8bbdc-119">`From`Предложение используется для указания исходных данных для запроса и переменных, которые используются для ссылки на элемент из исходной коллекции.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="8bbdc-120">Эти переменные называются *переменными диапазона*.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-120">These variables are called *range variables*.</span></span> <span data-ttu-id="8bbdc-121">`From`Предложение является обязательным для запроса, за исключением случаев, когда `Aggregate` предложение используется для задания запроса, возвращающего только агрегированные результаты.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="8bbdc-122">Дополнительные сведения см. в разделе [предложение Aggregate](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8bbdc-122">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="8bbdc-123">В запросе можно указать несколько `From` предложений, чтобы определить несколько коллекций для объединения.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="8bbdc-124">Если указано несколько коллекций, они проходят по отдельности или объединяются, если они связаны.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="8bbdc-125">Коллекции можно объединять неявным образом с помощью `Select` предложения или явно с помощью `Join` предложений или `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="8bbdc-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="8bbdc-126">В качестве альтернативы можно указать несколько переменных диапазона и коллекций в одном `From` предложении, при этом каждая связанная переменная диапазона и коллекция, отделенные друг от друга запятыми.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="8bbdc-127">В следующем примере кода показаны оба синтаксических параметра для `From` предложения.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="8bbdc-128">`From`Предложение определяет область запроса, аналогичную области `For` цикла.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="8bbdc-129">Таким образом, каждая `element` переменная диапазона в области запроса должна иметь уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="8bbdc-130">Поскольку можно указать несколько `From` предложений для запроса, последующие `From` предложения могут ссылаться на переменные диапазона в `From` предложении или они могут ссылаться на переменные диапазона в предыдущем `From` предложении.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="8bbdc-131">Например, в следующем примере показано вложенное `From` предложение, где коллекция во втором предложении основана на свойстве переменной диапазона в первом предложении.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="8bbdc-132">`From`За каждым предложением может следовать любое сочетание дополнительных предложений запроса для уточнения запроса.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="8bbdc-133">Запрос можно уточнить следующими способами.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="8bbdc-134">Объедините несколько коллекций неявным образом с помощью `From` `Select` предложений и или явно с помощью `Join` предложений или `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="8bbdc-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="8bbdc-135">Используйте `Where` предложение для фильтрации результатов запроса.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="8bbdc-136">Отсортируйте результат с помощью `Order By` предложения.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="8bbdc-137">Группировать аналогичные результаты вместе с помощью `Group By` предложения.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="8bbdc-138">Используйте `Aggregate` предложение для определения агрегатных функций для вычисления результата всего запроса.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="8bbdc-139">Используйте `Let` предложение, чтобы ввести переменную итерации, значение которой определяется выражением, а не коллекцией.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="8bbdc-140">Используйте `Distinct` предложение для пропуска повторяющихся результатов запроса.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="8bbdc-141">Выявление частей результата, возвращаемых с помощью `Skip` предложений, `Take` , `Skip While` и `Take While` .</span><span class="sxs-lookup"><span data-stu-id="8bbdc-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bbdc-142">Пример</span><span class="sxs-lookup"><span data-stu-id="8bbdc-142">Example</span></span>  

 <span data-ttu-id="8bbdc-143">Следующее выражение запроса использует `From` предложение для объявления переменной диапазона `cust` для каждого `Customer` объекта в `customers` коллекции.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="8bbdc-144">`Where`Предложение использует переменную диапазона для ограничения выходных данных для клиентов из указанной области.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="8bbdc-145">`For Each`Цикл отображает название компании для каждого клиента в результатах запроса.</span><span class="sxs-lookup"><span data-stu-id="8bbdc-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="8bbdc-146">См. также</span><span class="sxs-lookup"><span data-stu-id="8bbdc-146">See also</span></span>

- [<span data-ttu-id="8bbdc-147">Запросы</span><span class="sxs-lookup"><span data-stu-id="8bbdc-147">Queries</span></span>](index.md)
- <span data-ttu-id="8bbdc-148">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bbdc-148">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="8bbdc-149">Оператор For Each…Next</span><span class="sxs-lookup"><span data-stu-id="8bbdc-149">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="8bbdc-150">Оператор For…Next</span><span class="sxs-lookup"><span data-stu-id="8bbdc-150">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="8bbdc-151">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="8bbdc-151">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="8bbdc-152">Предложение WHERE</span><span class="sxs-lookup"><span data-stu-id="8bbdc-152">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="8bbdc-153">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="8bbdc-153">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="8bbdc-154">Предложение Distinct</span><span class="sxs-lookup"><span data-stu-id="8bbdc-154">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="8bbdc-155">Предложение Join</span><span class="sxs-lookup"><span data-stu-id="8bbdc-155">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="8bbdc-156">Предложение Group Join</span><span class="sxs-lookup"><span data-stu-id="8bbdc-156">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="8bbdc-157">Предложение ORDER BY</span><span class="sxs-lookup"><span data-stu-id="8bbdc-157">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="8bbdc-158">Предложение Let</span><span class="sxs-lookup"><span data-stu-id="8bbdc-158">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="8bbdc-159">Предложение Skip</span><span class="sxs-lookup"><span data-stu-id="8bbdc-159">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="8bbdc-160">Предложение Take</span><span class="sxs-lookup"><span data-stu-id="8bbdc-160">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="8bbdc-161">Предложение Skip While</span><span class="sxs-lookup"><span data-stu-id="8bbdc-161">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="8bbdc-162">Предложение Take While</span><span class="sxs-lookup"><span data-stu-id="8bbdc-162">Take While Clause</span></span>](take-while-clause.md)
