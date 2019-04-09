---
title: Примеры синтаксиса запросов на основе методов. Операторы элементов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 3656ea6d2d9602c3790ab4113b5c2f153b4f7c73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188595"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="2d692-102">Примеры синтаксиса запросов на основе методов. Операторы элементов</span><span class="sxs-lookup"><span data-stu-id="2d692-102">Method-Based Query Syntax Examples: Element Operators</span></span>
<span data-ttu-id="2d692-103">Примеры в этом разделе демонстрируют, как использовать <xref:System.Linq.Enumerable.First%2A> метод для запроса [модели AdventureWorks Sales](https://archive.codeplex.com/?p=msftdbprodsamples) с использованием синтаксиса запросов на основе методов.</span><span class="sxs-lookup"><span data-stu-id="2d692-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="2d692-104">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2d692-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2d692-105">Пример в этом разделе используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="2d692-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="2d692-106">First</span><span class="sxs-lookup"><span data-stu-id="2d692-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="2d692-107">Пример</span><span class="sxs-lookup"><span data-stu-id="2d692-107">Example</span></span>  
 <span data-ttu-id="2d692-108">В следующем примере используется <xref:System.Linq.Enumerable.First%2A> метод, чтобы найти первый адрес электронной почты, который начинается со строки «caroline».</span><span class="sxs-lookup"><span data-stu-id="2d692-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="2d692-109">См. также</span><span class="sxs-lookup"><span data-stu-id="2d692-109">See also</span></span>

- [<span data-ttu-id="2d692-110">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="2d692-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
