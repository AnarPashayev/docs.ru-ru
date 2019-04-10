---
title: EXISTS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 72d96c5f24fcedf870370de3792680831145a454
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311140"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="2e9d1-102">EXISTS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2e9d1-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="2e9d1-103">Определяет, является ли коллекция пустой.</span><span class="sxs-lookup"><span data-stu-id="2e9d1-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e9d1-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2e9d1-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="2e9d1-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="2e9d1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2e9d1-106">Любое допустимое выражение, возвращающее коллекцию.</span><span class="sxs-lookup"><span data-stu-id="2e9d1-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="2e9d1-107">NOT</span><span class="sxs-lookup"><span data-stu-id="2e9d1-107">NOT</span></span>  
 <span data-ttu-id="2e9d1-108">Указывает, что результат оператора EXISTS должен быть инвертирован.</span><span class="sxs-lookup"><span data-stu-id="2e9d1-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e9d1-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2e9d1-109">Return Value</span></span>  
 `true` <span data-ttu-id="2e9d1-110">Если коллекция не пуста; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="2e9d1-110">if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e9d1-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="2e9d1-111">Remarks</span></span>  
 <span data-ttu-id="2e9d1-112">EXISTS - это один из операторов работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e9d1-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="2e9d1-113">Все операторы работы с наборами [!INCLUDE[esql](../../../../../../includes/esql-md.md)] выполняются слева направо.</span><span class="sxs-lookup"><span data-stu-id="2e9d1-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="2e9d1-114">Сведения о порядке выполнения [!INCLUDE[esql](../../../../../../includes/esql-md.md)] операторы работы с наборами, см. в разделе [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2e9d1-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e9d1-115">Пример</span><span class="sxs-lookup"><span data-stu-id="2e9d1-115">Example</span></span>  
 <span data-ttu-id="2e9d1-116">В следующем запросе Entity SQL оператор EXISTS используется, чтобы определить, пуста ли коллекция.</span><span class="sxs-lookup"><span data-stu-id="2e9d1-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="2e9d1-117">Запрос основан на модели AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="2e9d1-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2e9d1-118">Для компиляции и запуска этого запроса выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="2e9d1-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2e9d1-119">Выполните процедуру, описанную в [как: Выполнение запроса, возвращающего результаты StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2e9d1-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2e9d1-120">Передайте следующий запрос в качестве аргумента методу `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="2e9d1-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="2e9d1-121">См. также</span><span class="sxs-lookup"><span data-stu-id="2e9d1-121">See also</span></span>

- [<span data-ttu-id="2e9d1-122">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2e9d1-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
