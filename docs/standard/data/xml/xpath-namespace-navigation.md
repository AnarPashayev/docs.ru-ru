---
title: Навигация по пространствам имен XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: 37b9d3e04e075c7ef95420c70881ba9b34e031ce
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709794"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="ae830-102">Навигация по пространствам имен XPath</span><span class="sxs-lookup"><span data-stu-id="ae830-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="ae830-103">Для использования запросов XPath с XML-документами необходимо правильно задавать адреса пространств имен XML и элементов, содержащихся в этих пространствах имен.</span><span class="sxs-lookup"><span data-stu-id="ae830-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="ae830-104">Использование пространств имен устраняет неоднозначность, возникающую, когда имена используются в нескольких контекстах. Например, имя `ID` может относиться к нескольким идентификаторам, связанным с различными элементами XML-документа.</span><span class="sxs-lookup"><span data-stu-id="ae830-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="ae830-105">В синтаксисе пространств имен задаются URI, имена и префиксы, по которым различаются элементы XML-документа.</span><span class="sxs-lookup"><span data-stu-id="ae830-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="ae830-106">В примере из этого раздела показано использование префиксов для навигации по XML-документу с помощью <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="ae830-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="ae830-107">Дополнительные сведения о пространствах имен и синтаксисе см. в разделе [XML Files: основные сведения о пространствах имен XML](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="ae830-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="ae830-108">Объявление пространств имен</span><span class="sxs-lookup"><span data-stu-id="ae830-108">Namespace Declarations</span></span>  
 <span data-ttu-id="ae830-109">Объявление пространств имен позволяет различать элементы XML-документа и обращаться к ним при использовании экземпляра <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="ae830-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="ae830-110">Префиксы пространств имен представляют сокращенный синтаксис для адресации пространств имен.</span><span class="sxs-lookup"><span data-stu-id="ae830-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="ae830-111">Префиксы определяются в форме `<e:Envelope>`e\` представляет сокращение формального URI пространства имен.</span><span class="sxs-lookup"><span data-stu-id="ae830-111">Prefixes are defined by the form: `<e:Envelope>`e\`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="ae830-112">Элемент `Body` можно определить как элемент пространства имен `Envelope`, используя синтаксис `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="ae830-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="ae830-113">Следующий XML-документ в примере навигации из следующего раздела будет упоминаться как `response.xml`.</span><span class="sxs-lookup"><span data-stu-id="ae830-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
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
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="ae830-114">Навигация по префиксу пространства имен</span><span class="sxs-lookup"><span data-stu-id="ae830-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="ae830-115">В коде из этого раздела используются объекты <xref:System.Xml.XPath.XPathNavigator> и <xref:System.Xml.XmlNamespaceManager>, чтобы выбрать элемент `Search` из XML-документа в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="ae830-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="ae830-116">Запрос `xpath` содержит префиксы пространства имен в каждом элементе пути.</span><span class="sxs-lookup"><span data-stu-id="ae830-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="ae830-117">Указание точного идентификатора пространства имен, которое содержит каждый элемент, гарантирует правильную навигацию к элементу `Search` методом <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae830-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="ae830-118">Точность полного указания имен и пространств имен дает не просто удобство.</span><span class="sxs-lookup"><span data-stu-id="ae830-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="ae830-119">Небольшой эксперимент с определением документа и кодом из предыдущих примеров может подтвердить, что навигация без полных имен элементов вызывает исключения.</span><span class="sxs-lookup"><span data-stu-id="ae830-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="ae830-120">Например, если указать определение элемента `<Search>` и строку запроса `xpath = "/s:Envelope/s:Body/Search";` без префикса пространства имен в элементе `Search`, то вместо элемента `null` будет возвращено значение `Search`.</span><span class="sxs-lookup"><span data-stu-id="ae830-120">For example, the element definition: `<Search>`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae830-121">См. также:</span><span class="sxs-lookup"><span data-stu-id="ae830-121">See also</span></span>

- [<span data-ttu-id="ae830-122">Доступ к XML-данным с помощью класса XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ae830-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="ae830-123">Выбор, вычисление и отбор XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ae830-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
