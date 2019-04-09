---
title: 'Транспорт: TCP-взаимодействие WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 9b2fcc2e7d96d2cfbb3b55934fa19ec24487bce7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162180"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="3e277-102">Транспорт: TCP-взаимодействие WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="3e277-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="3e277-103">В примере транспорта взаимодействия TCP WSE 3.0 демонстрируется реализация дуплексного сеанса TCP в качестве пользовательского транспорта Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3e277-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="3e277-104">Также демонстрируется использование расширяемости уровня канала для создания интерфейса по сети с существующими развернутыми системами.</span><span class="sxs-lookup"><span data-stu-id="3e277-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="3e277-105">Ниже показано, как построить этот пользовательский транспорт WCF:</span><span class="sxs-lookup"><span data-stu-id="3e277-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1.  <span data-ttu-id="3e277-106">Начиная с сокета TCP, создайте клиентские и серверные реализации интерфейса <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, использующие кадрирование DIME для разграничения границ сообщений.</span><span class="sxs-lookup"><span data-stu-id="3e277-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2.  <span data-ttu-id="3e277-107">Создайте фабрику каналов, которая подключается к службе TCP WSE и передает кадрированные сообщения через клиентские интерфейсы <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="3e277-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3.  <span data-ttu-id="3e277-108">Создайте прослушиватель канала для приема входящих подключений TCP и создания соответствующих каналов.</span><span class="sxs-lookup"><span data-stu-id="3e277-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4.  <span data-ttu-id="3e277-109">Убедитесь, что все исключения, связанные с сетью, нормализованы в соответствующий класс, унаследованный от <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="3e277-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5.  <span data-ttu-id="3e277-110">Добавьте элемент привязки, добавляющий пользовательский транспорт в стек каналов.</span><span class="sxs-lookup"><span data-stu-id="3e277-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="3e277-111">Дополнительные сведения см. в разделе [Добавление элемента привязки].</span><span class="sxs-lookup"><span data-stu-id="3e277-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="3e277-112">Создание IDuplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="3e277-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="3e277-113">Первый этап создания транспорта взаимодействия TCP WSE 3.0 - это реализация интерфейса <xref:System.ServiceModel.Channels.IDuplexSessionChannel> на основе класса <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="3e277-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> `WseTcpDuplexSessionChannel` <span data-ttu-id="3e277-114">Является производным от <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="3e277-114">derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="3e277-115">Логика передачи сообщения состоит из двух основных частей: (1) кодирование сообщения в байтах и (2) Кадрирование этих байтов и отправки их по сети.</span><span class="sxs-lookup"><span data-stu-id="3e277-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="3e277-116">Кроме того, устанавливается блокировка, чтобы вызовы Send() сохраняли гарантию порядка IDuplexSessionChannel и чтобы вызовы соответствующего сокета были правильно синхронизированы.</span><span class="sxs-lookup"><span data-stu-id="3e277-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 `WseTcpDuplexSessionChannel` <span data-ttu-id="3e277-117">использует <xref:System.ServiceModel.Channels.MessageEncoder> за преобразование <xref:System.ServiceModel.Channels.Message> в и из byte [].</span><span class="sxs-lookup"><span data-stu-id="3e277-117">uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="3e277-118">Так как это транспорт, канал `WseTcpDuplexSessionChannel` также отвечает за использование удаленного адреса, с которым был настроен канал.</span><span class="sxs-lookup"><span data-stu-id="3e277-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> `EncodeMessage` <span data-ttu-id="3e277-119">инкапсулирует логику для этого преобразования.</span><span class="sxs-lookup"><span data-stu-id="3e277-119">encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="3e277-120">После того как сообщение <xref:System.ServiceModel.Channels.Message> закодировано в байты, оно должно быть передано по сети.</span><span class="sxs-lookup"><span data-stu-id="3e277-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="3e277-121">Для этого требуется система определения границ сообщения.</span><span class="sxs-lookup"><span data-stu-id="3e277-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="3e277-122">WSE 3.0 использует версию [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) качестве протокола кадрирования.</span><span class="sxs-lookup"><span data-stu-id="3e277-122">WSE 3.0 uses a version of [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> `WriteData` <span data-ttu-id="3e277-123">инкапсулирует логику кадрирования для заключения массива byte [] в набор записей DIME.</span><span class="sxs-lookup"><span data-stu-id="3e277-123">encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="3e277-124">Логика приема сообщений очень похожа.</span><span class="sxs-lookup"><span data-stu-id="3e277-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="3e277-125">Основная сложность заключается в учете ситуаций, когда операция чтения сокета может вернуть меньше байтов, чем было запрошено.</span><span class="sxs-lookup"><span data-stu-id="3e277-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="3e277-126">Чтобы принять сообщение, `WseTcpDuplexSessionChannel` считывает байты из сети, декодирует кадрирование DIME, затем использует <xref:System.ServiceModel.Channels.MessageEncoder> для преобразования массива byte[] в сообщение <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="3e277-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="3e277-127">Базовый класс `WseTcpDuplexSessionChannel` предполагает, что он получает подключенный сокет.</span><span class="sxs-lookup"><span data-stu-id="3e277-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="3e277-128">Базовый класс обрабатывает завершение работы сокета.</span><span class="sxs-lookup"><span data-stu-id="3e277-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="3e277-129">Существуют три места, взаимодействующих с закрытием сокета:</span><span class="sxs-lookup"><span data-stu-id="3e277-129">There are three places that interface with socket closure:</span></span>  
  
