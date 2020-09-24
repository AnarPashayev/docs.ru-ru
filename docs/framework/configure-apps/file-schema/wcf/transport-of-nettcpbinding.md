---
title: <transport> из <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 8f752373c51992c51b747f5f4dc4a63910a387c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162196"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="1e986-102">\<transport> из \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="1e986-102">\<transport> of \<netTcpBinding></span></span>

<span data-ttu-id="1e986-103">Определяет тип требований безопасности на уровне сообщений для конечной точки, настроенной с помощью [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1e986-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="1e986-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1e986-104">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e986-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1e986-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1e986-106">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1e986-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e986-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1e986-107">Attributes</span></span>  
  
|<span data-ttu-id="1e986-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1e986-108">Attribute</span></span>|<span data-ttu-id="1e986-109">Описание</span><span class="sxs-lookup"><span data-stu-id="1e986-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e986-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="1e986-110">clientCredentialType</span></span>|<span data-ttu-id="1e986-111">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1e986-111">Optional.</span></span> <span data-ttu-id="1e986-112">Задает тип учетных данных, используемых при проверке подлинности клиента с помощью безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="1e986-112">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="1e986-113">— Значение по умолчанию — `Windows` .</span><span class="sxs-lookup"><span data-stu-id="1e986-113">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="1e986-114">— Этот атрибут имеет тип <xref:System.ServiceModel.TcpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="1e986-114">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="1e986-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="1e986-115">protectionLevel</span></span>|<span data-ttu-id="1e986-116">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1e986-116">Optional.</span></span> <span data-ttu-id="1e986-117">Определяет безопасность на уровне транспорта TCP.</span><span class="sxs-lookup"><span data-stu-id="1e986-117">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="1e986-118">Подпись сообщений уменьшает риск подделки сообщения сторонними лицами при его передаче.</span><span class="sxs-lookup"><span data-stu-id="1e986-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="1e986-119">Шифрование обеспечивает конфиденциальность на уровне данных во время транспортировки.</span><span class="sxs-lookup"><span data-stu-id="1e986-119">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="1e986-120">Значение по умолчанию — `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="1e986-120">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="1e986-121">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="1e986-121">sslProtocols</span></span>|<span data-ttu-id="1e986-122">Значение флага перечисления SslProtocols, указывающее, какие протоколы SslProtocols поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="1e986-122">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="1e986-123">Значение по умолчанию — TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="1e986-123">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="1e986-124">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="1e986-124">policyEnforcement</span></span>|<span data-ttu-id="1e986-125">Это перечисление указывает, когда следует применять <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.</span><span class="sxs-lookup"><span data-stu-id="1e986-125">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="1e986-126">1. Never — политика никогда не применяется (Расширенная защита отключена).</span><span class="sxs-lookup"><span data-stu-id="1e986-126">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="1e986-127">2. WhenSupported — политика применяется, только если клиент поддерживает расширенную защиту.</span><span class="sxs-lookup"><span data-stu-id="1e986-127">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="1e986-128">3. всегда — политика всегда применяется принудительно.</span><span class="sxs-lookup"><span data-stu-id="1e986-128">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="1e986-129">Клиенты, которые не поддерживают расширенную защиту, не смогут пройти проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="1e986-129">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="1e986-130">Атрибут clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="1e986-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="1e986-131">Значение</span><span class="sxs-lookup"><span data-stu-id="1e986-131">Value</span></span>|<span data-ttu-id="1e986-132">Описание</span><span class="sxs-lookup"><span data-stu-id="1e986-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e986-133">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="1e986-133">None</span></span>|<span data-ttu-id="1e986-134">Анонимный клиент.</span><span class="sxs-lookup"><span data-stu-id="1e986-134">The client is anonymous.</span></span> <span data-ttu-id="1e986-135">Это требует сертификата для службы.</span><span class="sxs-lookup"><span data-stu-id="1e986-135">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="1e986-136">Windows</span><span class="sxs-lookup"><span data-stu-id="1e986-136">Windows</span></span>|<span data-ttu-id="1e986-137">Задает проверку подлинности Windows для клиента с использованием согласования SP (согласование Kerberos).</span><span class="sxs-lookup"><span data-stu-id="1e986-137">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="1e986-138">Сертификат</span><span class="sxs-lookup"><span data-stu-id="1e986-138">Certificate</span></span>|<span data-ttu-id="1e986-139">Проверка подлинности клиента выполняется с использованием сертификата.</span><span class="sxs-lookup"><span data-stu-id="1e986-139">The client is authenticated using a certificate.</span></span> <span data-ttu-id="1e986-140">Это требует согласования SSL и сертификата для службы.</span><span class="sxs-lookup"><span data-stu-id="1e986-140">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="1e986-141">Атрибут protectionLevel</span><span class="sxs-lookup"><span data-stu-id="1e986-141">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="1e986-142">Значение</span><span class="sxs-lookup"><span data-stu-id="1e986-142">Value</span></span>|<span data-ttu-id="1e986-143">Описание</span><span class="sxs-lookup"><span data-stu-id="1e986-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e986-144">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="1e986-144">None</span></span>|<span data-ttu-id="1e986-145">Нет защиты.</span><span class="sxs-lookup"><span data-stu-id="1e986-145">No protection.</span></span>|  
|<span data-ttu-id="1e986-146">вход;</span><span class="sxs-lookup"><span data-stu-id="1e986-146">Sign</span></span>|<span data-ttu-id="1e986-147">Сообщения подписываются.</span><span class="sxs-lookup"><span data-stu-id="1e986-147">Messages are signed.</span></span>|  
|<span data-ttu-id="1e986-148">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="1e986-148">EncryptAndSign</span></span>|<span data-ttu-id="1e986-149">— Сообщения шифруются и подписываются.</span><span class="sxs-lookup"><span data-stu-id="1e986-149">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e986-150">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1e986-150">Child Elements</span></span>  

 <span data-ttu-id="1e986-151">Нет</span><span class="sxs-lookup"><span data-stu-id="1e986-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e986-152">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1e986-152">Parent Elements</span></span>  
  
|<span data-ttu-id="1e986-153">Элемент</span><span class="sxs-lookup"><span data-stu-id="1e986-153">Element</span></span>|<span data-ttu-id="1e986-154">Описание</span><span class="sxs-lookup"><span data-stu-id="1e986-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="1e986-155">Указывает возможности безопасности для [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="1e986-155">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e986-156">Remarks</span><span class="sxs-lookup"><span data-stu-id="1e986-156">Remarks</span></span>  

 <span data-ttu-id="1e986-157">Безопасность транспорта используется для обеспечения целостности и конфиденциальности сообщений SOAP и для взаимной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="1e986-157">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="1e986-158">Если этот режим безопасности выбран для какой-либо привязки, стек каналов настраивается с использованием безопасного транспорта, а сообщения SOAP защищаются с использованием безопасности транспорта, например Windows (Negotiate) или SSL по TCP.</span><span class="sxs-lookup"><span data-stu-id="1e986-158">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e986-159">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1e986-159">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="1e986-160">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="1e986-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1e986-161">Привязки</span><span class="sxs-lookup"><span data-stu-id="1e986-161">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1e986-162">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="1e986-162">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1e986-163">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="1e986-163">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
