---
title: GROUP BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 574d952e0183eb65c88864f2788eb7d698c9f2ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302950"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="d3486-102">GROUP BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d3486-102">GROUP BY (Entity SQL)</span></span>
<span data-ttu-id="d3486-103">Определяет группы, в которые должны быть помещены объекты, возвращаемые выражением запроса ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="d3486-103">Specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3486-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d3486-104">Syntax</span></span>  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3486-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d3486-105">Arguments</span></span>  
 `aliasedExpression`  
 <span data-ttu-id="d3486-106">Любое допустимое выражение запроса, в котором выполняется группирование.</span><span class="sxs-lookup"><span data-stu-id="d3486-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="d3486-107">Аргумент`expression` может быть свойством или нестатистическим выражением, ссылающимся на свойство, которое возвращается предложением FROM.</span><span class="sxs-lookup"><span data-stu-id="d3486-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="d3486-108">Каждое выражение в предложении GROUP BY должно иметь тип, который может быть проверен на равенство.</span><span class="sxs-lookup"><span data-stu-id="d3486-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="d3486-109">Такими типами обычно являются скалярные примитивы - числа, строки и даты.</span><span class="sxs-lookup"><span data-stu-id="d3486-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="d3486-110">Операция GROUP BY не может быть выполнена по коллекциям.</span><span class="sxs-lookup"><span data-stu-id="d3486-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3486-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="d3486-111">Remarks</span></span>  
 <span data-ttu-id="d3486-112">Если в предложении SELECT включены агрегатные функции \<список выбора >, GROUP BY вычисляет сводное значение для каждой группы.</span><span class="sxs-lookup"><span data-stu-id="d3486-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="d3486-113">Если задано предложение GROUP BY, то каждое имя свойства во всех нестатистических выражениях в списке выбора должно быть включено в список GROUP BY либо выражение GROUP BY должно точно соответствовать выражению списка выбора.</span><span class="sxs-lookup"><span data-stu-id="d3486-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3486-114">Если предложение ORDER BY не задано, то группы, возвращаемые предложением GROUP BY, не упорядочиваются.</span><span class="sxs-lookup"><span data-stu-id="d3486-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="d3486-115">Рекомендуется всегда пользоваться предложением ORDER BY, чтобы данные были представлены в определенном порядке.</span><span class="sxs-lookup"><span data-stu-id="d3486-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="d3486-116">Если предложение GROUP BY задано явным или неявным образом (например, в силу присутствия в запросе предложения HAVING), то текущая область является скрытой и появляется новая область.</span><span class="sxs-lookup"><span data-stu-id="d3486-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="d3486-117">Предложения SELECT, HAVING и ORDER BY больше не смогут ссылаться на имена элементов в предложении FROM.</span><span class="sxs-lookup"><span data-stu-id="d3486-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="d3486-118">Ссылка будет возможна только на сами выражения группирования.</span><span class="sxs-lookup"><span data-stu-id="d3486-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="d3486-119">Для этого каждому выражению группирования можно присвоить новые имена (псевдонимы).</span><span class="sxs-lookup"><span data-stu-id="d3486-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="d3486-120">Если для выражения группирования не задан псевдоним, то [!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается создать псевдоним согласно правилам создания псевдонимов, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d3486-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="d3486-121">Выражения в предложении GROUP BY не могут ссылаться на имена, определенные ранее в том же предложении GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="d3486-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="d3486-122">Помимо имен группирований, в предложениях SELECT, HAVING и ORDER BY могут быть указаны статистические функции.</span><span class="sxs-lookup"><span data-stu-id="d3486-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="d3486-123">Статистическая функция содержит выражение, которое вычисляется для каждого элемента в группе.</span><span class="sxs-lookup"><span data-stu-id="d3486-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="d3486-124">Статистический оператор объединяет значения этих выражений (обычно, но не всегда) в единственное значение.</span><span class="sxs-lookup"><span data-stu-id="d3486-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="d3486-125">Статистическое выражение может ссылаться на исходные имена элементов, которые видны в родительской области, или на любые новые имена, указанные в самом предложении GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="d3486-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="d3486-126">Хотя статистические выражения указываются в предложениях SELECT, HAVING и ORDER BY, они фактически вычисляются в той же области, что и выражения группирования, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d3486-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="d3486-127">В этом запросе предложение GROUP BY применяется для создания отчета о стоимости всех заказов с разбивкой по товарам.</span><span class="sxs-lookup"><span data-stu-id="d3486-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="d3486-128">Товару в выражении группирования присваивается имя `name` , которое затем указывается в списке выбора.</span><span class="sxs-lookup"><span data-stu-id="d3486-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="d3486-129">Запрос также содержит в списке выбора статистическую функцию `sum` , которая внутренним образом ссылается на цену и количество в строке заказа.</span><span class="sxs-lookup"><span data-stu-id="d3486-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="d3486-130">Каждое ключевое выражение GROUP BY должно содержать как минимум одну ссылку на область ввода.</span><span class="sxs-lookup"><span data-stu-id="d3486-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="d3486-131">Пример использования GROUP BY см. в статье [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d3486-131">For an example of using GROUP BY, see [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3486-132">Пример</span><span class="sxs-lookup"><span data-stu-id="d3486-132">Example</span></span>  
 <span data-ttu-id="d3486-133">В следующем запросе Entity SQL оператор GROUP BY задает группы, в которые помещаются объекты, возвращаемые запросом.</span><span class="sxs-lookup"><span data-stu-id="d3486-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="d3486-134">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="d3486-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d3486-135">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="d3486-135">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d3486-136">Выполните процедуру, описанную в [как: Выполнение запроса, возвращающего результаты PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d3486-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="d3486-137">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="d3486-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="d3486-138">См. также</span><span class="sxs-lookup"><span data-stu-id="d3486-138">See also</span></span>

- [<span data-ttu-id="d3486-139">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d3486-139">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="d3486-140">Выражения запросов</span><span class="sxs-lookup"><span data-stu-id="d3486-140">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
