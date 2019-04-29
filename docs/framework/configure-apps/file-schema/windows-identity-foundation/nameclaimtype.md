---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 5202e162a7eb5fc4e36d6a6c0a2c18af48872a69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791603"
---
# <a name="nameclaimtype"></a><span data-ttu-id="b5e92-101">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="b5e92-101">\<nameClaimType></span></span>
<span data-ttu-id="b5e92-102">Задает тип утверждения, указывающее <xref:System.Security.Principal.IIdentity.Name%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="b5e92-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="b5e92-103">Тип утверждения используется для поиска <xref:System.Security.Claims.Claim> в коллекцию <xref:System.Security.Claims.ClaimsIdentity> объектов, возвращенных <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> метод данного обработчика токенов.</span><span class="sxs-lookup"><span data-stu-id="b5e92-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="b5e92-104">Задайте значение соответствующее утверждение имени <xref:System.Security.Principal.IIdentity> созданные из этого обработчика токенов.</span><span class="sxs-lookup"><span data-stu-id="b5e92-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="b5e92-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b5e92-105">\<system.identityModel></span></span>  
<span data-ttu-id="b5e92-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b5e92-106">\<identityConfiguration></span></span>  
<span data-ttu-id="b5e92-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="b5e92-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b5e92-108">\<add></span><span class="sxs-lookup"><span data-stu-id="b5e92-108">\<add></span></span>  
<span data-ttu-id="b5e92-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="b5e92-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="b5e92-110">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="b5e92-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5e92-111">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b5e92-111">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5e92-112">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b5e92-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b5e92-113">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b5e92-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5e92-114">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b5e92-114">Attributes</span></span>  
  
|<span data-ttu-id="b5e92-115">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b5e92-115">Attribute</span></span>|<span data-ttu-id="b5e92-116">Описание</span><span class="sxs-lookup"><span data-stu-id="b5e92-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5e92-117">value</span><span class="sxs-lookup"><span data-stu-id="b5e92-117">value</span></span>|<span data-ttu-id="b5e92-118">Строка, указывающая URI, представляющий тип требования утверждения для <xref:System.Security.Principal.IIdentity.Name%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="b5e92-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="b5e92-119">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b5e92-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5e92-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b5e92-120">Child Elements</span></span>  
 <span data-ttu-id="b5e92-121">Нет</span><span class="sxs-lookup"><span data-stu-id="b5e92-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5e92-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b5e92-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b5e92-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="b5e92-123">Element</span></span>|<span data-ttu-id="b5e92-124">Описание</span><span class="sxs-lookup"><span data-stu-id="b5e92-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5e92-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="b5e92-125">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="b5e92-126">Предоставляет конфигурацию для <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> класса <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> класс или класс, производный от любого из этих классов.</span><span class="sxs-lookup"><span data-stu-id="b5e92-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5e92-127">Примечания</span><span class="sxs-lookup"><span data-stu-id="b5e92-127">Remarks</span></span>  
 <span data-ttu-id="b5e92-128">`<nameClaimType>` Наборов элементов <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> свойство при <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> объект инициализирован из конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b5e92-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5e92-129">Пример</span><span class="sxs-lookup"><span data-stu-id="b5e92-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5e92-130">См. также</span><span class="sxs-lookup"><span data-stu-id="b5e92-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
