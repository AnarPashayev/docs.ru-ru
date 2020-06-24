---
title: Значения членов данных по умолчанию
description: Сведения о том, как опустить элемент данных из сериализованных данных, если он имеет .NET Framework значение по умолчанию. WCF может повысить производительность, не применяя сериализацию по умолчанию.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
ms.openlocfilehash: 97946a6b7da14efdcb5229b4cc5d0799eb8d7723
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247381"
---
# <a name="data-member-default-values"></a>Значения членов данных по умолчанию
В .NET Framework типы имеют концепцию *значений по умолчанию*. Например, любой ссылочный тип имеет значение по умолчанию `null`, а значением по умолчанию для целого типа является ноль. Иногда требуется исключить член данных из сериализованных данных, если для него задано значение по умолчанию. Так как этот член имеет значение по умолчанию, нет необходимости сериализовывать фактическое значение; это повышает производительность.  
  
 Чтобы исключить член из сериализованных данных, задайте для свойства <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> атрибута <xref:System.Runtime.Serialization.DataMemberAttribute> значение `false` (по умолчанию задано значение `true`).  
  
> [!NOTE]
> Присваивать значение <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> свойству `false` следует только при конкретной необходимости, например для обеспечения взаимодействия или для уменьшения объема данных.  
  
## <a name="example"></a>Пример  
 В следующем коде у нескольких членов для свойства <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> задано значение `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 При сериализации экземпляра этого класса получается следующее: `employeeName` и `employeeID` сериализуются. Значение "null" для `employeeName` и нулевое значение для `employeeID` в явном виде указаны в сериализованных данных. Однако члены `position`, `salary` и `bonus` не сериализуются. Наконец, член `targetSalary` сериализуется как обычно, хотя для свойства <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> задано значение `false`, так как 57800 не соответствует принятому в платформе .NET значению по умолчанию для целого числа (а именно, ноль).  
  
### <a name="xml-representation"></a>Представление XML  
 При сериализации предыдущего примера в XML представление аналогично приведенному ниже.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 Атрибут `xsi:nil` является специальным атрибутом в пространстве имен экземпляров схемы XML интернет-консорциума (W3C), который обеспечивает совместимый способ явного указания значения "null". Обратите внимание, что в XML полностью отсутствует информация о членах данных со сведениями о должности, окладе и бонусах. Получатель может интерпретировать их как значения `null`, ноль и `null` соответственно. Не гарантируется, что десериализатор независимого разработчика выполнит правильную интерпретацию, поэтому не рекомендуется использовать такую схему. Класс <xref:System.Runtime.Serialization.DataContractSerializer> всегда выбирает правильную интерпретацию для отсутствующих значений.  
  
### <a name="interaction-with-isrequired"></a>Взаимодействие со свойством IsRequired  
 Как обсуждалось в разделе [Управление версиями контракта данных](data-contract-versioning.md), <xref:System.Runtime.Serialization.DataMemberAttribute> атрибут имеет <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> свойство (значение по умолчанию — `false` ). Это свойство указывает, должен ли определенный член данных присутствовать в сериализованных данных при десериализации. Если для свойства `IsRequired` задано значение `true` (означающее, что значение должно присутствовать), а для свойства <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> задано значение `false` (указывающее, что если значение равно значению по умолчанию, то оно может отсутствовать), сериализация значений по умолчанию для этого члена данных невозможна, так как результат будет противоречивым. Если для такого члена данных задано значение по умолчанию (обычно `null` или ноль) и производится попытка сериализации, возникает исключение <xref:System.Runtime.Serialization.SerializationException>.  
  
### <a name="schema-representation"></a>Представление схемы  
 Сведения о представлении схемы языка определения схемы XML (XSD) для элементов данных, если `EmitDefaultValue` свойство имеет значение `false` , обсуждаются в [справочнике по схеме контракта данных](data-contract-schema-reference.md). Тем не менее ниже приводятся краткие общие сведения:  
  
- Если параметр <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> имеет значение `false` , то он представлен в схеме в виде аннотации, относящейся к Windows Communication Foundation (WCF). Не существует совместимого способа представления этой информации. В частности, атрибут "default" в схеме не используется для этой цели, на атрибут `minOccurs` влияет только параметр <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>, а на атрибут `nillable` влияет только тип члена данных.  
  
- Фактическое значение по умолчанию, которое требуется использовать, в этой схеме отсутствует. Правильная интерпретация отсутствующего элемента зависит только от принимающей конечной точки.  
  
 При импорте схемы <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> свойство автоматически устанавливается в `false` каждый раз, когда обнаруживается заметка, упомянутая ранее для WCF. Он также имеет значение `false` для ссылочных типов, для которых `nillable` свойство имеет значение, `false` чтобы обеспечить поддержку конкретных сценариев взаимодействия, которые обычно возникают при использовании веб-служб ASP.NET.  
  
## <a name="see-also"></a>См. также

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
