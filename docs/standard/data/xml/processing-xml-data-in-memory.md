---
title: Обработка XML-данных в памяти
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 0f64b53588e08520d38c05ec6060f9aef58bd7d6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556490"
---
# <a name="processing-xml-data-in-memory"></a>Обработка XML-данных в памяти
Платформа Microsoft .NET Framework включает три модели обработки XML-данных: классы <xref:System.Xml.XmlDocument>, класс <xref:System.Xml.XPath.XPathDocument>, а также [LINQ to XML (C#)](../../linq/linq-xml-overview.md) и [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).  
  
 Класс <xref:System.Xml.XmlDocument> реализует базовую модель DOM W3C 1-го уровня и базовые рекомендации объекта DOM 2-го уровня. DOM - древовидное представление XML-документа в памяти (кэш). С помощью <xref:System.Xml.XmlDocument> и связанных классов можно конструировать XML-документы, загружать данные и обращаться к ним, изменять данные и сохранять изменения.  
  
 Класс <xref:System.Xml.XPath.XPathDocument> - доступное только для чтения хранилище данных в памяти, на базе модели данных XPath. В классе <xref:System.Xml.XPath.XPathNavigator> предусмотрено несколько вариантов редактирования и способов навигации с помощью модели курсора для XML-документов в доступном только для чтения классе <xref:System.Xml.XPath.XPathDocument>, а также в классе <xref:System.Xml.XmlDocument>.  
  
 [LINQ to XML](../../linq/linq-xml-overview.md) — это модель для обработки XML-данных, представленная на платформе .NET Framework версии 3.5. Это размещаемая в памяти модель, которая использует синтаксис [LINQ](../../../csharp/programming-guide/concepts/linq/index.md). LINQ расширяет синтаксис C# и Visual Basic, обеспечивая новые возможности запросов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Обработка XML-данных с использованием модели DOM](process-xml-data-using-the-dom-model.md)  
 Описывает использование класса <xref:System.Xml.XmlDocument> и связанных с ним классов для обработки XML-данных.  
  
 [Обработка XML-данных с использованием модели данных XPath](process-xml-data-using-the-xpath-data-model.md)  
 Описывает использование классов <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument> и <xref:System.Xml.XPath.XPathNavigator> для обработки XML-данных.  
  
 [Обработка XML-данных с помощью LINQ to XML](process-xml-data-using-linq-to-xml.md)  
 Содержит краткие общие сведения о LINQ to XML и ссылки на документацию LINQ to XML.  
  
## <a name="related-sections"></a>Связанные разделы  
 [XML-документы и данные](index.md)
