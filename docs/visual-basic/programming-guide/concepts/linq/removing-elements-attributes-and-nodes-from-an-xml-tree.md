---
title: Удаление элементов, атрибутов и узлов из дерева XML
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: f8be7fe521fb3c2662b105e34fd96fea1d1ac6e7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413415"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a>Удаление элементов, атрибутов и узлов из XML-дерева (Visual Basic)
Можно вносить изменения в XML-дерево, удаляя элементы, атрибуты и узлы других типов.  
  
 Удаление одного элемента или атрибута из XML-документа является простой операцией. Но при удалении коллекций элементов или атрибутов необходимо вначале материализовать коллекцию в список, а затем удалить элементы или атрибуты из списка. Наилучшим подходом является использование метода расширения <xref:System.Xml.Linq.Extensions.Remove%2A>, позволяющего выполнить эту задачу.  
  
 Основной причиной этого является то, что большинство коллекций, получаемых из XML-дерева, формируется с помощью отложенного выполнения. Если не проводится их предварительная материализация в список или не используются методы расширения, то становится возможным возникновение определенного класса ошибок. Дополнительные сведения см. в разделе [ошибки смешанного декларативного кода/императивного кода (LINQ to XML) (Visual Basic)](mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).  
  
 Следующие методы позволяют удалять узлы и атрибуты из XML-дерева.  
  
|Метод|Описание:|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Удаляет <xref:System.Xml.Linq.XAttribute> из его родительского элемента.|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Удаляет дочерние узлы из <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Удаляет содержимое и атрибуты из <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Удаляет атрибуты <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Передача `null` в качестве значения приводит к удалению атрибута.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Передача `null` в качестве значения приводит к удалению дочернего элемента.|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Удаляет <xref:System.Xml.Linq.XNode> из его родительского элемента.|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Удаляет каждый атрибут или элемент исходной коллекции из своего родительского элемента.|  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание:  
 В этом примере показано три подхода к удалению элементов. Сначала удаляется одиночный элемент. Затем он возвращает коллекцию элементов, материализует их с помощью оператора <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> и удаляет коллекцию. Наконец, он получает коллекцию элементов и удаляет их с помощью метода расширения <xref:System.Xml.Linq.Extensions.Remove%2A>.  
  
 Дополнительные сведения об <xref:System.Linq.Enumerable.ToList%2A> операторе см. в разделе [Преобразование типов данных (Visual Basic)](converting-data-types.md).  
  
### <a name="code"></a>Код  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
```  
  
### <a name="comments"></a>Комментарии  
 Этот код выводит следующие результаты:  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 Обратите внимание, что первый внучатый элемент был удален из `Child1`. Все внучатые элементы были удалены из `Child2` и `Child3`.  
  
## <a name="see-also"></a>См. также раздел

- [Изменение деревьев XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)
