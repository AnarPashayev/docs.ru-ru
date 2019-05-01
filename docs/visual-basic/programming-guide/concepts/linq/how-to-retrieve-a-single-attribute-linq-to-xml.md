---
title: Практическое руководство. Извлечение одного атрибута (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: f56bdf86e4b63bc952c1d139aac9ee619b5a5f6c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051290"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a>Практическое руководство. Извлечение одного атрибута (LINQ to XML) (Visual Basic)
В этом разделе приведены объяснения способа получения одного атрибута элемента при условии, что название атрибута известно. Это полезно для составления выражений запросов, при которых требуется найти элемент с определенным атрибутом.  
  
 Метод <xref:System.Xml.Linq.XElement.Attribute%2A> класса <xref:System.Xml.Linq.XElement> возвращает значение <xref:System.Xml.Linq.XAttribute> с указанным именем.  
  
## <a name="example"></a>Пример  
 В следующем примере используется метод <xref:System.Xml.Linq.XElement.Attribute%2A>.  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 В этом примере выполняется поиск всех потомков в дереве с названием `Phone`, затем атрибута с названием `type`.  
  
 Этот код выводит следующие результаты:  
  
```  
home  
work  
```  
  
## <a name="example"></a>Пример  
 Если требуется получить значение атрибута, можно его задать точно так же, как при работе с объектами <xref:System.Xml.Linq.XElement>. В следующем примере это показано.  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 Этот код выводит следующие результаты:  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] предоставляет явные операторы приведения класса <xref:System.Xml.Linq.XAttribute> к `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` и `GUID?`.  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует тот же код атрибута, что и в пространстве имен. Дополнительные сведения см. в разделе [работа с пространствами имен XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 Этот код выводит следующие результаты:  
  
```  
home  
work  
```  
  
## <a name="see-also"></a>См. также

- [Оси LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
