---
title: Сохранение пробелов при Serializing2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: e02335f564155fa8dc08fc3320ddc4e8c178a132
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666110"
---
# <a name="preserving-white-space-while-serializing"></a>Сохранение пробелов при сериализации
В этом разделе описывается управление пробелами при сериализации XML-дерева.  
  
 Типичный сценарий состоит в чтении XML с отступами, создании XML-дерева в памяти без текстовых узлов с пробелами (то есть без сохранения пробелов), выполнении определенных операций над XML и сохранении XML с отступами. При сериализации XML с форматированием сохраняются только значимые пробелы XML-дерева. Это поведение [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] по умолчанию.  
  
 Другой типичный сценарий заключается в чтении и изменении XML с уже существующими преднамеренными отступами. Эти отступы ни в коем случае изменять нельзя. Для этого в [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] можно сохранить пробелы при загрузке или синтаксическом анализе XML и отключить форматирование при сериализации XML.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Управление пробелами в методах сериализации XML-деревьев  
 Следующие методы классов <xref:System.Xml.Linq.XElement> и <xref:System.Xml.Linq.XDocument> позволяют сериализовать XML-дерево. Можно сериализовать XML-дерево в файл, объект <xref:System.IO.TextReader> или объект <xref:System.Xml.XmlReader>. Метод `ToString` позволяет сериализовать в строку.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Если метод не берет объект <xref:System.Xml.Linq.SaveOptions> в качестве аргумента, то этот метод отформатирует (расставит отступы) сериализованный XML. В этом случае все незначащие пробелы в XML-дереве удаляются.  
  
 Если метод берет объект <xref:System.Xml.Linq.SaveOptions> в качестве аргумента, то можно указать, что этот метод не должен форматировать (расставлять отступы) сериализованный XML. В этом случае все незначащие пробелы в XML-дереве сохраняются.  
  
## <a name="see-also"></a>См. также

- [Сериализация деревьев XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
