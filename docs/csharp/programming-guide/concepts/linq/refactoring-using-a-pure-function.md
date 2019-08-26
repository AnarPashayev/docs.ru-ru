---
title: Рефакторинг с использованием чистых функций (C#)
ms.date: 07/20/2015
ms.assetid: a3416a45-9e12-4e4a-9747-897f06eef510
ms.openlocfilehash: d1c4b1fc59e52fbd72dec1ee0e73e7198a083868
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591313"
---
# <a name="refactoring-using-a-pure-function-c"></a><span data-ttu-id="9cf84-102">Рефакторинг с использованием чистых функций (C#)</span><span class="sxs-lookup"><span data-stu-id="9cf84-102">Refactoring Using a Pure Function (C#)</span></span>
<span data-ttu-id="9cf84-103">В приведенном ниже примере выполняется оптимизация кода предыдущего примера [Рефакторинг с использованием метода расширения (C#)](./refactoring-using-an-extension-method.md) для использования чистой функции. При этом код, предназначенный для поиска текста абзаца, перемещен в чисто статический метод `ParagraphText`.</span><span class="sxs-lookup"><span data-stu-id="9cf84-103">The following example refactors the previous example, [Refactoring Using an Extension Method (C#)](./refactoring-using-an-extension-method.md), to use a pure function In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cf84-104">Пример</span><span class="sxs-lookup"><span data-stu-id="9cf84-104">Example</span></span>  
 <span data-ttu-id="9cf84-105">В данном примере обрабатывается документ WordprocessingML, из которого извлекаются узлы абзацев.</span><span class="sxs-lookup"><span data-stu-id="9cf84-105">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="9cf84-106">Также идентифицируется стиль каждого абзаца.</span><span class="sxs-lookup"><span data-stu-id="9cf84-106">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="9cf84-107">Этот пример основан на предыдущих примерах данного учебника.</span><span class="sxs-lookup"><span data-stu-id="9cf84-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="9cf84-108">Оптимизированный код поясняется в комментариях кода ниже.</span><span class="sxs-lookup"><span data-stu-id="9cf84-108">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="9cf84-109">Инструкции по созданию исходного документа для этого примера см. в разделе [Создание исходного документа в формате Office Open XML (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="9cf84-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="9cf84-110">В этом примере используются классы из сборки WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="9cf84-110">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="9cf84-111">Используются типы из пространства имен <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9cf84-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    // This is a new method that assembles the paragraph text.  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace =  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri,  
                      styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="9cf84-112">В этом примере выводятся те же результаты, что и после оптимизации кода:</span><span class="sxs-lookup"><span data-stu-id="9cf84-112">This example produces the same output as before the refactoring:</span></span>  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
### <a name="next-steps"></a><span data-ttu-id="9cf84-113">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="9cf84-113">Next Steps</span></span>  
 <span data-ttu-id="9cf84-114">В следующем примере показано, как выполнить проекцию XML в другую форму:</span><span class="sxs-lookup"><span data-stu-id="9cf84-114">The next example shows how to project XML into a different shape:</span></span>  
  
- [<span data-ttu-id="9cf84-115">Проецирование XML в другую форму (C#)</span><span class="sxs-lookup"><span data-stu-id="9cf84-115">Projecting XML in a Different Shape (C#)</span></span>](./projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="9cf84-116">См. также</span><span class="sxs-lookup"><span data-stu-id="9cf84-116">See also</span></span>

- [<span data-ttu-id="9cf84-117">Учебник. Обработка содержимого документа WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="9cf84-117">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="9cf84-118">Рефакторинг с использованием метода расширения (C#)</span><span class="sxs-lookup"><span data-stu-id="9cf84-118">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)
- [<span data-ttu-id="9cf84-119">Рефакторинг в чистые функции (C#)</span><span class="sxs-lookup"><span data-stu-id="9cf84-119">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)
