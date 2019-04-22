---
title: Практическое руководство. Загрузить XML из файла (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e2d337ad-8ac8-4671-b694-30e5ca1413b7
ms.openlocfilehash: b4f1f9abfa33b76e702b51221715da80c3f66421
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814968"
---
# <a name="how-to-load-xml-from-a-file-visual-basic"></a><span data-ttu-id="176d7-102">Практическое руководство. Загрузить XML из файла (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="176d7-102">How to: Load XML from a File (Visual Basic)</span></span>
<span data-ttu-id="176d7-103">В этом разделе показана загрузка XML из URI с помощью метода <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="176d7-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="176d7-104">Пример</span><span class="sxs-lookup"><span data-stu-id="176d7-104">Example</span></span>  
 <span data-ttu-id="176d7-105">В следующем примере показана загрузка XML-документа из файла.</span><span class="sxs-lookup"><span data-stu-id="176d7-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="176d7-106">В следующем примере загружается файл books.xml и происходит вывод XML-дерева на консоль.</span><span class="sxs-lookup"><span data-stu-id="176d7-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="176d7-107">В этом примере используется следующий XML-документ: [Пример XML-файла. Книги (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="176d7-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim booksFromFile As XElement = XElement.Load("books.xml")  
Console.WriteLine(booksFromFile)  
```  
  
 <span data-ttu-id="176d7-108">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="176d7-108">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="176d7-109">См. также</span><span class="sxs-lookup"><span data-stu-id="176d7-109">See also</span></span>

- [<span data-ttu-id="176d7-110">Синтаксический анализ XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="176d7-110">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
