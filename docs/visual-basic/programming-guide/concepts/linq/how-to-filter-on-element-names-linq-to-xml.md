---
title: Практическое руководство. Фильтрация по именам элементов (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
ms.openlocfilehash: ccb768030e10d73b839df71093a27ff11b918650
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394341"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a><span data-ttu-id="3ff4c-102">Как выполнить фильтрацию по именам элементов (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ff4c-102">How to: Filter on Element Names (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3ff4c-103">При вызове одного из методов, возвращающих коллекцию <xref:System.Collections.Generic.IEnumerable%601> элементов <xref:System.Xml.Linq.XElement>, можно осуществить фильтрацию по именам элементов.</span><span class="sxs-lookup"><span data-stu-id="3ff4c-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ff4c-104">Пример</span><span class="sxs-lookup"><span data-stu-id="3ff4c-104">Example</span></span>  
 <span data-ttu-id="3ff4c-105">В этом примере показано получение отфильтрованной коллекции потомков, в которой содержатся только потомки с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="3ff4c-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="3ff4c-106">В этом примере используется следующий XML-документ: [Пример XML-файла. Стандартный заказ на покупку (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3ff4c-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim items As IEnumerable(Of XElement) = _  
    From el In po...<ProductName> _  
    Select el  
For Each prdName As XElement In items  
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
Next  
```  
  
 <span data-ttu-id="3ff4c-107">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="3ff4c-107">This code produces the following output:</span></span>  
  
```console  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="3ff4c-108">В других методах, возвращающих коллекции <xref:System.Collections.Generic.IEnumerable%601> элементов <xref:System.Xml.Linq.XElement>, заложен тот же принцип.</span><span class="sxs-lookup"><span data-stu-id="3ff4c-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="3ff4c-109">Их сигнатуры подобны <xref:System.Xml.Linq.XContainer.Elements%2A> и <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ff4c-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="3ff4c-110">Ниже следует полный список методов, имеющих аналогичные сигнатурам методов:</span><span class="sxs-lookup"><span data-stu-id="3ff4c-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="3ff4c-111">Пример</span><span class="sxs-lookup"><span data-stu-id="3ff4c-111">Example</span></span>  
 <span data-ttu-id="3ff4c-112">Следующий пример демонстрирует тот же запрос XML, что и в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="3ff4c-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="3ff4c-113">Дополнительные сведения см. в разделе [Общие сведения о пространствах имен (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3ff4c-113">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3ff4c-114">В этом примере используется следующий XML-документ: [Пример XML-файла. Стандартный заказ на покупку в пространстве имен](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="3ff4c-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim items As IEnumerable(Of XElement) = _  
            From el In po...<aw:ProductName> _  
            Select el  
        For Each prdName As XElement In items  
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="3ff4c-115">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="3ff4c-115">This code produces the following output:</span></span>  
  
```console  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ff4c-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3ff4c-116">See also</span></span>

- [<span data-ttu-id="3ff4c-117">Оси LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ff4c-117">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
