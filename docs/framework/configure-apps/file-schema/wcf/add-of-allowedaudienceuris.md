---
title: <add> из <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: a3ad50462cfa268a1826b62603110be3c5ba33db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148282"
---
# <a name="add-of-allowedaudienceuris"></a>\<Добавить > из \<allowedAudienceUris >
Добавляет целевой универсальный код ресурса, для которого может быть задан маркер безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>, чтобы считаться допустимым для экземпляра <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 \<system.ServiceModel>  
\<варианты поведения >  
\<serviceBehaviors >  
\<поведение >  
\<serviceCredentials >  
\<issuedTokenAuthentication>  
\<allowedAudienceUris>  
\<Добавить > элемент для \<allowedAudienceUris >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|allowedAudienceUri|Строка, содержащая целевой универсальный код ресурса, для которого может быть задан маркер безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>, чтобы считаться допустимым в экземпляре <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<allowedAudienceUris>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|Представляет коллекцию целевых универсальных кодов ресурса (URI), для которых может быть задан маркер безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>, чтобы они считались допустимыми для экземпляра <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.|  
  
## <a name="remarks"></a>Примечания  
 Данную коллекцию следует использовать в федеративном приложении, которое использует службу маркеров безопасности (STS), выдающую маркеры безопасности <xref:System.IdentityModel.Tokens.SamlSecurityToken>. При выпуске маркера безопасности служба STS также может указать универсальный код ресурса (URI) веб-служб, для которых предназначен маркер безопасности, добавив выражение <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> к маркеру безопасности. Это позволяет коду <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> для веб-службы получателя проверить, что выданный маркер безопасности предназначен для данной службы, указав на необходимость выполнения соответствующей проверки. Для этого выполните следующие действия.  
  
-   Присвойте атрибуту `audienceUriMode` элемента `<issuedTokenAuthentication>` значение <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> или <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.  
  
-   Задайте набор допустимых универсальных кодов ресурса (URI), добавив их в данную коллекцию.  
  
 Дополнительные сведения см. в разделе <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Дополнительные сведения об использовании данного элемента конфигурации см. в разделе [как: Настройка учетных данных службы федерации](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>См. также

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<allowedAudienceUris>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)
- [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [Поведение безопасности](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Защита служб и клиентов](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Практическое руководство. Настройка учетных данных службы федерации](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
