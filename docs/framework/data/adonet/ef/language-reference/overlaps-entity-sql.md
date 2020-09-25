---
title: OVERLAPS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: 6902a44af343c37ccb26412738d9f96b28551814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204428"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="3c7a2-102">OVERLAPS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3c7a2-102">OVERLAPS (Entity SQL)</span></span>

<span data-ttu-id="3c7a2-103">Определяет, содержат ли две коллекции общие элементы.</span><span class="sxs-lookup"><span data-stu-id="3c7a2-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c7a2-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3c7a2-104">Syntax</span></span>  
  
```sql  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3c7a2-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="3c7a2-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="3c7a2-106">Любое допустимое выражение запроса, которое возвращает коллекцию для сравнения с коллекцией, возвращенной другим выражением запроса.</span><span class="sxs-lookup"><span data-stu-id="3c7a2-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="3c7a2-107">Все выражения должны иметь тот же тип, что и аргумент `expression`, или принадлежать к базовому или производному типу для типа этого аргумента.</span><span class="sxs-lookup"><span data-stu-id="3c7a2-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c7a2-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3c7a2-108">Return Value</span></span>  

 <span data-ttu-id="3c7a2-109">`true` , если две коллекции содержат общие элементы; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="3c7a2-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c7a2-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="3c7a2-110">Remarks</span></span>  

 <span data-ttu-id="3c7a2-111">Перекрытия обеспечивают функционально эквивалент следующего:</span><span class="sxs-lookup"><span data-stu-id="3c7a2-111">OVERLAPS provides functionally equivalent to the following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="3c7a2-112">Оператор OVERLAPS - это один из операторов работы с наборами в языке [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3c7a2-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="3c7a2-113">Все операторы работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] выполняются слева направо.</span><span class="sxs-lookup"><span data-stu-id="3c7a2-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="3c7a2-114">Сведения о приоритетах для [!INCLUDE[esql](../../../../../../includes/esql-md.md)] операторов набора см. в разделе [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3c7a2-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c7a2-115">Пример</span><span class="sxs-lookup"><span data-stu-id="3c7a2-115">Example</span></span>  

 <span data-ttu-id="3c7a2-116">В следующем запросе Entity SQL оператор OVERLAPS используется для определения, имеют ли две коллекции общее значение.</span><span class="sxs-lookup"><span data-stu-id="3c7a2-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="3c7a2-117">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="3c7a2-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3c7a2-118">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="3c7a2-118">To compile and run this, follow these steps:</span></span>  
  
1. <span data-ttu-id="3c7a2-119">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3c7a2-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3c7a2-120">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="3c7a2-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OVERLAPS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="3c7a2-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3c7a2-121">See also</span></span>

- [<span data-ttu-id="3c7a2-122">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3c7a2-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
