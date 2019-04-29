---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: ecf26263bf47e8b4609e7adc208f0a59a2fa795b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667331"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="4d881-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="4d881-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="4d881-102">Регистрирует диспетчер аутентификации утверждений для входящих утверждений.</span><span class="sxs-lookup"><span data-stu-id="4d881-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="4d881-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4d881-103">\<system.identityModel></span></span>  
<span data-ttu-id="4d881-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4d881-104">\<identityConfiguration></span></span>  
<span data-ttu-id="4d881-105">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="4d881-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d881-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4d881-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d881-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4d881-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4d881-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4d881-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d881-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4d881-109">Attributes</span></span>  
  
|<span data-ttu-id="4d881-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4d881-110">Attribute</span></span>|<span data-ttu-id="4d881-111">Описание</span><span class="sxs-lookup"><span data-stu-id="4d881-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d881-112">type</span><span class="sxs-lookup"><span data-stu-id="4d881-112">type</span></span>|<span data-ttu-id="4d881-113">Задает пользовательский тип, производный от <xref:System.Security.Claims.ClaimsAuthenticationManager> класса.</span><span class="sxs-lookup"><span data-stu-id="4d881-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="4d881-114">Дополнительные сведения о способах указания `type` атрибут, см. в разделе [пользовательский тип ссылки].</span><span class="sxs-lookup"><span data-stu-id="4d881-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d881-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4d881-115">Child Elements</span></span>  
 <span data-ttu-id="4d881-116">Если не `type` атрибут, или если `type` ссылки на атрибуты <xref:System.Security.Claims.ClaimsAuthenticationManager> класс, `<claimsAuthenticationManager>` элемент выполняет только дочерние элементы; тем не менее, классы, производные от <xref:System.Security.Claims.ClaimsAuthenticationManager> можно определить дочерние элементы конфигурации.</span><span class="sxs-lookup"><span data-stu-id="4d881-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d881-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4d881-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4d881-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="4d881-118">Element</span></span>|<span data-ttu-id="4d881-119">Описание</span><span class="sxs-lookup"><span data-stu-id="4d881-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d881-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4d881-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="4d881-121">Указывает параметры уровня службы идентификации.</span><span class="sxs-lookup"><span data-stu-id="4d881-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d881-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="4d881-122">Remarks</span></span>  
 <span data-ttu-id="4d881-123">Поведение по умолчанию, предоставляемых <xref:System.Security.Claims.ClaimsAuthenticationManager> класс выводит входящие утверждения.</span><span class="sxs-lookup"><span data-stu-id="4d881-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="4d881-124">Если не `type` атрибут указан или если `type` атрибут задает <xref:System.Security.Claims.ClaimsAuthenticationManager> класс, `<claimsAuthenticationManager>` элемент выполняет только дочерние элементы.</span><span class="sxs-lookup"><span data-stu-id="4d881-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="4d881-125">Можно указать `type` атрибут для регистрации типа производным от <xref:System.Security.Claims.ClaimsAuthenticationManager> класса, чтобы реализовать пользовательское поведение.</span><span class="sxs-lookup"><span data-stu-id="4d881-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="4d881-126">Производные классы могут поддерживает настройку с помощью дочерних элементов `<claimsAuthenticationManager>` элемент путем переопределения <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> метод для обработки этих элементов.</span><span class="sxs-lookup"><span data-stu-id="4d881-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="4d881-127">В схеме, определенной для дочерних элементов зависит от конструктора класса.</span><span class="sxs-lookup"><span data-stu-id="4d881-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="4d881-128">`<claimsAuthenticationManager>` Наборов элементов <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> свойство.</span><span class="sxs-lookup"><span data-stu-id="4d881-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d881-129">Пример</span><span class="sxs-lookup"><span data-stu-id="4d881-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
