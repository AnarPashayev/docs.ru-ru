---
title: <Event> Элемент (машинный код .NET)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e8ddf9ea72db63c72bfb5393709b4c20de2a14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163004"
---
# <a name="event-element-net-native"></a>\<Событие > элемент (машинный код .NET)
Применяет политику отражения среды выполнения к событию.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Тип атрибута|Описание|  
|---------------|--------------------|-----------------|  
|`Name`|Общие|Обязательный атрибут. Задает имя события.|  
|`Browse`|Отражение|Необязательный атрибут. Определяет запрос для получения сведений о событиях или перечисляет события, но не включает динамический доступ во время выполнения.|  
|`Dynamic`|Отражение|Необязательный атрибут. Управляет доступом среды выполнения к событию для включения динамического программирования. Эта политика гарантирует, что события могут обрабатываться динамически во время выполнения.|  
  
## <a name="name-attribute"></a>Name - атрибут  
  
|Значение|Описание|  
|-----------|-----------------|  
|*method_name*|Имя события. Тип события определяется родительским элементом [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) или [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).|  
  
## <a name="all-other-attributes"></a>Все остальные атрибуты  
  
|Значение|Описание|  
|-----------|-----------------|  
|*policy_setting*|Параметр, применяемый к этому типу политики для события. Допустимые значения: `Auto`, `Excluded`, `Included` и `Required`. Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<Тип >](../../../docs/framework/net-native/type-element-net-native.md)|Применяет политику отражения к типу и всем его членам.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Применяет политику отражения к сконструированному универсальному типу и всем его членам.|  
  
## <a name="remarks"></a>Примечания  
 Если политика события не определена явно, оно наследует политику среды выполнения своего родительского элемента.  
  
## <a name="see-also"></a>См. также

- [Ссылка на файл конфигурации директив среды выполнения (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Элементы директив среды выполнения](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Параметры политики директив среды выполнения](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
