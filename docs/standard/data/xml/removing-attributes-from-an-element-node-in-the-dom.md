---
title: Удаление атрибутов из узла элемента в DOM
ms.date: 03/30/2017
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
ms.openlocfilehash: 53922c55295e852a1aa62d847313fbd657a42541
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686765"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>Удаление атрибутов из узла элемента в DOM

Существует много способов удаления атрибутов. Один из них заключается в их удалении из коллекции атрибутов. Для этого выполняются следующие шаги.  
  
1. Возвратите коллекцию атрибутов из элемента с помощью кода `XmlAttributeCollection attrs = elem.Attributes;`.  
  
2. Удалите атрибут из коллекции атрибутов, используя один из трех методов.  
  
    - Метод <xref:System.Xml.XmlAttributeCollection.Remove%2A> удаляет указанный атрибут.  
  
    - Метод <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> удаляет все атрибуты из коллекции, оставляя элемент без атрибутов.  
  
    - Метод <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> удаляет атрибут из коллекции, используя его индексный номер.  
  
 Следующие методы удаляют атрибуты из узла элемента.  
  
- Метод <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> удаляет коллекцию атрибутов.  
  
- Метод <xref:System.Xml.XmlElement.RemoveAttribute%2A> удаляет из коллекции один атрибут по заданному имени.  
  
- Метод <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> удаляет из коллекции один атрибут по индексному номеру.  
  
 Чтобы удалить атрибут, можно также вернуть элемент, вернуть атрибут из коллекции атрибутов и напрямую удалить узел атрибута. Чтобы вернуть атрибут из коллекции атрибутов, можно использовать имя `XmlAttribute attr = attrs["attr_name"];`, индекс `XmlAttribute attr = attrs[0];` или полное имя, включая пространство имен `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.  
  
 Независимо от способа удаления атрибута, существуют специальные ограничения на удаление атрибутов, определенные в определении DTD как атрибуты по умолчанию. Атрибуты по умолчанию нельзя удалять, если не удален элемент, которому они принадлежат. Атрибуты по умолчанию всегда присутствуют в элементах, для которых декларированы атрибуты по умолчанию. Удаление атрибута по умолчанию из коллекции <xref:System.Xml.XmlAttributeCollection> или <xref:System.Xml.XmlElement> приводит к вставке замещающего атрибута в коллекцию <xref:System.Xml.XmlAttributeCollection> элемента и инициализации декларированного значения по умолчанию. Если существует элемент, определенный как `<book att1="1" att2="2" att3="3"></book>`, то существует элемент `book` с тремя атрибутами, объявленными по умолчанию. Реализация модели XML DOM гарантирует, что, пока существует элемент `book`, он имеет три атрибута по умолчанию: `att1`, `att2` и `att3`.  
  
 Если метод <xref:System.Xml.XmlAttribute> вызывается с атрибутом <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A>, он присваивает атрибуту значение String.Empty, поскольку атрибут не может существовать без значения.  
  
## <a name="see-also"></a>См. также

- [Модель объектов документов XML (DOM)](xml-document-object-model-dom.md)
