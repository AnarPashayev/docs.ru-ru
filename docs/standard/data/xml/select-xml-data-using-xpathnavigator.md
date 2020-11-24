---
title: Выборка XML-данных с помощью XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: 791c1d16db6a2079ccccebf4dc33d5a0eb12d3c5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824978"
---
# <a name="select-xml-data-using-xpathnavigator"></a>Выборка XML-данных с помощью XPathNavigator
Класс <xref:System.Xml.XPath.XPathNavigator> содержит набор методов, используемых для выборки набора узлов в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> с помощью выражения XPath. По набору выбранных узлов можно передвигаться в цикле итерации.  
  
## <a name="xpathnavigator-selection-methods"></a>Методы выбора в классе XPathNavigator  
 Класс <xref:System.Xml.XPath.XPathNavigator> содержит набор методов, используемых для выборки набора узлов в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> с помощью выражения XPath. Класс <xref:System.Xml.XPath.XPathNavigator> содержит также набор оптимизированных методов для выборки узлов-предков, дочерних узлов и узлов-потомков быстрее, чем это можно сделать с помощью выражения XPath. Набор выбранных узлов возвращается в объекте <xref:System.Xml.XPath.XPathNodeIterator> или, если набор состоит из одного узла, в объекте <xref:System.Xml.XPath.XPathNavigator>.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Выбор узлов с помощью выражений XPath  
 Для выбора узлов с помощью выражений XPath используется один из перечисленных ниже методов выборки.  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Эти методы возвращают набор узлов, по которому можно свободно перемещаться с помощью объекта <xref:System.Xml.XPath.XPathNodeIterator>, или, если выбран один узел, в объекте <xref:System.Xml.XPath.XPathNavigator>.  
  
 Перемещение с помощью объекта <xref:System.Xml.XPath.XPathNodeIterator> не влияет на позицию объекта <xref:System.Xml.XPath.XPathNavigator>, использованного для его создания. Объект <xref:System.Xml.XPath.XPathNavigator>, возвращаемый методами <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>, располагается в единственном возвращаемом узле и также не влияет на положение объекта <xref:System.Xml.XPath.XPathNavigator>, с помощью которого создавался.  
  
 В следующем примере показано создание объекта <xref:System.Xml.XPath.XPathNavigator> из объекта <xref:System.Xml.XPath.XPathDocument>, использование метода <xref:System.Xml.XPath.XPathNavigator.Select%2A> для выбора узлов в объекте <xref:System.Xml.XPath.XPathDocument> и использование объекта <xref:System.Xml.XPath.XPathNodeIterator> для итеративного прохода по выбранным узлам.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 В примере в качестве входных данных используется файл `books.xml`.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>Оптимизированные методы выбора  
 Методы <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> и <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> класса <xref:System.Xml.XPath.XPathNavigator> представляют выражения XPath, часто применяемые для получения дочерних узлов, узлов-потомков и узлов-предков. Эти методы оптимизированы по производительности и работают быстрее, чем соответствующие им выражения XPath. Методы <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> и <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> выбирают узлы-потомки, дочерние узлы и узлы-предки на основании значения <xref:System.Xml.XPath.XPathNodeType> или локального имени и URI-кода пространства имен узлов, которые нужно выбрать. Выбранные узлы-потомки, дочерние узлы и узлы-предки возвращаются в объекте <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="see-also"></a>См. также

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Обработка XML-данных с использованием модели данных XPath](process-xml-data-using-the-xpath-data-model.md)
- [Вычисление выражения XPath с помощью класса XPathNavigator](evaluate-xpath-expressions-using-xpathnavigator.md)
- [Соответствие узлов с помощью XPathNavigator](matching-nodes-using-xpathnavigator.md)
- [Типы узлов, распознаваемые запросами XPath](node-types-recognized-with-xpath-queries.md)
- [Запросы XPath и пространства имен](xpath-queries-and-namespaces.md)
- [Скомпилированные выражения XPath](compiled-xpath-expressions.md)
