---
title: Дуплексные службы
description: Узнайте, как создать в WCF контракт в виде дуплексной службы, который позволяет обеим конечным точкам отсылать сообщения друг другу по каналу, созданному клиентом.
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: a43bb63a0ccf1a34b79dce755c19f7ed4cb6c16c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247355"
---
# <a name="duplex-services"></a><span data-ttu-id="06651-103">Дуплексные службы</span><span class="sxs-lookup"><span data-stu-id="06651-103">Duplex Services</span></span>

<span data-ttu-id="06651-104">Дуплексный контракт службы - это шаблон обмена сообщениями, в котором обе конечные точки могут отправлять сообщения друг другу независимо друг от друга.</span><span class="sxs-lookup"><span data-stu-id="06651-104">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="06651-105">Следовательно, дуплексная служба может отправлять сообщения обратно конечной точке клиента, обеспечивая поведение, аналогичное событийному.</span><span class="sxs-lookup"><span data-stu-id="06651-105">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="06651-106">Дуплексная связь имеет место, когда клиент подключается к службе и предоставляет службе канал, по которому служба может отправлять сообщения обратно клиенту.</span><span class="sxs-lookup"><span data-stu-id="06651-106">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="06651-107">Обратите внимание, что событийное поведение дуплексных служб используется только в сеансе.</span><span class="sxs-lookup"><span data-stu-id="06651-107">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="06651-108">Создание дуплексного контракта предполагает создание двух интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="06651-108">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="06651-109">Первый - интерфейс контракта службы, описывающий операции, которые может вызывать клиент.</span><span class="sxs-lookup"><span data-stu-id="06651-109">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="06651-110">Этот контракт службы должен указывать *контракт обратного вызова* в <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> свойстве.</span><span class="sxs-lookup"><span data-stu-id="06651-110">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="06651-111">Контракт обратного вызова представляет собой интерфейс, определяющий операции, которые служба может вызывать в конечной точке клиента.</span><span class="sxs-lookup"><span data-stu-id="06651-111">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="06651-112">Дуплексный контракт не требует сеанса, хотя дуплексные привязки, предоставляемые системой, используют их.</span><span class="sxs-lookup"><span data-stu-id="06651-112">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="06651-113">Ниже приведен пример дуплексного контракта.</span><span class="sxs-lookup"><span data-stu-id="06651-113">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="06651-114">Класс `CalculatorService` реализует основной интерфейс `ICalculatorDuplex`.</span><span class="sxs-lookup"><span data-stu-id="06651-114">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="06651-115">Служба использует режим экземпляра <xref:System.ServiceModel.InstanceContextMode.PerSession> для поддержания результата для каждого сеанса.</span><span class="sxs-lookup"><span data-stu-id="06651-115">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="06651-116">Закрытое свойство `Callback` обращается к клиенту по каналу обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="06651-116">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="06651-117">Служба использует обратный вызов для отправки сообщений обратно клиенту через интерфейс обратного вызова, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="06651-117">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="06651-118">Для получения сообщений от службы клиент обязан предоставить класс, который реализует интерфейс обратного вызова дуплексного контракта.</span><span class="sxs-lookup"><span data-stu-id="06651-118">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="06651-119">В следующем примере кода демонстрируется класс `CallbackHandler`, реализующий интерфейс `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="06651-119">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="06651-120">Для клиента WCF, созданного для дуплексного контракта, требуется <xref:System.ServiceModel.InstanceContext> предоставить класс при создании.</span><span class="sxs-lookup"><span data-stu-id="06651-120">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="06651-121">Этот класс <xref:System.ServiceModel.InstanceContext> используется в качестве сайта для объекта, реализующего интерфейс обратного вызова и обрабатывающего сообщения, которые отправляются службой обратно.</span><span class="sxs-lookup"><span data-stu-id="06651-121">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="06651-122">Класс <xref:System.ServiceModel.InstanceContext> создается с экземпляром класса `CallbackHandler`.</span><span class="sxs-lookup"><span data-stu-id="06651-122">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="06651-123">Этот объект обрабатывает сообщения, отправляемые службой клиенту в интерфейсе обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="06651-123">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="06651-124">Необходимо настроить конфигурацию для службы таким образом, чтобы предоставлялась привязка, которая поддерживает как сеансовую, так и дуплексную связь.</span><span class="sxs-lookup"><span data-stu-id="06651-124">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="06651-125">Элемент `wsDualHttpBinding` поддерживает сеансовую и дуплексную связь, предоставляя двойные соединения HTTP (по одному для каждого направления).</span><span class="sxs-lookup"><span data-stu-id="06651-125">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="06651-126">На стороне клиента необходимо настроить адрес, который будет использоваться сервером для подключения к клиенту, как показано в следующем примере конфигурации.</span><span class="sxs-lookup"><span data-stu-id="06651-126">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="06651-127">Недуплексные клиенты, которые не смогли пройти проверку с помощью защищенного диалога, как правило, создают исключение <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="06651-127">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="06651-128">Однако если дуплексному клиенту, использующему защищенный диалог, не удается пройти проверку, клиент получает вместо этого исключение <xref:System.TimeoutException>.</span><span class="sxs-lookup"><span data-stu-id="06651-128">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="06651-129">Если при создании клиента/службы с использованием элемента `WSHttpBinding` не будет включена конечная точка обратного вызова клиента, будет получена следующая ошибка.</span><span class="sxs-lookup"><span data-stu-id="06651-129">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="06651-130">В следующем примере кода показано, как указать адрес конечной точки клиента программным способом.</span><span class="sxs-lookup"><span data-stu-id="06651-130">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

```csharp
WSDualHttpBinding binding = new WSDualHttpBinding();
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");
```

```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")
```

<span data-ttu-id="06651-131">В следующем образце кода показано, как задавать в конфигурации адрес конечной точки клиента.</span><span class="sxs-lookup"><span data-stu-id="06651-131">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

```xml
<client>
    <endpoint name ="ServerEndpoint"
          address="http://localhost:12000/DuplexTestUsingConfig/Server"
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"
            binding="wsDualHttpBinding"
           contract="IDuplexTest" />
