---
title: Элемент <dateTimeSerialization>
description: В этой статье описывается элемент <dateTimeSerialization>, который определяет режим сериализации объектов DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: a2684ab72c1fb109d711e333e01836d3399caf86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289646"
---
# <a name="datetimeserialization-element"></a>Элемент \<dateTimeSerialization>
Определяет режим сериализации объектов <xref:System.DateTime>.  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибуты|Описание|  
|----------------|-----------------|  
|`mode`|Необязательный элемент. Задает режим сериализации. Задайте одно из значений <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>. Значение по умолчанию: **RoundTrip**.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|system.xml.serialization|Элемент верхнего уровня для управления XML-сериализацией.|  
  
## <a name="remarks"></a>Примечания  
 На платформе .NET Framework версий 1.0, 1.1 и 2.0 и более поздних при присвоении этому свойству значения **Local** объекты <xref:System.DateTime> всегда форматируются как местное время. Это значит, что в сериализованные данные всегда включается информация о местном часовом поясе. Присвоение этому свойству значения **Local** обеспечивает совместимость с предыдущими версиями платформы .NET Framework.  
  
 На платформе .NET Framework версии 2.0 и более поздних, в которых для этого свойства задано значение **Roundtrip**, объекты <xref:System.DateTime> анализируются с целью выяснить, указан ли в них местный часовой пояс, время UTC или часовой пояс не указан. После этого объекты <xref:System.DateTime> сериализуются способом, обеспечивающим сохранение этой информации. Это является поведением по умолчанию, рекомендуемым для всех новых приложений, не взаимодействующих со старыми версиями платформы .NET Framework.  
  
## <a name="see-also"></a>См. также

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Схема файла конфигурации](../../framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions> Элемент](schemaimporterextensions-element.md)
- [Элемент \<add> для \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> Элемент](system-xml-serialization-element.md)
