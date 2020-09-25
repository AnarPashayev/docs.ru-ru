---
title: '* Перемножаемых (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 3dd77270e6765a0431dc473bbbcadeb6481a4699
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175659"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="af8e7-102">\* (умножение) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="af8e7-102">\* (Multiply) (Entity SQL)</span></span>

<span data-ttu-id="af8e7-103">умножает два выражения.</span><span class="sxs-lookup"><span data-stu-id="af8e7-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af8e7-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="af8e7-104">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="af8e7-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="af8e7-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="af8e7-106">Любое допустимое выражение с любым числовым типом данных.</span><span class="sxs-lookup"><span data-stu-id="af8e7-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="af8e7-107">Типы результата</span><span class="sxs-lookup"><span data-stu-id="af8e7-107">Result Types</span></span>  

 <span data-ttu-id="af8e7-108">Тип данных, который является результатом неявного повышения типов обоих аргументов.</span><span class="sxs-lookup"><span data-stu-id="af8e7-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="af8e7-109">Дополнительные сведения о неявном повышении типа см. в разделе [System Type](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="af8e7-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="af8e7-110">Пример</span><span class="sxs-lookup"><span data-stu-id="af8e7-110">Example</span></span>  

 <span data-ttu-id="af8e7-111">В следующем запросе Entity SQL арифметический оператор умножения (\*) используется для умножения двух чисел.</span><span class="sxs-lookup"><span data-stu-id="af8e7-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="af8e7-112">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="af8e7-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="af8e7-113">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="af8e7-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="af8e7-114">Выполните процедуру из статьи [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="af8e7-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="af8e7-115">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="af8e7-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="af8e7-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="af8e7-116">See also</span></span>

- [<span data-ttu-id="af8e7-117">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="af8e7-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
