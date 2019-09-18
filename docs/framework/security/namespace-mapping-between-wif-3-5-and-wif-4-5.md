---
title: Сопоставление пространств имен между WIF 3.5 и WIF 4.5
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
ms.openlocfilehash: d967ce931e81ca14645e7464943e1411264d6ca2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045403"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>Сопоставление пространств имен между WIF 3.5 и WIF 4.5

Начиная с .NET 4.5 Windows Identity Foundation (WIF) полностью интегрирована в .NET Framework. Эта интеграция привела к изменениям имен и некоторой консолидации пространств имен WIF и области API. В этом разделе приведены некоторые рекомендации и общее сопоставление пространств имен WIF 3.5 и WIF 4.5. Этот раздел не является исчерпывающим. В нем представлены общие сведения о том, как найти знакомые классы WIF 3.5 в WIF 4.5. Дополнительные сведения о различиях между WIF 3.5 и WIF 4.5 см. в разделе [Новые возможности Windows Identity Foundation 4.5](whats-new-in-wif.md). Руководство по миграции приложений, созданных с использованием WIF 3.5, в WIF 4.5 см. в разделе [Руководство по миграции приложения, созданного с использованием WIF 3.5, в WIF 4.5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).

## <a name="wif-35-to-wif-45-namespace-map"></a>Сопоставление пространств имен WIF 3.5 и WIF 4.5

Классы WIF, которые находились в пространствах имен `Microsoft.IdentityModel` в WIF 3.5, в WIF 4.5 распределены по следующим пространствам имен: `System.Security.Claims`, `System.ServiceModel.Security` и `System.IdentityModel`. Кроме того, некоторые пространства имен WIF 3.5 были объединены или полностью удалены в WIF 4.5.

> [!IMPORTANT]
> Следующие пространства имен `System.IdentityModel` содержат классы, которые реализуют модель удостоверений WCF на основе утверждений: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType> и <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. Модель удостоверений WCF на базе утверждений заменяется WIF. При создании решений на основе WIF не следует использовать классы из этих трех пространств имен.

В следующей таблице представлены сведения о том, как найти классы WIF 3.5 в WIF 4.5.

|**Пространство имен WIF 3.5**|**Пространство имен WIF 4.5**|**Комментарии**|
|-|-|-|
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|– Большинство классов, которые представляют константы, не реализованы.<br />– Классы, которые используются для создания служб маркеров безопасности, перемещены из `Microsoft.IdentityModel.SecurityTokenService` в <xref:System.IdentityModel?displayProperty=nameWithType>.<br />– Классы в `Microsoft.IdentityModel.Threading` перемещены в <xref:System.IdentityModel?displayProperty=nameWithType>.<br />– Классы `ExceptionMapper` и `MruSecurityTokenCache` не реализованы.|
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|– Интерфейсы `IClaimsPrincipal` и `IClaimsIdentity` не реализованы в WIF 4.5. Теперь <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> и <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> — это базовые классы, от которых наследуется большинство классов субъектов и удостоверений .NET. Это означает, что в WIF 4.5 не требуется использовать специализированные классы субъектов и удостоверений утверждений, такие как `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` и `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity`. Вместо них используйте <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> и <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType>. То же справедливо для других специализированных классов субъектов и удостоверений утверждений, которые использовались в WIF 3.5.<br />– Класс `Microsoft.IdentityModel.Claims.ClaimsCollection` не реализован в WIF 4.5. Вместо этого коллекции утверждений представлены в виде перечислимых коллекций типа <xref:System.Security.Claims.Claim?displayProperty=nameWithType>.<br />Теперь -   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> и <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> предоставляют методы, которые полностью поддерживают LINQ.|
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Некоторые элементы и классы в WIF 4.5 были удалены, у других были изменены имена; например, `Microsoft.IdentityModel.Configuration.ServiceConfiguration` теперь носит имя <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSIdentity`|Не реализовано в WIF 4.5|В WIF 3.5 присутствовали классы для поддержки CardSpace, эти классы не реализованы в WIF 4.5.|
|`Microsoft.IdentityModel.Protocols.WSTrust`|Разделено между пространствами имен <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> и <xref:System.ServiceModel.Security?displayProperty=nameWithType>.|Классы, представляющие артефакты WS-Trust (например, класс <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>), находятся в пространстве имен <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. Классы, которые представляют контракты службы WCF, узлы службы и каналы, позволяющие службе WCF обмениваться данными по протоколу WS-Trust, находятся в пространстве имен <xref:System.ServiceModel.Security?displayProperty=nameWithType>. К таким классам относится, например, класс <xref:System.ServiceModel.Security.WSTrustServiceHost>.|
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|Не реализовано в WIF 4.5|-|
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|Не реализовано в WIF 4.5|Включало классы, которые представляли константы шифрования XML в WIF 3.5. Эти константы не реализованы в WIF 4.5.|
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|Класс `EnvelopingSignature` и классы, которые представляют константы, не реализованы.|
|`Microsoft.IdentityModel.SecurityTokenService`|Разделено между пространствами имен <xref:System.IdentityModel?displayProperty=nameWithType>, <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> и <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>.|-|
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Большинство классов, которые предоставляют конфигурацию для пассивных сценариев (WS-Federation), были перемещены в <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>, однако некоторые из этих классов находятся в <xref:System.IdentityModel.Services?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Web.Controls`|Не реализовано в WIF 4.5|Классы в `Microsoft.IdentityModel.Web.Controls` реализуют федеративное пассивное управление входом в систему, которое отсутствует в WIF 4.5.|
|`Microsoft.IdentityModel.WindowsTokenService`|Не реализовано в WIF 4.5|-|

## <a name="see-also"></a>См. также

- [Новые возможности Windows Identity Foundation 4.5](whats-new-in-wif.md)
- [Руководства по миграции приложения, созданного с использованием WIF 3.5, в WIF 4.5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
