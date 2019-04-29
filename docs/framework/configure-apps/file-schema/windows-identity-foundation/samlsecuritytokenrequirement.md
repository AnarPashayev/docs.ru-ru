---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: e1b8acd48ee185b3c6c50f70321bb9ca66e8e02b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793865"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="85e2d-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="85e2d-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="85e2d-102">Предоставляет конфигурацию для <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> класса <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> класс или класс, производный от любого из этих классов.</span><span class="sxs-lookup"><span data-stu-id="85e2d-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="85e2d-103">Представленный <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> класса.</span><span class="sxs-lookup"><span data-stu-id="85e2d-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="85e2d-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="85e2d-104">\<system.identityModel></span></span>  
<span data-ttu-id="85e2d-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="85e2d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="85e2d-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="85e2d-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="85e2d-107">\<add></span><span class="sxs-lookup"><span data-stu-id="85e2d-107">\<add></span></span>  
<span data-ttu-id="85e2d-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="85e2d-108">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e2d-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85e2d-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85e2d-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="85e2d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="85e2d-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="85e2d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85e2d-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="85e2d-112">Attributes</span></span>  
  
|<span data-ttu-id="85e2d-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="85e2d-113">Attribute</span></span>|<span data-ttu-id="85e2d-114">Описание</span><span class="sxs-lookup"><span data-stu-id="85e2d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85e2d-115">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="85e2d-115">mapToWindows</span></span>|<span data-ttu-id="85e2d-116">Указывает ли обработчик токенов следует сопоставить маркер проверки в учетную запись Windows с помощью входящего утверждения имени участника-пользователя.</span><span class="sxs-lookup"><span data-stu-id="85e2d-116">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="85e2d-117">Значение по умолчанию — «false».</span><span class="sxs-lookup"><span data-stu-id="85e2d-117">The default is "false".</span></span>|  
|<span data-ttu-id="85e2d-118">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="85e2d-118">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="85e2d-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Значение, определяющее режим отзыва для сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="85e2d-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="85e2d-120">Значение по умолчанию — «В сети».</span><span class="sxs-lookup"><span data-stu-id="85e2d-120">The default value is "Online".</span></span>|  
|<span data-ttu-id="85e2d-121">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="85e2d-121">issuerCertificateValidationMode</span></span>|<span data-ttu-id="85e2d-122"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Значение, определяющее режим проверки для сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="85e2d-122">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="85e2d-123">Значение по умолчанию — «PeerOrChainTrust».</span><span class="sxs-lookup"><span data-stu-id="85e2d-123">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="85e2d-124">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="85e2d-124">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="85e2d-125">Объект <xref:System.Security.Cryptography.X509Certificates.StoreLocation> значение, которое указывает хранилище сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="85e2d-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="85e2d-126">Значение по умолчанию — «LocalMachine».</span><span class="sxs-lookup"><span data-stu-id="85e2d-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="85e2d-127">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="85e2d-127">issuerCertificateValidator</span></span>|<span data-ttu-id="85e2d-128">Пользовательский тип, производный от <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="85e2d-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="85e2d-129">Если `issuerCertificateValidationMode` атрибут «Custom», экземпляр этого типа используется для проверки сертификата издателя.</span><span class="sxs-lookup"><span data-stu-id="85e2d-129">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85e2d-130">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="85e2d-130">Child Elements</span></span>  
  
|<span data-ttu-id="85e2d-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="85e2d-131">Element</span></span>|<span data-ttu-id="85e2d-132">Описание</span><span class="sxs-lookup"><span data-stu-id="85e2d-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85e2d-133">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="85e2d-133">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="85e2d-134">Задает тип утверждения, указывающее <xref:System.Security.Principal.IIdentity.Name%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="85e2d-134">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="85e2d-135">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="85e2d-135">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="85e2d-136">Указывает тип утверждения, определяет тип утверждения роли в коллекции <xref:System.Security.Claims.ClaimsIdentity> объектов, возвращенных <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> метод из обработчика токенов.</span><span class="sxs-lookup"><span data-stu-id="85e2d-136">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85e2d-137">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="85e2d-137">Parent Elements</span></span>  
  
|<span data-ttu-id="85e2d-138">Элемент</span><span class="sxs-lookup"><span data-stu-id="85e2d-138">Element</span></span>|<span data-ttu-id="85e2d-139">Описание</span><span class="sxs-lookup"><span data-stu-id="85e2d-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85e2d-140">\<add></span><span class="sxs-lookup"><span data-stu-id="85e2d-140">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="85e2d-141">Добавляет обработчик токенов безопасности в коллекцию обработчиков токенов.</span><span class="sxs-lookup"><span data-stu-id="85e2d-141">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85e2d-142">Примечания</span><span class="sxs-lookup"><span data-stu-id="85e2d-142">Remarks</span></span>  
 <span data-ttu-id="85e2d-143">`<samlSecurityTokenRequirement>` Элемент, представленный объектом <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> класса в объектной модели и используется для настройки `SamlSecurityTokenRequirement` свойство <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> или <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="85e2d-143">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85e2d-144">Пример</span><span class="sxs-lookup"><span data-stu-id="85e2d-144">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
