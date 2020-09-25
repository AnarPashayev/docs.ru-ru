---
title: Практическое руководство. Вызов канонических функций
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: acfbdbaf21fe1d454b68dfef5bf4f88d8020ea65
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204454"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="d9ad7-102">Практическое руководство. Вызов канонических функций</span><span class="sxs-lookup"><span data-stu-id="d9ad7-102">How to: Call Canonical Functions</span></span>

<span data-ttu-id="d9ad7-103">Класс <xref:System.Data.Objects.EntityFunctions> содержит методы, предоставляющие доступ к каноническим функциям для использования в запросах LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="d9ad7-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="d9ad7-104">Сведения о канонических функциях см. в разделе [Канонические функции](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d9ad7-104">For information about canonical functions, see [Canonical Functions](canonical-functions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9ad7-105">Методы <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> и <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> в классе <xref:System.Data.Objects.EntityFunctions> не имеют эквивалентных канонических функций.</span><span class="sxs-lookup"><span data-stu-id="d9ad7-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="d9ad7-106">Канонические функции, которые производят вычисление по ряду значений и возвращают одиночное значение (известные также как статистические канонические функции), могут вызываться напрямую.</span><span class="sxs-lookup"><span data-stu-id="d9ad7-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="d9ad7-107">Другие канонические функции могут вызываться только в составе запроса LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="d9ad7-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="d9ad7-108">Чтобы вызвать агрегатную функцию напрямую, ей необходимо передать экземпляр <xref:System.Data.Objects.ObjectQuery%601>.</span><span class="sxs-lookup"><span data-stu-id="d9ad7-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="d9ad7-109">Дополнительные сведения см. в приведенном ниже втором примере.</span><span class="sxs-lookup"><span data-stu-id="d9ad7-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="d9ad7-110">Некоторые канонические функции можно вызвать с помощью методов среды CLR в запросах LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="d9ad7-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="d9ad7-111">Список методов CLR, соответствующих каноническим функциям, см. [в разделе Сопоставление методов CLR с каноническими](clr-method-to-canonical-function-mapping.md)функциями.</span><span class="sxs-lookup"><span data-stu-id="d9ad7-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9ad7-112">Пример</span><span class="sxs-lookup"><span data-stu-id="d9ad7-112">Example</span></span>  

 <span data-ttu-id="d9ad7-113">В следующем примере используется [модель AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="d9ad7-113">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="d9ad7-114">В этом примере выполняется запрос LINQ to Entities, в котором используется метод <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> для возврата всех продуктов, для которых разница между датами `SellEndDate` и `SellStartDate` меньше 365 суток:</span><span class="sxs-lookup"><span data-stu-id="d9ad7-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d9ad7-115">Пример</span><span class="sxs-lookup"><span data-stu-id="d9ad7-115">Example</span></span>  

 <span data-ttu-id="d9ad7-116">В следующем примере используется [модель AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="d9ad7-116">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="d9ad7-117">В этом примере напрямую вызывается статистическая функция <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> для возврата стандартного отклонения промежуточных итогов `SalesOrderHeader`.</span><span class="sxs-lookup"><span data-stu-id="d9ad7-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="d9ad7-118">Обратите внимание, что в функцию передается экземпляр <xref:System.Data.Objects.ObjectQuery%601>, что позволяет вызывать ее, хотя она и не входит в состав запроса LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="d9ad7-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d9ad7-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d9ad7-119">See also</span></span>

- [<span data-ttu-id="d9ad7-120">Вызов функций в запросах LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d9ad7-120">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="d9ad7-121">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d9ad7-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
