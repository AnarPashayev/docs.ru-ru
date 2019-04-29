---
title: Поиск стиля абзаца по умолчанию (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: 0694c9144e44e4a5de262f97581eb18943937243
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931317"
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a>Поиск стиля абзаца по умолчанию (Visual Basic)
Первая задача в учебнике "Обработка информации в документе WordprocessingML" заключается в поиске стиля абзацев по умолчанию в документе.  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере открывается документ Office Open XML WordprocessingML, осуществляется поиск секций с документом и стилями в пакете, а затем выполняется запрос, который находит имя стиля по умолчанию. Сведения о пакетах документа Office Open XML и частях, из которых они состоят, см. в разделе [сведения об Office Open XML документов WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Этот запрос находит узел с именем `w:style`, который имеет атрибут `w:type` со значением «paragraph», а также имеет атрибут `w:default` со значением «1». Так как XML-узел с этими атрибутами будет только один, запрос использует оператор <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType>, чтобы преобразовать коллекцию в один элемент. Затем он возвращает значение атрибута `w:styleId`.  
  
 В этом примере используются классы из сборки WindowsBase. Используются типы из пространства имен <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
### <a name="code"></a>Код  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
  
    Sub Main()  
  
        Const fileName As String = "SampleDoc.docx"  
  
        Const documentRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Const stylesRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If docPackageRelationship IsNot Nothing Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                ' Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        ' The following query finds all the paragraphs that have the default style.  
        Dim defParas As IEnumerable(Of XElement) = _  
            From style In styleDoc.Root.<w:style> _  
            Where style.@w:type.Equals("paragraph") And _  
                   style.@w:default.Equals("1") _  
            Select style  
        ' Then find the style of the first.  
        Dim defaultStyle As String = defParas.First().@w:styleId  
  
        Console.WriteLine("The default style is: " & defaultStyle)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>Комментарии  
 В этом примере выводятся следующие данные:  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Следующие шаги  
 В следующем примере будет создан похожий запрос, который ищет все абзацы в документе и их стили:  
  
- [Извлечение абзацев и стилей (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>См. также

- [Учебник. Управление содержимым в документе WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
