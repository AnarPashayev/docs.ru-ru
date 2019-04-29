---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 29e18cdda9e18addef4f0f32fd30e9abf6af78fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793852"
---
# <a name="securitytokenhandlerconfiguration"></a>\<securityTokenHandlerConfiguration>
Предоставляет конфигурацию для коллекции обработчиков токенов.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration>  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|saveBootstrapContext|Указывает, включаются ли токены начальной загрузки в токен сеанса. Также можно задать значение в коллекцию обработчиков токенов, задав `saveBootstrapContext` атрибут [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) элемент. Значение, заданное на коллекцию обработчиков токенов переопределяет значение, заданное в службе.|  
|maximumClockSkew|Объект <xref:System.TimeSpan> , указывающее максимальное допустимое время отклонения. Определяет максимальное допустимое время отклонения при выполнении операций, зависящих от времени, таких как проверка срока действия сеанса входа в систему. Значение по умолчанию — 5 минут «00: 05:00». Дополнительные сведения о способах указания <xref:System.TimeSpan> значения, см. в разделе [значения Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Также можно задать максимальную расфазировку синхронизирующих импульсов на уровне службы, задав `maximumClockSkew` атрибут [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) элемент. Значение, заданное на коллекцию обработчиков токенов переопределяет значение, заданное в службе.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<audienceUris>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|Задает набор URI, допустимых идентификаторов этой проверяющей стороне. Необязательный параметр.|  
|[\<кэширует >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Регистрирует кэши маркеров сеанса и обнаружения воспроизведения маркеров. Можно указать на уровне службы или в коллекцию обработчиков токенов безопасности. Необязательный параметр.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Управляет параметрами, используемых обработчиками токена для проверки сертификатов. Можно указать на уровне службы или в коллекцию обработчиков токенов безопасности. Эти параметры переопределяются в том случае, если настроен собственный проверяющий элемент управления указанным обработчиком. Необязательный параметр.|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Настраивает реестр имен издателей, используемый обработчиками в коллекцию обработчиков токенов. Необязательный параметр.|  
|[\<issuerTokenResolver>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|Регистрирует Сопоставитель токенов издателей, используемый обработчиками в коллекцию обработчиков токенов. Сопоставитель токенов издателей используется для разрешения токена подписывания на входящих токенов и сообщений. Необязательный параметр.|  
|[\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|Регистрирует Сопоставитель токенов служб, используемый обработчиками в коллекцию обработчиков токенов. Сопоставитель токенов служб используется для разрешения токена шифрования на входящих токенов и сообщений. Необязательный параметр.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Включает обнаружение воспроизведения токенов и определяет срок действия маркеров. Можно указать на уровне службы или в коллекцию обработчиков токенов безопасности. Необязательный параметр.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Задает коллекцию обработчиков токенов безопасности, которые зарегистрированы с конечной точкой.|  
  
## <a name="remarks"></a>Примечания  
 В этом разделе содержатся значения свойств для <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> объекта. Параметры, настроенные в этом разделе, переопределяют сконфигурирован в службе. Некоторые из этих параметров могут в свою очередь, переопределяться параметры, заданные в случае, когда обработчик добавляется в коллекцию обработчиков токенов безопасности.  
  
## <a name="example"></a>Пример  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
