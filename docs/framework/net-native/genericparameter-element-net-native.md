---
title: <GenericParameter> Элемент (машинный код .NET)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40fef845a55412e5731ec08bd1e038d6b311694c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111661"
---
# <a name="genericparameter-element-net-native"></a>\<GenericParameter > элемент (машинный код .NET)
Применяет политику к параметру типа универсального типа или метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Тип атрибута|Описание|  
|---------------|--------------------|-----------------|  
|`Name`|Общие|Обязательный атрибут. Имя универсального параметра. Например, для универсального делегата <xref:System.Func%603>, значение атрибута `Name` равно «TResult» для применения политики среды выполнения к возвращаемому значению делегата.|  
|`Activate`|Отражение|Необязательный атрибут. Управляет доступом среды выполнения к конструкторам для включения активации экземпляров.|  
|`Browse`|Отражение|Необязательный атрибут. Управляет запросами для получения сведений об элементах программы, но не включает доступ среды выполнения.|  
|`Dynamic`|Отражение|Необязательный атрибут. Управляет доступом среды выполнения ко всем членам типа, включая конструкторы, методы, поля, свойства и события, чтобы включить динамическое программирование.|  
|`Serialize`|Сериализация|Необязательный атрибут. Управляет доступом среды выполнения к конструкторам, полям и свойствам, позволяющим сериализовать и десериализовать экземпляры типа с помощью таких библиотек, как, например, сериализатор Newtonsoft JSON.|  
|`DataContractSerializer`|Сериализация|Необязательный атрибут. Определяет политику для сериализации, в которой используется класс <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Сериализация|Необязательный атрибут. Определяет политику для сериализации JSON, в которой используется класс <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Сериализация|Необязательный атрибут. Определяет политику для сериализации XML, в которой используется класс <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interop|Необязательный атрибут. Определяет политику для маршалинга ссылочных типов в среды выполнения Windows и COM.|  
|`MarshalDelegate`|Interop|Необязательный атрибут. Определяет политики для маршалинга типов делегатов как указателей функции на машинный код.|  
|`MarshalStructure`|Interop|Необязательный атрибут. Определяет политики для маршалинга типов значений в машинный код.|  
  
## <a name="name-attribute"></a>Name - атрибут  
  
|Значение|Описание|  
|-----------|-----------------|  
|*generic_parameter_name*|Обязательный атрибут. Имя универсального параметра типа. Например, для универсального делегата <xref:System.Func%603> значение *generic_parameter_name*, равное "TResult", применяет политику среды выполнения к возвращаемому значению делегата.|  
  
## <a name="all-other-attributes"></a>Все остальные атрибуты  
  
|Значение|Описание|  
|-----------|-----------------|  
|*policy_setting*|Параметр, применяемый для этого типа политики. Допустимые значения: `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` и `Required All`. Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<Метод >](../../../docs/framework/net-native/method-element-net-native.md)|Применяет политику отражения среды выполнения к конструктору или методу.|  
|[\<Тип >](../../../docs/framework/net-native/type-element-net-native.md)|Применяет политику отражения среды выполнения для конкретного типа, например, класса или структуры.|  
  
## <a name="remarks"></a>Примечания  
 Элемент `<GenericParameter>` является дочерним для элемента [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) или [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) и используется для применения политики к определенному параметру универсального типа, который задается его именем в сигнатуре универсального типа или метода.  
  
 Элемент `<GenericParameter>` особенно полезен при использовании сериализаторов. В следующем примере используется элемент `<GenericParameter>`, который позволяет применить политику к типу `T` в вызовах к перегрузкам метода [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) сериализатора NewtonSoft JSON.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a>См. также

- [\<Метод > элемент](../../../docs/framework/net-native/method-element-net-native.md)
- [\<Тип > элемент](../../../docs/framework/net-native/type-element-net-native.md)
- [Ссылка на файл конфигурации директив среды выполнения (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Параметры политики директив среды выполнения](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Элементы директив среды выполнения](../../../docs/framework/net-native/runtime-directive-elements.md)
