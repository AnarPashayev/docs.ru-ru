---
title: Практическое руководство. Загрузка XML-кода из файла (C#)
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: d3e7cdbb0691fafcfcfc684f4495f4785b4ea3e7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593178"
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="22f9f-102">Практическое руководство. Загрузка XML-кода из файла (C#)</span><span class="sxs-lookup"><span data-stu-id="22f9f-102">How to: Load XML from a File (C#)</span></span>
<span data-ttu-id="22f9f-103">В этом разделе показана загрузка XML из URI с помощью метода <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22f9f-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22f9f-104">Пример</span><span class="sxs-lookup"><span data-stu-id="22f9f-104">Example</span></span>  
 <span data-ttu-id="22f9f-105">В следующем примере показана загрузка XML-документа из файла.</span><span class="sxs-lookup"><span data-stu-id="22f9f-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="22f9f-106">В следующем примере загружается файл books.xml и происходит вывод XML-дерева на консоль.</span><span class="sxs-lookup"><span data-stu-id="22f9f-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="22f9f-107">В этом примере используется следующий XML-документ: [Пример XML-файла. Книги (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="22f9f-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="22f9f-108">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="22f9f-108">This code produces the following output:</span></span>  
  
```xml  
<Catalog>  
  <Book id="bk101">  
    <Author>Garghentini, Davide</Author>  
    <Title>XML Developer's Guide</Title>  
    <Genre>Computer</Genre>  
    <Price>44.95</Price>  
    <PublishDate>2000-10-01</PublishDate>  
    <Description>An in-depth look at creating applications   
      with XML.</Description>  
  </Book>  
  <Book id="bk102">  
    <Author>Garcia, Debra</Author>  
    <Title>Midnight Rain</Title>  
    <Genre>Fantasy</Genre>  
    <Price>5.95</Price>  
    <PublishDate>2000-12-16</PublishDate>  
    <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
  </Book>  
</Catalog>  
```  
  