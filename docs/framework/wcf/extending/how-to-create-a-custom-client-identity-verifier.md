---
title: Практическое руководство. Создание пользовательского средства проверки идентификации клиентов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: 86e7869efdba50d72cc61a1aebb767cf43927546
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795631"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="96b4e-102">Практическое руководство. Создание пользовательского средства проверки идентификации клиентов</span><span class="sxs-lookup"><span data-stu-id="96b4e-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="96b4e-103">Функция *идентификации* Windows Communication Foundation (WCF) позволяет клиенту заранее указать ожидаемое удостоверение службы.</span><span class="sxs-lookup"><span data-stu-id="96b4e-103">The *identity* feature of Windows Communication Foundation (WCF) enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="96b4e-104">Всякий раз, когда сервер доказывает свою подлинность клиенту, удостоверение проверяется на соответствие ожидаемому удостоверению.</span><span class="sxs-lookup"><span data-stu-id="96b4e-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="96b4e-105">(Сведения об удостоверении и принципах его работы см. в разделе [удостоверение службы и проверка подлинности](../feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="96b4e-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="96b4e-106">При необходимости процедуру проверки можно настроить, используя пользовательское средство проверки удостоверения.</span><span class="sxs-lookup"><span data-stu-id="96b4e-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="96b4e-107">Например, можно выполнять дополнительные процедуры проверки удостоверения службы.</span><span class="sxs-lookup"><span data-stu-id="96b4e-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="96b4e-108">В данном примере пользовательское средство проверки удостоверения проверяет дополнительные утверждения в сертификате X.509, возвращенном от сервера.</span><span class="sxs-lookup"><span data-stu-id="96b4e-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="96b4e-109">Пример приложения см. в разделе [Пример удостоверения службы](../samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="96b4e-109">For a sample application, see [Service Identity Sample](../samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="96b4e-110">Расширение класса EndpointIdentity</span><span class="sxs-lookup"><span data-stu-id="96b4e-110">To extend the EndpointIdentity class</span></span>  
  
1. <span data-ttu-id="96b4e-111">Определите новый класс, наследуемый от класса <xref:System.ServiceModel.EndpointIdentity>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="96b4e-112">В этом примере расширению присвоено имя `OrgEndpointIdentity`.</span><span class="sxs-lookup"><span data-stu-id="96b4e-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2. <span data-ttu-id="96b4e-113">Добавьте закрытые члены со свойствами, которые будут использоваться расширенным классом <xref:System.ServiceModel.Security.IdentityVerifier> для проверки удостоверения на соответствие утверждениям в маркере безопасности, возвращенном от службы.</span><span class="sxs-lookup"><span data-stu-id="96b4e-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="96b4e-114">В этом примере определено одно свойство: свойство `OrganizationClaim`.</span><span class="sxs-lookup"><span data-stu-id="96b4e-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="96b4e-115">Расширение класса IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="96b4e-115">To extend the IdentityVerifier class</span></span>  
  
1. <span data-ttu-id="96b4e-116">Определите новый класс, наследуемый от <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="96b4e-117">В этом примере расширению присвоено имя `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="96b4e-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. <span data-ttu-id="96b4e-118">Переопределите метод <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> .</span><span class="sxs-lookup"><span data-stu-id="96b4e-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="96b4e-119">Этот метод определяет, успешно ли пройдена проверка удостоверения.</span><span class="sxs-lookup"><span data-stu-id="96b4e-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3. <span data-ttu-id="96b4e-120">Метод `CheckAccess` имеет два параметра.</span><span class="sxs-lookup"><span data-stu-id="96b4e-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="96b4e-121">Первый представляет собой экземпляр класса <xref:System.ServiceModel.EndpointIdentity>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="96b4e-122">Второй является экземпляром класса <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="96b4e-123">В реализации метода необходимо проанализировать коллекцию утверждений, возвращенную свойством <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> класса <xref:System.IdentityModel.Policy.AuthorizationContext>, и выполнить требуемые процедуры проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="96b4e-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="96b4e-124">В этом примере сначала выполняется поиск утверждения типа "различающееся имя" (DistinguishedName), после чего имя сравнивается с расширением класса <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span><span class="sxs-lookup"><span data-stu-id="96b4e-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="96b4e-125">Реализация метода TryGetIdentity</span><span class="sxs-lookup"><span data-stu-id="96b4e-125">To implement the TryGetIdentity method</span></span>  
  
1. <span data-ttu-id="96b4e-126">Реализуйте метод <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A>, который определяет, может ли клиентом быть возвращен экземпляр класса <xref:System.ServiceModel.EndpointIdentity>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="96b4e-127">Инфраструктура WCF вызывает реализацию `TryGetIdentity` метода сначала, чтобы получить удостоверение службы из сообщения.</span><span class="sxs-lookup"><span data-stu-id="96b4e-127">The WCF infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="96b4e-128">Затем инфраструктура вызывает реализацию метода `CheckAccess` с возвращенными объектами `EndpointIdentity` и <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2. <span data-ttu-id="96b4e-129">Поместите в метод `TryGetIdentity` следующий код:</span><span class="sxs-lookup"><span data-stu-id="96b4e-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="96b4e-130">Реализация пользовательской привязки и задание пользовательского IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="96b4e-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1. <span data-ttu-id="96b4e-131">Создайте метод, который возвращает объект <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="96b4e-132">В этом примере сначала создается экземпляр класса <xref:System.ServiceModel.WSHttpBinding>, после чего для него задается режим безопасности <xref:System.ServiceModel.SecurityMode.Message>, а для его свойства <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> - значение <xref:System.ServiceModel.MessageCredentialType.None>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2. <span data-ttu-id="96b4e-133">Создайте коллекцию <xref:System.ServiceModel.Channels.BindingElementCollection> с помощью метода <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="96b4e-134">Возвратите из коллекции объект <xref:System.ServiceModel.Channels.SecurityBindingElement> и приведите его к переменной <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4. <span data-ttu-id="96b4e-135">Присвойте свойству <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> класса <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> в качестве значения новый экземпляр ранее созданного класса `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="96b4e-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. <span data-ttu-id="96b4e-136">Возвращаемая пользовательская привязка используется для создания экземпляра клиента и класса.</span><span class="sxs-lookup"><span data-stu-id="96b4e-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="96b4e-137">Клиент затем может выполнить пользовательскую проверку удостоверения службы, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="96b4e-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="96b4e-138">Пример</span><span class="sxs-lookup"><span data-stu-id="96b4e-138">Example</span></span>  
 <span data-ttu-id="96b4e-139">В следующем примере показана полная реализация класса <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="96b4e-140">Пример</span><span class="sxs-lookup"><span data-stu-id="96b4e-140">Example</span></span>  
 <span data-ttu-id="96b4e-141">В следующем примере показана полная реализация класса <xref:System.ServiceModel.EndpointIdentity>.</span><span class="sxs-lookup"><span data-stu-id="96b4e-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="96b4e-142">См. также</span><span class="sxs-lookup"><span data-stu-id="96b4e-142">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="96b4e-143">Образец идентификации службы</span><span class="sxs-lookup"><span data-stu-id="96b4e-143">Service Identity Sample</span></span>](../samples/service-identity-sample.md)
- [<span data-ttu-id="96b4e-144">Политика авторизации</span><span class="sxs-lookup"><span data-stu-id="96b4e-144">Authorization Policy</span></span>](../samples/authorization-policy.md)
