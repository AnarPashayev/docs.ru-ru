---
title: Примечания по реализации поддержки типов XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
ms.openlocfilehash: 91a685f122ff846217ea7a8677b29df430b65363
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290283"
---
# <a name="xml-type-support-implementation-notes"></a>Примечания по реализации поддержки типов XML
В этом разделе описываются определенные детали реализации, которые следует знать.  
  
## <a name="list-mappings"></a>Сопоставление списков  
 Типы <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]** и <xref:System.String> используются для представления типов списков языка XSD.  
  
## <a name="union-mappings"></a>Сопоставление объединений  
 Типы объединений представляются с помощью типов <xref:System.Xml.Schema.XmlAtomicValue> или <xref:System.String>. Следовательно, исходный тип или тип назначения всегда должны принадлежать либо к типу <xref:System.String>, либо к типу <xref:System.Xml.Schema.XmlAtomicValue>.  
  
 Если объект <xref:System.Xml.Schema.XmlSchemaDatatype> представляет тип списка, этот объект преобразует входное строковое значение в список, состоящий из одного или нескольких объектов. Если объект <xref:System.Xml.Schema.XmlSchemaDatatype> представляет тип объединения, тогда предпринимается попытка проанализировать входное значение как тип элемента объединения. В случае сбоя попытки синтаксического анализа предпринимается попытка преобразования следующего элемента объединения и т. д. - до тех пор, пока преобразование не будет успешным или пока не останется других типов элементов. В последнем случае возникает исключение.  
  
## <a name="differences-between-clr-and-xml-data-types"></a>Различия между типами данных CLR и XML  
 Ниже описывается ряд несоответствий, которые могут возникать между типами данных CLR и XML, и о том, как они преодолеваются.  
  
> [!NOTE]
> Префикс `xs` сопоставляется с <https://www.w3.org/2001/XMLSchema> и URI пространства имен.
  
### <a name="systemtimespan-and-xsduration"></a>System.TimeSpan и xs:duration  
 Тип `xs:duration` частично упорядочен в том смысле, что в нем представлены некоторые значения длительности, отличные друг от друга, но эквивалентные. Это означает, что для типа `xs:duration` значение 1 месяц (P1M) меньше чем 32 дня (P32D), больше чем 27 дней (P27D) и эквивалентно 28, 29 или 30 дням.  
  
 Класс <xref:System.TimeSpan> не поддерживает такое частичное упорядочение. Он предполагает использование определенного числа дней для 1 года и для 1 месяца: 365 дней и 30 дней соответственно.  
  
 Дополнительные сведения о типе `xs:duration` см. в документе W3C [Схема XML. Часть 2. Рекомендация по типам данных](https://www.w3.org/TR/xmlschema-2/).
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>Типы данных xs:time, григорианского календаря и System.DateTime  
 Когда значение `xs:time` сопоставляется с объектом <xref:System.DateTime>, поле <xref:System.DateTime.MinValue> используется для инициализации свойств даты объекта <xref:System.DateTime> (таких как <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A> и <xref:System.DateTime.Day%2A>) наименьшим из возможных значений <xref:System.DateTime>.  
  
 Подобным же образом экземпляры типов `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` и `xs:gMonthDay` сопоставляются с объектом <xref:System.DateTime>. Неиспользованные свойства объекта <xref:System.DateTime> получают значения поля <xref:System.DateTime.MinValue>.  
  
> [!NOTE]
> Не следует полагаться на значение свойства <xref:System.DateTime.Year%2A?displayProperty=nameWithType>, когда содержимое типизируется как `xs:gMonthDay`. Значение свойства <xref:System.DateTime.Year%2A?displayProperty=nameWithType> в этом случае всегда устанавливается равным 1904.  
  
### <a name="xsanyuri-and-systemuri"></a>Типы данных xs:anyURI и System.Uri  
 Когда экземпляр `xs:anyURI`, представляющий относительный идентификатор URI, сопоставляется с объектом <xref:System.Uri>, объект <xref:System.Uri> не имеет базового идентификатора URI.  
  
## <a name="see-also"></a>См. также

- [Поддержка типов в классах System.Xml](type-support-in-the-system-xml-classes.md)
