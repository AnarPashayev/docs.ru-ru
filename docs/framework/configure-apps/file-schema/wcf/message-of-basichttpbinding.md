---
title: <message> из <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 746acd91074863029211a1ca2584743c464c9ce1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083300"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="ccb0d-102">\<сообщение > из \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ccb0d-102">\<message> of \<basicHttpBinding></span></span>
<span data-ttu-id="ccb0d-103">Определяет параметры безопасности уровня сообщений для [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ccb0d-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="ccb0d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ccb0d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ccb0d-105">\<привязки ></span><span class="sxs-lookup"><span data-stu-id="ccb0d-105">\<bindings></span></span>  
<span data-ttu-id="ccb0d-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ccb0d-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="ccb0d-107">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="ccb0d-107">\<binding></span></span>  
<span data-ttu-id="ccb0d-108">\<Безопасность ></span><span class="sxs-lookup"><span data-stu-id="ccb0d-108">\<security></span></span>  
<span data-ttu-id="ccb0d-109">\<сообщение ></span><span class="sxs-lookup"><span data-stu-id="ccb0d-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccb0d-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ccb0d-110">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccb0d-111">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ccb0d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ccb0d-112">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccb0d-113">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ccb0d-113">Attributes</span></span>  
  
|<span data-ttu-id="ccb0d-114">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ccb0d-114">Attribute</span></span>|<span data-ttu-id="ccb0d-115">Описание</span><span class="sxs-lookup"><span data-stu-id="ccb0d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ccb0d-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ccb0d-116">algorithmSuite</span></span>|<span data-ttu-id="ccb0d-117">Задает алгоритмы шифрования сообщений и ключей.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="ccb0d-118">Этот атрибут имеет тип <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, который задает алгоритмы и размеры ключей.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="ccb0d-119">Эти алгоритмы соответствуют алгоритмам, заданным в спецификации языка политики безопасности (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="ccb0d-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="ccb0d-120">Значение по умолчанию — `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="ccb0d-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="ccb0d-121">clientCredentialType</span></span>|<span data-ttu-id="ccb0d-122">Задает тип учетных данных, используемых при проверке подлинности клиента с помощью безопасности на уровне сообщений.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="ccb0d-123">Значение по умолчанию — `UserName`.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="ccb0d-124">Атрибут clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="ccb0d-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ccb0d-125">Значение</span><span class="sxs-lookup"><span data-stu-id="ccb0d-125">Value</span></span>|<span data-ttu-id="ccb0d-126">Описание</span><span class="sxs-lookup"><span data-stu-id="ccb0d-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ccb0d-127">UserName</span><span class="sxs-lookup"><span data-stu-id="ccb0d-127">UserName</span></span>|<span data-ttu-id="ccb0d-128">— Требует проверки подлинности клиента на сервер с помощью имени пользователя.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="ccb0d-129">Эти учетные данные должны быть определены с помощью [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="ccb0d-129">This credential needs to be specified using the [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span></span><br /><span data-ttu-id="ccb0d-130">-WCF не поддерживает передачу хэш-кода пароля или получение ключей с помощью паролей и использование таких ключей для обеспечения безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-130">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="ccb0d-131">Таким образом WCF обеспечивает, что безопасность транспорта при использовании учетных данных UserName.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-131">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="ccb0d-132">Для `basicHttpBinding` это требует настройки канала SSL.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="ccb0d-133">Сертификат</span><span class="sxs-lookup"><span data-stu-id="ccb0d-133">Certificate</span></span>|<span data-ttu-id="ccb0d-134">Требует, чтобы при подключении к серверу проверка подлинности клиента проводилась с помощью сертификата.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="ccb0d-135">Учетные данные клиента в этом случае должны быть определены с помощью [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) и [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="ccb0d-135">The client credential in this case needs to be specified using [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) and the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="ccb0d-136">Кроме того, при использовании режима безопасности сообщений клиенту должен быть предоставлен сертификат службы.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="ccb0d-137">Учетные данные службы в этом случае должны быть определены с помощью <xref:System.ServiceModel.Description.ClientCredentials> класса или `ClientCredentials` элемент поведения и указав службы сертификат, с помощью [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="ccb0d-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccb0d-138">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ccb0d-138">Child Elements</span></span>  
 <span data-ttu-id="ccb0d-139">Нет</span><span class="sxs-lookup"><span data-stu-id="ccb0d-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccb0d-140">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ccb0d-140">Parent Elements</span></span>  
  
|<span data-ttu-id="ccb0d-141">Элемент</span><span class="sxs-lookup"><span data-stu-id="ccb0d-141">Element</span></span>|<span data-ttu-id="ccb0d-142">Описание</span><span class="sxs-lookup"><span data-stu-id="ccb0d-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccb0d-143">\<Безопасность ></span><span class="sxs-lookup"><span data-stu-id="ccb0d-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="ccb0d-144">Определяет возможности безопасности для [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ccb0d-144">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ccb0d-145">Пример</span><span class="sxs-lookup"><span data-stu-id="ccb0d-145">Example</span></span>  
 <span data-ttu-id="ccb0d-146">В образце демонстрируется реализация приложения, которое использует basicHttpBinding и безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="ccb0d-147">В следующем примере конфигурации для службы в определении конечной точки задаются привязка basicHttpBinding и ссылки на конфигурацию привязки с именем `Binding1`.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="ccb0d-148">Сертификат, используемый службой для своей проверки подлинности при подключении к клиенту, установлен в разделе `behaviors` файла конфигурации в элементе `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="ccb0d-149">Режим проверки, применяемый к сертификату, который клиент использует для своей проверки подлинности при подключении к службе, также установлен в разделе `behaviors` в элементе `clientCertificate`.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="ccb0d-150">Та же привязка и данные безопасности задаются в файле конфигурации клиента.</span><span class="sxs-lookup"><span data-stu-id="ccb0d-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
    <!-- This configuration defines the SecurityMode as Message and
         the clientCredentialType as Certificate. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
               is in the user's Trusted People store, then it will be trusted without performing a
               validation of the certificate's issuer chain. This setting is used here for convenience so that the
               sample can be run without having to have certificates issued by a certification authority (CA).
               This setting is less secure than the default, ChainTrust. The security implications of this
               setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="ccb0d-151">См. также</span><span class="sxs-lookup"><span data-stu-id="ccb0d-151">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="ccb0d-152">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="ccb0d-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ccb0d-153">Привязки</span><span class="sxs-lookup"><span data-stu-id="ccb0d-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ccb0d-154">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="ccb0d-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ccb0d-155">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="ccb0d-155">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ccb0d-156">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="ccb0d-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
