---
title: Безопасность сообщений с анонимным клиентом
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 058163c96bba036c3183695bf986b4d0424271ac
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595223"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="3c2e0-102">Безопасность сообщений с анонимным клиентом</span><span class="sxs-lookup"><span data-stu-id="3c2e0-102">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="3c2e0-103">В следующем сценарии показан клиент и служба, защищенные с помощью защиты сообщений Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3c2e0-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="3c2e0-104">Задача, поставленная при разработке, заключается в использовании безопасности сообщений, а не безопасности транспорта, чтобы в будущем возможно было использование более глубокой модели, использующей утверждения.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="3c2e0-105">Дополнительные сведения об использовании расширенных утверждений для авторизации см. [в статье Управление утверждениями и авторизацией с помощью модели удостоверений](managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="3c2e0-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="3c2e0-106">Пример приложения см. в разделе [безопасность сообщений анонимно](../samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="3c2e0-106">For a sample application, see [Message Security Anonymous](../samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="3c2e0-107">![Безопасность сообщений с анонимным клиентом](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="3c2e0-107">![Message security with an anonymous client](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="3c2e0-108">Характеристика</span><span class="sxs-lookup"><span data-stu-id="3c2e0-108">Characteristic</span></span>|<span data-ttu-id="3c2e0-109">Описание</span><span class="sxs-lookup"><span data-stu-id="3c2e0-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="3c2e0-110">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="3c2e0-110">Security Mode</span></span>|<span data-ttu-id="3c2e0-111">Сообщение</span><span class="sxs-lookup"><span data-stu-id="3c2e0-111">Message</span></span>|
|<span data-ttu-id="3c2e0-112">Взаимодействие</span><span class="sxs-lookup"><span data-stu-id="3c2e0-112">Interoperability</span></span>|<span data-ttu-id="3c2e0-113">Только WCF</span><span class="sxs-lookup"><span data-stu-id="3c2e0-113">WCF only</span></span>|
|<span data-ttu-id="3c2e0-114">Проверка подлинности (сервера)</span><span class="sxs-lookup"><span data-stu-id="3c2e0-114">Authentication (Server)</span></span>|<span data-ttu-id="3c2e0-115">Первоначальное согласование возможно только после проверки подлинности сервера, но не клиента</span><span class="sxs-lookup"><span data-stu-id="3c2e0-115">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="3c2e0-116">Проверка подлинности (клиента)</span><span class="sxs-lookup"><span data-stu-id="3c2e0-116">Authentication (Client)</span></span>|<span data-ttu-id="3c2e0-117">Нет</span><span class="sxs-lookup"><span data-stu-id="3c2e0-117">None</span></span>|
|<span data-ttu-id="3c2e0-118">Целостность</span><span class="sxs-lookup"><span data-stu-id="3c2e0-118">Integrity</span></span>|<span data-ttu-id="3c2e0-119">Да, используется общий контекст безопасности</span><span class="sxs-lookup"><span data-stu-id="3c2e0-119">Yes, using shared security context</span></span>|
|<span data-ttu-id="3c2e0-120">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="3c2e0-120">Confidentiality</span></span>|<span data-ttu-id="3c2e0-121">Да, используется общий контекст безопасности</span><span class="sxs-lookup"><span data-stu-id="3c2e0-121">Yes, using shared security context</span></span>|
|<span data-ttu-id="3c2e0-122">Транспорт</span><span class="sxs-lookup"><span data-stu-id="3c2e0-122">Transport</span></span>|<span data-ttu-id="3c2e0-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="3c2e0-123">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="3c2e0-124">Служба</span><span class="sxs-lookup"><span data-stu-id="3c2e0-124">Service</span></span>

<span data-ttu-id="3c2e0-125">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="3c2e0-126">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-126">Do one of the following:</span></span>

- <span data-ttu-id="3c2e0-127">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-127">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="3c2e0-128">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="3c2e0-129">Код</span><span class="sxs-lookup"><span data-stu-id="3c2e0-129">Code</span></span>

<span data-ttu-id="3c2e0-130">В следующем коде показано, как создать конечную точку службы, которая использует безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-130">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="3c2e0-131">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="3c2e0-131">Configuration</span></span>

<span data-ttu-id="3c2e0-132">Вместо кода можно использовать следующую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="3c2e0-133">Элемент поведения службы используется для указания сертификата, который используется для проверки подлинности службы для клиента.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="3c2e0-134">Элемент службы должен задавать поведение с помощью атрибута `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="3c2e0-135">Элемент привязки указывает, что типу учетных данных клиента присвоено значение `None`, позволяя анонимному клиенту использовать службу.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="3c2e0-136">Клиент</span><span class="sxs-lookup"><span data-stu-id="3c2e0-136">Client</span></span>

<span data-ttu-id="3c2e0-137">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="3c2e0-138">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-138">Do one of the following:</span></span>

- <span data-ttu-id="3c2e0-139">Создайте автономный клиент, используя код (и код клиента).</span><span class="sxs-lookup"><span data-stu-id="3c2e0-139">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="3c2e0-140">Создайте клиент, который не определяет никаких адресов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="3c2e0-141">Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="3c2e0-142">Пример.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-142">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="3c2e0-143">Код</span><span class="sxs-lookup"><span data-stu-id="3c2e0-143">Code</span></span>

<span data-ttu-id="3c2e0-144">В следующем примере кода создается экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="3c2e0-145">Привязка использует безопасность режима сообщений, и тип учетных данных клиента задан как None.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-145">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="3c2e0-146">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="3c2e0-146">Configuration</span></span>

<span data-ttu-id="3c2e0-147">Следующий код служит для настройки клиента.</span><span class="sxs-lookup"><span data-stu-id="3c2e0-147">The following code configures the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3c2e0-148">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="3c2e0-148">See also</span></span>

- [<span data-ttu-id="3c2e0-149">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="3c2e0-149">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="3c2e0-150">Защита распределенных приложений</span><span class="sxs-lookup"><span data-stu-id="3c2e0-150">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="3c2e0-151">Безопасность сообщений с возможностью анонимного доступа</span><span class="sxs-lookup"><span data-stu-id="3c2e0-151">Message Security Anonymous</span></span>](../samples/message-security-anonymous.md)
- [<span data-ttu-id="3c2e0-152">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="3c2e0-152">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="3c2e0-153">[Модель безопасности для Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3c2e0-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
