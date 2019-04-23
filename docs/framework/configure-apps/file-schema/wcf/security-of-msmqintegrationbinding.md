---
title: <security> из <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 8d79523db2a1567283b934abbd3de1adbbe6b0b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125792"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="bbffd-102">\<Безопасность > из \<msmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="bbffd-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="bbffd-103">Определяет параметры безопасности транспорта для канала интеграции очереди сообщений (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="bbffd-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="bbffd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bbffd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bbffd-105">\<привязки ></span><span class="sxs-lookup"><span data-stu-id="bbffd-105">\<bindings></span></span>  
<span data-ttu-id="bbffd-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="bbffd-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="bbffd-107">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="bbffd-107">\<binding></span></span>  
<span data-ttu-id="bbffd-108">\<Безопасность ></span><span class="sxs-lookup"><span data-stu-id="bbffd-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbffd-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bbffd-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbffd-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="bbffd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bbffd-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="bbffd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbffd-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="bbffd-112">Attributes</span></span>  
  
|<span data-ttu-id="bbffd-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="bbffd-113">Attribute</span></span>|<span data-ttu-id="bbffd-114">Описание</span><span class="sxs-lookup"><span data-stu-id="bbffd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bbffd-115">режим</span><span class="sxs-lookup"><span data-stu-id="bbffd-115">mode</span></span>|<span data-ttu-id="bbffd-116">Задает тип системы безопасности, отвечающей за целостность, конфиденциальность и проверку подлинности при использовании канала интеграции очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="bbffd-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="bbffd-117">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="bbffd-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bbffd-118">-None: Режим безопасности отключен.</span><span class="sxs-lookup"><span data-stu-id="bbffd-118">-   None: This disables security.</span></span><br /><span data-ttu-id="bbffd-119">-Транспорта: Защита и проверка подлинности предоставляются транспортом.</span><span class="sxs-lookup"><span data-stu-id="bbffd-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="bbffd-120">Это значение связано с безопасностью сообщений между двумя диспетчерами очереди.</span><span class="sxs-lookup"><span data-stu-id="bbffd-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="bbffd-121">Между приложением и диспетчером очереди безопасность сообщений не обеспечивается.</span><span class="sxs-lookup"><span data-stu-id="bbffd-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="bbffd-122">Существующие Msmq-приложения функционально равноценны такому режиму безопасности.</span><span class="sxs-lookup"><span data-stu-id="bbffd-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="bbffd-123">Значение по умолчанию — `Transport`.</span><span class="sxs-lookup"><span data-stu-id="bbffd-123">The default value is `Transport`.</span></span> <span data-ttu-id="bbffd-124">Это атрибут типа <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="bbffd-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbffd-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="bbffd-125">Child Elements</span></span>  
  
|<span data-ttu-id="bbffd-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="bbffd-126">Element</span></span>|<span data-ttu-id="bbffd-127">Описание</span><span class="sxs-lookup"><span data-stu-id="bbffd-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbffd-128">\<Транспорт ></span><span class="sxs-lookup"><span data-stu-id="bbffd-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="bbffd-129">Определяет параметры безопасности для транспорта интеграции очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="bbffd-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="bbffd-130">Это элемент типа <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="bbffd-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbffd-131">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="bbffd-131">Parent Elements</span></span>  
  
|<span data-ttu-id="bbffd-132">Элемент</span><span class="sxs-lookup"><span data-stu-id="bbffd-132">Element</span></span>|<span data-ttu-id="bbffd-133">Описание</span><span class="sxs-lookup"><span data-stu-id="bbffd-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbffd-134">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="bbffd-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bbffd-135">Элемент привязки [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bbffd-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbffd-136">См. также</span><span class="sxs-lookup"><span data-stu-id="bbffd-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="bbffd-137">Очереди в WCF</span><span class="sxs-lookup"><span data-stu-id="bbffd-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="bbffd-138">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="bbffd-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="bbffd-139">Привязки</span><span class="sxs-lookup"><span data-stu-id="bbffd-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="bbffd-140">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="bbffd-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bbffd-141">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="bbffd-141">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bbffd-142">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="bbffd-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="bbffd-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="bbffd-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
