---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 83061b283c9430af7bcda9cbc832811fa805ed4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104953"
---
# <a name="issuedtoken"></a><span data-ttu-id="08775-101">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="08775-101">\<issuedToken></span></span>
<span data-ttu-id="08775-102">Задает пользовательский маркер, используемый для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="08775-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="08775-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="08775-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="08775-104">\<варианты поведения ></span><span class="sxs-lookup"><span data-stu-id="08775-104">\<behaviors></span></span>  
<span data-ttu-id="08775-105">раздел endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="08775-105">endpointBehaviors section</span></span>  
<span data-ttu-id="08775-106">\<поведение ></span><span class="sxs-lookup"><span data-stu-id="08775-106">\<behavior></span></span>  
<span data-ttu-id="08775-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="08775-107">\<clientCredentials></span></span>  
<span data-ttu-id="08775-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="08775-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08775-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="08775-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08775-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="08775-110">Attributes and Elements</span></span>  
 <span data-ttu-id="08775-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="08775-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08775-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="08775-112">Attributes</span></span>  
  
|<span data-ttu-id="08775-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="08775-113">Attribute</span></span>|<span data-ttu-id="08775-114">Описание</span><span class="sxs-lookup"><span data-stu-id="08775-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="08775-115">Дополнительный логический атрибут, указывающий, выполняется ли кэширование маркеров.</span><span class="sxs-lookup"><span data-stu-id="08775-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="08775-116">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="08775-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="08775-117">Дополнительный строковый атрибут, указывающий, какие случайные значения (показатели энтропии) используются для операций «рукопожатия».</span><span class="sxs-lookup"><span data-stu-id="08775-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="08775-118">Допустимы следующие значения: `ClientEntropy`, `ServerEntropy` и `CombinedEntropy`. Значение по умолчанию - `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="08775-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="08775-119">Это атрибут типа <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="08775-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="08775-120">Дополнительный целочисленный атрибут, задающий время в процентах от срока действия (предоставляемого издателем маркера), которое может пройти до обновления маркера.</span><span class="sxs-lookup"><span data-stu-id="08775-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="08775-121">Диапазон значений: 0–100.</span><span class="sxs-lookup"><span data-stu-id="08775-121">Values are from 0 to 100.</span></span> <span data-ttu-id="08775-122">Значение по умолчанию, равное 60, указывает, что попытка возобновления предпринимается по истечении 60% времени.</span><span class="sxs-lookup"><span data-stu-id="08775-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="08775-123">Дополнительный атрибут, определяющий поведения канала во время связи с издателем.</span><span class="sxs-lookup"><span data-stu-id="08775-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="08775-124">Дополнительный атрибут, определяющий поведения канала во время связи с локальным издателем.</span><span class="sxs-lookup"><span data-stu-id="08775-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="08775-125">Дополнительный атрибут Timespan, задающий промежуток времени, в течение которого выданные маркеры сохраняются в кэше, если время не указывается издателем маркера (службой маркеров безопасности).</span><span class="sxs-lookup"><span data-stu-id="08775-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="08775-126">Значение по умолчанию — «10675199.02:48:05.4775807.»</span><span class="sxs-lookup"><span data-stu-id="08775-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08775-127">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="08775-127">Child Elements</span></span>  
  
|<span data-ttu-id="08775-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="08775-128">Element</span></span>|<span data-ttu-id="08775-129">Описание</span><span class="sxs-lookup"><span data-stu-id="08775-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08775-130">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="08775-130">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="08775-131">Определяет адрес локального издателя маркера и привязку, используемую для взаимодействия с конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="08775-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="08775-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="08775-132">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="08775-133">Задает поведения конечной точки, используемое при связи с локальным издателем.</span><span class="sxs-lookup"><span data-stu-id="08775-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08775-134">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="08775-134">Parent Elements</span></span>  
  
|<span data-ttu-id="08775-135">Элемент</span><span class="sxs-lookup"><span data-stu-id="08775-135">Element</span></span>|<span data-ttu-id="08775-136">Описание</span><span class="sxs-lookup"><span data-stu-id="08775-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08775-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="08775-137">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="08775-138">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="08775-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08775-139">Примечания</span><span class="sxs-lookup"><span data-stu-id="08775-139">Remarks</span></span>  
 <span data-ttu-id="08775-140">Выданный маркер представляет собой пользовательские учетные данные, используемые, например, при проверке подлинности с помощью службы маркеров безопасности при федеративном доступе.</span><span class="sxs-lookup"><span data-stu-id="08775-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="08775-141">По умолчанию используется маркер SAML.</span><span class="sxs-lookup"><span data-stu-id="08775-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="08775-142">Дополнительные сведения см. в разделе [Федерация и выданные маркеры](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="08775-142">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="08775-143">и [Федерация и выданные маркеры](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="08775-143">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="08775-144">Этот раздел содержит элементы, используемые для настройки локального издателя маркеров, или поведения, используемые при работе со службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="08775-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="08775-145">Инструкции по настройке клиента для использования локального издателя, см. в разделе [как: Настройка локального издателя](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="08775-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08775-146">См. также</span><span class="sxs-lookup"><span data-stu-id="08775-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="08775-147">Поведения безопасности</span><span class="sxs-lookup"><span data-stu-id="08775-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="08775-148">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="08775-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="08775-149">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="08775-149">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="08775-150">Защита клиентов</span><span class="sxs-lookup"><span data-stu-id="08775-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="08775-151">Практическое руководство. Создание федеративного клиента</span><span class="sxs-lookup"><span data-stu-id="08775-151">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="08775-152">Практическое руководство. Настройка локального издателя</span><span class="sxs-lookup"><span data-stu-id="08775-152">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="08775-153">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="08775-153">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
