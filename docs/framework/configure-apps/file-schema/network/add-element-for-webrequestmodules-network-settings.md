---
title: Элемент <add> для webRequestModules (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: 4c1116c088c12ad3859714c8d75704d0156c12f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188256"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<Добавить > элемент для webRequestModules (параметры сети)
Добавляет пользовательский модуль веб-запросов к приложению.  
  
 \<configuration>  
\<system.net>  
\<webRequestModules>  
\<add>  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))|**Описание**|  
|-------------------|---------------------|  
|`prefix`|Префикс URI для запросов, обрабатываемых этот модуль веб-запросов.|  
|`type`|Полное имя типа (обозначается <xref:System.Type.FullName%2A> свойства) и имя сборки (обозначается <xref:System.Reflection.Assembly.FullName%2A> свойство), разделенные запятыми, который реализует этот модуль веб-запросов.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|**Элемент**|**Описание**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Задает модули, используемые для запроса данных от сетевых узлов.|  
  
## <a name="remarks"></a>Примечания  
 `prefix` Атрибут определяет префикс URI, который использует указанный модуль веб-запросов. Модули веб-запросов обычно регистрируются для обработки конкретного протокола, например HTTP или FTP, но могут быть зарегистрированы для обработки запросов к конкретному серверу или пути на сервере.  
  
 Модуль веб-запросов создается в том случае, если соответствующий префикс URI передается на <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> метод.  
  
 Значение для `prefix` атрибут должен быть из ведущих символов является допустимым URI. Например, `http` или `http://www.contoso.com`.
  
 Значение для `type` атрибут должен быть допустимым именем типа и соответствующее имя сборки, разделенных запятыми.
  
## <a name="configuration-files"></a>Файлы конфигурации  
 Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).  
  
## <a name="example"></a>Пример  
 В следующем примере регистрируется пользовательский модуль веб-запросов для HTTP. Следует заменить значения для версии и PublicKeyToken правильными значениями для указанного модуля.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Net.WebRequest>
- [Схема параметров сети](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
