---
title: Извлечение абзацев и стилей
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: ad904abf9bd94e83b981859662c22787652e294f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413416"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Получение абзацев и их стилей (Visual Basic)
В этом примере составляется запрос, при котором получаются узлы абзацев из документа WordprocessingML. Также идентифицируется стиль каждого абзаца.  
  
 Этот запрос строится на основе запроса, приведенного в предыдущем примере, [с поиском стиля абзаца по умолчанию (Visual Basic)](finding-the-default-paragraph-style.md), который извлекает стиль по умолчанию из списка стилей. Эти сведения требуются для того, чтобы запрос мог идентифицировать стиль абзацев, для которых явно не установлен стиль. Стили абзацев устанавливаются при помощи элемента `w:pPr`. Если абзац не содержит этот элемент, выполняется форматирование стилем по умолчанию.  
  
 В этом разделе объясняется значение некоторых фрагментов запроса, после чего запрос показывается в составе целостного рабочего примера.  
  
## <a name="example"></a>Пример  
 Источник этого запроса по получению всех абзацев документа и их стилей таков:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Это выражение аналогично источнику запроса в предыдущем примере: [Поиск стиля абзаца по умолчанию (Visual Basic)](finding-the-default-paragraph-style.md). Основная разница в том, что здесь используется ось <xref:System.Xml.Linq.XContainer.Descendants%2A> вместо оси <xref:System.Xml.Linq.XContainer.Elements%2A>. В запросе используется ось <xref:System.Xml.Linq.XContainer.Descendants%2A>, поскольку в документах, в которых имеются разделы, абзацы не будут прямыми потомками элемента текста, а будут находиться на два уровня ниже в иерархии. За счет использования оси <xref:System.Xml.Linq.XContainer.Descendants%2A> этот код будет работать вне зависимости от того, используются разделы или нет.  
  
## <a name="example"></a>Пример  
 В этом разделе используется предложение `Let`, чтобы определить элемент, содержащий узел стиля. Если элемент не найден, то `styleNode` устанавливается в значение `Nothing`:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 Предложение `Let` сначала использует ось <xref:System.Xml.Linq.XContainer.Elements%2A> для поиска всех элементов с названием `pPr`, затем использует метод расширений <xref:System.Xml.Linq.Extensions.Elements%2A> для поиска всех дочерних элементов с названием `pStyle` и затем использует стандартный оператор запросов <xref:System.Linq.Enumerable.FirstOrDefault%2A> для объединения коллекции в одно целое. Если коллекция пуста, `styleNode` устанавливается в значение `Nothing`. Это выражение полезно для поиска потомков узла `pStyle`. Обратите внимание, что, если дочерний узел `pPr` не существует, код продолжает работать, а не выводит исключение. Вместо этого узел `styleNode` устанавливается в значение `Nothing`, что именно и требуется для предложения `Let`.  
  
 В этом запросе выполняется проецирование коллекции анонимного типа с двумя членами, `StyleName` и `ParagraphNode`.  
  
## <a name="example"></a>Пример  
 В данном примере обрабатывается документ WordprocessingML, из которого извлекаются узлы абзацев. Также идентифицируется стиль каждого абзаца. Этот пример основан на предыдущих примерах данного учебника. Новый запрос выявляется в комментариях в нижеприведенном коде.  
  
 Инструкции по созданию исходного документа для этого примера можно найти в статье [Создание исходного документа Office Open XML (Visual Basic)](creating-the-source-office-open-xml-document.md).  
  
 В этом примере используются классы, находящиеся в сборке WindowsBase. Используются типы из пространства имен <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 В этом примере при применении к документу, описанному в разделе [Создание исходного документа Office Open XML (Visual Basic)](creating-the-source-office-open-xml-document.md), выводится следующий результат.  
  
```console  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a>Next Steps  
 В следующем разделе, [получив текст абзацев (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), вы создадите запрос для получения текста абзацев.  
  
## <a name="see-also"></a>См. также раздел

- [Руководство. Управление содержимым в документе WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
