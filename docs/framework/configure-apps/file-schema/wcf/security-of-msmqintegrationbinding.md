---
title: <security> из <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 8d79523db2a1567283b934abbd3de1adbbe6b0b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670538"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="7bc65-102">\<Безопасность > из \<msmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="7bc65-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="7bc65-103">Определяет параметры безопасности транспорта для канала интеграции очереди сообщений (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="7bc65-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="7bc65-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7bc65-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7bc65-105">\<привязки ></span><span class="sxs-lookup"><span data-stu-id="7bc65-105">\<bindings></span></span>  
<span data-ttu-id="7bc65-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="7bc65-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="7bc65-107">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="7bc65-107">\<binding></span></span>  
<span data-ttu-id="7bc65-108">\<Безопасность ></span><span class="sxs-lookup"><span data-stu-id="7bc65-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bc65-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7bc65-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bc65-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7bc65-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7bc65-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7bc65-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bc65-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7bc65-112">Attributes</span></span>  
  
|<span data-ttu-id="7bc65-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="7bc65-113">Attribute</span></span>|<span data-ttu-id="7bc65-114">Описание</span><span class="sxs-lookup"><span data-stu-id="7bc65-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bc65-115">режим</span><span class="sxs-lookup"><span data-stu-id="7bc65-115">mode</span></span>|<span data-ttu-id="7bc65-116">Задает тип системы безопасности, отвечающей за целостность, конфиденциальность и проверку подлинности при использовании канала интеграции очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="7bc65-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="7bc65-117">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="7bc65-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7bc65-118">-None: Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="7bc65-118">-   None: This disables security.</span></span><br /><span data-ttu-id="7bc65-119">-Транспорта: Защита и проверка подлинности предоставляются транспортом.</span><span class="sxs-lookup"><span data-stu-id="7bc65-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="7bc65-120">Это значение связано с безопасностью сообщений между двумя диспетчерами очереди.</span><span class="sxs-lookup"><span data-stu-id="7bc65-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="7bc65-121">Между приложением и диспетчером очереди безопасность сообщений не обеспечивается.</span><span class="sxs-lookup"><span data-stu-id="7bc65-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="7bc65-122">Существующие Msmq-приложения функционально равноценны такому режиму безопасности.</span><span class="sxs-lookup"><span data-stu-id="7bc65-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="7bc65-123">Значение по умолчанию — `Transport`.</span><span class="sxs-lookup"><span data-stu-id="7bc65-123">The default value is `Transport`.</span></span> <span data-ttu-id="7bc65-124">Это атрибут типа <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="7bc65-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bc65-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7bc65-125">Child Elements</span></span>  
  
|<span data-ttu-id="7bc65-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="7bc65-126">Element</span></span>|<span data-ttu-id="7bc65-127">Описание</span><span class="sxs-lookup"><span data-stu-id="7bc65-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bc65-128">\<Транспорт ></span><span class="sxs-lookup"><span data-stu-id="7bc65-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="7bc65-129">Определяет параметры безопасности для транспорта интеграции очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="7bc65-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="7bc65-130">Это элемент типа <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7bc65-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7bc65-131">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7bc65-131">Parent Elements</span></span>  
  
|<span data-ttu-id="7bc65-132">Элемент</span><span class="sxs-lookup"><span data-stu-id="7bc65-132">Element</span></span>|<span data-ttu-id="7bc65-133">Описание</span><span class="sxs-lookup"><span data-stu-id="7bc65-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bc65-134">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="7bc65-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="7bc65-135">Элемент привязки [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7bc65-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bc65-136">См. также</span><span class="sxs-lookup"><span data-stu-id="7bc65-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="7bc65-137">Очереди в WCF</span><span class="sxs-lookup"><span data-stu-id="7bc65-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="7bc65-138">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="7bc65-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7bc65-139">Привязки</span><span class="sxs-lookup"><span data-stu-id="7bc65-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7bc65-140">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="7bc65-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7bc65-141">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="7bc65-141">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7bc65-142">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="7bc65-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="7bc65-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="7bc65-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
