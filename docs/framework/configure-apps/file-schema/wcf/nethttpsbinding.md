---
title: <netHttpsBinding>
ms.date: 03/30/2017
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
ms.openlocfilehash: 842f2acb3be03be8171bcf7312f230fc06754511
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2020
ms.locfileid: "84201048"
---
# \<netHttpsBinding>
<span data-ttu-id="b3d0b-101">Представляет привязку, которую служба Windows Communication Foundation (WCF) может использовать для настройки и предоставления конечных точек, которые могут взаимодействовать по протоколу HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-101">Represents a binding that a Windows Communication Foundation (WCF) service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="b3d0b-102">При использовании с дуплексным контрактом будут использоваться веб-сокеты, в противном случае будет использоваться протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-102">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netHttpsBinding>**  

## <a name="syntax"></a><span data-ttu-id="b3d0b-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b3d0b-103">Syntax</span></span>  
  
```xml  
<netHttpsBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netHttpsBinding>
```  
  
## <a name="type"></a><span data-ttu-id="b3d0b-104">Type</span><span class="sxs-lookup"><span data-stu-id="b3d0b-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3d0b-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b3d0b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b3d0b-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3d0b-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b3d0b-107">Attributes</span></span>  
  
|<span data-ttu-id="b3d0b-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b3d0b-108">Attribute</span></span>|<span data-ttu-id="b3d0b-109">Описание:</span><span class="sxs-lookup"><span data-stu-id="b3d0b-109">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="b3d0b-110">Логическое значение, определяющее, принимает ли клиент файлы Cookie и распространяет ли он их на будущие запросы.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-110">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="b3d0b-111">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-111">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b3d0b-112">Это свойство можно использовать при взаимодействии с веб-службами ASMX, которые используют файлы Cookie.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-112">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="b3d0b-113">В этом случае можно быть уверенным, что файлы cookie, возвращаемые с сервера, автоматически копируются во все последующие клиентские запросы к этой службе.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-113">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="b3d0b-114">Логическое значение, определяющее, будет ли выполняться обход прокси-сервера для локальных адресов.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="b3d0b-115">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b3d0b-116">Интернет-ресурс является локальным, если у него локальный адрес.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-116">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="b3d0b-117">Локальный адрес — это тот же компьютер, локальная локальная сеть или интрасеть, который идентифицируется в синтаксических случаях за счет отсутствия точки (.), как в URI `http://webserver/` и `http://localhost/` .</span><span class="sxs-lookup"><span data-stu-id="b3d0b-117">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs `http://webserver/` and `http://localhost/`.</span></span><br /><br /> <span data-ttu-id="b3d0b-118">Этот атрибут определяет, будут ли конечные точки, настроенные с помощью привязки BasicHttpBinding, использовать прокси-сервер при доступе к локальным ресурсам.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-118">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="b3d0b-119">Если значение этого атрибута `true`, запросы к локальным интернет-ресурсам не используют прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-119">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="b3d0b-120">Используйте имя узла (а не localhost), если необходимо, чтобы клиенты проходили через прокси-сервер при взаимодействии со службами на том же компьютере, когда для этого атрибута задано значение `true`.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-120">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="b3d0b-121">Если атрибут имеет значение `false`, все интернет-запросы выполняются через данный прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-121">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="b3d0b-122">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b3d0b-123">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b3d0b-124">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-124">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="b3d0b-125">Задает режим сравнения имен узлов HTTP для анализа универсальных кодов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="b3d0b-125">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="b3d0b-126">Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="b3d0b-126">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="b3d0b-127">Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-127">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="b3d0b-128">Целое значение, определяющее максимальный объем памяти, выделяемой для диспетчера буферов сообщений, получающих сообщения из канала.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-128">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="b3d0b-129">Значение по умолчанию - 524 288 (0x80 000) байт.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-129">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="b3d0b-130">Диспетчер буферов сокращает затраты ресурсов на использование буферов с помощью буферного пула.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-130">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="b3d0b-131">Буферы требуются для обработки службой сообщений, приходящих из канала.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-131">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="b3d0b-132">Если в буферном пуле недостаточно памяти для обработки потока сообщений, диспетчер буферов сообщений должен выделить дополнительную память из кучи CLR, что увеличивает нагрузку по сбору мусора.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-132">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="b3d0b-133">Значительное выделение памяти из мусорной кучи CLR указывает на то, что размер буферного пула слишком мал и производительность можно повысить за счет выделения большего объема памяти путем увеличения значения этого атрибута.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-133">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="b3d0b-134">Целое значение, указывающее максимальный размер (в байтах) буфера, хранящего сообщения во время их обработки для конечной точки, настроенной с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-134">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="b3d0b-135">Значение по умолчанию - 65 536 байт.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-135">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="b3d0b-136">Положительное целое число, определяющее максимальный размер сообщения (в байтах), включая заголовки, которое можно получить по каналу, настроенному с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-136">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="b3d0b-137">Отправитель получает ошибку SOAP, если размер сообщения оказывается слишком большим для получателя.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-137">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="b3d0b-138">Получатель отклоняет сообщение и создает запись о событии в журнале трассировки.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-138">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b3d0b-139">Значение по умолчанию: 65 536 байт.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-139">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="b3d0b-140">Определяет кодировщик, используемый для кодировки сообщения SOAP.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-140">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="b3d0b-141">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-141">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b3d0b-142">-Text: использование кодировщика текстовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-142">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="b3d0b-143">-MTOM: используйте кодировщик обмена сообщениями, механизм передачи сообщений 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="b3d0b-143">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="b3d0b-144">Значение по умолчанию - Text.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-144">The default is Text.</span></span> <span data-ttu-id="b3d0b-145">Это атрибут типа <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-145">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="b3d0b-146">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b3d0b-147">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b3d0b-148">Начиная с .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-148">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b3d0b-149">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b3d0b-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="b3d0b-150">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b3d0b-151">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b3d0b-152">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-152">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="b3d0b-153">Универсальный код ресурса (URI) содержит адрес прокси-сервера HTTP.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-153">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="b3d0b-154">Если для параметра `useSystemWebProxy` задано значение `true`, этот параметр должен иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-154">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="b3d0b-155">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-155">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b3d0b-156">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b3d0b-157">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b3d0b-158">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-158">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b3d0b-159">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b3d0b-160">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b3d0b-161">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-161">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="b3d0b-162">Задает кодировку, используемую при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-162">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b3d0b-163">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-163">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b3d0b-164">-BigEndianUnicode: Юникод байтов Encoding.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-164">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="b3d0b-165">-Unicode: 16-разрядная кодировка.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-165">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="b3d0b-166">-UTF8:8-разрядная кодировка</span><span class="sxs-lookup"><span data-stu-id="b3d0b-166">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="b3d0b-167">По умолчанию используется значение UTF8.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-167">The default is UTF8.</span></span> <span data-ttu-id="b3d0b-168">Это атрибут типа <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-168">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="b3d0b-169">Допустимое значение <xref:System.ServiceModel.TransferMode>, указывающее, следует ли буферизировать сообщения или передавать их потоком по запросу или отклику.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-169">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="b3d0b-170">Логическое значение, определяющее, должен ли использоваться автоматически настроенный системный прокси-сервер HTTP, если он доступен.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-170">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="b3d0b-171">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-171">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="b3d0b-172">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b3d0b-172">Child Elements</span></span>  
  
