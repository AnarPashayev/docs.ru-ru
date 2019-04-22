---
title: Практическое руководство. Фильтрация по атрибуту (XPath-LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ffefb9d6-45ec-4677-a396-dd9c2b36298f
ms.openlocfilehash: 0803fe7a5527a86fcb85abfc160abf34bb32fbb2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822743"
---
# <a name="how-to-filter-on-an-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="8c65a-102">Практическое руководство. Фильтрация по атрибуту (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c65a-102">How to: Filter on an Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8c65a-103">В этом разделе показано, как получать элементы-потомки с указанным именем и атрибут с заданным значением.</span><span class="sxs-lookup"><span data-stu-id="8c65a-103">This topic shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="8c65a-104">Выражение XPath:</span><span class="sxs-lookup"><span data-stu-id="8c65a-104">The XPath expression is:</span></span>  
  
 `.//Address[@Type='Shipping']`  
  
## <a name="example"></a><span data-ttu-id="8c65a-105">Пример</span><span class="sxs-lookup"><span data-stu-id="8c65a-105">Example</span></span>  
 <span data-ttu-id="8c65a-106">В этом примере обнаруживаются все элементы-потомки с именем `Address` и с атрибутом `Type`, имеющим значение «Доставка».</span><span class="sxs-lookup"><span data-stu-id="8c65a-106">This example finds all descendants elements with the name of `Address`, and with a `Type` attribute with a value of "Shipping".</span></span>  
  
 <span data-ttu-id="8c65a-107">В этом примере используется следующий XML-документ: [Пример XML-файла. Несколько заказов на покупку (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8c65a-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In po...<Address> _  
    Where el.@Type = "Shipping" _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    po.XPathSelectElements(".//Address[@Type='Shipping']")  
  
If (list1.Count = list2.Count And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="8c65a-108">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="8c65a-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Address Type="Shipping">  
  <Name>Ellen Adams</Name>  
  <Street>123 Maple Street</Street>  
  <City>Mill Valley</City>  
  <State>CA</State>  
  <Zip>10999</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Cristian Osorio</Name>  
  <Street>456 Main Street</Street>  
  <City>Buffalo</City>  
  <State>NY</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Jessica Arnold</Name>  
  <Street>4055 Madison Ave</Street>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c65a-109">См. также</span><span class="sxs-lookup"><span data-stu-id="8c65a-109">See also</span></span>

- [<span data-ttu-id="8c65a-110">LINQ to XML для пользователей XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c65a-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
