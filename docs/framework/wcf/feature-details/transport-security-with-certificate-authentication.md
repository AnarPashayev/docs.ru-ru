---
title: Безопасность транспорта с проверкой подлинности с использованием сертификатов
description: Узнайте, как WFC использует сертификаты для проверки подлинности сервера и клиента при использовании безопасности транспорта.
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: 3da1202a5ad3b953470b50dd5924b2ab45f301eb
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244782"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="b30c8-103">Безопасность транспорта с проверкой подлинности с использованием сертификатов</span><span class="sxs-lookup"><span data-stu-id="b30c8-103">Transport Security with Certificate Authentication</span></span>

<span data-ttu-id="b30c8-104">В этой статье рассматривается использование сертификатов X. 509 для проверки подлинности сервера и клиента при использовании безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="b30c8-104">This article discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="b30c8-105">Дополнительные сведения о сертификатах X.509 см. в разделе [Сертификаты открытого ключа X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span><span class="sxs-lookup"><span data-stu-id="b30c8-105">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="b30c8-106">Сертификаты должны выдаваться центром сертификации, который часто является сторонним издателем сертификатов.</span><span class="sxs-lookup"><span data-stu-id="b30c8-106">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="b30c8-107">В домене Windows Server для выдачи сертификатов клиентским компьютерам домена можно использовать службу сертификации Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b30c8-107">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="b30c8-108">В этом сценарии служба размещена в службах IIS, которые используют протокол SSL.</span><span class="sxs-lookup"><span data-stu-id="b30c8-108">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="b30c8-109">В службе задано использование сертификата SSL (X.509), чтобы клиенты могли проверять подлинность сервера.</span><span class="sxs-lookup"><span data-stu-id="b30c8-109">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="b30c8-110">В клиенте также задано использование сертификата X.509, что позволяет службе проверять подлинность клиента.</span><span class="sxs-lookup"><span data-stu-id="b30c8-110">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="b30c8-111">Клиент должен доверять сертификату сервера, а сервер ― сертификату клиента.</span><span class="sxs-lookup"><span data-stu-id="b30c8-111">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="b30c8-112">Фактический механизм, с помощью которого служба и клиент проверяют удостоверение другого пользователя, выходит за рамки этой статьи.</span><span class="sxs-lookup"><span data-stu-id="b30c8-112">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this article.</span></span> <span data-ttu-id="b30c8-113">Дополнительные сведения см. в статье [Цифровая подпись](https://en.wikipedia.org/wiki/Digital_signature) в Википедии.</span><span class="sxs-lookup"><span data-stu-id="b30c8-113">For more information, see [Digital Signature](https://en.wikipedia.org/wiki/Digital_signature) on Wikipedia.</span></span>
  
 <span data-ttu-id="b30c8-114">В этом сценарии реализуется шаблон обмена сообщениями «запрос-ответ», показанный на следующей схеме.</span><span class="sxs-lookup"><span data-stu-id="b30c8-114">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="b30c8-115">![Безопасная перенаправление с помощью сертификатов](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="b30c8-115">![Secure transfer using certificates](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="b30c8-116">Дополнительные сведения об использовании сертификата со службой см. в разделе [Работа с](working-with-certificates.md) сертификатами и [инструкции. Настройка порта с помощью SSL-сертификата](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="b30c8-116">For more information about using a certificate with a service, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="b30c8-117">В следующей таблице описываются различные особенности этого сценария.</span><span class="sxs-lookup"><span data-stu-id="b30c8-117">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="b30c8-118">Характеристика</span><span class="sxs-lookup"><span data-stu-id="b30c8-118">Characteristic</span></span>|<span data-ttu-id="b30c8-119">Описание</span><span class="sxs-lookup"><span data-stu-id="b30c8-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b30c8-120">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="b30c8-120">Security Mode</span></span>|<span data-ttu-id="b30c8-121">Транспортировка</span><span class="sxs-lookup"><span data-stu-id="b30c8-121">Transport</span></span>|  
|<span data-ttu-id="b30c8-122">Совместимость</span><span class="sxs-lookup"><span data-stu-id="b30c8-122">Interoperability</span></span>|<span data-ttu-id="b30c8-123">С существующими службами и клиентами веб-служб.</span><span class="sxs-lookup"><span data-stu-id="b30c8-123">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="b30c8-124">Проверка подлинности (сервера)</span><span class="sxs-lookup"><span data-stu-id="b30c8-124">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="b30c8-125">Проверка подлинности (клиента)</span><span class="sxs-lookup"><span data-stu-id="b30c8-125">Authentication (Client)</span></span>|<span data-ttu-id="b30c8-126">Да (с использованием SSL-сертификата)</span><span class="sxs-lookup"><span data-stu-id="b30c8-126">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="b30c8-127">Да (с использованием сертификата X.509)</span><span class="sxs-lookup"><span data-stu-id="b30c8-127">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="b30c8-128">Целостность данных</span><span class="sxs-lookup"><span data-stu-id="b30c8-128">Data Integrity</span></span>|<span data-ttu-id="b30c8-129">Да</span><span class="sxs-lookup"><span data-stu-id="b30c8-129">Yes</span></span>|  
|<span data-ttu-id="b30c8-130">Конфиденциальность данных</span><span class="sxs-lookup"><span data-stu-id="b30c8-130">Data Confidentiality</span></span>|<span data-ttu-id="b30c8-131">Да</span><span class="sxs-lookup"><span data-stu-id="b30c8-131">Yes</span></span>|  
|<span data-ttu-id="b30c8-132">Транспортировка</span><span class="sxs-lookup"><span data-stu-id="b30c8-132">Transport</span></span>|<span data-ttu-id="b30c8-133">HTTPS</span><span class="sxs-lookup"><span data-stu-id="b30c8-133">HTTPS</span></span>|  
|<span data-ttu-id="b30c8-134">Привязка</span><span class="sxs-lookup"><span data-stu-id="b30c8-134">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="b30c8-135">Настройка службы</span><span class="sxs-lookup"><span data-stu-id="b30c8-135">Configure the Service</span></span>  
 <span data-ttu-id="b30c8-136">Поскольку в этом сценарии служба размещается в службах IIS, он настраивается с помощью файла web.config.</span><span class="sxs-lookup"><span data-stu-id="b30c8-136">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="b30c8-137">В следующем примере содержимого файла web.config показано, как настроить в <xref:System.ServiceModel.WSHttpBinding> использование безопасности транспорта и учетных данных клиента X.509.</span><span class="sxs-lookup"><span data-stu-id="b30c8-137">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a><span data-ttu-id="b30c8-138">Настройка клиента</span><span class="sxs-lookup"><span data-stu-id="b30c8-138">Configure the Client</span></span>  
 <span data-ttu-id="b30c8-139">Настроить клиент можно в коде или в файле app.config.</span><span class="sxs-lookup"><span data-stu-id="b30c8-139">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="b30c8-140">В следующем примере показано, как настроить клиент в коде.</span><span class="sxs-lookup"><span data-stu-id="b30c8-140">The following example shows how to configure the client in code.</span></span>  
  
```csharp
// Create the binding.  
var myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.
var ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
var cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 <span data-ttu-id="b30c8-141">Также можно настроить клиент в файле App.config, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="b30c8-141">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b30c8-142">См. также</span><span class="sxs-lookup"><span data-stu-id="b30c8-142">See also</span></span>

- [<span data-ttu-id="b30c8-143">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="b30c8-143">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="b30c8-144">[Модель безопасности для Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b30c8-144">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
