---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 5f35029806172c3abe639052798c0a018e8514f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158608"
---
# \<ws2007HttpBinding>

<span data-ttu-id="1f520-101">Определяет привязку с возможностью взаимодействия, которая обеспечивает поддержку для правильных версий элементов привязки <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession> и <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f520-101">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="1f520-102">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f520-102">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f520-103">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1f520-103">Attributes and Elements</span></span>  

 <span data-ttu-id="1f520-104">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1f520-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f520-105">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1f520-105">Attributes</span></span>  
  
|<span data-ttu-id="1f520-106">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1f520-106">Attribute</span></span>|<span data-ttu-id="1f520-107">Описание</span><span class="sxs-lookup"><span data-stu-id="1f520-107">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="1f520-108">Значение, определяющее, принимает ли клиент файлы Cookie и распространяет ли он их на будущие запросы.</span><span class="sxs-lookup"><span data-stu-id="1f520-108">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="1f520-109">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="1f520-109">The default is `false`.</span></span><br /><br /> <span data-ttu-id="1f520-110">Это свойство можно использовать при взаимодействии с веб-службами ASP.NET (ASMX), которые используют файлы Cookie.</span><span class="sxs-lookup"><span data-stu-id="1f520-110">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="1f520-111">Это гарантирует, что эти файлы Cookie, возвращаемые с сервера, автоматически копируются во все последующие клиентские запросы к этой службе.</span><span class="sxs-lookup"><span data-stu-id="1f520-111">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="1f520-112">Значение, определяющее, будет ли выполняться обход прокси-сервера для локальных адресов.</span><span class="sxs-lookup"><span data-stu-id="1f520-112">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="1f520-113">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="1f520-113">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="1f520-114">Значение <xref:System.TimeSpan>, которое задает длительность временного интервала для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="1f520-114">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="1f520-115">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1f520-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f520-116">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1f520-116">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="1f520-117">Задает режим сравнения имен узлов HTTP для анализа универсальных идентификаторов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="1f520-117">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="1f520-118">Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="1f520-118">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="1f520-119">Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.</span><span class="sxs-lookup"><span data-stu-id="1f520-119">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="1f520-120">Максимальный размер буферного пула для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="1f520-120">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="1f520-121">Значение по умолчанию - 524 288 байт (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="1f520-121">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="1f520-122">Многие элементы Windows Communication Foundation (WCF) используют буферы.</span><span class="sxs-lookup"><span data-stu-id="1f520-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="1f520-123">Создание буферов при каждом использовании и их последующее уничтожение требует слишком много ресурсов; также много ресурсов расходуется при сборке мусора для буферов.</span><span class="sxs-lookup"><span data-stu-id="1f520-123">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="1f520-124">Буферные пулы позволяют забирать буфер из пула, использовать его, а затем возвращать обратно, когда он больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="1f520-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="1f520-125">Это позволяет избежать излишней нагрузки, связанной с созданием и уничтожением буферов.</span><span class="sxs-lookup"><span data-stu-id="1f520-125">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="1f520-126">Максимальный размер сообщения (в байтах), включая заголовки, которое можно получить по каналу, настроенному с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="1f520-126">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="1f520-127">Отправитель сообщения, которое превысит это ограничение, получает ошибку протокола SOAP.</span><span class="sxs-lookup"><span data-stu-id="1f520-127">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="1f520-128">Получатель отклоняет сообщение и создает запись о событии в журнале трассировки.</span><span class="sxs-lookup"><span data-stu-id="1f520-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1f520-129">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="1f520-129">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="1f520-130">Определяет кодировщик, используемый для кодировки сообщения.</span><span class="sxs-lookup"><span data-stu-id="1f520-130">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="1f520-131">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="1f520-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1f520-132">-   `Text`: Используйте кодировщик текстовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="1f520-132">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="1f520-133">-   `Mtom`: Используйте кодировщик обмена сообщениями с механизмом 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="1f520-133">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="1f520-134">Значение по умолчанию — `Text`.</span><span class="sxs-lookup"><span data-stu-id="1f520-134">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="1f520-135">Это атрибут типа <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="1f520-135">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="1f520-136">Имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="1f520-136">The configuration name of the binding.</span></span> <span data-ttu-id="1f520-137">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="1f520-137">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1f520-138">Начиная с .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="1f520-138">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1f520-139">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1f520-139">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1f520-140">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="1f520-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1f520-141">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1f520-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f520-142">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1f520-142">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="1f520-143">Универсальный код ресурса (URI), задающий адрес прокси-сервера HTTP.</span><span class="sxs-lookup"><span data-stu-id="1f520-143">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="1f520-144">Если параметр `useSystemWebProxy` имеет значение `true`, данный параметр должен иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="1f520-144">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="1f520-145">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="1f520-145">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1f520-146">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="1f520-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1f520-147">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1f520-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f520-148">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1f520-148">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1f520-149">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="1f520-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1f520-150">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1f520-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f520-151">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1f520-151">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="1f520-152">Задает кодировку, используемую при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="1f520-152">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="1f520-153">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="1f520-153">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1f520-154">-   `UnicodeFffeTextEncoding`: Кодировка с обратным порядком байтов Юникода.</span><span class="sxs-lookup"><span data-stu-id="1f520-154">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="1f520-155">-   `Utf16TextEncoding`: 16-разрядная кодировка.</span><span class="sxs-lookup"><span data-stu-id="1f520-155">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="1f520-156">-   `Utf8TextEncoding`: 8-разрядная кодировка.</span><span class="sxs-lookup"><span data-stu-id="1f520-156">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="1f520-157">Значение по умолчанию — `Utf8TextEncoding`.</span><span class="sxs-lookup"><span data-stu-id="1f520-157">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="1f520-158">Это атрибут типа <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="1f520-158">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="1f520-159">Значение, определяющее, поддерживает ли привязка потоки WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="1f520-159">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="1f520-160">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="1f520-160">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="1f520-161">Значение, определяющее, должен ли использоваться автоматически настроенный системный прокси-сервер HTTP.</span><span class="sxs-lookup"><span data-stu-id="1f520-161">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="1f520-162">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="1f520-162">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f520-163">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1f520-163">Child Elements</span></span>  
  
