---
title: Элемент <proxy> (параметры сети)
description: <proxy>Элемент Параметры сети определяет параметры прокси-сервера в .NET Framework. Эта статья содержит пример.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 0d462fcc92fc1be5ddbc2e76237d8436219c7295
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504541"
---
# <a name="proxy-element-network-settings"></a>Элемент \<proxy> (параметры сети)
Определяет прокси-сервер.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a>Синтаксис  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))|**Описание**|  
|-------------------|---------------------|  
|`autoDetect`|Указывает, обнаруживается ли прокси-сервер автоматически. Значение по умолчанию — `unspecified`.|  
|`bypassonlocal`|Указывает, используется ли прокси-сервер для локальных ресурсов. Локальные ресурсы включают локальный сервер ( `http://localhost` , `http://loopback` или `http://127.0.0.1` ) и URI без точки ( `http://webserver` ). Значение по умолчанию — `unspecified`.|  
|`proxyaddress`|Указывает используемый URI прокси-сервера.|  
|`scriptLocation`|Указывает расположение скрипта конфигурации. Не используйте `bypassonlocal` атрибут с этим атрибутом. |  
|`usesystemdefault`|Указывает, следует ли использовать параметры прокси-сервера Internet Explorer. Если задано значение `true` , последующие атрибуты будут переопределять параметры прокси-сервера Internet Explorer. Значение по умолчанию — `unspecified`.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|**Элемент**|**Описание**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Настраивает прокси-сервер протокола передачи гипертекста (HTTP).|  
  
## <a name="text-value"></a>Текстовое значение  
  
## <a name="remarks"></a>Примечания  
 `proxy`Элемент определяет прокси-сервер для приложения. Если этот элемент отсутствует в файле конфигурации, .NET Framework будет использовать параметры прокси-сервера в Internet Explorer.  
  
 Значение `proxyaddress` атрибута должно представлять собой универсальный код ресурса (URI) правильного формата.  
  
 `scriptLocation`Атрибут относится к автоматическому обнаружению скриптов конфигурации прокси-сервера. <xref:System.Net.WebProxy>Класс будет пытаться разместить скрипт конфигурации (обычно с именем WPAD. dat), если в Internet Explorer выбран параметр **использовать скрипт автоматической настройки** . Если `bypassonlocal` для задано любое значение, `scriptLocation` то параметр игнорируется.
  
 Используйте `usesystemdefault` атрибут для приложений .NET Framework версии 1,1, которые переносятся на версию 2,0.  
  
 Если `proxyaddress` атрибут указывает на недопустимый прокси-сервер по умолчанию, возникает исключение. Свойство <xref:System.Exception.InnerException%2A> исключения должно иметь дополнительные сведения о первопричине ошибки.  
  
## <a name="configuration-files"></a>Файлы конфигурации  
 Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).  
  
## <a name="example"></a>Пример  
 В следующем примере используются значения по умолчанию из прокси-сервера Internet Explorer, указывается адрес прокси-сервера и выполняется обход прокси-сервера для локального доступа.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Схема параметров сети](index.md)
