---
title: Элемент <add> для <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: d7500620aed1165ff365fee8529230ba252dbc4b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120098"
---
# <a name="add-element-for-switches"></a>\<Добавить > элемент для \<коммутаторы >
Задает уровень, на котором установлен ключ трассировки.  
  
 \<configuration>  
\<system.diagnostics>  
\<Параметры >  
\<add>  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|**name**|Обязательный атрибут.<br /><br /> Указывает имя переключателя. Значение этого атрибута соответствует *displayName* параметр, передаваемый конструктору переключателя.|  
|**value**|Обязательный атрибут.<br /><br /> Задает уровень переключателя.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|  
|`switches`|Содержит ключи трассировки и уровень, на котором они установлены.|  
|`system.diagnostics`|Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.|  
  
## <a name="remarks"></a>Примечания  
 Уровень переключателя трассировки можно изменить, поместив его в файле конфигурации. Если значение параметра равно <xref:System.Diagnostics.BooleanSwitch>, вы можете включать и отключать. Если значение параметра равно <xref:System.Diagnostics.TraceSwitch>, можно назначать различные уровни для указания типов трассировки или отладки сообщений выходные данные приложения.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать  **\<Добавить >** задаваемого элемента `General` для переключателя трассировки <xref:System.Diagnostics.TraceLevel> уровня и включить `Data` логический переключатель трассировки.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [Схема параметров трассировки и отладки](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
