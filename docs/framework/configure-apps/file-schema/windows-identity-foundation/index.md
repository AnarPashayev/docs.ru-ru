---
title: Схема конфигурации Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 9c8009b4d95e5aa2c3d9bb8a8958040127a9e628
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791673"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="f5bb3-102">Схема конфигурации Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="f5bb3-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="f5bb3-103">В представленных в этом разделе статьях приводятся сведения о схеме конфигурации Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="f5bb3-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="f5bb3-104">Можно также настроить приложение для использования посредством классов, предоставляемых платформой WIF.</span><span class="sxs-lookup"><span data-stu-id="f5bb3-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="f5bb3-105">Эти классы указываются в разделах, посвященных соответствующим элементам схемы.</span><span class="sxs-lookup"><span data-stu-id="f5bb3-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="f5bb3-106">Ниже показана базовая структура тегов XML, предоставляемая схемой конфигурации WIF.</span><span class="sxs-lookup"><span data-stu-id="f5bb3-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="f5bb3-107">Атрибуты не приводятся.</span><span class="sxs-lookup"><span data-stu-id="f5bb3-107">Attributes are omitted.</span></span> <span data-ttu-id="f5bb3-108">Выделенные комментарии указывают на основные компоненты схемы.</span><span class="sxs-lookup"><span data-stu-id="f5bb3-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<system.identityModel>  
    <!-- Service Configuration -->  
    <identityConfiguration>  
        <caches>  
            <sessionSecurityTokenCache />  
            <tokenReplayCache />  
        </caches>  
  
        <certificateValidation>  
            <certificateValidator />   
        </certificateValidation>  
  
        <claimsAuthenticationManager />  
  
        <claimsAuthorizationManager>  
            <optionalConfigurationElement>  
        </claimsAuthorizationManager>  
  
        <claimTypeRequired>  
            <claimType />   
        </claimTypeRequired>  
  
        <tokenReplayDetection />  
  
        <!-- Security Token Handler Collection Configuration -->  
        <securityTokenHandlers>  
            <add>  
                <!-- Can take an optional configuration element which can be one of  
                     the following or a custom element -->  
                <samlSecurityTokenHandlerRequirement>  
                    <nameClaimType>  
                    <roleClaimType>   
                </samlSecurityTokenHandlerRequirement>  
  
                <sessionSecurityTokenHandlerRequirement />  
                <x509SecurityTokenHandlerRequirement />  
                <userNameSecurityTokenHandlerRequirement />  
            </add>  
            <clear />  
            <remove />  
            <securityTokenHandlerConfiguration>  
                <audienceUris>  
                    <add>  
                    <clear>  
                    <remove>  
                </audienceUris>  
  
                <caches>  
                    <sessionSecurityTokenCache />  
                    <tokenReplayCache />  
                </caches>  
  
                <certificateValidation>  
                    <certificateValidator>   
                </certificateValidation>  
  
                <issuerNameRegistry>  
                    <!-- Can take an optional configuration element which can be   
                         the <trustedIssuers> element to configure a configuration-based  
                         issuer name registry or can be a custom element -->  
                    <trustedIssuers>  
                        <add>  
                        <clear>  
                        <remove>  
                    </trustedIssuers>  
                </issuerNameRegistry>  
  
                <issuerTokenResolver />  
                <serviceTokenResolver />  
                <tokenReplayDetection />  
            </securityTokenHandlerConfiguration>  
        </securityTokenHandlers>  
    </identityConfiguration>  
</system.identityModel>  
  
<system.identityModel.services>  
    <!-- Federation Authentication Configuration -->  
    <federatedAuthentication>  
        <cookieHandler>  
            <chunkedCookieHandler />  
            <customCookieHandler />  
        </cookieHandler>  
  
        <serviceCertificate>  
            <certificateReference>  
        </serviceCertificate>  
  
        <wsFederation />  
    </federatedAuthentication>  
</system.identityModel.services>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="f5bb3-109">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="f5bb3-109">In This Section</span></span>  
 <span data-ttu-id="f5bb3-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Предоставляет конфигурацию для включения параметров WIF в приложениях.</span><span class="sxs-lookup"><span data-stu-id="f5bb3-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="f5bb3-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Предоставляет конфигурацию пассивной федерации посредством WIF.</span><span class="sxs-lookup"><span data-stu-id="f5bb3-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="f5bb3-112">Настраивает модуль проверки подлинности сеансов (SAM) и модуль федеративной проверки подлинности (WSFAM).</span><span class="sxs-lookup"><span data-stu-id="f5bb3-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
