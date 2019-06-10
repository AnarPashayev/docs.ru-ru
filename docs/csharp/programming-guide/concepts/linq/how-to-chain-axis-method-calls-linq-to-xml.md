---
title: Практическое руководство. Связанные вызовы метода оси (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 39113c1b96ea7376d61c606aaa5f79715dbe3cab
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485920"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="ddb4c-102">Практическое руководство. Связанные вызовы метода оси (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb4c-102">How to: Chain Axis Method Calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="ddb4c-103">Обычно при написании кода вы будете придерживаться схемы, по которой вызывается метод оси, после чего вызывается одна из осей метода расширений.</span><span class="sxs-lookup"><span data-stu-id="ddb4c-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="ddb4c-104">Существуют две оси с именем `Elements`, которые возвращают коллекцию элементов: методы <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> и <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ddb4c-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ddb4c-105">Можно сочетать эти две оси таким образом, чтобы найти все элементы с указанным именем на заданной глубине дерева.</span><span class="sxs-lookup"><span data-stu-id="ddb4c-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddb4c-106">Пример</span><span class="sxs-lookup"><span data-stu-id="ddb4c-106">Example</span></span>  
 <span data-ttu-id="ddb4c-107">В этом примере с помощью методов<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> и <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> выполняется поиск всех элементов `Name` во всех элементах `Address` во всех элементах `PurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="ddb4c-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="ddb4c-108">В этом примере используется следующий XML-документ: [Пример XML-файла. Несколько заказов на покупку (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ddb4c-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="ddb4c-109">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="ddb4c-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="ddb4c-110">Такой подход оправдан, поскольку одна из реализаций оси `Elements` представляет собой метод расширений <xref:System.Collections.Generic.IEnumerable%601> по отношению к <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="ddb4c-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="ddb4c-111"><xref:System.Xml.Linq.XElement> вычисляется из <xref:System.Xml.Linq.XContainer>, что позволяет вызвать метод <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> по результатам вызова метода <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ddb4c-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddb4c-112">Пример</span><span class="sxs-lookup"><span data-stu-id="ddb4c-112">Example</span></span>  
 <span data-ttu-id="ddb4c-113">Иногда может потребоваться получить все элементы с определенной глубины структуры элементов при условии, что неизвестно, имеются промежуточные предки или нет.</span><span class="sxs-lookup"><span data-stu-id="ddb4c-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="ddb4c-114">Например, в следующем документе может потребоваться получение всех элементов `ConfigParameter`, которые являются дочерними по отношению к элементу `Customer`, кроме `ConfigParameter`, которые являются дочерними по отношению к элементу `Root`.</span><span class="sxs-lookup"><span data-stu-id="ddb4c-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="ddb4c-115">Чтобы это реализовать, можно использовать ось <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ddb4c-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="ddb4c-116">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="ddb4c-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="ddb4c-117">Пример</span><span class="sxs-lookup"><span data-stu-id="ddb4c-117">Example</span></span>  
 <span data-ttu-id="ddb4c-118">Следующий пример демонстрирует тот же способ обработки XML, что и в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="ddb4c-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="ddb4c-119">Дополнительные сведения см. в разделе [Работа с пространствами имен XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ddb4c-119">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ddb4c-120">В этом примере используется следующий XML-документ: [Пример XML-файла. Несколько заказов на покупку в пространстве имен](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="ddb4c-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="ddb4c-121">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="ddb4c-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddb4c-122">См. также</span><span class="sxs-lookup"><span data-stu-id="ddb4c-122">See also</span></span>

- [<span data-ttu-id="ddb4c-123">Оси LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ddb4c-123">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
