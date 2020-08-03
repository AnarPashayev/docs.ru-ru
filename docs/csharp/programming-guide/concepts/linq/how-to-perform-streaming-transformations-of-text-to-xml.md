---
title: Выполнение потоковых преобразований текста в XML (C#)
description: Узнайте, как в C# выполнить потоковое преобразование текста в XML с построчной обработкой текстового файла и использовать запрос LINQ для обработки текстового файла.
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: f933064be70d39b59cf7dbe51b4ee92e5226647a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104753"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="ea4ca-103">Выполнение потоковых преобразований текста в XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ea4ca-103">How to perform streaming transformations of text to XML (C#)</span></span>

<span data-ttu-id="ea4ca-104">Одним из вариантов обработки текстового файла является написание метода расширения, который обрабатывает текстовый файл построчно при помощи конструкции `yield return`.</span><span class="sxs-lookup"><span data-stu-id="ea4ca-104">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="ea4ca-105">Затем можно будет написать запрос LINQ, обрабатывающий текстовый файл в отложенной манере.</span><span class="sxs-lookup"><span data-stu-id="ea4ca-105">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="ea4ca-106">При использовании объекта <xref:System.Xml.Linq.XStreamingElement> для формирования выходного потока можно создать преобразование из текстового файла в XML, которое будет использовать минимальный объем памяти независимо от размера исходного текстового файла.</span><span class="sxs-lookup"><span data-stu-id="ea4ca-106">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

 <span data-ttu-id="ea4ca-107">Следует сказать несколько слов о потоковых преобразованиях.</span><span class="sxs-lookup"><span data-stu-id="ea4ca-107">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="ea4ca-108">Потоковое преобразование лучше всего применять в ситуациях, когда можно обработать весь файл один раз, а также если можно обработать строки в том порядке, в котором они расположены в исходном документе.</span><span class="sxs-lookup"><span data-stu-id="ea4ca-108">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="ea4ca-109">Если файл требуется обрабатывать более одного раза или необходимо сортировать строки перед обработкой, потоковый метод теряет многие из своих преимуществ.</span><span class="sxs-lookup"><span data-stu-id="ea4ca-109">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>

## <a name="example"></a><span data-ttu-id="ea4ca-110">Пример</span><span class="sxs-lookup"><span data-stu-id="ea4ca-110">Example</span></span>

 <span data-ttu-id="ea4ca-111">В качестве исходного для этого примера используется текстовый файл People.txt.</span><span class="sxs-lookup"><span data-stu-id="ea4ca-111">The following text file, People.txt, is the source for this example.</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 <span data-ttu-id="ea4ca-112">Следующий код содержит метод расширения, который обрабатывает строки текстового файла в отложенной манере.</span><span class="sxs-lookup"><span data-stu-id="ea4ca-112">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
        while ((line = source.ReadLine()) != null)
        {
            yield return line;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
            from line in sr.Lines()
            let items = line.Split(',')
            where !line.StartsWith("#")
            select new XElement("Person",
                       new XAttribute("ID", items[0]),
                       new XElement("First", items[1]),
                       new XElement("Last", items[2]),
                       new XElement("Occupation", items[3])
                   )
        );
        Console.WriteLine(xmlTree);
        sr.Close();
    }
}
```

 <span data-ttu-id="ea4ca-113">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="ea4ca-113">This example produces the following output:</span></span>

```xml
<Root>
  <Person ID="1">
    <First>Tai</First>
    <Last>Yee</Last>
    <Occupation>Writer</Occupation>
  </Person>
  <Person ID="2">
    <First>Nikolay</First>
    <Last>Grachev</Last>
    <Occupation>Programmer</Occupation>
  </Person>
  <Person ID="3">
    <First>David</First>
    <Last>Wright</Last>
    <Occupation>Inventor</Occupation>
  </Person>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="ea4ca-114">См. также</span><span class="sxs-lookup"><span data-stu-id="ea4ca-114">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
