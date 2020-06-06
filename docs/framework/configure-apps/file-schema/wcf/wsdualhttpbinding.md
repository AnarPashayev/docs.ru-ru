---
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 01360ae8288b3cb7374597ad77935f634eb0a519
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139280"
---
# \<wsDualHttpBinding>
<span data-ttu-id="67502-101">Определяет безопасную, надежную привязку с возможностью взаимодействия, которая подходит для дуплексных контрактов службы или связи посредством посредников протокола SOAP.</span><span class="sxs-lookup"><span data-stu-id="67502-101">Defines a secure, reliable and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsDualHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="67502-102">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="67502-102">Syntax</span></span>  
  
```xml  
<wsDualHttpBinding>
  <binding name="String"
          closeTimeout="TimeSpan"
          openTimeout="TimeSpan"
          receiveTimeout="TimeSpan"
          sendTimeout="TimeSpan"
          bypassProxyOnLocal="Boolean"
          clientBaseAddress="URI"
          transactionFlow="Boolean"
          hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
          maxBufferPoolSize="integer"
          maxReceivedMessageSize="Integer"
          messageEncoding="Text/Mtom"
          proxyAddress="URI"
          textEncoding="Unicode/BigEndianUnicode/UTF8"
          useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan" />
    <security mode="None/Message">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsDualHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67502-103">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="67502-103">Attributes and Elements</span></span>  
 <span data-ttu-id="67502-104">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="67502-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67502-105">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="67502-105">Attributes</span></span>  
  
|<span data-ttu-id="67502-106">Атрибут</span><span class="sxs-lookup"><span data-stu-id="67502-106">Attribute</span></span>|<span data-ttu-id="67502-107">Описание:</span><span class="sxs-lookup"><span data-stu-id="67502-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67502-108">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="67502-108">bypassProxyOnLocal</span></span>|<span data-ttu-id="67502-109">Логическое значение, определяющее, будет ли выполняться обход прокси-сервера для локальных адресов.</span><span class="sxs-lookup"><span data-stu-id="67502-109">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="67502-110">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="67502-110">The default is `false`.</span></span>|  
|<span data-ttu-id="67502-111">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="67502-111">clientBaseAddress</span></span>|<span data-ttu-id="67502-112">Универсальный код ресурса (URI), задающий базовый адрес, который клиент прослушивает для получения сообщений ответа от службы.</span><span class="sxs-lookup"><span data-stu-id="67502-112">A URI that sets the base address that the client listens to for response messages from the service.</span></span> <span data-ttu-id="67502-113">Если значение задано, для прослушивания используется этот адрес (плюс per-channelGUID).</span><span class="sxs-lookup"><span data-stu-id="67502-113">If specified, this address (plus a per-channelGUID) is used for listening.</span></span> <span data-ttu-id="67502-114">Если значение не задано, базовый адрес клиента создается в соответствии с транспортом.</span><span class="sxs-lookup"><span data-stu-id="67502-114">If the value is not specified, the client base address is generated in a transport-specific manner.</span></span> <span data-ttu-id="67502-115">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="67502-115">The default is `null`.</span></span>|  
|<span data-ttu-id="67502-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="67502-116">closeTimeout</span></span>|<span data-ttu-id="67502-117">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="67502-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="67502-118">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="67502-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="67502-119">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="67502-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="67502-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="67502-120">hostnameComparisonMode</span></span>|<span data-ttu-id="67502-121">Задает режим сравнения имен узлов HTTP для анализа универсальных кодов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="67502-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="67502-122">Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="67502-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="67502-123">Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.</span><span class="sxs-lookup"><span data-stu-id="67502-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="67502-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="67502-124">maxBufferPoolSize</span></span>|<span data-ttu-id="67502-125">Целое число, задающее максимальный размер буферного пула для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="67502-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="67502-126">Значение по умолчанию - 524 288 байт (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="67502-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="67502-127">Многие элементы Windows Communication Foundation (WCF) используют буферы.</span><span class="sxs-lookup"><span data-stu-id="67502-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="67502-128">При создании буферов и их уничтожении после каждого использования расходуется слишком много ресурсов; при сборке мусора для буферов также расходуется слишком много ресурсов.</span><span class="sxs-lookup"><span data-stu-id="67502-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="67502-129">Буферные пулы позволяют брать буфер из пула, использовать его, а затем возвращать обратно, когда он больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="67502-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="67502-130">Это позволяет избежать излишней нагрузки, связанной с созданием и уничтожением буферов.</span><span class="sxs-lookup"><span data-stu-id="67502-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="67502-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="67502-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="67502-132">Положительное целое число, задающее, в байтах, максимальный размер сообщения (включая заголовки), которое можно получить по каналу, настроенному с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="67502-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="67502-133">Отправитель сообщения, превышающего это ограничение, получит ошибку SOAP.</span><span class="sxs-lookup"><span data-stu-id="67502-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="67502-134">Получатель отклоняет сообщение и создает запись о событии в журнале трассировки.</span><span class="sxs-lookup"><span data-stu-id="67502-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="67502-135">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="67502-135">The default is 65536.</span></span>|  
|<span data-ttu-id="67502-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="67502-136">messageEncoding</span></span>|<span data-ttu-id="67502-137">Определяет кодировщик, используемый для кодировки сообщения.</span><span class="sxs-lookup"><span data-stu-id="67502-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="67502-138">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="67502-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="67502-139">-Text: использование кодировщика текстовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="67502-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="67502-140">-MTOM: используйте кодировщик обмена сообщениями, механизм передачи сообщений 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="67502-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="67502-141">— Значение по умолчанию — Text.</span><span class="sxs-lookup"><span data-stu-id="67502-141">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="67502-142">Это атрибут типа <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="67502-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="67502-143">name</span><span class="sxs-lookup"><span data-stu-id="67502-143">name</span></span>|<span data-ttu-id="67502-144">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="67502-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="67502-145">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="67502-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="67502-146">Начиная с .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="67502-146">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="67502-147">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="67502-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="67502-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="67502-148">openTimeout</span></span>|<span data-ttu-id="67502-149">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="67502-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="67502-150">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="67502-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="67502-151">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="67502-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="67502-152">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="67502-152">proxyAddress</span></span>|<span data-ttu-id="67502-153">Универсальный код ресурса (URI), задающий адрес прокси-сервера HTTP.</span><span class="sxs-lookup"><span data-stu-id="67502-153">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="67502-154">Если параметр `useDefaultWebProxy` имеет значение `true`, данный параметр должен иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="67502-154">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="67502-155">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="67502-155">The default is `null`.</span></span>|  
|<span data-ttu-id="67502-156">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="67502-156">receiveTimeout</span></span>|<span data-ttu-id="67502-157">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="67502-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="67502-158">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="67502-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="67502-159">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="67502-159">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="67502-160">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="67502-160">sendTimeout</span></span>|<span data-ttu-id="67502-161">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="67502-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="67502-162">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="67502-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="67502-163">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="67502-163">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="67502-164">textEncoding</span><span class="sxs-lookup"><span data-stu-id="67502-164">textEncoding</span></span>|<span data-ttu-id="67502-165">Задает кодировку, используемую при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="67502-165">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="67502-166">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="67502-166">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="67502-167">-BigEndianUnicode: Юникод байтов Encoding.</span><span class="sxs-lookup"><span data-stu-id="67502-167">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="67502-168">-Unicode: 16-разрядная кодировка.</span><span class="sxs-lookup"><span data-stu-id="67502-168">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="67502-169">-UTF8:8-разрядная кодировка</span><span class="sxs-lookup"><span data-stu-id="67502-169">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="67502-170">По умолчанию используется значение UTF8.</span><span class="sxs-lookup"><span data-stu-id="67502-170">The default is UTF8.</span></span> <span data-ttu-id="67502-171">Это атрибут типа <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="67502-171">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="67502-172">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="67502-172">transactionFlow</span></span>|<span data-ttu-id="67502-173">Логическое значение, определяющее, поддерживает ли привязка потоковые спецификации WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="67502-173">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="67502-174">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="67502-174">The default is `false`.</span></span>|  
|<span data-ttu-id="67502-175">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="67502-175">useDefaultWebProxy</span></span>|<span data-ttu-id="67502-176">Логическое значение, указывающее, должен ли использоваться автоматически настроенный системный прокси-сервер HTTP.</span><span class="sxs-lookup"><span data-stu-id="67502-176">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="67502-177">Если данный атрибут имеет значение `null`, прокси-адрес должен быть равен `true` (то есть не задан).</span><span class="sxs-lookup"><span data-stu-id="67502-177">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="67502-178">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="67502-178">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67502-179">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="67502-179">Child Elements</span></span>  
  
|<span data-ttu-id="67502-180">Элемент</span><span class="sxs-lookup"><span data-stu-id="67502-180">Element</span></span>|<span data-ttu-id="67502-181">Описание</span><span class="sxs-lookup"><span data-stu-id="67502-181">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsdualhttpbinding.md)|<span data-ttu-id="67502-182">Определяет параметры безопасности привязки.</span><span class="sxs-lookup"><span data-stu-id="67502-182">Defines the security settings for the binding.</span></span> <span data-ttu-id="67502-183">Это элемент типа <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="67502-183">This element is of type <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="67502-184">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="67502-184">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="67502-185">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="67502-185">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="67502-186">Указывает, устанавливаются ли между конечными точками канала надежные сеансы.</span><span class="sxs-lookup"><span data-stu-id="67502-186">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67502-187">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="67502-187">Parent Elements</span></span>  
  
|<span data-ttu-id="67502-188">Элемент</span><span class="sxs-lookup"><span data-stu-id="67502-188">Element</span></span>|<span data-ttu-id="67502-189">Описание</span><span class="sxs-lookup"><span data-stu-id="67502-189">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="67502-190">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="67502-190">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67502-191">Примечания</span><span class="sxs-lookup"><span data-stu-id="67502-191">Remarks</span></span>  
 <span data-ttu-id="67502-192">Объект `WSDualHttpBinding` предоставляет такую же поддержку протоколам веб-служб, как и объект `WSHttpBinding`, но применяется для дуплексных контрактов.</span><span class="sxs-lookup"><span data-stu-id="67502-192">The `WSDualHttpBinding` provides the same support for Web Service protocols as the `WSHttpBinding`, but for use with duplex contracts.</span></span> <span data-ttu-id="67502-193">`WSDualHttpBinding` поддерживает только безопасность SOAP и требует надежного обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="67502-193">`WSDualHttpBinding` only supports SOAP security and requires reliable messaging.</span></span> <span data-ttu-id="67502-194">Для этой привязки необходимо, чтобы клиент имел открытый универсальный код ресурса (URI), предоставляющий конечную точку обратного вызова для службы.</span><span class="sxs-lookup"><span data-stu-id="67502-194">This binding requires that the client has a public URI that provides a callback endpoint for the service.</span></span> <span data-ttu-id="67502-195">Это обеспечивается атрибутом `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="67502-195">This is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="67502-196">Двойная привязка предоставляет службе IP-адрес клиента.</span><span class="sxs-lookup"><span data-stu-id="67502-196">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="67502-197">Клиенту следует использовать механизм безопасности, чтобы гарантировать, что подключение выполняется только к доверенным службам.</span><span class="sxs-lookup"><span data-stu-id="67502-197">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
 <span data-ttu-id="67502-198">Эту привязку можно использовать для надежной связи посредством одного или нескольких посредников протокола SOAP.</span><span class="sxs-lookup"><span data-stu-id="67502-198">This binding can be used to communicate reliably through one or more SOAP intermediaries.</span></span>  
  
 <span data-ttu-id="67502-199">По умолчанию эта привязка создает стек времени выполнения с WS-ReliableMessaging для надежности, WS-Security для безопасности и проверки подлинности сообщений, HTTP для доставки сообщений и кодировкой сообщений Text/XML.</span><span class="sxs-lookup"><span data-stu-id="67502-199">By default, this binding generates a runtime stack with WS-ReliableMessaging for reliability, WS-Security for message security and authentication, HTTP for message delivery, and a Text/XML message encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67502-200">Пример</span><span class="sxs-lookup"><span data-stu-id="67502-200">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsDualHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 clientBaseAddress="http://localhost:8001/client/"
                 transactionFlow="true"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00" />
          <security mode="None">
            <message clientCredentialType="None"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128" />
          </security>
        </binding>
      </wsDualHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="67502-201">См. также</span><span class="sxs-lookup"><span data-stu-id="67502-201">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [<span data-ttu-id="67502-202">Привязки</span><span class="sxs-lookup"><span data-stu-id="67502-202">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="67502-203">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="67502-203">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="67502-204">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="67502-204">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
