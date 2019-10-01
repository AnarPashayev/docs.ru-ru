---
title: Элемент <servicePointManager> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: 95ad1880cbb832a17311e7e63e9203f53257f65f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697712"
---
# <a name="servicepointmanager-element-network-settings"></a>Элемент > @no__t 0servicePointManager (параметры сети)
Настраивает подключения к сетевым ресурсам.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<servicePointManager >**  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|**Attribute (XElement Dynamic Property)** (Attribute (динамическое свойство XElement))|**Описание**|  
|-------------------|---------------------|  
|`checkCertificateName`|Указывает, должна ли система проверять имя сертификата на соответствие имени узла сервера перед использованием сертификата. Значение по умолчанию — `true`.|  
|`checkCertificateRevocationList`|Указывает, должна ли система проверять, отозван ли сертификат перед использованием сертификата. Значение по умолчанию — `false`.|  
|`dnsRefreshTimeout`|Указывает, как долго кэшируются разрешения службы доменных имен (DNS) в сочетании с параметром циклического перебора DNS в миллисекундах. По умолчанию установлено значение 120 000 миллисекунд (2 минуты).|  
|`enableDnsRoundRobin`|Указывает, должны ли разрешения DNS имен узлов с несколькими IP-адресами возвращать все адреса или только первый из них. Значение по умолчанию — `false`.|  
|`encryptionPolicy`|Указывает политику шифрования, применяемую к сеансу SSL/TLS на экземпляре <xref:System.Net.ServicePointManager>. Возможные значения эквивалентны значениям перечисления <xref:System.Net.Security.EncryptionPolicy>. Использование <xref:System.Security.Authentication.CipherAlgorithmType.Null> обязательно, если для политики шифрования задано значение `NoEncryption`. Значение по умолчанию — `RequireEncryption`.|  
|`expect100Continue`|Указывает, должны ли методы POST принимать ответ `100-continue` от сервера. Значение по умолчанию — `true`.|  
|`useNagleAlgorithm`|Указывает, используют ли подключения, управляемые диспетчером точек обслуживания, алгоритм Nagle. Значение по умолчанию — `true`.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|**Элемент**|**Описание**|  
|-----------------|---------------------|  
|[Параметры](settings-element-network-settings.md)|Настраивает основные параметры сети для пространства имен <xref:System.Net>.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="configuration-files"></a>Файлы конфигурации  
 Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).  
  
## <a name="see-also"></a>См. также

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Схема параметров сети](index.md)
