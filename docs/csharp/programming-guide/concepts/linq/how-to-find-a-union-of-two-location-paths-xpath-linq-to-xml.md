---
title: Практическое руководство. Поиск объединения двух путей расположения (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 9fc88a8784958294ba6077893a5d54110de335a0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593740"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Практическое руководство. Поиск объединения двух путей расположения (XPath-LINQ to XML) (C#)
XPath позволяет найти объединение результатов определения двух путей доступа XPath.  
  
 Выражение XPath:  
  
 `//Category|//Price`  
  
 Те же результаты можно получить с помощью стандартного оператора запроса <xref:System.Linq.Enumerable.Concat%2A>.  
  
## <a name="example"></a>Пример  
 В этом примере осуществляется поиск всех элементов `Category` и всех элементов `Price` и объединение их в одну коллекцию. Обратите внимание, что в запросе [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] вызывается метод <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> для упорядочения результатов. Эти результаты вычисления выражения XPath также представлены в той же последовательности, что и в документе.  
  
 В этом примере используется следующий XML-документ: [Пример XML-файла. Числовые данные (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  
 В этом примере выводятся следующие данные:  
  
```  
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
  