-   <span data-ttu-id="3e277-130">OnAbort - закрыть сокет некорректно (жесткое закрытие).</span><span class="sxs-lookup"><span data-stu-id="3e277-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
-   <span data-ttu-id="3e277-131">On[Begin]Close - закрыть сокет корректно (мягкое закрытие).</span><span class="sxs-lookup"><span data-stu-id="3e277-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
-   <span data-ttu-id="3e277-132">session.CloseOutputSession -- завершить работу исходящего потока данных (закрытие наполовину).</span><span class="sxs-lookup"><span data-stu-id="3e277-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="3e277-133">Фабрика каналов</span><span class="sxs-lookup"><span data-stu-id="3e277-133">Channel Factory</span></span>  
 <span data-ttu-id="3e277-134">Следующий этап создания транспорта TCP - реализация <xref:System.ServiceModel.Channels.IChannelFactory> для каналов клиентов.</span><span class="sxs-lookup"><span data-stu-id="3e277-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
-   `WseTcpChannelFactory` <span data-ttu-id="3e277-135">является производным от <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >.</span><span class="sxs-lookup"><span data-stu-id="3e277-135">derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="3e277-136">Это фабрика, которая переопределяет `OnCreateChannel` для создания каналов клиентов.</span><span class="sxs-lookup"><span data-stu-id="3e277-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` <span data-ttu-id="3e277-137">Добавляет логику в базовый `WseTcpDuplexSessionChannel` для подключения к серверу TCP в `channel.Open` времени.</span><span class="sxs-lookup"><span data-stu-id="3e277-137">adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="3e277-138">Сначала имя узла разрешается в IP-адрес, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="3e277-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   <span data-ttu-id="3e277-139">Затем имя узла подключается в цикле к первому доступному IP-адресу, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="3e277-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   <span data-ttu-id="3e277-140">Как часть контракта канала, все специфичные для домена расширения заключаются в оболочку, как `SocketException` в <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="3e277-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="3e277-141">Прослушиватель канала</span><span class="sxs-lookup"><span data-stu-id="3e277-141">Channel Listener</span></span>  
 <span data-ttu-id="3e277-142">Следующий этап создания транспорта TCP - реализация <xref:System.ServiceModel.Channels.IChannelListener> для приема каналов сервера.</span><span class="sxs-lookup"><span data-stu-id="3e277-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