|<span data-ttu-id="1f520-164">Элемент</span><span class="sxs-lookup"><span data-stu-id="1f520-164">Element</span></span>|<span data-ttu-id="1f520-165">Описание</span><span class="sxs-lookup"><span data-stu-id="1f520-165">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="1f520-166">Определяет параметры безопасности привязки.</span><span class="sxs-lookup"><span data-stu-id="1f520-166">Defines the security settings for the binding.</span></span> <span data-ttu-id="1f520-167">Это элемент типа <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="1f520-167">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="1f520-168">Определяет ограничения по сложности сообщений протокола SOAP, которые могут обрабатываться конечными точками, настроенными с помощью этой привязки.</span><span class="sxs-lookup"><span data-stu-id="1f520-168">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="1f520-169">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="1f520-169">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="1f520-170">Указывает, устанавливаются ли между конечными точками канала надежные сеансы.</span><span class="sxs-lookup"><span data-stu-id="1f520-170">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f520-171">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1f520-171">Parent Elements</span></span>  
  
|<span data-ttu-id="1f520-172">Элемент</span><span class="sxs-lookup"><span data-stu-id="1f520-172">Element</span></span>|<span data-ttu-id="1f520-173">Описание</span><span class="sxs-lookup"><span data-stu-id="1f520-173">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="1f520-174">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="1f520-174">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f520-175">Remarks</span><span class="sxs-lookup"><span data-stu-id="1f520-175">Remarks</span></span>  

 <span data-ttu-id="1f520-176">Привязка `WS2007HttpBinding` добавляет системную привязку, аналогичную `WSHttpBinding`, однако использует версии OASIS протоколов ReliableSession, Security и TransactionFlow.</span><span class="sxs-lookup"><span data-stu-id="1f520-176">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="1f520-177">При использовании этой привязки изменение объектной модели или настроек по умолчанию не требуется.</span><span class="sxs-lookup"><span data-stu-id="1f520-177">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f520-178">Пример</span><span class="sxs-lookup"><span data-stu-id="1f520-178">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="1f520-179">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1f520-179">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="1f520-180">Привязки</span><span class="sxs-lookup"><span data-stu-id="1f520-180">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1f520-181">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="1f520-181">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1f520-182">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="1f520-182">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
