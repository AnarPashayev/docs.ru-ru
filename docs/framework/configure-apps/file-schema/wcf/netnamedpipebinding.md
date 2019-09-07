---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: b8bdfeb8f042d892280226e0f7c08b6804eabca9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400194"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="59aff-101">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="59aff-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="59aff-102">Это безопасная и надежная привязка, оптимизированная для обмена данными между процессами компьютера.</span><span class="sxs-lookup"><span data-stu-id="59aff-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="59aff-103">По умолчанию она создает стек связи среды выполнения, использующей WS-ReliableMessaging для обеспечения надежности, режим безопасности транспорта в целях безопасности передачи, именованные каналы для доставки сообщений, а также кодирование двоичных сообщений.</span><span class="sxs-lookup"><span data-stu-id="59aff-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
<span data-ttu-id="59aff-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="59aff-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="59aff-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="59aff-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="59aff-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<привязки >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="59aff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="59aff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="59aff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59aff-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="59aff-108">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59aff-109">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="59aff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="59aff-110">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="59aff-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59aff-111">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="59aff-111">Attributes</span></span>  
  
|<span data-ttu-id="59aff-112">Атрибут</span><span class="sxs-lookup"><span data-stu-id="59aff-112">Attribute</span></span>|<span data-ttu-id="59aff-113">Описание</span><span class="sxs-lookup"><span data-stu-id="59aff-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59aff-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="59aff-114">closeTimeout</span></span>|<span data-ttu-id="59aff-115">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="59aff-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="59aff-116">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="59aff-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="59aff-117">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="59aff-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="59aff-118">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="59aff-118">hostNameComparisonMode</span></span>|<span data-ttu-id="59aff-119">Задает режим сравнения имен узлов HTTP для анализа универсальных кодов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="59aff-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="59aff-120">Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="59aff-120">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="59aff-121">Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.</span><span class="sxs-lookup"><span data-stu-id="59aff-121">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="59aff-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="59aff-122">maxBufferPoolSize</span></span>|<span data-ttu-id="59aff-123">Целое число, задающее максимальный размер буферного пула для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="59aff-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="59aff-124">Значение по умолчанию - 524 288 байт (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="59aff-124">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="59aff-125">Многие элементы Windows Communication Foundation (WCF) используют буферы.</span><span class="sxs-lookup"><span data-stu-id="59aff-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="59aff-126">При создании буферов и их уничтожении после каждого использования расходуется слишком много ресурсов; при сборке мусора для буферов также расходуется слишком много ресурсов.</span><span class="sxs-lookup"><span data-stu-id="59aff-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="59aff-127">Буферные пулы позволяют брать буфер из пула, использовать его, а затем возвращать обратно, когда он больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="59aff-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="59aff-128">Это позволяет избежать излишней нагрузки, связанной с созданием и уничтожением буферов.</span><span class="sxs-lookup"><span data-stu-id="59aff-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="59aff-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="59aff-129">maxBufferSize</span></span>|<span data-ttu-id="59aff-130">Положительное целое число, указывающее максимальный размер буфера, используемого для хранения сообщений в памяти (в байтах).</span><span class="sxs-lookup"><span data-stu-id="59aff-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="59aff-131">Если буфер полон, избыточные данные остаются в основном сокете до тех пор, пока буфер не освободится.</span><span class="sxs-lookup"><span data-stu-id="59aff-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="59aff-132">Данное значение не может быть меньше значения атрибута `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="59aff-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="59aff-133">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="59aff-133">The default is 65536.</span></span> <span data-ttu-id="59aff-134">Дополнительные сведения см. в разделе <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="59aff-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="59aff-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="59aff-135">maxConnections</span></span>|<span data-ttu-id="59aff-136">Целое число, указывающее максимальное число входящих и исходящих подключений, которые будут созданы/приняты службой.</span><span class="sxs-lookup"><span data-stu-id="59aff-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="59aff-137">Входящие и исходящие подключения считаются относительно отдельного предела, определенного этим атрибутом.</span><span class="sxs-lookup"><span data-stu-id="59aff-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="59aff-138">Входящие соединения сверх указанного предела помещаются в очередь и обрабатываются по мере освобождения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="59aff-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="59aff-139">Исходящие соединения сверх указанного предела помещаются в очередь и обрабатываются по мере освобождения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="59aff-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="59aff-140">Значение по умолчанию — 10.</span><span class="sxs-lookup"><span data-stu-id="59aff-140">The default is 10.</span></span>|  
|<span data-ttu-id="59aff-141">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="59aff-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="59aff-142">Положительное целое число, задающее, в байтах, максимальный размер сообщения (включая заголовки), которое можно получить по каналу, настроенному с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="59aff-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="59aff-143">Отправитель сообщения, превышающего это ограничение, получит ошибку SOAP.</span><span class="sxs-lookup"><span data-stu-id="59aff-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="59aff-144">Получатель отклоняет сообщение и создает запись о событии в журнале трассировки.</span><span class="sxs-lookup"><span data-stu-id="59aff-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="59aff-145">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="59aff-145">The default is 65536.</span></span>|  
|<span data-ttu-id="59aff-146">имя</span><span class="sxs-lookup"><span data-stu-id="59aff-146">name</span></span>|<span data-ttu-id="59aff-147">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="59aff-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="59aff-148">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="59aff-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="59aff-149">Начиная с версии [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] для привязок и поведений необязательно задавать имена.</span><span class="sxs-lookup"><span data-stu-id="59aff-149">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="59aff-150">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="59aff-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="59aff-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="59aff-151">openTimeout</span></span>|<span data-ttu-id="59aff-152">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="59aff-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="59aff-153">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="59aff-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="59aff-154">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="59aff-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="59aff-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="59aff-155">receiveTimeout</span></span>|<span data-ttu-id="59aff-156">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="59aff-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="59aff-157">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="59aff-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="59aff-158">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="59aff-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="59aff-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="59aff-159">sendTimeout</span></span>|<span data-ttu-id="59aff-160">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="59aff-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="59aff-161">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="59aff-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="59aff-162">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="59aff-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="59aff-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="59aff-163">transactionFlow</span></span>|<span data-ttu-id="59aff-164">Логическое значение, определяющее, поддерживает ли привязка потоковые спецификации WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="59aff-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="59aff-165">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="59aff-165">The default is `false`.</span></span>|  
|<span data-ttu-id="59aff-166">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="59aff-166">transactionProtocol</span></span>|<span data-ttu-id="59aff-167">Указывает протокол транзакций, используемый с данной привязкой.</span><span class="sxs-lookup"><span data-stu-id="59aff-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="59aff-168">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="59aff-168">Valid values are</span></span><br /><br /> <span data-ttu-id="59aff-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="59aff-169">-   OleTransactions</span></span><br /><span data-ttu-id="59aff-170">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="59aff-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="59aff-171">Значение по умолчанию - OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="59aff-171">The default is OleTransactions.</span></span> <span data-ttu-id="59aff-172">Это атрибут типа <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="59aff-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="59aff-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="59aff-173">transferMode</span></span>|<span data-ttu-id="59aff-174">Значение <xref:System.ServiceModel.TransferMode>, которое указывает, следует ли помещать сообщения в буфер или передавать их потоком по запросу или отклику.</span><span class="sxs-lookup"><span data-stu-id="59aff-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59aff-175">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="59aff-175">Child Elements</span></span>  
  
|<span data-ttu-id="59aff-176">Элемент</span><span class="sxs-lookup"><span data-stu-id="59aff-176">Element</span></span>|<span data-ttu-id="59aff-177">Описание</span><span class="sxs-lookup"><span data-stu-id="59aff-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59aff-178">\<> безопасности</span><span class="sxs-lookup"><span data-stu-id="59aff-178">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="59aff-179">Определяет параметры безопасности привязки.</span><span class="sxs-lookup"><span data-stu-id="59aff-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="59aff-180">Это элемент типа <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="59aff-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|<span data-ttu-id="59aff-181">[\<Реадеркуотас >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="59aff-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="59aff-182">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="59aff-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="59aff-183">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="59aff-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59aff-184">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="59aff-184">Parent Elements</span></span>  
  
|<span data-ttu-id="59aff-185">Элемент</span><span class="sxs-lookup"><span data-stu-id="59aff-185">Element</span></span>|<span data-ttu-id="59aff-186">Описание</span><span class="sxs-lookup"><span data-stu-id="59aff-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59aff-187">\<привязки ></span><span class="sxs-lookup"><span data-stu-id="59aff-187">\<bindings></span></span>](bindings.md)|<span data-ttu-id="59aff-188">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="59aff-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59aff-189">Примечания</span><span class="sxs-lookup"><span data-stu-id="59aff-189">Remarks</span></span>  
 <span data-ttu-id="59aff-190">`NetNamedPipeBinding` создает стек связи среды выполнения по умолчанию, использующий режим безопасности транспорта, именованные каналы для доставки сообщений, а также кодирование двоичных сообщений.</span><span class="sxs-lookup"><span data-stu-id="59aff-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="59aff-191">Эта привязка предоставляется системой Windows Communication Foundation (WCF) в качестве средства обмена данными на компьютере.</span><span class="sxs-lookup"><span data-stu-id="59aff-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="59aff-192">Она также поддерживает транзакции.</span><span class="sxs-lookup"><span data-stu-id="59aff-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="59aff-193">Конфигурация по умолчанию для `NetNamedPipeBinding` аналогична конфигурации, предоставленной `NetTcpBinding`, но она существенно проще, поскольку реализация WCF предназначена только для использования в пределах компьютера и, следовательно, содержит меньшее число предоставляемых функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="59aff-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="59aff-194">Наиболее существенным отличием является то, что параметр `securityMode` содержит только значения `None` и `Transport`.</span><span class="sxs-lookup"><span data-stu-id="59aff-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="59aff-195">Поддержка безопасности SOAP не предусмотрена.</span><span class="sxs-lookup"><span data-stu-id="59aff-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="59aff-196">Режим безопасности настраивается с помощью дополнительного атрибута `securityMode`.</span><span class="sxs-lookup"><span data-stu-id="59aff-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59aff-197">Пример</span><span class="sxs-lookup"><span data-stu-id="59aff-197">Example</span></span>  
 <span data-ttu-id="59aff-198">В следующем примере демонстрируется применение привязки NetNamedPipeBinding, обеспечивающей обмен данными между процессами одного компьютера.</span><span class="sxs-lookup"><span data-stu-id="59aff-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="59aff-199">Использование именованных каналов для обмена данными между компьютерами не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="59aff-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="59aff-200">Привязка задается в файлах конфигурации для клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="59aff-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="59aff-201">Тип привязки указывается в атрибуте `binding` элемента `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="59aff-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="59aff-202">Чтобы настроить привязку netNamedPipeBinding и изменить некоторые ее параметры, необходимо определить конфигурацию привязки.</span><span class="sxs-lookup"><span data-stu-id="59aff-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="59aff-203">Конечная точка должна ссылаться на конфигурацию привязки по имени с атрибутом `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="59aff-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="59aff-204">В этом примере конфигурации привязки присвоено имя «Binding1».</span><span class="sxs-lookup"><span data-stu-id="59aff-204">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="59aff-205">См. также</span><span class="sxs-lookup"><span data-stu-id="59aff-205">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="59aff-206">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="59aff-206">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="59aff-207">Привязки</span><span class="sxs-lookup"><span data-stu-id="59aff-207">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="59aff-208">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="59aff-208">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="59aff-209">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="59aff-209">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
