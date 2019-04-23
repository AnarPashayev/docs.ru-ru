---
title: SELECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: d6250871b8e22b73b49a94ee7ae7835f53a7c7cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306434"
---
# <a name="select-entity-sql"></a><span data-ttu-id="17dde-102">SELECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="17dde-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="17dde-103">Указывает элементы, возвращаемые запросом.</span><span class="sxs-lookup"><span data-stu-id="17dde-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17dde-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17dde-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="17dde-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="17dde-105">Arguments</span></span>  
 <span data-ttu-id="17dde-106">ALL</span><span class="sxs-lookup"><span data-stu-id="17dde-106">ALL</span></span>  
 <span data-ttu-id="17dde-107">Указывает на то, что в результирующем наборе могут появляться повторяющиеся элементы.</span><span class="sxs-lookup"><span data-stu-id="17dde-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="17dde-108">ALL является значением по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="17dde-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="17dde-109">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="17dde-109">DISTINCT</span></span>  
 <span data-ttu-id="17dde-110">Указывает, что в результирующем наборе возвращаются только уникальные результаты.</span><span class="sxs-lookup"><span data-stu-id="17dde-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="17dde-111">VALUE</span><span class="sxs-lookup"><span data-stu-id="17dde-111">VALUE</span></span>  
 <span data-ttu-id="17dde-112">Позволяет указать только один элемент и не добавляет оболочку строк.</span><span class="sxs-lookup"><span data-stu-id="17dde-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="17dde-113">Любое допустимое выражение, указывающее число первых результатов, возвращаемых запросом, в формате `top(expr)`.</span><span class="sxs-lookup"><span data-stu-id="17dde-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="17dde-114">Параметр LIMIT [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) оператор также можно выбрать первые n элементов в результирующем наборе.</span><span class="sxs-lookup"><span data-stu-id="17dde-114">The LIMIT parameter of the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="17dde-115">Выражение в следующем формате.</span><span class="sxs-lookup"><span data-stu-id="17dde-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="17dde-116">`expr` as `identifier` &#124; `expr`</span><span class="sxs-lookup"><span data-stu-id="17dde-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="17dde-117">Литерал или выражение.</span><span class="sxs-lookup"><span data-stu-id="17dde-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17dde-118">Примечания</span><span class="sxs-lookup"><span data-stu-id="17dde-118">Remarks</span></span>  
 <span data-ttu-id="17dde-119">Предложение SELECT вычисляется после [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), и [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) будут вычислены предложения.</span><span class="sxs-lookup"><span data-stu-id="17dde-119">The SELECT clause is evaluated after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), and [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="17dde-120">В предложении SELECT могут быть указаны только те элементы, которые в настоящий момент находящиеся в области (из предложения FROM, из внешних областей).</span><span class="sxs-lookup"><span data-stu-id="17dde-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="17dde-121">Если указано предложение GROUP BY, то предложение SELECT может ссылаться только на псевдонимы для ключей GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="17dde-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="17dde-122">Обращение к элементам предложения FROM допустимо только в агрегатных функциях.</span><span class="sxs-lookup"><span data-stu-id="17dde-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="17dde-123">Список, содержащий одно или более выражений запросов, следующих за ключевым словом SELECT, называется списком выбора, или более формально - проекцией.</span><span class="sxs-lookup"><span data-stu-id="17dde-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="17dde-124">Наиболее распространенная форма проекции - единственное выражение запроса.</span><span class="sxs-lookup"><span data-stu-id="17dde-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="17dde-125">Если выбрать элемент `member1` из коллекции `collection1`, то будет подготовлена новая коллекция всех значений `member1` для каждого объекта в `collection1`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="17dde-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="17dde-126">Например, если `customers` является коллекцией типа `Customer` со свойством `Name` типа `string`, то выбор `Name` из `customers` даст коллекцию строк, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="17dde-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="17dde-127">Можно также воспользоваться синтаксисом JOIN (FULL, INNER, LEFT, OUTER, ON и RIGHT).</span><span class="sxs-lookup"><span data-stu-id="17dde-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="17dde-128">ON требуется для внутренних соединений и недопустим для перекрестных соединений.</span><span class="sxs-lookup"><span data-stu-id="17dde-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="17dde-129">Предложения выбора строк и значений</span><span class="sxs-lookup"><span data-stu-id="17dde-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="17dde-130">поддерживает два варианта предложения SELECT.</span><span class="sxs-lookup"><span data-stu-id="17dde-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="17dde-131">Первый из них - выбор строк, указывается ключевым словом SELECT и может быть использован для указания одного или нескольких проецируемых значений. Поскольку к возвращенным значениям неявным образом добавляется оболочка строк, то результатом выражения запроса всегда является мультимножество строк.</span><span class="sxs-lookup"><span data-stu-id="17dde-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="17dde-132">Для каждого выражения запроса в выборе строки должен быть указан псевдоним.</span><span class="sxs-lookup"><span data-stu-id="17dde-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="17dde-133">Если псевдоним не указан, то[!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается создать его на основе правил создания псевдонимов.</span><span class="sxs-lookup"><span data-stu-id="17dde-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="17dde-134">Другой тип предложения SELECT, выбор значения, идентифицируется ключевым словом SELECT VALUE.</span><span class="sxs-lookup"><span data-stu-id="17dde-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="17dde-135">Он позволяет указать только одно значение и не добавляет оболочку строк.</span><span class="sxs-lookup"><span data-stu-id="17dde-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="17dde-136">Выбор строк всегда можно выразить в терминах VALUE SELECT, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="17dde-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="17dde-137">Модификаторы All и Distinct</span><span class="sxs-lookup"><span data-stu-id="17dde-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="17dde-138">В обоих вариантах предложения SELECT языка [!INCLUDE[esql](../../../../../../includes/esql-md.md)] могут быть указаны модификаторы ALL и DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="17dde-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="17dde-139">Если задан модификатор DISTINCT, то повторяющиеся значения исключаются из коллекции, полученной в результате выполнения выражения запроса (до предложения SELECT включительно).</span><span class="sxs-lookup"><span data-stu-id="17dde-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="17dde-140">Если задан модификатор ALL, то исключение повторяющихся значений не выполняется. ALL является модификатором по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="17dde-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="17dde-141">Отличия от языка Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="17dde-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="17dde-142">В отличие от Transact-SQL, язык [!INCLUDE[esql](../../../../../../includes/esql-md.md)] не поддерживает использование аргумента «\*» в предложении SELECT.</span><span class="sxs-lookup"><span data-stu-id="17dde-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="17dde-143">Вместо этого в языке [!INCLUDE[esql](../../../../../../includes/esql-md.md)] запросы могут проецировать целые записи, ссылаясь на псевдонимы коллекций из предложения FROM, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="17dde-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="17dde-144">Предыдущее выражение запроса [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] выражается на языке [!INCLUDE[esql](../../../../../../includes/esql-md.md)] следующим образом.</span><span class="sxs-lookup"><span data-stu-id="17dde-144">The previous [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="17dde-145">Пример</span><span class="sxs-lookup"><span data-stu-id="17dde-145">Example</span></span>  
 <span data-ttu-id="17dde-146">В следующем запросе Entity SQL оператор SELECT используется для задания элементов, возвращаемых запросом.</span><span class="sxs-lookup"><span data-stu-id="17dde-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="17dde-147">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="17dde-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="17dde-148">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="17dde-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="17dde-149">Выполните процедуру, описанную в [как: Выполнение запроса, возвращающего результаты StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="17dde-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="17dde-150">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="17dde-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="17dde-151">См. также</span><span class="sxs-lookup"><span data-stu-id="17dde-151">See also</span></span>

- [<span data-ttu-id="17dde-152">Выражения запросов</span><span class="sxs-lookup"><span data-stu-id="17dde-152">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [<span data-ttu-id="17dde-153">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="17dde-153">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="17dde-154">TOP</span><span class="sxs-lookup"><span data-stu-id="17dde-154">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
