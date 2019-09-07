---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: b5ab3c3ad070499d686ea74b9fd459e89f380cfa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397967"
---
# <a name="issuedtoken"></a><span data-ttu-id="5bd5d-101">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="5bd5d-101">\<issuedToken></span></span>
<span data-ttu-id="5bd5d-102">Задает пользовательский маркер, используемый для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="5bd5d-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5bd5d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5bd5d-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5bd5d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5bd5d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> поведения**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5bd5d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5bd5d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5bd5d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="5bd5d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> поведения**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5bd5d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="5bd5d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5bd5d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="5bd5d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedToken >**</span><span class="sxs-lookup"><span data-stu-id="5bd5d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd5d-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5bd5d-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bd5d-111">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5bd5d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5bd5d-112">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bd5d-113">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5bd5d-113">Attributes</span></span>  
  
|<span data-ttu-id="5bd5d-114">Атрибут</span><span class="sxs-lookup"><span data-stu-id="5bd5d-114">Attribute</span></span>|<span data-ttu-id="5bd5d-115">Описание</span><span class="sxs-lookup"><span data-stu-id="5bd5d-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="5bd5d-116">Дополнительный логический атрибут, указывающий, выполняется ли кэширование маркеров.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="5bd5d-117">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="5bd5d-118">Дополнительный строковый атрибут, указывающий, какие случайные значения (показатели энтропии) используются для операций «рукопожатия».</span><span class="sxs-lookup"><span data-stu-id="5bd5d-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="5bd5d-119">Допустимы следующие значения: `ClientEntropy`, `ServerEntropy` и `CombinedEntropy`. Значение по умолчанию - `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="5bd5d-120">Это атрибут типа <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="5bd5d-121">Дополнительный целочисленный атрибут, задающий время в процентах от срока действия (предоставляемого издателем маркера), которое может пройти до обновления маркера.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="5bd5d-122">Диапазон значений: 0–100.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-122">Values are from 0 to 100.</span></span> <span data-ttu-id="5bd5d-123">Значение по умолчанию, равное 60, указывает, что попытка возобновления предпринимается по истечении 60% времени.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="5bd5d-124">Дополнительный атрибут, определяющий поведения канала во время связи с издателем.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="5bd5d-125">Дополнительный атрибут, определяющий поведения канала во время связи с локальным издателем.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="5bd5d-126">Дополнительный атрибут Timespan, задающий промежуток времени, в течение которого выданные маркеры сохраняются в кэше, если время не указывается издателем маркера (службой маркеров безопасности).</span><span class="sxs-lookup"><span data-stu-id="5bd5d-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="5bd5d-127">Значение по умолчанию — "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="5bd5d-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bd5d-128">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5bd5d-128">Child Elements</span></span>  
  
|<span data-ttu-id="5bd5d-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="5bd5d-129">Element</span></span>|<span data-ttu-id="5bd5d-130">Описание</span><span class="sxs-lookup"><span data-stu-id="5bd5d-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bd5d-131">\<Локалиссуер ></span><span class="sxs-lookup"><span data-stu-id="5bd5d-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="5bd5d-132">Определяет адрес локального издателя маркера и привязку, используемую для взаимодействия с конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="5bd5d-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5bd5d-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="5bd5d-134">Задает поведения конечной точки, используемое при связи с локальным издателем.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5bd5d-135">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5bd5d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5bd5d-136">Элемент</span><span class="sxs-lookup"><span data-stu-id="5bd5d-136">Element</span></span>|<span data-ttu-id="5bd5d-137">Описание</span><span class="sxs-lookup"><span data-stu-id="5bd5d-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bd5d-138">\<> clientCredentials</span><span class="sxs-lookup"><span data-stu-id="5bd5d-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="5bd5d-139">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bd5d-140">Примечания</span><span class="sxs-lookup"><span data-stu-id="5bd5d-140">Remarks</span></span>  
 <span data-ttu-id="5bd5d-141">Выданный маркер представляет собой пользовательские учетные данные, используемые, например, при проверке подлинности с помощью службы маркеров безопасности при федеративном доступе.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="5bd5d-142">По умолчанию используется маркер SAML.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="5bd5d-143">Дополнительные сведения см. в разделе [Федерация и выданные токены](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="5bd5d-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="5bd5d-144">и [Федерации и выданных токенов](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="5bd5d-144">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="5bd5d-145">Этот раздел содержит элементы, используемые для настройки локального издателя маркеров, или поведения, используемые при работе со службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="5bd5d-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="5bd5d-146">Инструкции по настройке клиента для использования локального издателя см. в разделе [как Настройка локального издателя](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="5bd5d-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd5d-147">См. также</span><span class="sxs-lookup"><span data-stu-id="5bd5d-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="5bd5d-148">Поведения безопасности</span><span class="sxs-lookup"><span data-stu-id="5bd5d-148">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5bd5d-149">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="5bd5d-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5bd5d-150">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="5bd5d-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5bd5d-151">Защита клиентов</span><span class="sxs-lookup"><span data-stu-id="5bd5d-151">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="5bd5d-152">Практическое руководство. Создание федеративного клиента</span><span class="sxs-lookup"><span data-stu-id="5bd5d-152">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="5bd5d-153">Практическое руководство. Настройка локального издателя</span><span class="sxs-lookup"><span data-stu-id="5bd5d-153">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="5bd5d-154">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="5bd5d-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
