---
title: Практическое руководство. Анализ контекста безопасности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
ms.openlocfilehash: 40950614892ddfd4eb24194f0389e057a5a13378
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272948"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="8889f-102">Практическое руководство. Анализ контекста безопасности</span><span class="sxs-lookup"><span data-stu-id="8889f-102">How to: Examine the Security Context</span></span>

<span data-ttu-id="8889f-103">При программировании служб Windows Communication Foundation (WCF) контекст безопасности службы позволяет определить сведения о клиентских учетных данных и утверждениях, используемых для проверки подлинности в службе.</span><span class="sxs-lookup"><span data-stu-id="8889f-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="8889f-104">Это осуществляется с помощью свойств класса <xref:System.ServiceModel.ServiceSecurityContext>.</span><span class="sxs-lookup"><span data-stu-id="8889f-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="8889f-105">Например, извлечь удостоверение текущего клиента можно с помощью свойства <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> или <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="8889f-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="8889f-106">Чтобы определить, является ли клиент анонимным, следует использовать свойство <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>.</span><span class="sxs-lookup"><span data-stu-id="8889f-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="8889f-107">Кроме того, перебором коллекции утверждений в свойстве <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> можно определить, какие утверждения делаются от имени клиента.</span><span class="sxs-lookup"><span data-stu-id="8889f-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="8889f-108">Получение текущего контекста безопасности</span><span class="sxs-lookup"><span data-stu-id="8889f-108">To get the current security context</span></span>  
  
- <span data-ttu-id="8889f-109">Для получения текущего контекста безопасности необходимо получить доступ к статическому свойству <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="8889f-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="8889f-110">После этого можно проверять любые свойства текущего контекста из ссылки.</span><span class="sxs-lookup"><span data-stu-id="8889f-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="8889f-111">Определение удостоверения вызывающего объекта</span><span class="sxs-lookup"><span data-stu-id="8889f-111">To determine the identity of the caller</span></span>  
  
1. <span data-ttu-id="8889f-112">Выведите на печать значение свойств <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> и <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="8889f-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="8889f-113">Анализ утверждений вызывающего объекта</span><span class="sxs-lookup"><span data-stu-id="8889f-113">To parse the claims of a caller</span></span>  
  
1. <span data-ttu-id="8889f-114">Верните текущий класс <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="8889f-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="8889f-115">Используйте свойство <xref:System.ServiceModel.ServiceSecurityContext.Current%2A>, чтобы вернуть текущий контекст безопасности службы, и верните контекст `AuthorizationContext` с помощью свойства <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.</span><span class="sxs-lookup"><span data-stu-id="8889f-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2. <span data-ttu-id="8889f-116">Проанализируйте коллекцию объектов <xref:System.IdentityModel.Claims.ClaimSet>, возвращаемую свойством <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> класса <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="8889f-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8889f-117">Пример</span><span class="sxs-lookup"><span data-stu-id="8889f-117">Example</span></span>  

 <span data-ttu-id="8889f-118">В следующем примере выводятся на печать значения свойств <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> и <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> текущего контекста безопасности, свойство <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, значение ресурса утверждения и свойство <xref:System.IdentityModel.Claims.Claim.Right%2A> каждого утверждения текущего контекста безопасности.</span><span class="sxs-lookup"><span data-stu-id="8889f-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8889f-119">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="8889f-119">Compiling the Code</span></span>  

 <span data-ttu-id="8889f-120">В коде используются следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="8889f-120">The code uses the following namespaces:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="8889f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="8889f-121">See also</span></span>

- [<span data-ttu-id="8889f-122">Защита служб</span><span class="sxs-lookup"><span data-stu-id="8889f-122">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="8889f-123">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="8889f-123">Service Identity and Authentication</span></span>](./feature-details/service-identity-and-authentication.md)
