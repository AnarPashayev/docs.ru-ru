---
title: Безопасность сообщений при использовании клиентом сертификата
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: fb68487746a7dc9cec1d1473b445bccc7b2b23c2
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424879"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="2fee4-102">Безопасность сообщений при использовании клиентом сертификата</span><span class="sxs-lookup"><span data-stu-id="2fee4-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="2fee4-103">В следующем сценарии показаны клиент Windows Communication Foundation (WCF) и служба, защищенные с помощью режима безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="2fee4-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="2fee4-104">Проверка подлинности клиента и службы выполняется с помощью сертификатов.</span><span class="sxs-lookup"><span data-stu-id="2fee4-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="2fee4-105">Дополнительные сведения см. в разделе [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="2fee4-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>

 ![Снимок экрана с клиента с помощью сертификата.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="2fee4-107">Образец приложения, см. в разделе [сертификат безопасности сообщений](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="2fee4-107">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="2fee4-108">Характеристика</span><span class="sxs-lookup"><span data-stu-id="2fee4-108">Characteristic</span></span>|<span data-ttu-id="2fee4-109">Описание</span><span class="sxs-lookup"><span data-stu-id="2fee4-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2fee4-110">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="2fee4-110">Security Mode</span></span>|<span data-ttu-id="2fee4-111">Сообщение</span><span class="sxs-lookup"><span data-stu-id="2fee4-111">Message</span></span>|  
|<span data-ttu-id="2fee4-112">Взаимодействие</span><span class="sxs-lookup"><span data-stu-id="2fee4-112">Interoperability</span></span>|<span data-ttu-id="2fee4-113">Только WCF</span><span class="sxs-lookup"><span data-stu-id="2fee4-113">WCF only</span></span>|  
|<span data-ttu-id="2fee4-114">Проверка подлинности (сервера)</span><span class="sxs-lookup"><span data-stu-id="2fee4-114">Authentication (Server)</span></span>|<span data-ttu-id="2fee4-115">Использование сертификатов служб</span><span class="sxs-lookup"><span data-stu-id="2fee4-115">Using service certificate</span></span>|  
|<span data-ttu-id="2fee4-116">Проверка подлинности (клиента)</span><span class="sxs-lookup"><span data-stu-id="2fee4-116">Authentication (Client)</span></span>|<span data-ttu-id="2fee4-117">Использование сертификатов клиента</span><span class="sxs-lookup"><span data-stu-id="2fee4-117">Using client certificate</span></span>|  
|<span data-ttu-id="2fee4-118">Целостность</span><span class="sxs-lookup"><span data-stu-id="2fee4-118">Integrity</span></span>|<span data-ttu-id="2fee4-119">Да</span><span class="sxs-lookup"><span data-stu-id="2fee4-119">Yes</span></span>|  
|<span data-ttu-id="2fee4-120">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="2fee4-120">Confidentiality</span></span>|<span data-ttu-id="2fee4-121">Да</span><span class="sxs-lookup"><span data-stu-id="2fee4-121">Yes</span></span>|  
|<span data-ttu-id="2fee4-122">Transport</span><span class="sxs-lookup"><span data-stu-id="2fee4-122">Transport</span></span>|<span data-ttu-id="2fee4-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="2fee4-123">HTTP</span></span>|  
|<span data-ttu-id="2fee4-124">Привязка</span><span class="sxs-lookup"><span data-stu-id="2fee4-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="2fee4-125">Служба</span><span class="sxs-lookup"><span data-stu-id="2fee4-125">Service</span></span>  
 <span data-ttu-id="2fee4-126">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="2fee4-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="2fee4-127">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="2fee4-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="2fee4-128">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2fee4-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="2fee4-129">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="2fee4-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2fee4-130">Код</span><span class="sxs-lookup"><span data-stu-id="2fee4-130">Code</span></span>  
 <span data-ttu-id="2fee4-131">В следующем коде показано создание конечной точки службы, которая использует безопасность сообщений для установления защищенного контекста.</span><span class="sxs-lookup"><span data-stu-id="2fee4-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="2fee4-132">Параметр Configuration</span><span class="sxs-lookup"><span data-stu-id="2fee4-132">Configuration</span></span>  
 <span data-ttu-id="2fee4-133">Вместо кода можно использовать следующую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="2fee4-133">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCertificateClient"   
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="2fee4-134">"Клиент";</span><span class="sxs-lookup"><span data-stu-id="2fee4-134">Client</span></span>  
 <span data-ttu-id="2fee4-135">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="2fee4-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="2fee4-136">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="2fee4-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="2fee4-137">Создайте автономный клиент, используя код (и код клиента).</span><span class="sxs-lookup"><span data-stu-id="2fee4-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="2fee4-138">Создайте клиент, который не определяет никаких адресов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="2fee4-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="2fee4-139">Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2fee4-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="2fee4-140">Пример:</span><span class="sxs-lookup"><span data-stu-id="2fee4-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="2fee4-141">Код</span><span class="sxs-lookup"><span data-stu-id="2fee4-141">Code</span></span>  
 <span data-ttu-id="2fee4-142">Следующий код служит для создания клиента.</span><span class="sxs-lookup"><span data-stu-id="2fee4-142">The following code creates the client.</span></span> <span data-ttu-id="2fee4-143">Привязка осуществляется к безопасности режима сообщений, и типу учетных данных клиента присваивается значение `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="2fee4-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="2fee4-144">Параметр Configuration</span><span class="sxs-lookup"><span data-stu-id="2fee4-144">Configuration</span></span>  
 <span data-ttu-id="2fee4-145">В следующей конфигурации задается сертификат клиента с помощью поведения конечной точки.</span><span class="sxs-lookup"><span data-stu-id="2fee4-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="2fee4-146">Дополнительные сведения см. в разделе [Работа с сертификатами](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2fee4-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="2fee4-147">В коде также используется <`identity`> элемент для указания доменных имен (DNS) из ожидаемой идентификации сервера.</span><span class="sxs-lookup"><span data-stu-id="2fee4-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="2fee4-148">Дополнительные сведения об удостоверении см. в разделе [службы идентификации и проверки подлинности](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2fee4-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fee4-149">См. также</span><span class="sxs-lookup"><span data-stu-id="2fee4-149">See also</span></span>

- [<span data-ttu-id="2fee4-150">Общие сведения о безопасности</span><span class="sxs-lookup"><span data-stu-id="2fee4-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="2fee4-151">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="2fee4-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2fee4-152">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="2fee4-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2fee4-153">Модель безопасности для Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="2fee4-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
