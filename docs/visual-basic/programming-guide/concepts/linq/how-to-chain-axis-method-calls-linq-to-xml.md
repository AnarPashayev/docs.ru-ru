---
title: Практическое руководство. Связанные вызовы метода оси (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
ms.openlocfilehash: 2b74bcd9b9b61ddbfddcdbdf4c48af6b2fbd68a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832053"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a>Практическое руководство. Связанные вызовы метода оси (LINQ to XML) (Visual Basic)
Обычно при написании кода вы будете придерживаться схемы, по которой вызывается метод оси, после чего вызывается одна из осей метода расширений.  
  
 Существуют две оси с именем `Elements`, которые возвращают коллекцию элементов: методы <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> и <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>. Можно сочетать эти две оси таким образом, чтобы найти все элементы с указанным именем на заданной глубине дерева.  
  
## <a name="example"></a>Пример  
 В этом примере с помощью методов<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> и <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> выполняется поиск всех элементов `Name` во всех элементах `Address` во всех элементах `PurchaseOrder`.  
  
 В этом примере используется следующий XML-документ: [Пример XML-файла. Несколько заказов на покупку (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 Такой подход оправдан, поскольку одна из реализаций оси `Elements` представляет собой метод расширений <xref:System.Collections.Generic.IEnumerable%601> по отношению к <xref:System.Xml.Linq.XContainer>. <xref:System.Xml.Linq.XElement> вычисляется из <xref:System.Xml.Linq.XContainer>, что позволяет вызвать метод <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> по результатам вызова метода <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Пример  
 Иногда может потребоваться получить все элементы с определенной глубины структуры элементов при условии, что неизвестно, имеются промежуточные предки или нет. Например, в следующем документе может потребоваться получение всех элементов `ConfigParameter`, которые являются дочерними по отношению к элементу `Customer`, кроме `ConfigParameter`, которые являются дочерними по отношению к элементу `Root`.  
  
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
  
 Чтобы это реализовать, можно использовать ось <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> следующим образом.  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует тот же способ обработки XML, что и в пространстве имен. Дополнительные сведения см. в разделе [работа с пространствами имен XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 В этом примере используется следующий XML-документ: [Пример XML-файла. Несколько заказов на покупку в пространстве имен](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim names As IEnumerable(Of XElement) = _  
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _  
            Select el  
        For Each e As XElement In names  
            Console.WriteLine(e)  
        Next  
    End Sub  
End Module  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>См. также

- [Оси LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
