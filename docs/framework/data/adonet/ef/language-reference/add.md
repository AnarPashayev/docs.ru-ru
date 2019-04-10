---
title: + (Добавление)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: 8ecbb7a8b38625f248dbfb5974bb8c64eb482ca2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328274"
---
# <a name="-add"></a><span data-ttu-id="6493d-102">+ (сложение)</span><span class="sxs-lookup"><span data-stu-id="6493d-102">+ (Add)</span></span>
<span data-ttu-id="6493d-103">Складывает два числа.</span><span class="sxs-lookup"><span data-stu-id="6493d-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6493d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6493d-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6493d-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="6493d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6493d-106">Любое допустимое выражение с любым числовым типом данных.</span><span class="sxs-lookup"><span data-stu-id="6493d-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="6493d-107">Типы результата</span><span class="sxs-lookup"><span data-stu-id="6493d-107">Result Types</span></span>  
 <span data-ttu-id="6493d-108">Тип данных, который является результатом неявного повышения типов обоих аргументов.</span><span class="sxs-lookup"><span data-stu-id="6493d-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="6493d-109">Дополнительные сведения о неявном повышении уровня типов, см. в разделе [система типов](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6493d-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6493d-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="6493d-110">Remarks</span></span>  
 <span data-ttu-id="6493d-111">Для типов EDM.String сложение является объединением строк.</span><span class="sxs-lookup"><span data-stu-id="6493d-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6493d-112">Пример</span><span class="sxs-lookup"><span data-stu-id="6493d-112">Example</span></span>  
 <span data-ttu-id="6493d-113">В следующем запросе Entity SQL арифметический оператор сложения (+) используется для сложения двух чисел.</span><span class="sxs-lookup"><span data-stu-id="6493d-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="6493d-114">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="6493d-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6493d-115">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="6493d-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6493d-116">Выполните процедуру, описанную в [как: Выполнение запроса, возвращающего результаты StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6493d-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6493d-117">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="6493d-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="6493d-118">См. также</span><span class="sxs-lookup"><span data-stu-id="6493d-118">See also</span></span>

- [<span data-ttu-id="6493d-119">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6493d-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="6493d-120">Типы концептуальной модели (CSDL)</span><span class="sxs-lookup"><span data-stu-id="6493d-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
