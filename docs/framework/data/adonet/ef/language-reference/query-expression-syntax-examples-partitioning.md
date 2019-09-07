---
title: Примеры синтаксиса выражений запросов. Секционирование
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: b845564c02b55b8729efc893d7eecc48bd60f710
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398549"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="b7f57-102">Примеры синтаксиса выражений запросов. Секционирование</span><span class="sxs-lookup"><span data-stu-id="b7f57-102">Query Expression Syntax Examples: Partitioning</span></span>
<span data-ttu-id="b7f57-103">В примерах этого раздела показано, как использовать <xref:System.Linq.Enumerable.Skip%2A> методы и <xref:System.Linq.Enumerable.Take%2A> для запроса [модели AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) с помощью синтаксиса выражения запроса.</span><span class="sxs-lookup"><span data-stu-id="b7f57-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="b7f57-104">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b7f57-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b7f57-105">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="b7f57-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="b7f57-106">Skip</span><span class="sxs-lookup"><span data-stu-id="b7f57-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="b7f57-107">Пример</span><span class="sxs-lookup"><span data-stu-id="b7f57-107">Example</span></span>  
 <span data-ttu-id="b7f57-108">В следующем примере метод <xref:System.Linq.Enumerable.Skip%2A> используется для получения всех адресов в Сиэттле, кроме первых двух.</span><span class="sxs-lookup"><span data-stu-id="b7f57-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="b7f57-109">Take</span><span class="sxs-lookup"><span data-stu-id="b7f57-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="b7f57-110">Пример</span><span class="sxs-lookup"><span data-stu-id="b7f57-110">Example</span></span>  
 <span data-ttu-id="b7f57-111">В следующем примере метод <xref:System.Linq.Enumerable.Take%2A> используется для получения первых трех адресов в Сиэттле.</span><span class="sxs-lookup"><span data-stu-id="b7f57-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="b7f57-112">См. также</span><span class="sxs-lookup"><span data-stu-id="b7f57-112">See also</span></span>

- [<span data-ttu-id="b7f57-113">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b7f57-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