-   `WseTcpChannelListener` <span data-ttu-id="3e277-143">является производным от <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > и переопределяет On [Begin] Open и On [Begin] Close для управления временем существования его прослушивающих сокетов.</span><span class="sxs-lookup"><span data-stu-id="3e277-143">derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="3e277-144">В OnOpen создается сокет для прослушивания по IP_ANY.</span><span class="sxs-lookup"><span data-stu-id="3e277-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="3e277-145">Более сложные реализации могут создавать второй сокет для прослушивания также и по IPv6.</span><span class="sxs-lookup"><span data-stu-id="3e277-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="3e277-146">Они могут также допускать задание IP-адреса в имени узла.</span><span class="sxs-lookup"><span data-stu-id="3e277-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="3e277-147">Когда принимается новый сокет, инициализируется новый канал сервера с этим сокетом.</span><span class="sxs-lookup"><span data-stu-id="3e277-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="3e277-148">Все операции ввода и вывода уже реализованы в базовом классе, поэтому этот канал отвечает за инициализацию сокета.</span><span class="sxs-lookup"><span data-stu-id="3e277-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="3e277-149">Добавление элемента привязки</span><span class="sxs-lookup"><span data-stu-id="3e277-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="3e277-150">Теперь, когда фабрики и каналы построены, они должны быть предоставлены среде выполнения ServiceModel через привязку.</span><span class="sxs-lookup"><span data-stu-id="3e277-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="3e277-151">Привязка - это коллекция элементов привязки, представляющая стек связи для адреса службы.</span><span class="sxs-lookup"><span data-stu-id="3e277-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="3e277-152">Каждый элемент стека представлен элементом привязки.</span><span class="sxs-lookup"><span data-stu-id="3e277-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="3e277-153">В этом примере в качестве элемента привязки выступает элемент `WseTcpTransportBindingElement`, являющийся производным элемента <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="3e277-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="3e277-154">Он поддерживает <xref:System.ServiceModel.Channels.IDuplexSessionChannel> и переопределяет следующие методы создания фабрик, связанных с нашей привязкой.</span><span class="sxs-lookup"><span data-stu-id="3e277-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="3e277-155">Он также содержит члены для клонирования элемента `BindingElement` и возврата схемы (wse.tcp).</span><span class="sxs-lookup"><span data-stu-id="3e277-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="3e277-156">Тестовая консоль WSE TCP</span><span class="sxs-lookup"><span data-stu-id="3e277-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="3e277-157">Тестовый код для использования этого образца транспорта находится в файле TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="3e277-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="3e277-158">Ниже показано, как выполнить построение и запуск образца `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="3e277-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="3e277-159">Тестовый код создает пользовательскую привязку, которая использует MTOM для кодирования и `WseTcpTransport` для транспорта.</span><span class="sxs-lookup"><span data-stu-id="3e277-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="3e277-160">Он также настраивает AddressingVersion для соответствия WSE 3.0, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="3e277-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="3e277-161">Он состоит из двух тестов - один тест настраивает типизированного клиента с помощью кода, созданного из WSE 3.0 WSDL.</span><span class="sxs-lookup"><span data-stu-id="3e277-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="3e277-162">Второй тест использует WCF как клиент и сервер, отправляя сообщения непосредственно по интерфейсам API канала.</span><span class="sxs-lookup"><span data-stu-id="3e277-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="3e277-163">При выполнении этого образца ожидаются следующие выходные данные.</span><span class="sxs-lookup"><span data-stu-id="3e277-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="3e277-164">Клиент:</span><span class="sxs-lookup"><span data-stu-id="3e277-164">Client:</span></span>  
  
```  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 <span data-ttu-id="3e277-165">Сервер:</span><span class="sxs-lookup"><span data-stu-id="3e277-165">Server:</span></span>  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3e277-166">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="3e277-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3e277-167">Для выполнения этого примера необходимо, чтобы были установлены WSE 3.0 и пример WSE `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="3e277-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="3e277-168">Вы можете скачать [WSE 3.0 из MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span><span class="sxs-lookup"><span data-stu-id="3e277-168">You can download [WSE 3.0 from MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e277-169">Так как WSE 3.0 не поддерживается в [!INCLUDE[lserver](../../../../includes/lserver-md.md)], пример `TcpSyncStockService` невозможно установить или выполнить в этой операционной системе.</span><span class="sxs-lookup"><span data-stu-id="3e277-169">Because WSE 3.0 is not supported on [!INCLUDE[lserver](../../../../includes/lserver-md.md)], you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1.  <span data-ttu-id="3e277-170">После установки примера `TcpSyncStockService` выполните следующие операции.</span><span class="sxs-lookup"><span data-stu-id="3e277-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1.  <span data-ttu-id="3e277-171">Откройте `TcpSyncStockService` в Visual Studio (Обратите внимание, что пример TcpSyncStockService устанавливается с WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="3e277-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="3e277-172">Он не является частью кода данного примера.).</span><span class="sxs-lookup"><span data-stu-id="3e277-172">It is not part of this sample's code).</span></span>  
  
    2.  <span data-ttu-id="3e277-173">Установите проект StockService в качестве проекта для запуска.</span><span class="sxs-lookup"><span data-stu-id="3e277-173">Set the StockService project as the start up project.</span></span>  
  
    3.  <span data-ttu-id="3e277-174">Откройте файл StockService.cs в проекте StockService и закомментируйте атрибут [Policy] класса `StockService`.</span><span class="sxs-lookup"><span data-stu-id="3e277-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="3e277-175">Таким образом в примере отключается безопасность.</span><span class="sxs-lookup"><span data-stu-id="3e277-175">This disables security from the sample.</span></span> <span data-ttu-id="3e277-176">Хотя WCF могут взаимодействовать с WSE 3.0 защищенные конечные точки, чтобы сфокусировать данный пример на пользовательском транспорте TCP отключен безопасности.</span><span class="sxs-lookup"><span data-stu-id="3e277-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4.  <span data-ttu-id="3e277-177">Нажмите клавишу F5, чтобы запустить `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="3e277-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="3e277-178">Служба запускается в новом окне консоли.</span><span class="sxs-lookup"><span data-stu-id="3e277-178">The service starts in a new console window.</span></span>  
  
    5.  <span data-ttu-id="3e277-179">Откройте пример транспорта TCP в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e277-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6.  <span data-ttu-id="3e277-180">Обновите переменную "hostname" в файле TestCode.cs, чтобы она соответствовала имени компьютера, на котором запущена служба `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="3e277-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7.  <span data-ttu-id="3e277-181">Нажмите клавишу F5, чтобы запустить пример транспорта TCP.</span><span class="sxs-lookup"><span data-stu-id="3e277-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8.  <span data-ttu-id="3e277-182">Тестовый клиент транспорта TCP запускается в новой консоли.</span><span class="sxs-lookup"><span data-stu-id="3e277-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="3e277-183">Клиент запрашивает у службы цены акций и отображает результаты в своем окне консоли.</span><span class="sxs-lookup"><span data-stu-id="3e277-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
