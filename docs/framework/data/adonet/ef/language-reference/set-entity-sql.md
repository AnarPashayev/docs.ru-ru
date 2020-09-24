---
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 2ac7db5b22ad21eb152788b6c6d6a8e65c1f6a7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169639"
---
# <a name="set-entity-sql"></a><span data-ttu-id="ded3d-102">SET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ded3d-102">SET (Entity SQL)</span></span>

<span data-ttu-id="ded3d-103">Выражение SET используется для преобразования коллекции объектов в набор путем получения новой коллекции, из которой удалены все повторяющиеся элементы.</span><span class="sxs-lookup"><span data-stu-id="ded3d-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ded3d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ded3d-104">Syntax</span></span>  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="ded3d-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="ded3d-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="ded3d-106">Любое допустимое выражение запроса, возвращающее коллекцию.</span><span class="sxs-lookup"><span data-stu-id="ded3d-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ded3d-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="ded3d-107">Remarks</span></span>  

 <span data-ttu-id="ded3d-108">Выражение набора `SET(c)` логически эквивалентно следующей инструкции SELECT:</span><span class="sxs-lookup"><span data-stu-id="ded3d-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="ded3d-109">Оператор`SET` - это один из операторов работы с наборами в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ded3d-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ded3d-110">Все операторы работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] выполняются слева направо.</span><span class="sxs-lookup"><span data-stu-id="ded3d-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ded3d-111">Дополнительные сведения см. в разделе, [за исключением](except-entity-sql.md) сведений о приоритете для [!INCLUDE[esql](../../../../../../includes/esql-md.md)] операторов набора.</span><span class="sxs-lookup"><span data-stu-id="ded3d-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ded3d-112">Пример</span><span class="sxs-lookup"><span data-stu-id="ded3d-112">Example</span></span>  

 <span data-ttu-id="ded3d-113">В следующем запросе Entity SQL используется выражение SET для преобразования коллекции объектов в набор.</span><span class="sxs-lookup"><span data-stu-id="ded3d-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="ded3d-114">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="ded3d-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ded3d-115">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="ded3d-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ded3d-116">Выполните процедуру, описанную в разделе [инструкции. выполнение запроса, возвращающего тип PrimitiveType результаты](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ded3d-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="ded3d-117">Передайте следующий запрос в качестве аргумента методу `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="ded3d-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a><span data-ttu-id="ded3d-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ded3d-118">See also</span></span>

- [<span data-ttu-id="ded3d-119">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ded3d-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
