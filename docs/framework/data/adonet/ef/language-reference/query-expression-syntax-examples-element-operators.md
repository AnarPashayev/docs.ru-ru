---
title: Примеры синтаксиса выражений запросов. Операторы элементов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 1b73e22e79c665763390561a1e48b2583ec6cd27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614444"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="b728c-102">Примеры синтаксиса выражений запросов. Операторы элементов</span><span class="sxs-lookup"><span data-stu-id="b728c-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="b728c-103">Примеры в этом разделе демонстрируют, как использовать <xref:System.Linq.Enumerable.First%2A> метод для запроса [модели AdventureWorks Sales](https://archive.codeplex.com/?p=msftdbprodsamples) с использованием синтаксиса выражений запроса.</span><span class="sxs-lookup"><span data-stu-id="b728c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using the query expression syntax.</span></span> <span data-ttu-id="b728c-104">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b728c-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b728c-105">В примерах в этом разделе используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="b728c-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="b728c-106">First</span><span class="sxs-lookup"><span data-stu-id="b728c-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="b728c-107">Пример</span><span class="sxs-lookup"><span data-stu-id="b728c-107">Example</span></span>  
 <span data-ttu-id="b728c-108">В следующем примере используется метод <xref:System.Linq.Enumerable.First%2A> для возврата первого контактного лица с фамилией «Brooke».</span><span class="sxs-lookup"><span data-stu-id="b728c-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="b728c-109">См. также</span><span class="sxs-lookup"><span data-stu-id="b728c-109">See also</span></span>

- [<span data-ttu-id="b728c-110">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b728c-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
