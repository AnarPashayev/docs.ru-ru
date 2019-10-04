---
title: Элемент <serviceAuthorization>
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834013"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="4f15c-102">Элемент > @no__t 0serviceAuthorization</span><span class="sxs-lookup"><span data-stu-id="4f15c-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="4f15c-103">Задает параметры авторизации доступа к операциям службы.</span><span class="sxs-lookup"><span data-stu-id="4f15c-103">Specifies settings that authorize access to service operations</span></span>

<span data-ttu-id="4f15c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4f15c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4f15c-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4f15c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4f15c-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<behaviors >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4f15c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="4f15c-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4f15c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="4f15c-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t – 7[ **&nbsp;0behavior >** ](behavior-of-servicebehaviors.md)1</span><span class="sxs-lookup"><span data-stu-id="4f15c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\</span></span>
<span data-ttu-id="4f15c-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1serviceAuthorization >**</span><span class="sxs-lookup"><span data-stu-id="4f15c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="4f15c-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4f15c-110">Syntax</span></span>

```xml
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f15c-111">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="4f15c-111">Attributes and elements</span></span>

<span data-ttu-id="4f15c-112">В следующих разделах описываются атрибуты, дочерние элементы и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4f15c-112">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="4f15c-113">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4f15c-113">Attributes</span></span>

|<span data-ttu-id="4f15c-114">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4f15c-114">Attribute</span></span>|<span data-ttu-id="4f15c-115">Описание</span><span class="sxs-lookup"><span data-stu-id="4f15c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f15c-116">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="4f15c-116">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="4f15c-117">Логическое значение, которое определяет, должны ли все операции службы олицетворять вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="4f15c-117">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="4f15c-118">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="4f15c-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="4f15c-119">Если конкретная операция службы олицетворяет вызывающий объект, контекст потока переключается на контекст вызывающего объекта перед выполнением указанной службы.</span><span class="sxs-lookup"><span data-stu-id="4f15c-119">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="4f15c-120">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="4f15c-120">principalPermissionMode</span></span>|<span data-ttu-id="4f15c-121">Определяет участников, используемых для выполнения операций на сервере.</span><span class="sxs-lookup"><span data-stu-id="4f15c-121">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="4f15c-122">В эти значения входят:</span><span class="sxs-lookup"><span data-stu-id="4f15c-122">Values include the following:</span></span><br /><br /> <span data-ttu-id="4f15c-123">— Нет</span><span class="sxs-lookup"><span data-stu-id="4f15c-123">-   None</span></span><br /><span data-ttu-id="4f15c-124">-Усевиндовсграупс</span><span class="sxs-lookup"><span data-stu-id="4f15c-124">-   UseWindowsGroups</span></span><br /><span data-ttu-id="4f15c-125">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="4f15c-125">-   UseAspNetRoles</span></span><br /><span data-ttu-id="4f15c-126">— Пользовательский</span><span class="sxs-lookup"><span data-stu-id="4f15c-126">-   Custom</span></span><br /><br /> <span data-ttu-id="4f15c-127">Значение по умолчанию - «UseWindowsGroups».</span><span class="sxs-lookup"><span data-stu-id="4f15c-127">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="4f15c-128">Это значение типа <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="4f15c-128">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="4f15c-129">Дополнительные сведения об использовании этого атрибута см. в разделе [How to: Ограничьте доступ с помощью класса PrincipalPermissionAttribute @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="4f15c-129">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="4f15c-130">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="4f15c-130">roleProviderName</span></span>|<span data-ttu-id="4f15c-131">Строка, указывающая имя поставщика роли, который предоставляет сведения о роли для приложения Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4f15c-131">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="4f15c-132">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="4f15c-132">The default is an empty string.</span></span>|  
|<span data-ttu-id="4f15c-133">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="4f15c-133">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="4f15c-134">Строка, содержащая имя типа диспетчера авторизации служб.</span><span class="sxs-lookup"><span data-stu-id="4f15c-134">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="4f15c-135">Дополнительные сведения см. в разделе <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="4f15c-135">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="4f15c-136">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4f15c-136">Child elements</span></span>

|<span data-ttu-id="4f15c-137">Элемент</span><span class="sxs-lookup"><span data-stu-id="4f15c-137">Element</span></span>|<span data-ttu-id="4f15c-138">Описание</span><span class="sxs-lookup"><span data-stu-id="4f15c-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f15c-139">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="4f15c-139">authorizationPolicies</span></span>|<span data-ttu-id="4f15c-140">Содержит коллекцию типов политик авторизации, которые можно добавить с помощью ключевого слова`add`.</span><span class="sxs-lookup"><span data-stu-id="4f15c-140">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="4f15c-141">Каждая политика авторизации содержит один обязательный атрибут `policyType`, который имеет строковый тип.</span><span class="sxs-lookup"><span data-stu-id="4f15c-141">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="4f15c-142">Данный атрибут определяет политику авторизации, которая позволяет преобразовывать один набор входных требований в другой набор требований.</span><span class="sxs-lookup"><span data-stu-id="4f15c-142">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="4f15c-143">В зависимости от этого может быть предоставлено управление доступом или отказано в предоставлении управления доступом.</span><span class="sxs-lookup"><span data-stu-id="4f15c-143">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="4f15c-144">Дополнительные сведения см. в разделе <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="4f15c-144">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="4f15c-145">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4f15c-145">Parent elements</span></span>

|<span data-ttu-id="4f15c-146">Элемент</span><span class="sxs-lookup"><span data-stu-id="4f15c-146">Element</span></span>|<span data-ttu-id="4f15c-147">Описание</span><span class="sxs-lookup"><span data-stu-id="4f15c-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f15c-148">@no__t 1behavior ></span><span class="sxs-lookup"><span data-stu-id="4f15c-148">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="4f15c-149">Содержит коллекцию параметров для поведения службы.</span><span class="sxs-lookup"><span data-stu-id="4f15c-149">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="4f15c-150">Примечания</span><span class="sxs-lookup"><span data-stu-id="4f15c-150">Remarks</span></span>

<span data-ttu-id="4f15c-151">Этот раздел содержит элементы, влияющие на авторизацию, поставщики пользовательских ролей и олицетворение.</span><span class="sxs-lookup"><span data-stu-id="4f15c-151">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="4f15c-152">Атрибут `principalPermissionMode` указывает группы пользователей, которые следует использовать при авторизации использования защищенного метода.</span><span class="sxs-lookup"><span data-stu-id="4f15c-152">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="4f15c-153">Значение по умолчанию - `UseWindowsGroups`. Оно указывает, что при попытке доступа к ресурсу поиск удостоверения выполняется в таких группах Windows, как «Администраторы» или «Пользователи».</span><span class="sxs-lookup"><span data-stu-id="4f15c-153">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="4f15c-154">Можно также указать `UseAspNetRoles`, чтобы использовать настраиваемого поставщика ролей, настроенного в элементе @no__t -1system. Web >, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="4f15c-154">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

```xml
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```
  
<span data-ttu-id="4f15c-155">В следующем коде показан `roleProviderName`, используемый с атрибутом `principalPermissionMode`:</span><span class="sxs-lookup"><span data-stu-id="4f15c-155">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="4f15c-156">Подробный пример использования этого элемента конфигурации см. в разделе [авторизация доступа к операциям службы](../../../wcf/samples/authorizing-access-to-service-operations.md) и [политикам авторизации](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="4f15c-156">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4f15c-157">См. также</span><span class="sxs-lookup"><span data-stu-id="4f15c-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="4f15c-158">Поведения безопасности</span><span class="sxs-lookup"><span data-stu-id="4f15c-158">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="4f15c-159">Авторизация доступа к операциям службы</span><span class="sxs-lookup"><span data-stu-id="4f15c-159">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- <span data-ttu-id="4f15c-160">[Практическое руководство. Создание пользовательского диспетчера авторизации для службы @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="4f15c-160">[How to: Create a Custom Authorization Manager for a Service](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)</span></span>
- <span data-ttu-id="4f15c-161">[Практическое руководство. Ограничение доступа с помощью класса PrincipalPermissionAttribute @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="4f15c-161">[How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)</span></span>
- [<span data-ttu-id="4f15c-162">Политика авторизации</span><span class="sxs-lookup"><span data-stu-id="4f15c-162">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
