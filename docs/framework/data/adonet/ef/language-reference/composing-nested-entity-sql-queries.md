---
title: Составление вложенных запросов Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 3aa2e53b584eece9cc5e2d26791c78ffe33f9e35
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251140"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="d05f6-102">Составление вложенных запросов Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d05f6-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="d05f6-103">- это богатый функциональный язык.</span><span class="sxs-lookup"><span data-stu-id="d05f6-103">is a rich functional language.</span></span> <span data-ttu-id="d05f6-104">Стандартный блок [!INCLUDE[esql](../../../../../../includes/esql-md.md)] является выражением.</span><span class="sxs-lookup"><span data-stu-id="d05f6-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="d05f6-105">В отличие от обычного SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , не ограничивается табличным результирующим набором: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] поддерживает составление сложных выражений, которые могут иметь литералы, параметры или вложенные выражения.</span><span class="sxs-lookup"><span data-stu-id="d05f6-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="d05f6-106">Значение в выражении может быть параметризовано или состоять из другого выражения.</span><span class="sxs-lookup"><span data-stu-id="d05f6-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="d05f6-107">Вложенные выражения</span><span class="sxs-lookup"><span data-stu-id="d05f6-107">Nested Expressions</span></span>  
 <span data-ttu-id="d05f6-108">Вложенное выражение можно разместить в любом месте, где допустим тип возвращаемого им значения.</span><span class="sxs-lookup"><span data-stu-id="d05f6-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="d05f6-109">Например:</span><span class="sxs-lookup"><span data-stu-id="d05f6-109">For example:</span></span>  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="d05f6-110">Вложенный запрос можно разместить в предложении проекции.</span><span class="sxs-lookup"><span data-stu-id="d05f6-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="d05f6-111">Например:</span><span class="sxs-lookup"><span data-stu-id="d05f6-111">For example:</span></span>  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="d05f6-112">В [!INCLUDE[esql](../../../../../../includes/esql-md.md)] вложенные запросы всегда должны быть заключены в скобки.</span><span class="sxs-lookup"><span data-stu-id="d05f6-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="d05f6-113">В следующем примере показывается, как правильно вкладывать выражения [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [Как Закажите объединение двух запросов](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d05f6-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="d05f6-114">Вложенные запросы в проекции</span><span class="sxs-lookup"><span data-stu-id="d05f6-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="d05f6-115">Вложенные запросы в предложении проекции могут быть переведены в запросы декартового произведения на сервере.</span><span class="sxs-lookup"><span data-stu-id="d05f6-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="d05f6-116">На некоторых внутренних серверах, в том числе на серверах SLQ Server, это может привести к чрезмерному разрастанию таблицы TempDB, что может отрицательно сказаться на производительности.</span><span class="sxs-lookup"><span data-stu-id="d05f6-116">In some backend servers, including SLQ Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="d05f6-117">Ниже приводится пример подобного запроса:</span><span class="sxs-lookup"><span data-stu-id="d05f6-117">The following is an example of such a query:</span></span>  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="d05f6-118">Упорядочение вложенных запросов</span><span class="sxs-lookup"><span data-stu-id="d05f6-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="d05f6-119">Платформа Entity Framework позволяет разместить вложенное выражение в любом месте запроса.</span><span class="sxs-lookup"><span data-stu-id="d05f6-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="d05f6-120">Поскольку Entity SQL обеспечивает большую гибкость в написании запросов, можно создавать запросы, содержащие упорядочивание вложенных запросов.</span><span class="sxs-lookup"><span data-stu-id="d05f6-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="d05f6-121">Однако порядок во вложенном запросе не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="d05f6-121">However, the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="d05f6-122">См. также</span><span class="sxs-lookup"><span data-stu-id="d05f6-122">See also</span></span>

- [<span data-ttu-id="d05f6-123">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d05f6-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
