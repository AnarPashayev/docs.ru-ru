---
title: Практическое руководство. Создание подтверждающих учетных данных
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 2f922f2df424b0ca2a468ae2f6cb8e8753e1d8a1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635496"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="78d1f-102">Практическое руководство. Создание подтверждающих учетных данных</span><span class="sxs-lookup"><span data-stu-id="78d1f-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="78d1f-103">Некоторые пользовательские схемы безопасности требуют нескольких учетных данных.</span><span class="sxs-lookup"><span data-stu-id="78d1f-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="78d1f-104">Например, служба может потребовать от клиента не только имя пользователя и пароль, но и учетные данные, доказывающие, что возраст клиента старше 18 лет.</span><span class="sxs-lookup"><span data-stu-id="78d1f-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="78d1f-105">Вторые учетные данные являются *вспомогательными учетными данными*.</span><span class="sxs-lookup"><span data-stu-id="78d1f-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="78d1f-106">В этом разделе объясняется, как реализовать эти учетные данные в клиентском приложении Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="78d1f-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78d1f-107">Спецификация для поддержки учетных данных является частью спецификации WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="78d1f-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="78d1f-108">Дополнительные сведения см. в разделе [спецификации безопасности веб-служб](https://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="78d1f-108">For more information, see [Web Services Security Specifications](https://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="78d1f-109">Вспомогательные маркеры</span><span class="sxs-lookup"><span data-stu-id="78d1f-109">Supporting Tokens</span></span>  
 <span data-ttu-id="78d1f-110">Вкратце, при использовании безопасности сообщений, *основные учетные данные* всегда используется для защиты сообщения (например, сертификат X.509 или билет Kerberos).</span><span class="sxs-lookup"><span data-stu-id="78d1f-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="78d1f-111">Как определено в спецификации, привязка безопасности использует *маркеры* для защиты обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="78d1f-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="78d1f-112">Объект *маркера* является представлением учетных данных безопасности.</span><span class="sxs-lookup"><span data-stu-id="78d1f-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="78d1f-113">Привязка безопасности использует основной маркер, определенный в политике привязки безопасности, для создания подписи.</span><span class="sxs-lookup"><span data-stu-id="78d1f-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="78d1f-114">Эта подпись называется *подпись сообщения*.</span><span class="sxs-lookup"><span data-stu-id="78d1f-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="78d1f-115">Чтобы расширить утверждения, предоставляемые маркером, связанным с подписью сообщения, можно задать дополнительные маркеры.</span><span class="sxs-lookup"><span data-stu-id="78d1f-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="78d1f-116">Подтверждение, подпись и шифрование</span><span class="sxs-lookup"><span data-stu-id="78d1f-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="78d1f-117">Наличие вспомогательных учетных данных приводит к *вспомогательного маркера* передаются в сообщении.</span><span class="sxs-lookup"><span data-stu-id="78d1f-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="78d1f-118">Спецификация WS-SecurityPolicy определяет четыре способа прикрепления вспомогательного маркера к сообщению (см. следующую таблицу).</span><span class="sxs-lookup"><span data-stu-id="78d1f-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="78d1f-119">Цель</span><span class="sxs-lookup"><span data-stu-id="78d1f-119">Purpose</span></span>|<span data-ttu-id="78d1f-120">Описание</span><span class="sxs-lookup"><span data-stu-id="78d1f-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78d1f-121">Со знаком</span><span class="sxs-lookup"><span data-stu-id="78d1f-121">Signed</span></span>|<span data-ttu-id="78d1f-122">Вспомогательный маркер включен в заголовок безопасности и подписан подписью сообщения.</span><span class="sxs-lookup"><span data-stu-id="78d1f-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="78d1f-123">Подтверждающий</span><span class="sxs-lookup"><span data-stu-id="78d1f-123">Endorsing</span></span>|<span data-ttu-id="78d1f-124">*Подтверждающий маркер* подпись сообщения.</span><span class="sxs-lookup"><span data-stu-id="78d1f-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="78d1f-125">Подписанный и подтверждающий</span><span class="sxs-lookup"><span data-stu-id="78d1f-125">Signed and Endorsing</span></span>|<span data-ttu-id="78d1f-126">Подписанные подтверждающие маркеры подписывают весь элемент `ds:Signature`, произведенный из подписи сообщения, и сами подписываются этой подписью сообщения; то есть оба маркера (маркер, используемый для подписи сообщения, и подписанный подтверждающий маркер) подписывают друг друга.</span><span class="sxs-lookup"><span data-stu-id="78d1f-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="78d1f-127">Подписанный и шифрующий</span><span class="sxs-lookup"><span data-stu-id="78d1f-127">Signed and Encrypting</span></span>|<span data-ttu-id="78d1f-128">Подписанные, зашифрованные вспомогательные маркеры - это подписанные вспомогательные маркеры, которые шифруются при появлении в `wsse:SecurityHeader`.</span><span class="sxs-lookup"><span data-stu-id="78d1f-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="78d1f-129">Программирование вспомогательных учетных данных</span><span class="sxs-lookup"><span data-stu-id="78d1f-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="78d1f-130">Чтобы создать службу, использующую вспомогательные маркеры, необходимо создать [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="78d1f-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="78d1f-131">(Дополнительные сведения см. в разделе [как: Создание пользовательской привязки с использованием элемента SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="78d1f-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="78d1f-132">Первым шагом в создании пользовательской привязки является создание элемента привязки безопасности одного из трех следующих типов.</span><span class="sxs-lookup"><span data-stu-id="78d1f-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="78d1f-133">Все классы наследуются от элемента привязки безопасности <xref:System.ServiceModel.Channels.SecurityBindingElement>, включающего четыре взаимосвязанных свойства.</span><span class="sxs-lookup"><span data-stu-id="78d1f-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="78d1f-134">Области</span><span class="sxs-lookup"><span data-stu-id="78d1f-134">Scopes</span></span>  
 <span data-ttu-id="78d1f-135">Для вспомогательных учетных данных существует две области.</span><span class="sxs-lookup"><span data-stu-id="78d1f-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="78d1f-136">*Вспомогательные маркеры конечной точки* поддерживают все операции конечной точки.</span><span class="sxs-lookup"><span data-stu-id="78d1f-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="78d1f-137">Это значит, что учетные данные, представляемые вспомогательным маркером, могут использоваться всякий раз при вызове операций конечной точки.</span><span class="sxs-lookup"><span data-stu-id="78d1f-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="78d1f-138">*Вспомогательные маркеры операции* поддерживают только конкретную операцию конечной точки.</span><span class="sxs-lookup"><span data-stu-id="78d1f-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="78d1f-139">Имена свойств показывают, что вспомогательные учетные данные могут быть обязательными или необязательными.</span><span class="sxs-lookup"><span data-stu-id="78d1f-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="78d1f-140">То есть, если вспомогательные учетные данные имеются, они используются, хотя в этом нет необходимости, так как при отсутствии вспомогательных учетных данных не происходит сбой проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="78d1f-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="78d1f-141">Процедуры</span><span class="sxs-lookup"><span data-stu-id="78d1f-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="78d1f-142">Создание пользовательской привязки, которая включает вспомогательные учетные данные</span><span class="sxs-lookup"><span data-stu-id="78d1f-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="78d1f-143">Создайте элемент привязки безопасности.</span><span class="sxs-lookup"><span data-stu-id="78d1f-143">Create a security binding element.</span></span> <span data-ttu-id="78d1f-144">В следующем примере продемонстрировано создание элемента привязки безопасности <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> в режиме проверки подлинности `UserNameForCertificate`.</span><span class="sxs-lookup"><span data-stu-id="78d1f-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="78d1f-145">Воспользуйтесь методом <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="78d1f-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="78d1f-146">Добавьте вспомогательный параметр в коллекцию типов, возвращаемых соответствующим свойством (`Endorsing`, `Signed`, `SignedEncrypted` или `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="78d1f-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="78d1f-147">Типы в пространстве имен <xref:System.ServiceModel.Security.Tokens> включают наиболее часто используемые типы, такие как <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="78d1f-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78d1f-148">Пример</span><span class="sxs-lookup"><span data-stu-id="78d1f-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="78d1f-149">Описание</span><span class="sxs-lookup"><span data-stu-id="78d1f-149">Description</span></span>  
 <span data-ttu-id="78d1f-150">В следующем примере показано, как создать экземпляр <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> и добавить экземпляр класса <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> в коллекцию, возвращенную свойством Endorsing.</span><span class="sxs-lookup"><span data-stu-id="78d1f-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="78d1f-151">Код</span><span class="sxs-lookup"><span data-stu-id="78d1f-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="78d1f-152">См. также</span><span class="sxs-lookup"><span data-stu-id="78d1f-152">See also</span></span>

- [<span data-ttu-id="78d1f-153">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="78d1f-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
