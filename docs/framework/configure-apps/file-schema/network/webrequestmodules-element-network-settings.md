---
title: Элемент <webRequestModules> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154547"
---
# <a name="webrequestmodules-element-network-settings"></a>Элемент \<webRequestModules> (параметры сети)
Указывает модули, используемые для запроса сведений от сетевых узлов.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|**Элемент**|**Описание**|  
|-----------------|---------------------|  
|[добавление](add-element-for-webrequestmodules-network-settings.md)|Добавляет пользовательский модуль веб-запросов в приложение.|  
|[открытым](clear-element-for-webrequestmodules-network-settings.md)|Удаляет из приложения все зарегистрированные модули веб-запросов.|  
|[remove](remove-element-for-webrequestmodules-network-settings.md)|Удаляет пользовательский модуль веб-запросов из приложения.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|**Элемент**|**Описание**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Содержит параметры сети, определяющие способ подключения .NET Framework к Интернету.|  
  
## <a name="remarks"></a>Примечания  
 Элемент `webRequestModules` регистрирует потомки класса <xref:System.Net.WebRequest>, чтобы обработать запросы информации к сетевым узлам. Модули веб-запросов должны реализовывать <xref:System.Net.IWebRequestCreate> интерфейс.  
  
 .NET Framework включает модули веб-запросов для URI, которые начинаются с `http://` , `https://` и `file://` . Модули по умолчанию можно переопределить только путем регистрации пользовательского модуля в файле конфигурации.  
  
## <a name="configuration-files"></a>Файлы конфигурации  
 Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).  
  
## <a name="example"></a>Пример  
 В следующем примере регистрируется HTTP-модуль по умолчанию. Необходимо заменить значения для Version и PublicKeyToken правильными значениями для указанного модуля.  
  
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
- <xref:System.Net.IWebRequestCreate>
- [Схема параметров сети](index.md)
