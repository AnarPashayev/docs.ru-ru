---
title: Элемент <security> для <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 15740144b0aad7eb2798db4712e4769d08d893a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186866"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="fdcaf-102">\<Безопасность > элемент \<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="fdcaf-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="fdcaf-103">Определяет параметры безопасности [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="fdcaf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fdcaf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fdcaf-105">\<привязки ></span><span class="sxs-lookup"><span data-stu-id="fdcaf-105">\<bindings></span></span>  
<span data-ttu-id="fdcaf-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="fdcaf-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="fdcaf-107">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="fdcaf-107">\<binding></span></span>  
<span data-ttu-id="fdcaf-108">\<Безопасность ></span><span class="sxs-lookup"><span data-stu-id="fdcaf-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdcaf-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fdcaf-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdcaf-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fdcaf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fdcaf-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdcaf-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fdcaf-112">Attributes</span></span>  
  
|<span data-ttu-id="fdcaf-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fdcaf-113">Attribute</span></span>|<span data-ttu-id="fdcaf-114">Описание</span><span class="sxs-lookup"><span data-stu-id="fdcaf-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="fdcaf-115">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-115">Optional.</span></span> <span data-ttu-id="fdcaf-116">Задает тип применяемого механизма обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="fdcaf-117">Значение по умолчанию — `Message`.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-117">The default value is `Message`.</span></span> <span data-ttu-id="fdcaf-118">Это атрибут типа <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="fdcaf-119">Атрибут mode</span><span class="sxs-lookup"><span data-stu-id="fdcaf-119">mode Attribute</span></span>  
  
|<span data-ttu-id="fdcaf-120">Значение</span><span class="sxs-lookup"><span data-stu-id="fdcaf-120">Value</span></span>|<span data-ttu-id="fdcaf-121">Описание</span><span class="sxs-lookup"><span data-stu-id="fdcaf-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fdcaf-122">Нет</span><span class="sxs-lookup"><span data-stu-id="fdcaf-122">None</span></span>|<span data-ttu-id="fdcaf-123">Во время передачи сообщение SOAP не защищено.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="fdcaf-124">Сообщение</span><span class="sxs-lookup"><span data-stu-id="fdcaf-124">Message</span></span>|<span data-ttu-id="fdcaf-125">Целостность, конфиденциальность, проверка подлинности сервера и проверка подлинности клиента обеспечиваются с помощью средств безопасности сообщений SOAP.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="fdcaf-126">По умолчанию текст сообщений шифруется и подписывается.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="fdcaf-127">Служба должна быть настроена с использованием сертификата.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="fdcaf-128">Проверка подлинности клиента основана на маркере, выданного клиенту службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="fdcaf-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="fdcaf-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="fdcaf-130">Целостность, конфиденциальность и проверка подлинности сервера обеспечиваются с помощью HTTPS.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="fdcaf-131">Служба должна быть настроена с использованием сертификата.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="fdcaf-132">Проверка подлинности клиента выполняется с помощью средств безопасности сообщений SOAP и основана на маркере, выданном клиенту службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdcaf-133">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fdcaf-133">Child Elements</span></span>  
  
|<span data-ttu-id="fdcaf-134">Элемент</span><span class="sxs-lookup"><span data-stu-id="fdcaf-134">Element</span></span>|<span data-ttu-id="fdcaf-135">Описание</span><span class="sxs-lookup"><span data-stu-id="fdcaf-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdcaf-136">\<сообщение ></span><span class="sxs-lookup"><span data-stu-id="fdcaf-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="fdcaf-137">Определяет параметры безопасности уровня сообщений.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="fdcaf-138">Это элемент типа <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="fdcaf-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fdcaf-139">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fdcaf-139">Parent Elements</span></span>  
  
|<span data-ttu-id="fdcaf-140">Элемент</span><span class="sxs-lookup"><span data-stu-id="fdcaf-140">Element</span></span>|<span data-ttu-id="fdcaf-141">Описание</span><span class="sxs-lookup"><span data-stu-id="fdcaf-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdcaf-142">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="fdcaf-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="fdcaf-143">Определяет все возможности привязки [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fdcaf-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdcaf-144">См. также</span><span class="sxs-lookup"><span data-stu-id="fdcaf-144">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="fdcaf-145">Практическое руководство. Создание WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fdcaf-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="fdcaf-146">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="fdcaf-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fdcaf-147">Выбор типа учетных данных</span><span class="sxs-lookup"><span data-stu-id="fdcaf-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="fdcaf-148">Привязки</span><span class="sxs-lookup"><span data-stu-id="fdcaf-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="fdcaf-149">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="fdcaf-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fdcaf-150">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="fdcaf-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="fdcaf-151">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="fdcaf-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
