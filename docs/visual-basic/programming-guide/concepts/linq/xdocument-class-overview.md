---
title: Общие сведения о классе XDocument (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: f9a531b9e90a8d6511dd0a2c6fc3131c9bfe1e89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834287"
---
# <a name="xdocument-class-overview-visual-basic"></a>Общие сведения о классе XDocument (Visual Basic)
В этом разделе представлен класс <xref:System.Xml.Linq.XDocument>.  
  
## <a name="overview-of-the-xdocument-class"></a>Общие сведения о классе XDocument  
 Класс <xref:System.Xml.Linq.XDocument> содержит сведения, необходимые для допустимого XML-документа. К ним относятся XML-декларация, инструкции по обработке и комментарии.  
  
 Отметим, что, если требуются только конкретные функции, обеспечиваемые классом <xref:System.Xml.Linq.XDocument>, необходимо создавать только объекты <xref:System.Xml.Linq.XDocument>. Во многих случаях пользователь может работать непосредственно с <xref:System.Xml.Linq.XElement>. Непосредственная работа с <xref:System.Xml.Linq.XElement> реализует более простую модель программирования.  
  
 Интерфейс <xref:System.Xml.Linq.XDocument> является производным от интерфейса <xref:System.Xml.Linq.XContainer>. Поэтому он может содержать дочерние узлы. Однако объекты <xref:System.Xml.Linq.XDocument> могут иметь только по одному дочернему узлу <xref:System.Xml.Linq.XElement>. Это обстоятельство отражает стандарт XML, согласно которому в XML-документе может содержаться лишь один корневой элемент.  
  
## <a name="components-of-xdocument"></a>Компоненты XDocument  
 Документ <xref:System.Xml.Linq.XDocument> может включать в себя следующие элементы:  
  
-   Один объект <xref:System.Xml.Linq.XDeclaration>. <xref:System.Xml.Linq.XDeclaration> позволяет указать соответствующие части XML-объявления: версию XML, кодировку документа, а также то, является ли этот XML-документ изолированным.  
  
-   Один объект <xref:System.Xml.Linq.XElement>. Это корневой узел XML-документа.  
  
-   Любое количество объектов <xref:System.Xml.Linq.XProcessingInstruction>. Инструкция по обработке передает сведения в приложение, обрабатывающее XML-код.  
  
-   Любое количество объектов <xref:System.Xml.Linq.XComment>. Комментарии и корневой элемент находятся на одном уровне. Объект <xref:System.Xml.Linq.XComment> не может быть первым аргументом в списке, так как XML-документ не может начинаться с комментария.  
  
-   Один тип документа <xref:System.Xml.Linq.XDocumentType> для DTD.  
  
 При сериализации документа <xref:System.Xml.Linq.XDocument>, даже если значением декларации `XDocument.Declaration` является `null`, выходные данные будут иметь XML-декларацию, если для свойства `Writer.Settings.OmitXmlDeclaration` автор указал значение `false` (применяется по умолчанию).  
  
 По умолчанию [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] указывает для версии значение «1.0», а для кодировки значение «utf-8».  
  
## <a name="using-xelement-without-xdocument"></a>Использование XElement без XDocument  
 Как уже отмечалось, класс <xref:System.Xml.Linq.XElement> является основным классом интерфейса программирования [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Во многих случаях приложение не требует создания документа. Класс <xref:System.Xml.Linq.XElement> позволяет создавать XML-дерево, добавлять к нему другие XML-деревья, изменять XML-дерево и сохранять его.  
  
## <a name="using-xdocument"></a>Использование XDocument  
 При создании объектов <xref:System.Xml.Linq.XDocument> используется функциональное построение, так же как и при создании объектов <xref:System.Xml.Linq.XElement>.  
  
 Следующий фрагмент кода создает объект <xref:System.Xml.Linq.XDocument> и ассоциированные с ним вложенные объекты.  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 В результате анализа файла test.xml получается следующий выход:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a>См. также

- [Обзор LINQ to XML программирования (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
