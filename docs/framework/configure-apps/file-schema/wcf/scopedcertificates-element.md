---
title: Элемент <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 73e78a6ca27ed45e1eadc7121987b75f79bc6aa5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670642"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="212df-102">\<scopedCertificates > элемент</span><span class="sxs-lookup"><span data-stu-id="212df-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="212df-103">Представляет коллекцию сертификатов X.509, предоставленную конкретными службами (в области действия) для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="212df-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="212df-104">Эта коллекция обычно используется, чтобы задать сертификаты служб для служб маркеров безопасности в федеративной инфраструктуре.</span><span class="sxs-lookup"><span data-stu-id="212df-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="212df-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="212df-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="212df-106">\<варианты поведения ></span><span class="sxs-lookup"><span data-stu-id="212df-106">\<behaviors></span></span>  
<span data-ttu-id="212df-107">раздел endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="212df-107">endpointBehaviors section</span></span>  
<span data-ttu-id="212df-108">\<поведение ></span><span class="sxs-lookup"><span data-stu-id="212df-108">\<behavior></span></span>  
<span data-ttu-id="212df-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="212df-109">\<clientCredentials></span></span>  
<span data-ttu-id="212df-110">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="212df-110">\<serviceCertificate></span></span>  
<span data-ttu-id="212df-111">\<scopedCertificates > элемент</span><span class="sxs-lookup"><span data-stu-id="212df-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="212df-112">\<Добавить > элемент для \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="212df-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="212df-113">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="212df-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="212df-114">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="212df-114">Attributes and Elements</span></span>  
 <span data-ttu-id="212df-115">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="212df-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="212df-116">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="212df-116">Attributes</span></span>  
 <span data-ttu-id="212df-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="212df-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="212df-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="212df-118">Child Elements</span></span>  
  
|<span data-ttu-id="212df-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="212df-119">Element</span></span>|<span data-ttu-id="212df-120">Описание</span><span class="sxs-lookup"><span data-stu-id="212df-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="212df-121">\<add></span><span class="sxs-lookup"><span data-stu-id="212df-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|<span data-ttu-id="212df-122">Добавляет сертификат X.509 в коллекцию сертификатов в области действия.</span><span class="sxs-lookup"><span data-stu-id="212df-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="212df-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="212df-123">Parent Elements</span></span>  
  
|<span data-ttu-id="212df-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="212df-124">Element</span></span>|<span data-ttu-id="212df-125">Описание</span><span class="sxs-lookup"><span data-stu-id="212df-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="212df-126">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="212df-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="212df-127">Задает сертификат для использования при проверке подлинности службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="212df-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="212df-128">Примечания</span><span class="sxs-lookup"><span data-stu-id="212df-128">Remarks</span></span>  
 <span data-ttu-id="212df-129">Эта коллекция позволяет клиенту настроить сертификаты служб для использования на основе URL-адреса службы, с которой он связывается.</span><span class="sxs-lookup"><span data-stu-id="212df-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="212df-130">Это особенно полезно в сценариях с выданным маркером, в которых клиент может связываться с несколькими службами (с конечной службой, а также с промежуточными службами маркеров безопасности).</span><span class="sxs-lookup"><span data-stu-id="212df-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="212df-131">Для привязок, в которых используется безопасность сообщений на основе сертификатов, этот сертификат используется для шифрования сообщений службе; предполагается также, что он будет использоваться службой для подписи ответов клиенту.</span><span class="sxs-lookup"><span data-stu-id="212df-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="212df-132">Если для привязки необходим сертификат для службы, а конкретный сертификат для URL-адреса службы в элементе ScopedCertificates отсутствует, то используется сертификат по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="212df-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="212df-133">Дополнительные сведения см. в разделе «Сертификаты в области действия» [как: Создание федеративного клиента](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="212df-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="212df-134">Пример</span><span class="sxs-lookup"><span data-stu-id="212df-134">Example</span></span>  
 <span data-ttu-id="212df-135">В следующем примере задается сертификат службы для клиента для использования при взаимодействии с конечными точками, именем домена которых является `http://www.contoso.com` по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="212df-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="212df-136">См. также</span><span class="sxs-lookup"><span data-stu-id="212df-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="212df-137">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="212df-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="212df-138">Практическое руководство. Создание федеративного клиента</span><span class="sxs-lookup"><span data-stu-id="212df-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="212df-139">\<add></span><span class="sxs-lookup"><span data-stu-id="212df-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)
- [<span data-ttu-id="212df-140">Защита клиентов</span><span class="sxs-lookup"><span data-stu-id="212df-140">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="212df-141">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="212df-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
