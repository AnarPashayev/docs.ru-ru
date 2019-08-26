---
title: Практическое руководство. Извлечение одного атрибута (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4a1be51c7f0e89a8f211ae523eb102282bd9747b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592648"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="13bf0-102">Практическое руководство. Извлечение одного атрибута (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="13bf0-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="13bf0-103">В этом разделе приведены объяснения способа получения одного атрибута элемента при условии, что название атрибута известно.</span><span class="sxs-lookup"><span data-stu-id="13bf0-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="13bf0-104">Это полезно для составления выражений запросов, при которых требуется найти элемент с определенным атрибутом.</span><span class="sxs-lookup"><span data-stu-id="13bf0-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="13bf0-105">Метод <xref:System.Xml.Linq.XElement.Attribute%2A> класса <xref:System.Xml.Linq.XElement> возвращает значение <xref:System.Xml.Linq.XAttribute> с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="13bf0-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13bf0-106">Пример</span><span class="sxs-lookup"><span data-stu-id="13bf0-106">Example</span></span>  
 <span data-ttu-id="13bf0-107">В следующем примере используется метод <xref:System.Xml.Linq.XElement.Attribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="13bf0-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="13bf0-108">В этом примере выполняется поиск всех потомков в дереве с названием `Phone`, затем атрибута с названием `type`.</span><span class="sxs-lookup"><span data-stu-id="13bf0-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="13bf0-109">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="13bf0-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="13bf0-110">Пример</span><span class="sxs-lookup"><span data-stu-id="13bf0-110">Example</span></span>  
 <span data-ttu-id="13bf0-111">Если требуется получить значение атрибута, можно его задать точно так же, как при работе с объектами <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="13bf0-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="13bf0-112">В следующем примере это показано.</span><span class="sxs-lookup"><span data-stu-id="13bf0-112">The following example demonstrates this.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =   
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="13bf0-113">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="13bf0-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="13bf0-114">предоставляет явные операторы приведения класса <xref:System.Xml.Linq.XAttribute> к `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` и `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="13bf0-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13bf0-115">Пример</span><span class="sxs-lookup"><span data-stu-id="13bf0-115">Example</span></span>  
 <span data-ttu-id="13bf0-116">Следующий пример демонстрирует тот же код атрибута, что и в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="13bf0-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="13bf0-117">Дополнительные сведения см. в статье [Обзор пространств имен DFS (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="13bf0-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 <span data-ttu-id="13bf0-118">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="13bf0-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="13bf0-119">См. также</span><span class="sxs-lookup"><span data-stu-id="13bf0-119">See also</span></span>

- [<span data-ttu-id="13bf0-120">Оси LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="13bf0-120">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