</client>
<bindings>
    <wsDualHttpBinding>
        <binding name="WSDualHttpBinding_IDuplexTest"
          clientBaseAddress="http://localhost:8000/myClient/" >
            <security mode="None"/>
         </binding>
    </wsDualHttpBinding>
</bindings>
```

> [!WARNING]
> <span data-ttu-id="06651-132">Дуплексная модель не обнаруживает автоматическое обнаружение того, когда служба или клиент закрывают свой канал.</span><span class="sxs-lookup"><span data-stu-id="06651-132">The duplex model doesn't automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="06651-133">Поэтому, если клиент неожиданно завершает работу, по умолчанию служба не будет уведомлена, или если служба неожиданно завершает работу, клиент не будет уведомлен.</span><span class="sxs-lookup"><span data-stu-id="06651-133">So if a client unexpectedly terminates, by default the service will not be notified, or if a service unexpectedly terminates, the client will not be notified.</span></span> <span data-ttu-id="06651-134">При использовании отключенной службы <xref:System.ServiceModel.CommunicationException> возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="06651-134">If you use a service that is disconnected, the <xref:System.ServiceModel.CommunicationException> exception is raised.</span></span> <span data-ttu-id="06651-135">Клиенты и службы могут реализовать собственный протокол для уведомления друг друга по усмотрению.</span><span class="sxs-lookup"><span data-stu-id="06651-135">Clients and services can implement their own protocol to notify each other if they so choose.</span></span> <span data-ttu-id="06651-136">Дополнительные сведения об обработке ошибок см. в разделе [Обработка ошибок WCF](../wcf-error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="06651-136">For more information on error handling, see [WCF Error Handling](../wcf-error-handling.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06651-137">См. также</span><span class="sxs-lookup"><span data-stu-id="06651-137">See also</span></span>

- [<span data-ttu-id="06651-138">Дуплекс</span><span class="sxs-lookup"><span data-stu-id="06651-138">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="06651-139">Задание поведения клиента во время выполнения</span><span class="sxs-lookup"><span data-stu-id="06651-139">Specifying Client Run-Time Behavior</span></span>](../specifying-client-run-time-behavior.md)
- [<span data-ttu-id="06651-140">Практическое руководство. Создание фабрики каналов и ее использование для создания каналов и управления ими</span><span class="sxs-lookup"><span data-stu-id="06651-140">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
