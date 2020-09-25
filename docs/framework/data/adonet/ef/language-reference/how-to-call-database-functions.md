---
title: Практическое руководство. Вызов функций базы данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: a4cf77000af56ed2a6445beaef2d7856486b85db
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173670"
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="761fb-102">Практическое руководство. Вызов функций базы данных</span><span class="sxs-lookup"><span data-stu-id="761fb-102">How to: Call Database Functions</span></span>

<span data-ttu-id="761fb-103">Класс <xref:System.Data.Objects.SqlClient.SqlFunctions> содержит методы среды CLR, предоставляющие доступ к функциям SQL Server для использования в запросах LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="761fb-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="761fb-104">При использовании методов <xref:System.Data.Objects.SqlClient.SqlFunctions> в запросах LINQ to Entities в базе данных выполняются соответствующие функции базы данных.</span><span class="sxs-lookup"><span data-stu-id="761fb-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="761fb-105">Функции базы данных, которые производят вычисление по ряду значений и возвращают одиночное значение (известные также как статистические функции баз данных), могут вызываться напрямую.</span><span class="sxs-lookup"><span data-stu-id="761fb-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="761fb-106">Другие канонические функции могут вызываться только в составе запроса LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="761fb-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="761fb-107">Чтобы вызвать агрегатную функцию напрямую, ей необходимо передать экземпляр <xref:System.Data.Objects.ObjectQuery%601>.</span><span class="sxs-lookup"><span data-stu-id="761fb-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="761fb-108">Дополнительные сведения см. в приведенном ниже втором примере.</span><span class="sxs-lookup"><span data-stu-id="761fb-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="761fb-109">Методы класса <xref:System.Data.Objects.SqlClient.SqlFunctions> поддерживаются только в функциях SQL Server.</span><span class="sxs-lookup"><span data-stu-id="761fb-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="761fb-110">Аналогичные классы, предоставляющие функции баз данных, могут быть доступны в других поставщиках.</span><span class="sxs-lookup"><span data-stu-id="761fb-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="761fb-111">Пример</span><span class="sxs-lookup"><span data-stu-id="761fb-111">Example</span></span>  

 <span data-ttu-id="761fb-112">В следующем примере используется [модель AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="761fb-112">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="761fb-113">В примере выполняется запрос LINQ to Entities, в котором с помощью метода <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> возвращаются все контакты, в которых фамилия начинается с «Si»:</span><span class="sxs-lookup"><span data-stu-id="761fb-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="761fb-114">Пример</span><span class="sxs-lookup"><span data-stu-id="761fb-114">Example</span></span>  

 <span data-ttu-id="761fb-115">В следующем примере используется [модель AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="761fb-115">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="761fb-116">В примере напрямую вызывается статистический метод <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A>.</span><span class="sxs-lookup"><span data-stu-id="761fb-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="761fb-117">Обратите внимание, что в функцию передается экземпляр <xref:System.Data.Objects.ObjectQuery%601>, что позволяет вызывать ее, хотя она и не входит в состав запроса LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="761fb-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="761fb-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="761fb-118">See also</span></span>

- [<span data-ttu-id="761fb-119">Вызов функций в запросах LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="761fb-119">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="761fb-120">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="761fb-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
