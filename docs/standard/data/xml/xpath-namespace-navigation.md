---
title: Навигация по пространствам имен XPath
ms.date: 03/30/2017
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: d5350f0c8f73c5efb0f7d9e4c492a841b4978c36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720897"
---
# <a name="xpath-namespace-navigation"></a>Навигация по пространствам имен XPath

Для использования запросов XPath с XML-документами необходимо правильно задавать адреса пространств имен XML и элементов, содержащихся в этих пространствах имен. Использование пространств имен устраняет неоднозначность, возникающую, когда имена используются в нескольких контекстах. Например, имя `ID` может относиться к нескольким идентификаторам, связанным с различными элементами XML-документа. В синтаксисе пространств имен задаются URI, имена и префиксы, по которым различаются элементы XML-документа.  
  
 В примере из этого раздела показано использование префиксов для навигации по XML-документу с помощью <xref:System.Xml.XPath.XPathNavigator>. Дополнительные сведения о пространствах имен и синтаксисе см. в разделе [Файл XML: общие сведения о пространствах имен XML](/previous-versions/dotnet/articles/bb986013(v=msdn.10)).  
  
## <a name="namespace-declarations"></a>Объявление пространств имен  

 Объявление пространств имен позволяет различать элементы XML-документа и обращаться к ним при использовании экземпляра <xref:System.Xml.XPath.XPathNavigator>. Префиксы пространств имен представляют сокращенный синтаксис для адресации пространств имен.  
  
 Префиксы определяются в следующей форме. `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` В этом синтаксисе префикс `e` представляет сокращение формального URI пространства имен. Элемент `Body` можно определить как элемент пространства имен `Envelope`, используя синтаксис `e:Body`.  
  
 Следующий XML-документ в примере навигации из следующего раздела будет упоминаться как `response.xml`.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a>Навигация по префиксу пространства имен  

 В коде из этого раздела используются объекты <xref:System.Xml.XPath.XPathNavigator> и <xref:System.Xml.XmlNamespaceManager>, чтобы выбрать элемент `Search` из XML-документа в предыдущем разделе. Запрос `xpath` содержит префиксы пространства имен в каждом элементе пути. Указание точного идентификатора пространства имен, которое содержит каждый элемент, гарантирует правильную навигацию к элементу `Search` методом <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>.  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 Точность полного указания имен и пространств имен дает не просто удобство. Небольшой эксперимент с определением документа и кодом из предыдущих примеров может подтвердить, что навигация без полных имен элементов вызывает исключения. Например, если указать определение элемента `<Search xmlns="http://schemas.microsoft.com/v1/Search">` и строку запроса `xpath = "/s:Envelope/s:Body/Search";` без префикса пространства имен в элементе `Search`, то вместо элемента `null` будет возвращено значение `Search`.  
  
## <a name="see-also"></a>См. также

- [Доступ к XML-данным с помощью класса XPathNavigator](accessing-xml-data-using-xpathnavigator.md)
- [Выбор, вычисление и отбор XML-данных с помощью XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
