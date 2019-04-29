---
title: Предложение Where (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 5632e69039baebb3d1f1fd90c04586d9e50fe40f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945214"
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="2937e-102">Предложение Where (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2937e-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="2937e-103">Определяет условия фильтрации запроса.</span><span class="sxs-lookup"><span data-stu-id="2937e-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2937e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2937e-104">Syntax</span></span>  
  
```  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="2937e-105">Части</span><span class="sxs-lookup"><span data-stu-id="2937e-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="2937e-106">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2937e-106">Required.</span></span> <span data-ttu-id="2937e-107">Выражение, определяющее, включаются ли в коллекции выходных значений для текущего элемента в коллекции.</span><span class="sxs-lookup"><span data-stu-id="2937e-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="2937e-108">Выражение должно возвращать `Boolean` значение или его эквивалент `Boolean` значение.</span><span class="sxs-lookup"><span data-stu-id="2937e-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="2937e-109">Если условие принимает значение `True`, элемент включается в результат запроса; в противном случае, элемент исключается из результата запроса.</span><span class="sxs-lookup"><span data-stu-id="2937e-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2937e-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="2937e-110">Remarks</span></span>  
 <span data-ttu-id="2937e-111">`Where` Предложение позволяет фильтровать запросы к данным, выбрав только элементы, которые соответствуют определенным критериям.</span><span class="sxs-lookup"><span data-stu-id="2937e-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="2937e-112">Элементы, значения которых вызвать `Where` предложение для вычисления `True` включены в результат запроса; другие элементы исключаются.</span><span class="sxs-lookup"><span data-stu-id="2937e-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="2937e-113">Выражение, которое используется в `Where` должны иметь предложение `Boolean` или его эквивалент `Boolean`, такие как целое число, результатом которого является `False` если его значение равно нулю.</span><span class="sxs-lookup"><span data-stu-id="2937e-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="2937e-114">Можно объединить несколько выражений в `Where` предложение с помощью логических операторов, таких как `And`, `Or`, `AndAlso`, `OrElse`, `Is`, и `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="2937e-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="2937e-115">По умолчанию, выражения запроса не вычисляются до к ним осуществляется доступ, например, когда они находятся привязкой к данным или прошедших итерацию через в `For` цикла.</span><span class="sxs-lookup"><span data-stu-id="2937e-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="2937e-116">В результате `Where` предложение вычисляется только в том случае, пока не осуществляется доступ к запросу.</span><span class="sxs-lookup"><span data-stu-id="2937e-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="2937e-117">Если у вас есть значения, внешним по отношению к запроса, которые используются в `Where` предложение, убедитесь, что соответствующее значение используется в `Where` предложение во время выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="2937e-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="2937e-118">Дополнительные сведения о выполнении запросов см. в разделе [Your первого запроса LINQ записи](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="2937e-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="2937e-119">Можно вызывать функции в `Where` предложение, чтобы выполнить расчет или операцию над значением из текущего элемента в коллекции.</span><span class="sxs-lookup"><span data-stu-id="2937e-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="2937e-120">Вызов функции в `Where` предложение может вызвать запрос для выполнения сразу же при определении, а не при доступе.</span><span class="sxs-lookup"><span data-stu-id="2937e-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="2937e-121">Дополнительные сведения о выполнении запросов см. в разделе [Your первого запроса LINQ записи](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span><span class="sxs-lookup"><span data-stu-id="2937e-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2937e-122">Пример</span><span class="sxs-lookup"><span data-stu-id="2937e-122">Example</span></span>  
 <span data-ttu-id="2937e-123">В следующем запросе используется выражение `From` предложение для объявления переменной диапазона `cust` для каждого `Customer` объекта в `customers` коллекции.</span><span class="sxs-lookup"><span data-stu-id="2937e-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="2937e-124">`Where` Предложение использует переменную диапазона для ограничения выходных данных клиентов из заданной области.</span><span class="sxs-lookup"><span data-stu-id="2937e-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="2937e-125">`For Each` Цикл имя компании для каждого клиента в результатах запроса.</span><span class="sxs-lookup"><span data-stu-id="2937e-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="2937e-126">Пример</span><span class="sxs-lookup"><span data-stu-id="2937e-126">Example</span></span>  
 <span data-ttu-id="2937e-127">В следующем примере используется `And` и `Or` логические операторы в `Where` предложение.</span><span class="sxs-lookup"><span data-stu-id="2937e-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="2937e-128">См. также</span><span class="sxs-lookup"><span data-stu-id="2937e-128">See also</span></span>

- <span data-ttu-id="2937e-129">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2937e-129">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="2937e-130">Запросы</span><span class="sxs-lookup"><span data-stu-id="2937e-130">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="2937e-131">Предложение From</span><span class="sxs-lookup"><span data-stu-id="2937e-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="2937e-132">Предложение Select</span><span class="sxs-lookup"><span data-stu-id="2937e-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="2937e-133">Оператор For Each...Next</span><span class="sxs-lookup"><span data-stu-id="2937e-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
