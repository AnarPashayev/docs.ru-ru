---
title: Поиск стиля абзаца по умолчанию (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 5cbe1ad7b3a384448a4e570156b45f57446e73e6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485989"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="312f5-102">Поиск стиля абзаца по умолчанию (C#)</span><span class="sxs-lookup"><span data-stu-id="312f5-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="312f5-103">Первая задача в учебнике "Обработка информации в документе WordprocessingML" заключается в поиске стиля абзацев по умолчанию в документе.</span><span class="sxs-lookup"><span data-stu-id="312f5-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="312f5-104">Пример</span><span class="sxs-lookup"><span data-stu-id="312f5-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="312f5-105">Описание</span><span class="sxs-lookup"><span data-stu-id="312f5-105">Description</span></span>  
 <span data-ttu-id="312f5-106">В следующем примере открывается документ Office Open XML WordprocessingML, осуществляется поиск секций с документом и стилями в пакете, а затем выполняется запрос, который находит имя стиля по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="312f5-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="312f5-107">Сведения о пакетах документов Office Open XML и частях, из которых они состоят, см. в разделе [Сведения о документах WordprocessingML в формате Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/wordprocessingml-document-with-styles.md).</span><span class="sxs-lookup"><span data-stu-id="312f5-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="312f5-108">Этот запрос находит узел с именем `w:style`, который имеет атрибут `w:type` со значением «paragraph», а также имеет атрибут `w:default` со значением «1».</span><span class="sxs-lookup"><span data-stu-id="312f5-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="312f5-109">Так как XML-узел с этими атрибутами будет только один, запрос использует оператор <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType>, чтобы преобразовать коллекцию в один элемент.</span><span class="sxs-lookup"><span data-stu-id="312f5-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="312f5-110">Затем он возвращает значение атрибута `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="312f5-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="312f5-111">В этом примере используются классы из сборки WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="312f5-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="312f5-112">Используются типы из пространства имен <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="312f5-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="312f5-113">Код</span><span class="sxs-lookup"><span data-stu-id="312f5-113">Code</span></span>  
  
```csharp  
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
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a><span data-ttu-id="312f5-114">Комментарии</span><span class="sxs-lookup"><span data-stu-id="312f5-114">Comments</span></span>  
 <span data-ttu-id="312f5-115">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="312f5-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="312f5-116">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="312f5-116">Next Steps</span></span>  
 <span data-ttu-id="312f5-117">В следующем примере будет создан похожий запрос, который ищет все абзацы в документе и их стили:</span><span class="sxs-lookup"><span data-stu-id="312f5-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="312f5-118">Извлечение абзацев и стилей (C#)</span><span class="sxs-lookup"><span data-stu-id="312f5-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  