---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 8c7b7c9b42ac72b878aed4e12298dc3655f1e707
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793878"
---
# <a name="roleclaimtype"></a><span data-ttu-id="3d2cd-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="3d2cd-101">\<roleClaimType></span></span>
<span data-ttu-id="3d2cd-102">Указывает тип утверждения, определяет тип утверждения роли в коллекции <xref:System.Security.Claims.ClaimsIdentity> объектов, возвращенных <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> метод из обработчика токенов.</span><span class="sxs-lookup"><span data-stu-id="3d2cd-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="3d2cd-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3d2cd-103">\<system.identityModel></span></span>  
<span data-ttu-id="3d2cd-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3d2cd-104">\<identityConfiguration></span></span>  
<span data-ttu-id="3d2cd-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="3d2cd-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3d2cd-106">\<add></span><span class="sxs-lookup"><span data-stu-id="3d2cd-106">\<add></span></span>  
<span data-ttu-id="3d2cd-107">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="3d2cd-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="3d2cd-108">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="3d2cd-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d2cd-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3d2cd-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d2cd-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3d2cd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3d2cd-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3d2cd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d2cd-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3d2cd-112">Attributes</span></span>  
  
|<span data-ttu-id="3d2cd-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3d2cd-113">Attribute</span></span>|<span data-ttu-id="3d2cd-114">Описание</span><span class="sxs-lookup"><span data-stu-id="3d2cd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d2cd-115">value</span><span class="sxs-lookup"><span data-stu-id="3d2cd-115">value</span></span>|<span data-ttu-id="3d2cd-116">Строка, указывающая URI, представляющий тип требования утверждения для тип утверждения роли.</span><span class="sxs-lookup"><span data-stu-id="3d2cd-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d2cd-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3d2cd-117">Child Elements</span></span>  
 <span data-ttu-id="3d2cd-118">Нет</span><span class="sxs-lookup"><span data-stu-id="3d2cd-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d2cd-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3d2cd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3d2cd-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="3d2cd-120">Element</span></span>|<span data-ttu-id="3d2cd-121">Описание</span><span class="sxs-lookup"><span data-stu-id="3d2cd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d2cd-122">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="3d2cd-122">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="3d2cd-123">Предоставляет конфигурацию для <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> класса <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> класс или класс, производный от любого из этих классов.</span><span class="sxs-lookup"><span data-stu-id="3d2cd-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d2cd-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="3d2cd-124">Remarks</span></span>  
 <span data-ttu-id="3d2cd-125">`<roleClaimType>` Наборов элементов <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> свойство при <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> объект инициализирован из конфигурации.</span><span class="sxs-lookup"><span data-stu-id="3d2cd-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d2cd-126">Пример</span><span class="sxs-lookup"><span data-stu-id="3d2cd-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d2cd-127">См. также</span><span class="sxs-lookup"><span data-stu-id="3d2cd-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
