---
title: Практическое руководство. Поиск атрибутов одноуровневых элементов с указанным именем (XPath-LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: 709c21cee37c42f7633b2b108b8846ddd8e3b4e7
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249900"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="ac849-102">Практическое руководство. Поиск атрибутов одноуровневых элементов с указанным именем (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac849-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ac849-103">В этом разделе показано, как найти все атрибуты одноуровневых элементов контекстного узла.</span><span class="sxs-lookup"><span data-stu-id="ac849-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="ac849-104">В коллекции возвращаются только атрибуты с заданным именем.</span><span class="sxs-lookup"><span data-stu-id="ac849-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="ac849-105">Выражение XPath:</span><span class="sxs-lookup"><span data-stu-id="ac849-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="ac849-106">Пример</span><span class="sxs-lookup"><span data-stu-id="ac849-106">Example</span></span>  
 <span data-ttu-id="ac849-107">В этом примере вначале происходит поиск элемента `Book`, затем всех одноуровневых элементов с именем `Book`, а после этого всех атрибутов с именем `id`.</span><span class="sxs-lookup"><span data-stu-id="ac849-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="ac849-108">Результатом становится коллекция атрибутов.</span><span class="sxs-lookup"><span data-stu-id="ac849-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="ac849-109">В этом примере используется следующий XML-документ: [Пример XML-файла. Книги (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ac849-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books as XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>(0)  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XAttribute) = _  
    From el In book.Parent.<Book> _  
    Select el.Attribute("id")  
  
' XPath expression  
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _  
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()  
  
If list1.Count() = list2.Count() And _  
        (list1.Intersect(list2)).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XAttribute In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="ac849-110">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="ac849-110">This example produces the following output:</span></span>  
  
```console  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac849-111">См. также</span><span class="sxs-lookup"><span data-stu-id="ac849-111">See also</span></span>

- [<span data-ttu-id="ac849-112">LINQ to XML для пользователей XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac849-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
