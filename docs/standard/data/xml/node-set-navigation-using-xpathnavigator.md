---
title: Навигация в наборе узлов с помощью XPathNavigator
ms.date: 03/30/2017
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
ms.openlocfilehash: 592acfb5e4065d707f4dda09f349e8b783656148
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714306"
---
# <a name="node-set-navigation-using-xpathnavigator"></a>Навигация в наборе узлов с помощью XPathNavigator

Навигацию по узлам в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> обеспечивают методы просмотра набора узлов класса <xref:System.Xml.XPath.XPathNavigator>. Возможен просмотр всех узлов или набора выбранных узлов, возвращаемого одним из методов выбора класса <xref:System.Xml.XPath.XPathNavigator>.  
  
## <a name="element-node-set-navigation"></a>Навигация в наборе узлов элементов  

 В классе <xref:System.Xml.XPath.XPathNavigator> предусмотрено несколько методов, используемых для навигации по узлам элементов. В следующей таблице показаны доступные методы навигации и описания способов перемещения. В таблицу не включены методы, применяемые для навигации по узлам атрибутов и пространств имен.  
  
 Дополнительные сведения о выборе узлов объекта <xref:System.Xml.XPath.XPathNavigator> см. в руководстве по [выбору, вычислению и отбору данных XML с помощью XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Дополнительные сведения о навигации по узлам атрибутов и пространств имен см. в руководстве по [навигации в узлах атрибутов и пространств имен с помощью XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Метод|Описание|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в положение указанного объекта <xref:System.Xml.XPath.XPathNavigator>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в дочерний узел текущего узла.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в первый узел одного уровня с текущим узлом.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в первый дочерний узел текущего узла.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в указанный элемент в порядке следования документов.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в узел, имеющий атрибут типа `ID` со значением, которое совпадает с данным значением <xref:System.String>.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в следующий узел одного уровня с текущим узлом.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в родительский узел текущего узла.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в предыдущий узел одного уровня с текущим узлом.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в корневой узел XML-документа.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Навигация по узлам комментариев и инструкций по обработке  

 Следующие методы класса <xref:System.Xml.XPath.XPathNavigator> допустимы для перемещения комментариев и инструкций по обработке из других узлов в XML-документ.  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>См. также

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Обработка XML-данных с использованием модели данных XPath](process-xml-data-using-the-xpath-data-model.md)
- [Навигация по узлам атрибутов и пространств имен с помощью XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Извлечение XML-данных с помощью XPathNavigator](extract-xml-data-using-xpathnavigator.md)
- [Доступ к XML-данным со строгой типизацией с помощью XPathNavigator](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
