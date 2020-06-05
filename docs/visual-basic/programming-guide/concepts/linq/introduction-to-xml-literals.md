---
title: Общие сведения о литералах XML в Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 8b92d22727c50274d57a5e407a0ca42807de3a94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397588"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Знакомство с литералами XML в Visual Basic
В этом разделе содержатся сведения о создании деревьев XML в Visual Basic.  
  
 Сведения об использовании результатов запросов LINQ в качестве содержимого XML-дерева см. в разделе [функциональное построение (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).  
  
 Дополнительные сведения о литералах XML в Visual Basic см. в разделе [обзор LINQ to XML в Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>Создание деревьев XML  
 В следующем примере показано, как создать объект <xref:System.Xml.Linq.XElement>. В этом случае дерево `contacts`:  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a>Создание объекта XElement с простым содержимым  
 Следующим образом можно создать объект <xref:System.Xml.Linq.XElement> с простым содержимым.  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Создание пустого элемента  
 Следующим образом можно создать пустой объект <xref:System.Xml.Linq.XElement>:  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Использование внедренных выражений  
 Важной характеристикой XML-литералов является использование внедренных выражений. Внедренные выражения позволяют вычислять выражения и вставлять результаты вычисления в XML-дерево. Если результат выражения имеет тип объекта <xref:System.Xml.Linq.XElement>, элемент вставляется в дерево. Если результат выражения имеет тип объекта <xref:System.Xml.Linq.XAttribute>, атрибут вставляется в дерево. Элементы и атрибуты можно вставлять в дерево, только если они допустимы.  
  
 Важно отметить, что только простое выражение может входить во внедренное выражение. Можно внедрять несколько инструкций. Если выражение выходит за пределы одной строки, нужно использовать знак объединения строк.  
  
 Если использовать внедренное выражение для добавления существующих узлов (включая элементы) и атрибутов в новое XML-дерево и если существующие узлы уже имеют родителей, узлы копируются. Скопированные узлы присоединяются к новому XML-дереву. Если существующие узлы не имеют родителей, узлы просто присоединяются к новому XML-дереву. Это демонстрирует последний пример из данного раздела.  
  
 В следующем примере используется внедренное выражение для вставки элементов в дерево:  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>Использование внедренных выражений в содержимом  
 Можно использовать внедренное выражение для создания содержимого элемента:  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Использование запросов LINQ во внедренном выражении  
 Можно использовать результаты запросов LINQ для создания содержимого элемента:  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>Использование внедренных выражений для создания имен узлов  
 Можно также использовать внедренные выражения для вычисления имен атрибутов, значений атрибутов, имен элементов и значений элементов:  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>Сравнение клонирования и присоединения  
 Как уже было сказано, если использовать внедренное выражение для добавления существующих узлов (включая элементы) и атрибутов в новое XML-дерево и если существующие узлы уже имеют родителей, узлы копируются и присоединяются к новому XML-дереву. Если существующие узлы не имеют родителей, узлы просто присоединяются к новому XML-дереву.  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 В этом примере выводятся следующие данные:  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>См. также

- [Создание деревьев XML (Visual Basic)](creating-xml-trees.md)
