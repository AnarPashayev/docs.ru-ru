---
title: Практическое руководство. Чтение и запись закодированного документа
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: f66737429950e04f447dfbd58cf47b6434a22976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397912"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a>Руководство. чтение и запись закодированного документа (Visual Basic)

Чтобы создать закодированный XML-документ, следует добавить объект <xref:System.Xml.Linq.XDeclaration> в XML-дерево, задав требуемое имя кодовой страницы для кодировки.

Любое значение, возвращенное методом <xref:System.Text.Encoding.WebName%2A>, является допустимым.

При чтении закодированного документа свойству <xref:System.Xml.Linq.XDeclaration.Encoding%2A> нужно будет задать имя этой кодовой страницы.

Если свойству <xref:System.Xml.Linq.XDeclaration.Encoding%2A> задать допустимое имя кодовой страницы, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] выполняет сериализацию с указанной кодировкой.

## <a name="example"></a>Пример

В следующем примере создаются два документа: один с кодировкой utf-8, а другой с кодировкой utf-16. Документы затем загружаются, а кодировка указывается в консоли.

```vb
Console.WriteLine("Creating a document with utf-8 encoding")
Dim encodedDoc8 As XDocument = _
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>
        <Root>Content</Root>

encodedDoc8.Save("EncodedUtf8.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)
Console.WriteLine()

Console.WriteLine("Creating a document with utf-16 encoding")
Dim encodedDoc16 As XDocument = _
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>
        <Root>Content</Root>

encodedDoc16.Save("EncodedUtf16.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)
Console.WriteLine()

Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)
Console.WriteLine()

Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)
```

В этом примере выводятся следующие данные:

```console
Creating a document with utf-8 encoding
Encoding is:utf-8

Creating a document with utf-16 encoding
Encoding is:utf-16

Encoded document:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root>Content</Root>

Encoding of loaded document is:utf-8

Encoded document:
<?xml version="1.0" encoding="utf-16" standalone="yes"?>
<Root>Content</Root>

Encoding of loaded document is:utf-16
```

## <a name="see-also"></a>См. также раздел

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [Расширенное программирование LINQ to XML (Visual Basic)](advanced-linq-to-xml-programming.md)