|<span data-ttu-id="b3d0b-173">Элемент</span><span class="sxs-lookup"><span data-stu-id="b3d0b-173">Element</span></span>|<span data-ttu-id="b3d0b-174">Описание</span><span class="sxs-lookup"><span data-stu-id="b3d0b-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|<span data-ttu-id="b3d0b-175">Определяет параметры безопасности привязки.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-175">Defines the security settings for the binding.</span></span> <span data-ttu-id="b3d0b-176">Это элемент типа <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-176">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="b3d0b-177">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-177">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b3d0b-178">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-178">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3d0b-179">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b3d0b-179">Parent Elements</span></span>  
  
|<span data-ttu-id="b3d0b-180">Элемент</span><span class="sxs-lookup"><span data-stu-id="b3d0b-180">Element</span></span>|<span data-ttu-id="b3d0b-181">Описание</span><span class="sxs-lookup"><span data-stu-id="b3d0b-181">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="b3d0b-182">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3d0b-183">Примечания</span><span class="sxs-lookup"><span data-stu-id="b3d0b-183">Remarks</span></span>  
 <span data-ttu-id="b3d0b-184">Привязка NetHttpsBinding использует протокол HTTPS в качестве транспорта для отправки сообщений.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-184">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="b3d0b-185">При использовании с дуплексным контрактом будут использоваться веб-сокеты.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-185">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="b3d0b-186">При использовании контракта типа «запрос-ответ» привязка NetHttpsBinding будет работать как BasicHttpsBinding с двоичным кодировщиком.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-186">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="b3d0b-187">По умолчанию безопасность отключена, но может быть добавлена установка для атрибута Mode [\<security>](security-of-basichttpbinding.md) дочернего элемента значения, отличного от `None` .</span><span class="sxs-lookup"><span data-stu-id="b3d0b-187">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="b3d0b-188">По умолчанию используется кодировка сообщений «Text» и кодировка текста «UTF-8».</span><span class="sxs-lookup"><span data-stu-id="b3d0b-188">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3d0b-189">Пример</span><span class="sxs-lookup"><span data-stu-id="b3d0b-189">Example</span></span>  
 <span data-ttu-id="b3d0b-190">В следующем примере показано использование привязки <xref:System.ServiceModel.NetHttpBinding>, которая обеспечивает связь по протоколу HTTPS и максимальные возможности взаимодействия с веб-службами первого и второго поколений.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-190">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="b3d0b-191">Привязка задается в файлах конфигурации для клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-191">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="b3d0b-192">Тип привязки задан в атрибуте `binding` элемента `<endpoint>`.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-192">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="b3d0b-193">Если необходимо настроить основную привязку и изменить некоторые из ее параметров, необходимо определить конфигурацию привязки.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-193">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="b3d0b-194">Конечная точка должна ссылаться на конфигурацию привязки по имени с помощью атрибута `bindingConfiguration` элемента `<endpoint>`, как показано в следующем примере кода конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-194">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a><span data-ttu-id="b3d0b-195">Пример</span><span class="sxs-lookup"><span data-stu-id="b3d0b-195">Example</span></span>  
 <span data-ttu-id="b3d0b-196">Начиная с .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-196">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b3d0b-197">Функции из предыдущего примера можно выполнить, удалив bindingConfiguration из адреса конечной точки и имени из привязки.</span><span class="sxs-lookup"><span data-stu-id="b3d0b-197">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name from the binding.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpsBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpsBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Binary"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpsBinding>
  </bindings>
</system.serviceModel>
```  
  
 <span data-ttu-id="b3d0b-198">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b3d0b-198">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d0b-199">См. также</span><span class="sxs-lookup"><span data-stu-id="b3d0b-199">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="b3d0b-200">Привязки</span><span class="sxs-lookup"><span data-stu-id="b3d0b-200">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b3d0b-201">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="b3d0b-201">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b3d0b-202">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="b3d0b-202">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
