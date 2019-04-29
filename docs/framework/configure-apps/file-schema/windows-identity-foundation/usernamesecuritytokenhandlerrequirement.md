---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 18769794da8528f085c567264827db5aa6b214f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790459"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="b6b2a-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="b6b2a-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="b6b2a-102">Предоставляет конфигурацию для <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> классом или производными классами.</span><span class="sxs-lookup"><span data-stu-id="b6b2a-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="b6b2a-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b6b2a-103">\<system.identityModel></span></span>  
<span data-ttu-id="b6b2a-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b6b2a-104">\<identityConfiguration></span></span>  
<span data-ttu-id="b6b2a-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="b6b2a-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b6b2a-106">\<add></span><span class="sxs-lookup"><span data-stu-id="b6b2a-106">\<add></span></span>  
<span data-ttu-id="b6b2a-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="b6b2a-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b2a-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b6b2a-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6b2a-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b6b2a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b6b2a-110">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b6b2a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6b2a-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b6b2a-111">Attributes</span></span>  
  
|<span data-ttu-id="b6b2a-112">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b6b2a-112">Attribute</span></span>|<span data-ttu-id="b6b2a-113">Описание</span><span class="sxs-lookup"><span data-stu-id="b6b2a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6b2a-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="b6b2a-114">membershipProviderName</span></span>|<span data-ttu-id="b6b2a-115">Указывает <xref:System.Web.Security.MembershipProvider> , рекомендуется использовать обработчик токенов безопасности.</span><span class="sxs-lookup"><span data-stu-id="b6b2a-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6b2a-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b6b2a-116">Child Elements</span></span>  
 <span data-ttu-id="b6b2a-117">Нет</span><span class="sxs-lookup"><span data-stu-id="b6b2a-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6b2a-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b6b2a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b6b2a-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="b6b2a-119">Element</span></span>|<span data-ttu-id="b6b2a-120">Описание</span><span class="sxs-lookup"><span data-stu-id="b6b2a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6b2a-121">\<add></span><span class="sxs-lookup"><span data-stu-id="b6b2a-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="b6b2a-122">Добавляет обработчик токенов безопасности в коллекцию обработчиков токенов.</span><span class="sxs-lookup"><span data-stu-id="b6b2a-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6b2a-123">Примечания</span><span class="sxs-lookup"><span data-stu-id="b6b2a-123">Remarks</span></span>  
 <span data-ttu-id="b6b2a-124">`<userNameSecurityTokenHandlerRequirement>` Наборов элементов <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> свойство при <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> объект инициализирован из конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b6b2a-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6b2a-125">Пример</span><span class="sxs-lookup"><span data-stu-id="b6b2a-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
