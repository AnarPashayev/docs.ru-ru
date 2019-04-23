---
title: Безопасность сообщений с использованием взаимных сертификатов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: 8fc8d6d4a63b7a752fb8c26991d904761fdcebdd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076026"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="fd0e3-102">Безопасность сообщений с использованием взаимных сертификатов</span><span class="sxs-lookup"><span data-stu-id="fd0e3-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="fd0e3-103">В следующем сценарии показаны службы Windows Communication Foundation (WCF) и клиента, защищенный с помощью режима безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="fd0e3-104">Проверка подлинности клиента и службы выполняется с помощью сертификатов.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="fd0e3-105">Данный сценарий поддерживает возможность взаимодействия, поскольку в нем используется WS-Security с профилем маркера сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd0e3-106">Данный сценарий не выполняет согласование сертификата службы.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="fd0e3-107">Сертификат службы должен быть предоставлен клиенту перед началом любой связи.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="fd0e3-108">Сертификат сервера может быть распределен приложением или предоставлен во внеполосной связи.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="fd0e3-109">![Безопасность с использованием взаимных сертификатов сообщений](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="fd0e3-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="fd0e3-110">Характеристика</span><span class="sxs-lookup"><span data-stu-id="fd0e3-110">Characteristic</span></span>|<span data-ttu-id="fd0e3-111">Описание</span><span class="sxs-lookup"><span data-stu-id="fd0e3-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="fd0e3-112">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="fd0e3-112">Security Mode</span></span>|<span data-ttu-id="fd0e3-113">Сообщение</span><span class="sxs-lookup"><span data-stu-id="fd0e3-113">Message</span></span>|  
|<span data-ttu-id="fd0e3-114">Взаимодействие</span><span class="sxs-lookup"><span data-stu-id="fd0e3-114">Interoperability</span></span>|<span data-ttu-id="fd0e3-115">Да, с клиентами и службами, совместимыми с профилем маркера WS-Security и сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="fd0e3-116">Проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="fd0e3-116">Authentication</span></span>|<span data-ttu-id="fd0e3-117">Взаимная проверка подлинности сервера и клиента.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="fd0e3-118">Целостность</span><span class="sxs-lookup"><span data-stu-id="fd0e3-118">Integrity</span></span>|<span data-ttu-id="fd0e3-119">Да</span><span class="sxs-lookup"><span data-stu-id="fd0e3-119">Yes</span></span>|  
|<span data-ttu-id="fd0e3-120">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="fd0e3-120">Confidentiality</span></span>|<span data-ttu-id="fd0e3-121">Да</span><span class="sxs-lookup"><span data-stu-id="fd0e3-121">Yes</span></span>|  
|<span data-ttu-id="fd0e3-122">Transport</span><span class="sxs-lookup"><span data-stu-id="fd0e3-122">Transport</span></span>|<span data-ttu-id="fd0e3-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="fd0e3-123">HTTP</span></span>|  
|<span data-ttu-id="fd0e3-124">Привязка</span><span class="sxs-lookup"><span data-stu-id="fd0e3-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="fd0e3-125">Служба</span><span class="sxs-lookup"><span data-stu-id="fd0e3-125">Service</span></span>  
 <span data-ttu-id="fd0e3-126">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="fd0e3-127">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="fd0e3-128">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="fd0e3-129">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fd0e3-130">Код</span><span class="sxs-lookup"><span data-stu-id="fd0e3-130">Code</span></span>  
 <span data-ttu-id="fd0e3-131">В следующем коде показано, как создать конечную точку службы, которая использует безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="fd0e3-132">Служба требует прохождения проверки подлинности сертификата.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="fd0e3-133">Параметр Configuration</span><span class="sxs-lookup"><span data-stu-id="fd0e3-133">Configuration</span></span>  
 <span data-ttu-id="fd0e3-134">Вместо кода для создания той же службы можно использовать следующую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"   
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="serviceCredentialBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="fd0e3-135">"Клиент";</span><span class="sxs-lookup"><span data-stu-id="fd0e3-135">Client</span></span>  
 <span data-ttu-id="fd0e3-136">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="fd0e3-137">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="fd0e3-138">Создайте автономный клиент, используя код (и код клиента).</span><span class="sxs-lookup"><span data-stu-id="fd0e3-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="fd0e3-139">Создайте клиент, который не определяет никаких адресов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="fd0e3-140">Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="fd0e3-141">Пример:</span><span class="sxs-lookup"><span data-stu-id="fd0e3-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="fd0e3-142">Код</span><span class="sxs-lookup"><span data-stu-id="fd0e3-142">Code</span></span>  
 <span data-ttu-id="fd0e3-143">Следующий код служит для создания клиента.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-143">The following code creates the client.</span></span> <span data-ttu-id="fd0e3-144">Режим безопасности установлен в Message, и типу учетных данных клиента присвоено значение Certificate.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="fd0e3-145">Параметр Configuration</span><span class="sxs-lookup"><span data-stu-id="fd0e3-145">Configuration</span></span>  
 <span data-ttu-id="fd0e3-146">Следующий код служит для настройки клиента.</span><span class="sxs-lookup"><span data-stu-id="fd0e3-146">The following configures the client.</span></span> <span data-ttu-id="fd0e3-147">Сертификат клиента должен быть указан с помощью [ \<clientCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="fd0e3-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="fd0e3-148">Кроме того, сертификат службы задается с помощью [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="fd0e3-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"   
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd0e3-149">См. также</span><span class="sxs-lookup"><span data-stu-id="fd0e3-149">See also</span></span>

- [<span data-ttu-id="fd0e3-150">Общие сведения о безопасности</span><span class="sxs-lookup"><span data-stu-id="fd0e3-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="fd0e3-151">Модель безопасности для Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="fd0e3-151">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
- [<span data-ttu-id="fd0e3-152">Практическое руководство. Создание и настройка временных сертификатов в WCF для обеспечения безопасности транспорта во время разработки</span><span class="sxs-lookup"><span data-stu-id="fd0e3-152">How to: Create and Install Temporary Certificates in WCF for Transport Security During Development</span></span>](https://go.microsoft.com/fwlink/?LinkId=244264)
