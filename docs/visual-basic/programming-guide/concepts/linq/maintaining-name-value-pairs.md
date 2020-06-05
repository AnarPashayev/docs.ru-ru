---
title: Обслуживание пар "имя — значение"
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: 1e30f010311dda393f65b1424e56f5b5ad014963
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389221"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>Поддержка пар "имя-значение" (Visual Basic)
Множеству приложений приходится сохранять данные, которые лучше всего хранить в виде пар «имя-значение». Эти данные могут представлять сведения о конфигурации или глобальные параметры. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] содержит несколько методов, которые облегчают хранение пар «имя-значение». Можно либо оставить информацию в виде атрибутов, либо в виде набора дочерних элементов.  
  
 Одно из отличий между хранением информации в виде атрибутов и в виде дочерних элементов состоит в том, что атрибуты имеют ограничение в том, что для элемента может быть только один атрибут с данным именем. Это ограничение не относится к дочерним элементам.  
  
## <a name="setattributevalue-and-setelementvalue"></a>Методы SetAttributeValue и SetElementValue  
 Два метода <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> и <xref:System.Xml.Linq.XElement.SetElementValue%2A> облегчают хранение в виде пар «имя-значение». Эти два метода имеют похожую семантику.  
  
 С помощью метода <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> можно добавлять, изменять и удалять атрибуты данного элемента.  
  
- При вызове метода <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> с несуществующим именем атрибута этот метод создаст новый атрибут и добавит его в указанный элемент.  
  
- При вызове метода <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> с существующим именем атрибута и с указанным содержимым содержимое данного атрибута замещается указанным содержимым.  
  
- При вызове метода <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> с существующим именем атрибута и с указанием значения NULL в качестве содержимого атрибут удаляется из своего родителя.  
  
 С помощью метода <xref:System.Xml.Linq.XElement.SetElementValue%2A> можно добавлять, изменять и удалять дочерние элементы данного элемента.  
  
- При вызове метода <xref:System.Xml.Linq.XElement.SetElementValue%2A> с несуществующим именем дочернего элемента этот метод создаст новый элемент и добавит его к указанному элементу.  
  
- При вызове метода <xref:System.Xml.Linq.XElement.SetElementValue%2A> с существующим именем элемента и с указанным содержимым содержимое данного элемента замещается указанным содержимым.  
  
- При вызове метода <xref:System.Xml.Linq.XElement.SetElementValue%2A> с существующим именем атрибута и с указанием значения NULL в качестве содержимого атрибут удаляется из своего родителя.  
  
## <a name="example"></a>Пример  
 Следующий пример показывает, как создать элемент без атрибутов. Затем используется метод <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> для создания и поддержания списка пар «имя-значение».  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>Пример  
 Следующий пример показывает, как создать элемент без дочерних элементов. Затем используется метод <xref:System.Xml.Linq.XElement.SetElementValue%2A> для создания и поддержания списка пар «имя-значение».  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 В этом примере выводятся следующие данные:  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>
----
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>
```  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [Изменение деревьев XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)
