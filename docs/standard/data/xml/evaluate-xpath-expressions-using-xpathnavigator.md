---
title: Вычисление выражения XPath с помощью класса XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: 19e3287a990bbfd793bce892b14f08f31c53faa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687207"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>Вычисление выражения XPath с помощью класса XPathNavigator

Класс <xref:System.Xml.XPath.XPathNavigator> содержит метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> для вычисления выражения Xpath. Метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> принимает выражение XPath, вычисляет его и возвращает соответствующий стандарту W3C тип XPath Boolean, Number, String или Node Set, основанный на результате вычисления выражения XPath.  
  
## <a name="the-evaluate-method"></a>Метод Evaluate  

 Метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> принимает выражение XPath, вычисляет его и возвращает типизированный результат Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>) или Node Set (<xref:System.Xml.XPath.XPathNodeIterator>). К примеру, метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> можно использовать в математическом методе. В следующем примере кода рассчитывается совокупная стоимость всех книг в файле `books.xml`.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 В примере в качестве входных данных используется файл `books.xml`.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>Функции position и last  

 Метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> перегружен. Один из методов <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> принимает объект <xref:System.Xml.XPath.XPathNodeIterator> в качестве параметра. Данный конкретный метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> идентичен методу <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>, который принимает в качестве параметра только объект <xref:System.Xml.XPath.XPathExpression>; единственное отличие состоит в том, что первый метод допускает применение в качестве аргумента набора узлов для обозначения текущего контекста, в котором будут осуществляться вычисления. Этот контекст требуется для функций `position()` и `last()`, поскольку они работают относительно текущего узла контекста. Если функции `position()` и `last()` не используются в качестве предикатов в шаге доступа, эти функции требуют ссылки на набор узлов для выполнения вычислений; иначе функции `position` и `last` возвращают значение `0`.  
  
## <a name="see-also"></a>См. также

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Обработка XML-данных с использованием модели данных XPath](process-xml-data-using-the-xpath-data-model.md)
- [Выборка XML-данных с помощью XPathNavigator](select-xml-data-using-xpathnavigator.md)
- [Соответствие узлов с помощью XPathNavigator](matching-nodes-using-xpathnavigator.md)
- [Типы узлов, распознаваемые запросами XPath](node-types-recognized-with-xpath-queries.md)
- [Запросы XPath и пространства имен](xpath-queries-and-namespaces.md)
- [Скомпилированные выражения XPath](compiled-xpath-expressions.md)
