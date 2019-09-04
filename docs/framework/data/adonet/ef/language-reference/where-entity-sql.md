---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 8dd0e34a6669b2147052befb17b8f4ff8395aabc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248485"
---
# <a name="where-entity-sql"></a><span data-ttu-id="de2b5-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="de2b5-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="de2b5-103">Предложение WHERE применяется непосредственно после предложения [from](from-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="de2b5-103">The WHERE clause is applied directly after the [FROM](from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de2b5-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="de2b5-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="de2b5-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="de2b5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="de2b5-106">Тип Boolean.</span><span class="sxs-lookup"><span data-stu-id="de2b5-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de2b5-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="de2b5-107">Remarks</span></span>  
 <span data-ttu-id="de2b5-108">В предложении WHERE есть та же семантика, которая описана для Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="de2b5-108">The WHERE clause has the same semantics as described for Transact-SQL.</span></span> <span data-ttu-id="de2b5-109">Она ограничивает набор объектов, полученный выражением запроса, выбирая из исходной коллекции только те элементы, которые соответствуют условию.</span><span class="sxs-lookup"><span data-stu-id="de2b5-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="de2b5-110">Выражение `e` должно иметь тип Boolean.</span><span class="sxs-lookup"><span data-stu-id="de2b5-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="de2b5-111">Предложение WHERE применяется непосредственно после предложения FROM, до выполнения любого группирования, упорядочения или проекции.</span><span class="sxs-lookup"><span data-stu-id="de2b5-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="de2b5-112">Все имена элементов, определенные в предложении FROM, доступны в выражении предложения WHERE.</span><span class="sxs-lookup"><span data-stu-id="de2b5-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de2b5-113">См. также</span><span class="sxs-lookup"><span data-stu-id="de2b5-113">See also</span></span>

- [<span data-ttu-id="de2b5-114">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="de2b5-114">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="de2b5-115">Выражения запросов</span><span class="sxs-lookup"><span data-stu-id="de2b5-115">Query Expressions</span></span>](query-expressions-entity-sql.md)
