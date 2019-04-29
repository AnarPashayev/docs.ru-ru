---
title: Предварительная атомизация объектов XName (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 250b7aa8060c8196c28725fded090e2a63a0ee54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665849"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>Предварительная атомизация объектов XName (LINQ to XML) (Visual Basic)
Одним из способов повышения производительности в LINQ to XML является предварительная атомизация объектов <xref:System.Xml.Linq.XName>. Предварительная атомизация состоит в том, что необходимо назначить строке объект <xref:System.Xml.Linq.XName>, прежде чем создавать XML-дерево с использованием конструкторов классов <xref:System.Xml.Linq.XElement> и <xref:System.Xml.Linq.XAttribute>. Затем, вместо того чтобы передавать строку в конструктор, где будет выполнено ее неявное преобразование в объект <xref:System.Xml.Linq.XName>, можно передать инициализированный объект <xref:System.Xml.Linq.XName>.  
  
 Таким способом можно повысить производительность при создании большого XML-дерева с рядом повторяющихся имен. Для этого перед построением XML-дерева необходимо объявить и инициализировать объекты <xref:System.Xml.Linq.XName>, а затем в качестве имен элементов и атрибутов указать эти объекты <xref:System.Xml.Linq.XName> вместо строк. Эта техника может дать существенный рост производительности, когда создается большое количество элементов (или атрибутов) с одним и тем же именем.  
  
 Чтобы принять решение об использовании предварительной атомизации, протестируйте этот прием в вашем конкретном случае.  
  
## <a name="example"></a>Пример  
 В следующем примере это показано.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 Следующий пример демонстрирует ту же технику, когда XML-документ находится в пространстве имен.  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 Следующий пример наиболее приближен к реальной ситуации. В этом примере содержимое элементов предоставляется запросом.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 Производительность кода в предыдущем примере выше, чем в следующем, где не выполняется предварительная атомизация имен.  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>См. также

- [Производительность (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [Атомарные объекты XName и XNamespace (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
