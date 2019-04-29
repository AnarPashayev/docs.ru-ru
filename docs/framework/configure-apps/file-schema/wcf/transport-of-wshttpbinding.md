---
title: <transport> из <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: ea025751020d6d98292f6bc3ecfe9421af0cb793
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788223"
---
# <a name="transport-of-wshttpbinding"></a>\<Транспорт > из \<wsHttpBinding >

Определяет параметры проверки подлинности для HTTP-транспорта.

\<system.serviceModel > \
\<привязки > \
\<wsHttpBinding > \
\<Привязка > \
\<Безопасность > \
\<Транспорт >

## <a name="syntax"></a>Синтаксис

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a>Тип

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a>Атрибуты и элементы

В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`clientCredentialType`|Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе. Это атрибут типа <xref:System.ServiceModel.HttpClientCredentialType>.|
|`proxyCredentialType`|Задает учетные данные, используемые для проверки подлинности клиента при подключении к прокси-серверу домена. Это атрибут типа <xref:System.ServiceModel.HttpProxyCredentialType>.|
|`realm`|Строка, указывающая область проверки подлинности для обычной проверки подлинности или дайджест-проверки подлинности. Значение по умолчанию - пустая строка.<br /><br /> Область проверки подлинности задает по крайней мере имя основного узла, выполняющего проверку подлинности. Она также может указывать коллекцию пользователей, которым разрешен доступ. Пользователь может запросить область проверки подлинности, чтобы выяснить, какое из нескольких возможных сочетаний имен пользователей и паролей можно использовать.|
|`policyEnforcement`|Это перечисление указывает, когда следует применять <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.<br /><br /> 1.  Never - политика никогда не применяется (расширенная защита отключена).<br />2.  WhenSupported - политика применяется только тогда, когда клиент поддерживает расширенную защиту.<br />3.  Always - политика применяется всегда. Клиенты, которые не поддерживают расширенную защиту, не смогут пройти проверку подлинности.|

## <a name="clientcredentialtype-attribute"></a>Атрибут clientCredentialType

|Значение|Описание|
|-----------|-----------------|
|`None`|Режим безопасности отключен.|
|`Basic`|Используется обычная проверка подлинности.|
|`Digest`|Используется дайджест-проверка подлинности.|
|`Ntlm`|Используется проверка подлинности NTLM в качестве резервной в домене Windows.|
|`Windows`|Используется встроенная проверка подлинности Windows.|
|`Certificate`|Для проверки подлинности клиента используются сертификаты X.509.|

## <a name="proxycredentialtype-attribute"></a>Атрибут proxyCredentialType

|Значение|Описание|
|-----------|-----------------|
|`None`|Режим безопасности отключен.|
|`Basic`|Используется обычная проверка подлинности.|
|`Digest`|Используется дайджест-проверка подлинности.|
|`Ntlm`|Используется проверка подлинности NTLM в качестве резервной в домене Windows.|
|`Windows`|Используется встроенная проверка подлинности Windows.|
|`Certificate`|Для проверки подлинности клиента используются сертификаты X.509.|

### <a name="child-elements"></a>Дочерние элементы

Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[\<Безопасность >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Представляет возможности безопасности [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).|

## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [Защита служб и клиентов](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Привязки](../../../../../docs/framework/wcf/bindings.md)
- [Настройка привязок, предоставляемых системой](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Использование привязок для настройки служб и клиентов](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Привязка >](../../../../../docs/framework/misc/binding.md)
