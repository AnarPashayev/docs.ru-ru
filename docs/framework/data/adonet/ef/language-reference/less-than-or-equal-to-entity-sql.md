---
title: <= (меньше или равно) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: 09f2a7f53d00739b8542cb1149397f24d3b04f42
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161806"
---
# <a name="-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="9d6f4-102">\<= (меньше или равно) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9d6f4-102">\<= (Less Than or Equal To) (Entity SQL)</span></span>

<span data-ttu-id="9d6f4-103">Сравнивает два выражения и определяет, имеет ли левое выражение значение, меньшее или равное значению правого выражения.</span><span class="sxs-lookup"><span data-stu-id="9d6f4-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6f4-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9d6f4-104">Syntax</span></span>  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9d6f4-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="9d6f4-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="9d6f4-106">Любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="9d6f4-106">Any valid expression.</span></span> <span data-ttu-id="9d6f4-107">Оба выражения должны иметь типы данных, допускающие неявное преобразование.</span><span class="sxs-lookup"><span data-stu-id="9d6f4-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9d6f4-108">Типы результата</span><span class="sxs-lookup"><span data-stu-id="9d6f4-108">Result Types</span></span>  

 <span data-ttu-id="9d6f4-109">Значение`true` , если левое выражение меньше или равно правому выражению. В противном случае - значение `false`.</span><span class="sxs-lookup"><span data-stu-id="9d6f4-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d6f4-110">Пример</span><span class="sxs-lookup"><span data-stu-id="9d6f4-110">Example</span></span>  

 <span data-ttu-id="9d6f4-111">Следующий запрос Entity SQL использует оператор сравнения <= для сравнения двух выражений и определяет, имеет ли левое выражение значение, меньшее или равное значению правого выражения.</span><span class="sxs-lookup"><span data-stu-id="9d6f4-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="9d6f4-112">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="9d6f4-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9d6f4-113">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="9d6f4-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9d6f4-114">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9d6f4-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9d6f4-115">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="9d6f4-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="9d6f4-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9d6f4-116">See also</span></span>

- [<span data-ttu-id="9d6f4-117">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9d6f4-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
