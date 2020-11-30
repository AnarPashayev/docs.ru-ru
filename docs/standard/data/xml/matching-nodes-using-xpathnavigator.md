---
title: Соответствие узлов с помощью XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: 2d598a4ddfe84eec7288d111fc156dd0c555a10e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720130"
---
# <a name="matching-nodes-using-xpathnavigator"></a>Соответствие узлов с помощью XPathNavigator

Класс <xref:System.Xml.XPath.XPathNavigator> содержит метод <xref:System.Xml.XPath.XPathNavigator.Matches%2A> для проверки совпадения узла и выражения XPath. Метод <xref:System.Xml.XPath.XPathNavigator.Matches%2A> принимает в качестве входного аргумента выражение XPath и возвращает значение типа <xref:System.Boolean>, указывающее, совпадает ли текущий узел с заданным выражением XPath или скомпилированным объектом <xref:System.Xml.XPath.XPathExpression>.  
  
## <a name="matching-nodes"></a>Совпадение узлов  

 Метод <xref:System.Xml.XPath.XPathNavigator.Matches%2A> возвращает значение `true`, если текущий узел совпадает с заданным выражением XPath. Например, в следующем примере кода метод <xref:System.Xml.XPath.XPathNavigator.Matches%2A> вернет значение `true`, если текущим узлом является элемент `b`, а элемент `b` содержащий атрибут `c`.  
  
> [!NOTE]
> Метод <xref:System.Xml.XPath.XPathNavigator.Matches%2A> не изменяет состояние объекта <xref:System.Xml.XPath.XPathNavigator>.  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Обработка XML-данных с использованием модели данных XPath](process-xml-data-using-the-xpath-data-model.md)
- [Выборка XML-данных с помощью XPathNavigator](select-xml-data-using-xpathnavigator.md)
- [Вычисление выражения XPath с помощью класса XPathNavigator](evaluate-xpath-expressions-using-xpathnavigator.md)
- [Типы узлов, распознаваемые запросами XPath](node-types-recognized-with-xpath-queries.md)
- [Запросы XPath и пространства имен](xpath-queries-and-namespaces.md)
- [Скомпилированные выражения XPath](compiled-xpath-expressions.md)
