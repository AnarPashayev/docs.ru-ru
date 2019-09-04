---
title: THEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: c64e440e8cd8f86706db69d923ba7085d0cb3b3a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248995"
---
# <a name="then-entity-sql"></a><span data-ttu-id="8d4ed-102">THEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8d4ed-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="8d4ed-103">Результат предложения WHEN, если оно оценивается как значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8d4ed-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d4ed-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8d4ed-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8d4ed-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="8d4ed-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="8d4ed-106">Любое допустимое выражение типа Boolean.</span><span class="sxs-lookup"><span data-stu-id="8d4ed-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="8d4ed-107">Любое допустимое выражение запроса, возвращающее коллекцию.</span><span class="sxs-lookup"><span data-stu-id="8d4ed-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d4ed-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="8d4ed-108">Remarks</span></span>  
 <span data-ttu-id="8d4ed-109">Если аргумент `when_expression` оценивается как значение `true`, результатом является соответствующее значение `then-expression`.</span><span class="sxs-lookup"><span data-stu-id="8d4ed-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="8d4ed-110">Если не выполнено ни одно из условий предложения WHEN, оценивается выражение `else-expression` .</span><span class="sxs-lookup"><span data-stu-id="8d4ed-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="8d4ed-111">Однако, если выражение `else-expression`отсутствует, результат равен NULL.</span><span class="sxs-lookup"><span data-stu-id="8d4ed-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="8d4ed-112">Пример см. в разделе [case](case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8d4ed-112">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d4ed-113">Пример</span><span class="sxs-lookup"><span data-stu-id="8d4ed-113">Example</span></span>  
 <span data-ttu-id="8d4ed-114">В следующем запросе Entity SQL с помощью выражения CASE оценивается набор выражений типа `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="8d4ed-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="8d4ed-115">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="8d4ed-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8d4ed-116">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="8d4ed-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8d4ed-117">Выполните процедуру, описанную в [разделе инструкции. Выполнение запроса, возвращающего тип PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md)результаты.</span><span class="sxs-lookup"><span data-stu-id="8d4ed-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="8d4ed-118">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="8d4ed-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="8d4ed-119">См. также</span><span class="sxs-lookup"><span data-stu-id="8d4ed-119">See also</span></span>

- [<span data-ttu-id="8d4ed-120">CASE</span><span class="sxs-lookup"><span data-stu-id="8d4ed-120">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="8d4ed-121">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8d4ed-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
