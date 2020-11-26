---
title: Программирование безопасности WCF
description: Узнайте, как создать безопасное приложение WCF, включая проверку подлинности, конфиденциальность и целостность.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 4ffbf6a05abd3ed9ebcea4b2e85f0dc305a4f2db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244773"
---
# <a name="programming-wcf-security"></a><span data-ttu-id="dd9ad-103">Программирование безопасности WCF</span><span class="sxs-lookup"><span data-stu-id="dd9ad-103">Programming WCF Security</span></span>

<span data-ttu-id="dd9ad-104">В этом разделе описываются фундаментальные задачи программирования, используемые для создания безопасного Windows Communication Foundation (WCF) приложения.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-104">This topic describes the fundamental programming tasks used to create a secure Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="dd9ad-105">В этом разделе рассматриваются только проверка подлинности, конфиденциальность и целостность, называемая *безопасностью перемещения*.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-105">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="dd9ad-106">В этом разделе не рассматривается авторизация (Управление доступом к ресурсам или службам). сведения об авторизации см. в разделе [авторизация](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-106">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd9ad-107">Чтобы получить ценные сведения о концепциях безопасности, особенно в отношении WCF, ознакомьтесь с набором руководств по работе с шаблонами и практическими рекомендациями на MSDN в [сценариях, шаблонах и руководствах по реализации усовершенствований веб-служб (WSE) 3,0](/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-107">For a valuable introduction to security concepts, especially in regard to WCF, see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="dd9ad-108">Программирование безопасности WCF основывается на трех шагах: режим безопасности, тип учетных данных клиента и значения учетных данных.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-108">Programming WCF security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="dd9ad-109">Эти действия можно выполнить с помощью кода или конфигурации.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-109">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="dd9ad-110">Задание режима безопасности</span><span class="sxs-lookup"><span data-stu-id="dd9ad-110">Setting the Security Mode</span></span>  

 <span data-ttu-id="dd9ad-111">Ниже описаны общие шаги для программирования с использованием режима безопасности в WCF.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-111">The following explains the general steps for programming with the security mode in WCF:</span></span>  
  
1. <span data-ttu-id="dd9ad-112">Выберите одну из предопределенных привязок, отвечающих требованиям приложения.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-112">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="dd9ad-113">Список вариантов привязки см. в разделе привязки, [предоставляемые системой](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-113">For a list of the binding choices, see [System-Provided Bindings](../system-provided-bindings.md).</span></span> <span data-ttu-id="dd9ad-114">По умолчанию практически во всех привязках включены функции безопасности.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-114">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="dd9ad-115">Единственным исключением является <xref:System.ServiceModel.BasicHttpBinding> класс (с использованием конфигурации, [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-115">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="dd9ad-116">Выбранная привязка определяет транспорт.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-116">The binding you select determines the transport.</span></span> <span data-ttu-id="dd9ad-117">Например, привязка <xref:System.ServiceModel.WSHttpBinding> использует протокол HTTP в качестве транспорта; привязка <xref:System.ServiceModel.NetTcpBinding> использует протокол TCP.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-117">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2. <span data-ttu-id="dd9ad-118">Выберите один из режимов безопасности привязки.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-118">Select one of the security modes for the binding.</span></span> <span data-ttu-id="dd9ad-119">Обратите внимание, что выбранная привязка определяет выбор доступных режимов.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-119">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="dd9ad-120">Например, привязка <xref:System.ServiceModel.WSDualHttpBinding> не позволяет обеспечить безопасность транспорта (это изменить нельзя).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-120">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="dd9ad-121">Аналогично, привязки <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> и <xref:System.ServiceModel.NetNamedPipeBinding> не обеспечивают безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-121">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="dd9ad-122">Доступны три варианта.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-122">You have three choices:</span></span>  
  
    1. `Transport`  
  
         <span data-ttu-id="dd9ad-123">Безопасность транспорта зависит от механизма, используемого в выбранной привязке.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-123">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="dd9ad-124">Например, при использовании привязки `WSHttpBinding` в качестве механизма безопасности выступает протокол SSL (который также служит механизмом для протокола HTTPS).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-124">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="dd9ad-125">Основное преимущество безопасности транспорта заключается в обеспечении большой пропускной способности независимо от используемого типа транспорта.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-125">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="dd9ad-126">Однако имеются два ограничения. Первое ограничение - транспортный механизм определяет тип учетных данных, используемых для проверки подлинности пользователя.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-126">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="dd9ad-127">Этот недостаток проявляется, только если служба взаимодействует с другими службами, которым требуются другие типы учетных данных.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-127">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="dd9ad-128">Второе ограничение заключается в том, что безопасность применяется не на уровне сообщений, поэтому безопасность реализуется последовательным, а не сквозным способом.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-128">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="dd9ad-129">Это ограничение представляет проблему только в том случае, если на пути сообщения между клиентом и службой имеются посредники.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-129">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> <span data-ttu-id="dd9ad-130">Дополнительные сведения о том, какой транспорт использовать, см. в разделе [Выбор транспорта](choosing-a-transport.md).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-130">For more information about which transport to use, see [Choosing a Transport](choosing-a-transport.md).</span></span> <span data-ttu-id="dd9ad-131">Дополнительные сведения об использовании безопасности транспорта см. в статье [Общие сведения о безопасности транспорта](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-131">For more information about using transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>  
  
    2. `Message`  
  
         <span data-ttu-id="dd9ad-132">Под безопасностью сообщений понимается наличие в каждом сообщении необходимых заголовок и данных для обеспечения безопасности сообщения.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-132">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="dd9ad-133">Поскольку состав заголовков не является фиксированным, можно включать любое количество учетных данных.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-133">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="dd9ad-134">Это становится важным в случае взаимодействия с другими службами, которым требуются учетные данные определенного типа, которые невозможно предоставить с помощью транспортного механизма, или если сообщение необходимо использовать для нескольких служб, которым требуются различные учетные данные.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-134">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         <span data-ttu-id="dd9ad-135">Дополнительные сведения см. в разделе [безопасность сообщений](message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-135">For more information, see [Message Security](message-security-in-wcf.md).</span></span>  
  
    3. `TransportWithMessageCredential`  
  
         <span data-ttu-id="dd9ad-136">В этом случае транспортный уровень используется для защиты передачи сообщений. При этом каждое сообщение включает расширенные учетные данные, необходимые другим службам.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-136">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="dd9ad-137">Этот способ сочетает повышение производительности механизма безопасности транспорта с наличием различных учетных данных механизма безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-137">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="dd9ad-138">Его можно использовать со следующими привязками: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding> и <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-138">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="dd9ad-139">Если принято решение использовать безопасность транспорта для протокола HTTP (т.е. протокол HTTPS), необходимо настроить узел с сертификатом SSL и включить SSL для порта.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-139">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> <span data-ttu-id="dd9ad-140">Дополнительные сведения см. в разделе [Безопасность транспорта HTTP](http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-140">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
4. <span data-ttu-id="dd9ad-141">Если используется привязка <xref:System.ServiceModel.WSHttpBinding> и при этом не требуется устанавливать безопасный сеанс, следует присвоить свойству <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> значение `false`.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-141">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="dd9ad-142">Безопасный сеанс создается, когда клиент и служба создают канал с использованием симметричного ключа (клиент и служба используют один и тот же ключ в течение всего диалога вплоть до его завершения).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-142">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="dd9ad-143">Задание типа учетных данных клиента</span><span class="sxs-lookup"><span data-stu-id="dd9ad-143">Setting the Client Credential Type</span></span>  

 <span data-ttu-id="dd9ad-144">Выберите необходимый тип учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-144">Select a client credential type as appropriate.</span></span> <span data-ttu-id="dd9ad-145">Дополнительные сведения см. [в разделе Выбор типа учетных данных](selecting-a-credential-type.md).</span><span class="sxs-lookup"><span data-stu-id="dd9ad-145">For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).</span></span> <span data-ttu-id="dd9ad-146">Доступны следующие типы учетных данных клиента:</span><span class="sxs-lookup"><span data-stu-id="dd9ad-146">The following client credential types are available:</span></span>  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 <span data-ttu-id="dd9ad-147">Тип учетных данных задается с учетом выбранного режима.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-147">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="dd9ad-148">Например, если выбрана привязка `wsHttpBinding` и задан режим Message, необходимо также присвоить атрибуту `clientCredentialType` элемента Message одно из следующих значений: `None`, `Windows`, `UserName`, `Certificate` или `IssuedToken`, как показано в следующем примере конфигурации.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-148">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="dd9ad-149">Или в коде:</span><span class="sxs-lookup"><span data-stu-id="dd9ad-149">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="dd9ad-150">Задание значений учетных данных службы</span><span class="sxs-lookup"><span data-stu-id="dd9ad-150">Setting Service Credential Values</span></span>  

 <span data-ttu-id="dd9ad-151">После выбора типа учетных данных необходимо задать фактические значения учетных данных, которые будут использоваться службой и клиентом.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-151">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="dd9ad-152">Задание учетных данных для службы осуществляется с помощью класса <xref:System.ServiceModel.Description.ServiceCredentials>. Свойство <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> класса <xref:System.ServiceModel.ServiceHostBase> возвращает эти учетные данные.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-152">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="dd9ad-153">Используемая привязка заключает в себе тип учетных данных службы, выбранный режим безопасности и тип учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-153">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="dd9ad-154">В следующем примере задается сертификат для учетных данных службы.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-154">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="dd9ad-155">Задание значений учетных данных клиента</span><span class="sxs-lookup"><span data-stu-id="dd9ad-155">Setting Client Credential Values</span></span>  

 <span data-ttu-id="dd9ad-156">Задание учетных данных для клиента осуществляется с помощью класса <xref:System.ServiceModel.Description.ClientCredentials>. Свойство <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> класса <xref:System.ServiceModel.ClientBase%601> возвращает эти учетные данные.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-156">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="dd9ad-157">В следующем примере задается сертификат для учетных данных клиента с использованием протокола TCP.</span><span class="sxs-lookup"><span data-stu-id="dd9ad-157">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dd9ad-158">См. также</span><span class="sxs-lookup"><span data-stu-id="dd9ad-158">See also</span></span>

- [<span data-ttu-id="dd9ad-159">Базовое программирование для WCF</span><span class="sxs-lookup"><span data-stu-id="dd9ad-159">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- [<span data-ttu-id="dd9ad-160">Типовые сценарии безопасности</span><span class="sxs-lookup"><span data-stu-id="dd9ad-160">Common Security Scenarios</span></span>](common-security-scenarios.md)
