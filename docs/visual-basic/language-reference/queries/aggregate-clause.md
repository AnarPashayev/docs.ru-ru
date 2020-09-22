---
title: Aggregate Clause
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: be2e401c7931b2637c14a3ea3b742a2c09917939
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869991"
---
# <a name="aggregate-clause-visual-basic"></a><span data-ttu-id="b8b66-102">Предложение Aggregate (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8b66-102">Aggregate Clause (Visual Basic)</span></span>

<span data-ttu-id="b8b66-103">Применяет одну или несколько агрегатных функций к коллекции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-103">Applies one or more aggregate functions to a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8b66-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b8b66-104">Syntax</span></span>  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="b8b66-105">Компоненты</span><span class="sxs-lookup"><span data-stu-id="b8b66-105">Parts</span></span>  
  
|<span data-ttu-id="b8b66-106">Термин</span><span class="sxs-lookup"><span data-stu-id="b8b66-106">Term</span></span>|<span data-ttu-id="b8b66-107">Определение</span><span class="sxs-lookup"><span data-stu-id="b8b66-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="b8b66-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b8b66-108">Required.</span></span> <span data-ttu-id="b8b66-109">Переменная, используемая для прохода по элементам коллекции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-109">Variable used to iterate through the elements of the collection.</span></span>|  
|`type`|<span data-ttu-id="b8b66-110">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b8b66-110">Optional.</span></span> <span data-ttu-id="b8b66-111">Тип параметра `element`.</span><span class="sxs-lookup"><span data-stu-id="b8b66-111">The type of `element`.</span></span> <span data-ttu-id="b8b66-112">Если тип не указан, тип `element` выводится из `collection` .</span><span class="sxs-lookup"><span data-stu-id="b8b66-112">If no type is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="b8b66-113">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b8b66-113">Required.</span></span> <span data-ttu-id="b8b66-114">Ссылается на коллекцию для обработки.</span><span class="sxs-lookup"><span data-stu-id="b8b66-114">Refers to the collection to operate on.</span></span>|  
|`clause`|<span data-ttu-id="b8b66-115">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b8b66-115">Optional.</span></span> <span data-ttu-id="b8b66-116">Одно или несколько предложений запроса, например `Where` предложение, для уточнения результата запроса с целью применения предложения Aggregate или предложений к.</span><span class="sxs-lookup"><span data-stu-id="b8b66-116">One or more query clauses, such as a `Where` clause, to refine the query result to apply the aggregate clause or clauses to.</span></span>|  
|`expressionList`|<span data-ttu-id="b8b66-117">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b8b66-117">Required.</span></span> <span data-ttu-id="b8b66-118">Одно или несколько выражений с разделителями-запятыми, которые обозначают агрегатную функцию, применяемую к коллекции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-118">One or more comma-delimited expressions that identify an aggregate function to apply to the collection.</span></span> <span data-ttu-id="b8b66-119">Можно применить псевдоним к агрегатной функции, чтобы указать имя элемента для результата запроса.</span><span class="sxs-lookup"><span data-stu-id="b8b66-119">You can apply an alias to an aggregate function to specify a member name for the query result.</span></span> <span data-ttu-id="b8b66-120">Если псевдоним не указан, используется имя агрегатной функции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-120">If no alias is supplied, the name of the aggregate function is used.</span></span> <span data-ttu-id="b8b66-121">Примеры см. в разделе агрегатные функции далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="b8b66-121">For examples, see the section about aggregate functions later in this topic.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8b66-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="b8b66-122">Remarks</span></span>  

 <span data-ttu-id="b8b66-123">`Aggregate`Предложение можно использовать для включения в запросы агрегатных функций.</span><span class="sxs-lookup"><span data-stu-id="b8b66-123">The `Aggregate` clause can be used to include aggregate functions in your queries.</span></span> <span data-ttu-id="b8b66-124">Агрегатные функции выполняют проверки и вычисления для набора значений и возвращают одно значение.</span><span class="sxs-lookup"><span data-stu-id="b8b66-124">Aggregate functions perform checks and computations over a set of values and return a single value.</span></span> <span data-ttu-id="b8b66-125">Доступ к вычисленному значению можно получить с помощью члена типа результата запроса.</span><span class="sxs-lookup"><span data-stu-id="b8b66-125">You can access the computed value by using a member of the query result type.</span></span> <span data-ttu-id="b8b66-126">Стандартные агрегатные функции, которые можно использовать, — это функции,,,,,, `All` `Any` `Average` `Count` `LongCount` `Max` `Min` и `Sum` .</span><span class="sxs-lookup"><span data-stu-id="b8b66-126">The standard aggregate functions that you can use are the `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, and `Sum` functions.</span></span> <span data-ttu-id="b8b66-127">Эти функции знакомы разработчикам, знакомым со статистическими выражениями в SQL.</span><span class="sxs-lookup"><span data-stu-id="b8b66-127">These functions are familiar to developers who are familiar with aggregates in SQL.</span></span> <span data-ttu-id="b8b66-128">Они описаны в следующем разделе этой статьи.</span><span class="sxs-lookup"><span data-stu-id="b8b66-128">They are described in the following section of this topic.</span></span>  
  
 <span data-ttu-id="b8b66-129">Результат агрегатной функции включается в результат запроса в виде поля типа результата запроса.</span><span class="sxs-lookup"><span data-stu-id="b8b66-129">The result of an aggregate function is included in the query result as a field of the query result type.</span></span> <span data-ttu-id="b8b66-130">Можно указать псевдоним для результата агрегатной функции, чтобы указать имя элемента типа результата запроса, который будет содержать статистическое значение.</span><span class="sxs-lookup"><span data-stu-id="b8b66-130">You can supply an alias for the aggregate function result to specify the name of the member of the query result type that will hold the aggregate value.</span></span> <span data-ttu-id="b8b66-131">Если псевдоним не указан, используется имя агрегатной функции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-131">If no alias is supplied, the name of the aggregate function is used.</span></span>  
  
 <span data-ttu-id="b8b66-132">`Aggregate`Предложение может начинать запрос или включать его в запрос в качестве дополнительного предложения.</span><span class="sxs-lookup"><span data-stu-id="b8b66-132">The `Aggregate` clause can begin a query, or it can be included as an additional clause in a query.</span></span> <span data-ttu-id="b8b66-133">Если `Aggregate` предложение начинает запрос, результатом является единственное значение, которое является результатом агрегатной функции, указанной в `Into` предложении.</span><span class="sxs-lookup"><span data-stu-id="b8b66-133">If the `Aggregate` clause begins a query, the result is a single value that is the result of the aggregate function specified in the `Into` clause.</span></span> <span data-ttu-id="b8b66-134">Если в предложении указано более одной агрегатной функции `Into` , запрос возвращает один тип с отдельным свойством для ссылки на результат каждой агрегатной функции в `Into` предложении.</span><span class="sxs-lookup"><span data-stu-id="b8b66-134">If more than one aggregate function is specified in the `Into` clause, the query returns a single type with a separate property to reference the result of each aggregate function in the `Into` clause.</span></span> <span data-ttu-id="b8b66-135">Если `Aggregate` предложение включено в запрос как дополнительное предложение, тип, возвращаемый в коллекции запросов, будет иметь отдельное свойство для ссылки на результат каждой агрегатной функции в `Into` предложении.</span><span class="sxs-lookup"><span data-stu-id="b8b66-135">If the `Aggregate` clause is included as an additional clause in a query, the type returned in the query collection will have a separate property to reference the result of each aggregate function in the `Into` clause.</span></span>  
  
## <a name="aggregate-functions"></a><span data-ttu-id="b8b66-136">Агрегатные функции</span><span class="sxs-lookup"><span data-stu-id="b8b66-136">Aggregate Functions</span></span>

<span data-ttu-id="b8b66-137">Ниже приведены стандартные агрегатные функции, которые можно использовать с `Aggregate` предложением.</span><span class="sxs-lookup"><span data-stu-id="b8b66-137">The following are the standard aggregate functions that can be used with the `Aggregate` clause.</span></span>  
  
### <a name="all"></a><span data-ttu-id="b8b66-138">Все</span><span class="sxs-lookup"><span data-stu-id="b8b66-138">All</span></span>

<span data-ttu-id="b8b66-139">Возвращает значение, `true` Если все элементы в коллекции соответствуют заданному условию. в противном случае возвращает `false` .</span><span class="sxs-lookup"><span data-stu-id="b8b66-139">Returns `true` if all elements in the collection satisfy a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="b8b66-140">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b8b66-140">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a><span data-ttu-id="b8b66-141">Любой</span><span class="sxs-lookup"><span data-stu-id="b8b66-141">Any</span></span>

<span data-ttu-id="b8b66-142">Возвращает значение, `true` Если любой элемент в коллекции удовлетворяет заданному условию; в противном случае возвращает `false` .</span><span class="sxs-lookup"><span data-stu-id="b8b66-142">Returns `true` if any element in the collection satisfies a specified condition; otherwise returns `false`.</span></span> <span data-ttu-id="b8b66-143">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b8b66-143">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a><span data-ttu-id="b8b66-144">Среднее значение</span><span class="sxs-lookup"><span data-stu-id="b8b66-144">Average</span></span>

<span data-ttu-id="b8b66-145">Вычисляет среднее значение всех элементов в коллекции или вычисляет заданное выражение для всех элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-145">Computes the average of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="b8b66-146">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b8b66-146">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a><span data-ttu-id="b8b66-147">Count</span><span class="sxs-lookup"><span data-stu-id="b8b66-147">Count</span></span>

<span data-ttu-id="b8b66-148">Подсчитывает количество элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-148">Counts the number of elements in the collection.</span></span> <span data-ttu-id="b8b66-149">Можно указать необязательное `Boolean` выражение, чтобы подсчитать только количество элементов в коллекции, удовлетворяющее условию.</span><span class="sxs-lookup"><span data-stu-id="b8b66-149">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="b8b66-150">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b8b66-150">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a><span data-ttu-id="b8b66-151">Group</span><span class="sxs-lookup"><span data-stu-id="b8b66-151">Group</span></span>

<span data-ttu-id="b8b66-152">Относится к результатам запроса, сгруппированным в результате `Group By` `Group Join` предложения OR.</span><span class="sxs-lookup"><span data-stu-id="b8b66-152">Refers to query results that are grouped as a result of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="b8b66-153">`Group`Функция допустима только в `Into` предложении `Group By` `Group Join` предложения OR.</span><span class="sxs-lookup"><span data-stu-id="b8b66-153">The `Group` function is valid only in the `Into` clause of a `Group By` or `Group Join` clause.</span></span> <span data-ttu-id="b8b66-154">Дополнительные сведения и примеры см. в разделе предложение [Group By](group-by-clause.md) и [предложение Group Join](group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b8b66-154">For more information and examples, see [Group By Clause](group-by-clause.md) and [Group Join Clause](group-join-clause.md).</span></span>

### <a name="longcount"></a><span data-ttu-id="b8b66-155">LongCount</span><span class="sxs-lookup"><span data-stu-id="b8b66-155">LongCount</span></span>

<span data-ttu-id="b8b66-156">Подсчитывает количество элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-156">Counts the number of elements in the collection.</span></span> <span data-ttu-id="b8b66-157">Можно указать необязательное `Boolean` выражение, чтобы подсчитать только количество элементов в коллекции, удовлетворяющее условию.</span><span class="sxs-lookup"><span data-stu-id="b8b66-157">You can supply an optional `Boolean` expression to count only the number of elements in the collection that satisfy a condition.</span></span> <span data-ttu-id="b8b66-158">Возвращает результат в виде `Long` .</span><span class="sxs-lookup"><span data-stu-id="b8b66-158">Returns the result as a `Long`.</span></span> <span data-ttu-id="b8b66-159">Пример см. в разделе `Count` агрегатная функция.</span><span class="sxs-lookup"><span data-stu-id="b8b66-159">For an example, see the `Count` aggregate function.</span></span>

### <a name="max"></a><span data-ttu-id="b8b66-160">Макс.</span><span class="sxs-lookup"><span data-stu-id="b8b66-160">Max</span></span>

<span data-ttu-id="b8b66-161">Вычисление максимального значения из коллекции или вычисление заданного выражения для всех элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-161">Computes the maximum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="b8b66-162">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b8b66-162">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a><span data-ttu-id="b8b66-163">Min</span><span class="sxs-lookup"><span data-stu-id="b8b66-163">Min</span></span>

<span data-ttu-id="b8b66-164">Вычисление минимального значения из коллекции или вычисление заданного выражения для всех элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-164">Computes the minimum value from the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="b8b66-165">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b8b66-165">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a><span data-ttu-id="b8b66-166">SUM</span><span class="sxs-lookup"><span data-stu-id="b8b66-166">Sum</span></span>

<span data-ttu-id="b8b66-167">Вычисляет сумму всех элементов в коллекции или вычисляет заданное выражение для всех элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="b8b66-167">Computes the sum of all elements in the collection, or computes a supplied expression for all elements in the collection.</span></span> <span data-ttu-id="b8b66-168">Ниже приведен пример:</span><span class="sxs-lookup"><span data-stu-id="b8b66-168">The following is an example:</span></span>

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a><span data-ttu-id="b8b66-169">Пример</span><span class="sxs-lookup"><span data-stu-id="b8b66-169">Example</span></span>  

<span data-ttu-id="b8b66-170">В следующем примере показано, как использовать `Aggregate` предложение для применения агрегатных функций к результату запроса.</span><span class="sxs-lookup"><span data-stu-id="b8b66-170">The following example shows how to use the `Aggregate` clause to apply aggregate functions to a query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a><span data-ttu-id="b8b66-171">Создание определяемых пользователем агрегатных функций</span><span class="sxs-lookup"><span data-stu-id="b8b66-171">Creating User-Defined Aggregate Functions</span></span>

 <span data-ttu-id="b8b66-172">Можно включить собственные пользовательские агрегатные функции в выражение запроса, добавив методы расширения в <xref:System.Collections.Generic.IEnumerable%601> тип.</span><span class="sxs-lookup"><span data-stu-id="b8b66-172">You can include your own custom aggregate functions in a query expression by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> type.</span></span> <span data-ttu-id="b8b66-173">Пользовательский метод может затем выполнить вычисление или операцию над перечислимой коллекцией, на которую ссылается агрегатная функция.</span><span class="sxs-lookup"><span data-stu-id="b8b66-173">Your custom method can then perform a calculation or operation on the enumerable collection that has referenced your aggregate function.</span></span> <span data-ttu-id="b8b66-174">Дополнительные сведения о методах расширения см. в разделе [Методы расширения](../../programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b8b66-174">For more information about extension methods, see [Extension Methods](../../programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
 <span data-ttu-id="b8b66-175">Например, в следующем примере показана пользовательская агрегатная функция, которая вычисляет медианное значение коллекции чисел.</span><span class="sxs-lookup"><span data-stu-id="b8b66-175">For example, the following example shows a custom aggregate function that calculates the median value of a collection of numbers.</span></span> <span data-ttu-id="b8b66-176">Существует две перегрузки `Median` метода расширения.</span><span class="sxs-lookup"><span data-stu-id="b8b66-176">There are two overloads of the `Median` extension method.</span></span> <span data-ttu-id="b8b66-177">Первая перегрузка принимает в качестве входных данных коллекцию типа `IEnumerable(Of Double)` .</span><span class="sxs-lookup"><span data-stu-id="b8b66-177">The first overload accepts, as input, a collection of type `IEnumerable(Of Double)`.</span></span> <span data-ttu-id="b8b66-178">Если `Median` для поля запроса типа вызывается агрегатная функция `Double` , этот метод будет вызван.</span><span class="sxs-lookup"><span data-stu-id="b8b66-178">If the `Median` aggregate function is called for a query field of type `Double`, this method will be called.</span></span> <span data-ttu-id="b8b66-179">Второй перегруженный `Median` метод может передаваться любым универсальным типом.</span><span class="sxs-lookup"><span data-stu-id="b8b66-179">The second overload of the `Median` method can be passed any generic type.</span></span> <span data-ttu-id="b8b66-180">Универсальная перегрузка `Median` метода принимает второй параметр, который ссылается на `Func(Of T, Double)` лямбда-выражение, чтобы проецировать значение для типа (из коллекции) в качестве соответствующего значения типа `Double` .</span><span class="sxs-lookup"><span data-stu-id="b8b66-180">The generic overload of the `Median` method takes a second parameter that references the `Func(Of T, Double)` lambda expression to project a value for a type (from a collection) as the corresponding value of type `Double`.</span></span> <span data-ttu-id="b8b66-181">Затем оно делегирует вычисление значения медианы другой перегрузке `Median` метода.</span><span class="sxs-lookup"><span data-stu-id="b8b66-181">It then delegates the calculation of the median value to the other overload of the `Median` method.</span></span> <span data-ttu-id="b8b66-182">Дополнительные сведения о лямбда-выражениях см. в разделе [лямбда-выражения](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b8b66-182">For more information about lambda expressions, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 <span data-ttu-id="b8b66-183">В следующем примере показаны образцы запросов, которые вызывают `Median` агрегатную функцию для коллекции типа `Integer` , и коллекцию типа `Double` .</span><span class="sxs-lookup"><span data-stu-id="b8b66-183">The following example shows sample queries that call the `Median` aggregate function on a collection of type `Integer`, and a collection of type `Double`.</span></span> <span data-ttu-id="b8b66-184">Запрос, вызывающий `Median` агрегатную функцию в коллекции типа, `Double` вызывает перегрузку `Median` метода, принимающего в качестве входных данных коллекцию типа `Double` .</span><span class="sxs-lookup"><span data-stu-id="b8b66-184">The query that calls the `Median` aggregate function on the collection of type `Double` calls the overload of the `Median` method that accepts, as input, a collection of type `Double`.</span></span> <span data-ttu-id="b8b66-185">Запрос, вызывающий `Median` агрегатную функцию для коллекции типа `Integer` , вызывает универсальную перегрузку `Median` метода.</span><span class="sxs-lookup"><span data-stu-id="b8b66-185">The query that calls the `Median` aggregate function on the collection of type `Integer` calls the generic overload of the `Median` method.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="b8b66-186">См. также</span><span class="sxs-lookup"><span data-stu-id="b8b66-186">See also</span></span>

- <span data-ttu-id="b8b66-187">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8b66-187">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="b8b66-188">Запросы</span><span class="sxs-lookup"><span data-stu-id="b8b66-188">Queries</span></span>](index.md)
- [<span data-ttu-id="b8b66-189">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="b8b66-189">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="b8b66-190">Предложение FROM</span><span class="sxs-lookup"><span data-stu-id="b8b66-190">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="b8b66-191">Предложение WHERE</span><span class="sxs-lookup"><span data-stu-id="b8b66-191">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="b8b66-192">Предложение Group By</span><span class="sxs-lookup"><span data-stu-id="b8b66-192">Group By Clause</span></span>](group-by-clause.md)
