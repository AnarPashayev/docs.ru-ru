---
title: Выполнение запросов деревьям XML
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 22e3dd873e2be8381f3d8da8f7c4284d09e45543
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411874"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="cf260-102">Выполнение запросов к деревьям XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf260-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="cf260-103">В этом разделе приведены примеры запросов [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf260-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="cf260-104">Дополнительные сведения о создании запросов LINQ см. [в разделе Начало работы с LINQ в Visual Basic](getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="cf260-104">For more information about writing LINQ queries, see [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="cf260-105">После создания экземпляра XML-дерева наиболее эффективным способом извлечения данных из дерева становится запись запросов.</span><span class="sxs-lookup"><span data-stu-id="cf260-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="cf260-106">Кроме того, применение запросов в сочетании с функциональным построением позволяет создать новый XML-документ, имеющий другую форму по сравнению с исходным документом.</span><span class="sxs-lookup"><span data-stu-id="cf260-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf260-107">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="cf260-107">In This Section</span></span>  
  
|<span data-ttu-id="cf260-108">Раздел</span><span class="sxs-lookup"><span data-stu-id="cf260-108">Topic</span></span>|<span data-ttu-id="cf260-109">Описание</span><span class="sxs-lookup"><span data-stu-id="cf260-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="cf260-110">Основные запросы (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf260-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)|<span data-ttu-id="cf260-111">Содержит общие примеры запросов к XML-деревьям.</span><span class="sxs-lookup"><span data-stu-id="cf260-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="cf260-112">Проекции и преобразования (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf260-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="cf260-113">Содержит общие примеры получения проекции и преобразования XML-деревьев.</span><span class="sxs-lookup"><span data-stu-id="cf260-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="cf260-114">Дополнительные методы запросов (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf260-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="cf260-115">Показывает способы выполнения запросов, применимые в более сложных сценариях.</span><span class="sxs-lookup"><span data-stu-id="cf260-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="cf260-116">LINQ to XML для пользователей XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf260-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)|<span data-ttu-id="cf260-117">Представляет число выражений XPath и их эквивалентов [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf260-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="cf260-118">Чистые функциональные преобразования XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf260-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](pure-functional-transformations-of-xml.md)|<span data-ttu-id="cf260-119">Представляет небольшой учебник по написанию запросов в стиле функционального программирования.</span><span class="sxs-lookup"><span data-stu-id="cf260-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf260-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="cf260-120">See also</span></span>

- [<span data-ttu-id="cf260-121">Руководством по программированию (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf260-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](programming-guide-linq-to-xml.md)
- [<span data-ttu-id="cf260-122">Приступая к работе с LINQ в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf260-122">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
