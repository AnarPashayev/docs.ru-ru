---
title: Практическое руководство. Поиск объединения двух путей расположения (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: ebb2ddc3a7ba5e08e99cecca01294e5ad3182e8b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253850"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="d5613-102">Практическое руководство. Поиск объединения двух путей расположения (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5613-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d5613-103">XPath позволяет найти объединение результатов определения двух путей доступа XPath.</span><span class="sxs-lookup"><span data-stu-id="d5613-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="d5613-104">Выражение XPath:</span><span class="sxs-lookup"><span data-stu-id="d5613-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="d5613-105">Те же результаты можно получить с помощью стандартного оператора запроса <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5613-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5613-106">Пример</span><span class="sxs-lookup"><span data-stu-id="d5613-106">Example</span></span>  
 <span data-ttu-id="d5613-107">В этом примере осуществляется поиск всех элементов `Category` и всех элементов `Price` и объединение их в одну коллекцию.</span><span class="sxs-lookup"><span data-stu-id="d5613-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="d5613-108">Обратите внимание, что в запросе [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] вызывается метод <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> для упорядочения результатов.</span><span class="sxs-lookup"><span data-stu-id="d5613-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="d5613-109">Эти результаты вычисления выражения XPath также представлены в той же последовательности, что и в документе.</span><span class="sxs-lookup"><span data-stu-id="d5613-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="d5613-110">В этом примере используется следующий XML-документ: [Пример XML-файла. Числовые данные (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d5613-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d5613-111">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="d5613-111">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  