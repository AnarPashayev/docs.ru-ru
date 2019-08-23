---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 3c4edc17fd669fbe23ec38ff26a61e867c04c561
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915066"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="a5256-101">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a5256-101">\<wsFederationHttpBinding></span></span>

<span data-ttu-id="a5256-102">Определяет привязку, которая поддерживает спецификацию WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="a5256-102">Defines a binding that supports WS-Federation.</span></span>

<span data-ttu-id="a5256-103">\<системой. ServiceModel > </span><span class="sxs-lookup"><span data-stu-id="a5256-103">\<system.ServiceModel></span></span>\
<span data-ttu-id="a5256-104">\<привязки > </span><span class="sxs-lookup"><span data-stu-id="a5256-104">\<bindings></span></span>\
<span data-ttu-id="a5256-105">wsFederationBinding, элемент</span><span class="sxs-lookup"><span data-stu-id="a5256-105">wsFederationBinding element</span></span>

## <a name="syntax"></a><span data-ttu-id="a5256-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a5256-106">Syntax</span></span>

```xml
<wsFederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsFederationBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5256-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a5256-107">Attributes and Elements</span></span>

<span data-ttu-id="a5256-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a5256-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5256-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a5256-109">Attributes</span></span>

|<span data-ttu-id="a5256-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a5256-110">Attribute</span></span>|<span data-ttu-id="a5256-111">Описание</span><span class="sxs-lookup"><span data-stu-id="a5256-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a5256-112">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="a5256-112">bypassProxyOnLocal</span></span>|<span data-ttu-id="a5256-113">Логическое значение, определяющее, будет ли выполняться обход прокси-сервера для локальных адресов.</span><span class="sxs-lookup"><span data-stu-id="a5256-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="a5256-114">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="a5256-114">The default is `false`.</span></span>|
|<span data-ttu-id="a5256-115">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="a5256-115">closeTimeout</span></span>|<span data-ttu-id="a5256-116">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="a5256-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a5256-117">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a5256-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a5256-118">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a5256-118">The default is 00:01:00.</span></span>|
|<span data-ttu-id="a5256-119">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="a5256-119">hostnameComparisonMode</span></span>|<span data-ttu-id="a5256-120">Задает режим сравнения имен узлов HTTP для анализа универсальных кодов ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="a5256-120">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="a5256-121">Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI).</span><span class="sxs-lookup"><span data-stu-id="a5256-121">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="a5256-122">Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.</span><span class="sxs-lookup"><span data-stu-id="a5256-122">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="a5256-123">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a5256-123">maxBufferPoolSize</span></span>|<span data-ttu-id="a5256-124">Целое число, задающее максимальный размер буферного пула для этой привязки.</span><span class="sxs-lookup"><span data-stu-id="a5256-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="a5256-125">Значение по умолчанию - 524 288 байт (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="a5256-125">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="a5256-126">Многие элементы Windows Communication Foundation (WCF) используют буферы.</span><span class="sxs-lookup"><span data-stu-id="a5256-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="a5256-127">При создании буферов и их уничтожении после каждого использования расходуется слишком много ресурсов; при сборке мусора для буферов также расходуется слишком много ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a5256-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="a5256-128">Буферные пулы позволяют брать буфер из пула, использовать его, а затем возвращать обратно, когда он больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="a5256-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="a5256-129">Это позволяет избежать излишней нагрузки, связанной с созданием и уничтожением буферов.</span><span class="sxs-lookup"><span data-stu-id="a5256-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="a5256-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a5256-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="a5256-131">Положительное целое число, задающее, в байтах, максимальный размер сообщения (включая заголовки), которое можно получить по каналу, настроенному с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="a5256-131">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="a5256-132">Отправитель сообщения, превышающего это ограничение, получит ошибку SOAP.</span><span class="sxs-lookup"><span data-stu-id="a5256-132">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="a5256-133">Получатель отклоняет сообщение и создает запись о событии в журнале трассировки.</span><span class="sxs-lookup"><span data-stu-id="a5256-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a5256-134">Значение по умолчанию — 65536.</span><span class="sxs-lookup"><span data-stu-id="a5256-134">The default is 65536.</span></span>|
|<span data-ttu-id="a5256-135">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="a5256-135">messageEncoding</span></span>|<span data-ttu-id="a5256-136">Определяет кодировщик, используемый для кодировки сообщения.</span><span class="sxs-lookup"><span data-stu-id="a5256-136">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="a5256-137">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="a5256-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a5256-138">Полнотекстовым Использование кодировщика текстовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="a5256-138">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="a5256-139">MTOM Используйте кодировщик обмена сообщениями с механизмом 1,0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="a5256-139">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="a5256-140">Значение по умолчанию - Text.</span><span class="sxs-lookup"><span data-stu-id="a5256-140">The default is Text.</span></span><br /><br /> <span data-ttu-id="a5256-141">Это атрибут типа <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="a5256-141">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="a5256-142">имя</span><span class="sxs-lookup"><span data-stu-id="a5256-142">name</span></span>|<span data-ttu-id="a5256-143">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="a5256-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a5256-144">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="a5256-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a5256-145">Начиная с версии [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] для привязок и поведений необязательно задавать имена.</span><span class="sxs-lookup"><span data-stu-id="a5256-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a5256-146">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a5256-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="a5256-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="a5256-147">openTimeout</span></span>|<span data-ttu-id="a5256-148">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="a5256-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a5256-149">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a5256-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a5256-150">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a5256-150">The default is 00:01:00.</span></span>|
|<span data-ttu-id="a5256-151">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="a5256-151">privacyNoticeAt</span></span>|<span data-ttu-id="a5256-152">Строка, задающая универсальный код ресурса (URI), определяющий расположение примечания о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="a5256-152">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="a5256-153">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="a5256-153">privacyNoticeVersion</span></span>|<span data-ttu-id="a5256-154">Целое число, определяющее версию текущего уведомления о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="a5256-154">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="a5256-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="a5256-155">proxyAddress</span></span>|<span data-ttu-id="a5256-156">Универсальный код ресурса (URI), задающий адрес прокси-сервера HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5256-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="a5256-157">Если параметр `useDefaultWebProxy` имеет значение `true`, данный параметр должен иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="a5256-157">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="a5256-158">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="a5256-158">The default is `null`.</span></span>|
|<span data-ttu-id="a5256-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="a5256-159">receiveTimeout</span></span>|<span data-ttu-id="a5256-160">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="a5256-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a5256-161">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a5256-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a5256-162">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a5256-162">The default is 00:10:00.</span></span>|
|<span data-ttu-id="a5256-163">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="a5256-163">sendTimeout</span></span>|<span data-ttu-id="a5256-164">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="a5256-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a5256-165">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a5256-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a5256-166">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a5256-166">The default is 00:01:00.</span></span>|
|<span data-ttu-id="a5256-167">textEncoding</span><span class="sxs-lookup"><span data-stu-id="a5256-167">textEncoding</span></span>|<span data-ttu-id="a5256-168">Задает кодировку, используемую при отправке сообщений через привязку.</span><span class="sxs-lookup"><span data-stu-id="a5256-168">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="a5256-169">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="a5256-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a5256-170">BigEndianUnicode Кодировка байтов Юникода.</span><span class="sxs-lookup"><span data-stu-id="a5256-170">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="a5256-171">Юникод 16-разрядная кодировка.</span><span class="sxs-lookup"><span data-stu-id="a5256-171">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="a5256-172">ОБРАТНО 8-разрядная кодировка</span><span class="sxs-lookup"><span data-stu-id="a5256-172">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="a5256-173">Значение по умолчанию - UTF8.</span><span class="sxs-lookup"><span data-stu-id="a5256-173">The default is UTF8.</span></span> <span data-ttu-id="a5256-174">Это атрибут типа <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="a5256-174">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="a5256-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="a5256-175">transactionFlow</span></span>|<span data-ttu-id="a5256-176">Логическое значение, определяющее, поддерживает ли привязка потоковые спецификации WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="a5256-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="a5256-177">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="a5256-177">The default is `false`.</span></span>|
|<span data-ttu-id="a5256-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="a5256-178">useDefaultWebProxy</span></span>|<span data-ttu-id="a5256-179">Логическое значение, указывающее, должен ли использоваться автоматически настроенный системный прокси-сервер HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5256-179">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="a5256-180">Если данный атрибут имеет значение `null`, прокси-адрес должен быть равен `true` (то есть не задан).</span><span class="sxs-lookup"><span data-stu-id="a5256-180">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="a5256-181">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="a5256-181">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a5256-182">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a5256-182">Child Elements</span></span>

|<span data-ttu-id="a5256-183">Элемент</span><span class="sxs-lookup"><span data-stu-id="a5256-183">Element</span></span>|<span data-ttu-id="a5256-184">Описание</span><span class="sxs-lookup"><span data-stu-id="a5256-184">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5256-185">\<> безопасности</span><span class="sxs-lookup"><span data-stu-id="a5256-185">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="a5256-186">Определяет параметры безопасности сообщения.</span><span class="sxs-lookup"><span data-stu-id="a5256-186">Defines the security settings for the message.</span></span> <span data-ttu-id="a5256-187">Это элемент типа <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a5256-187">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="a5256-188">[\<Реадеркуотас >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a5256-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="a5256-189">Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки.</span><span class="sxs-lookup"><span data-stu-id="a5256-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a5256-190">Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a5256-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="a5256-191">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a5256-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="a5256-192">Указывает, устанавливаются ли между конечными точками канала надежные сеансы.</span><span class="sxs-lookup"><span data-stu-id="a5256-192">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a5256-193">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a5256-193">Parent Elements</span></span>

|<span data-ttu-id="a5256-194">Элемент</span><span class="sxs-lookup"><span data-stu-id="a5256-194">Element</span></span>|<span data-ttu-id="a5256-195">Описание</span><span class="sxs-lookup"><span data-stu-id="a5256-195">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5256-196">\<привязки ></span><span class="sxs-lookup"><span data-stu-id="a5256-196">\<bindings></span></span>](bindings.md)|<span data-ttu-id="a5256-197">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="a5256-197">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a5256-198">Примечания</span><span class="sxs-lookup"><span data-stu-id="a5256-198">Remarks</span></span>

<span data-ttu-id="a5256-199">Федерация - это возможность совместного использования удостоверений в нескольких системах в целях проверки подлинности и авторизации.</span><span class="sxs-lookup"><span data-stu-id="a5256-199">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="a5256-200">Эти удостоверения могут ссылаться на пользователей или на компьютеры.</span><span class="sxs-lookup"><span data-stu-id="a5256-200">These identities can refer to users or to machines.</span></span> <span data-ttu-id="a5256-201">Федеративный протокол HTTP поддерживает безопасность SOAP и безопасность в смешанном режиме, но не поддерживает использование исключительно безопасности транспорта.</span><span class="sxs-lookup"><span data-stu-id="a5256-201">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="a5256-202">Эта привязка обеспечивает поддержку Windows Communication Foundation (WCF) для протокола WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="a5256-202">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="a5256-203">Службы, настроенные с использованием этой привязки, должны использовать транспорт HTTP.</span><span class="sxs-lookup"><span data-stu-id="a5256-203">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="a5256-204">Привязки состоят из стека элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="a5256-204">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="a5256-205">Стек элементов привязки в</span><span class="sxs-lookup"><span data-stu-id="a5256-205">The stack of binding elements in</span></span>

<span data-ttu-id="a5256-206">`wsFederationHttpBinding` идентичен тому, что содержится в `wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="a5256-206">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="a5256-207"><xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>если [ \<для > безопасности](security-of-wsfederationhttpbinding.md) задано значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a5256-207">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="a5256-208">Элемент управления определяет сведения о параметрах безопасности сообщений в [ \<> сообщений.](message-element-of-wsfederationhttpbinding.md) `wsFederationHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="a5256-208">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="a5256-209">Обратите внимание, что [ \<элемент Security >](security-of-wsfederationhttpbinding.md) предоставляет доступ get только в том случае, если безопасность, используемая привязкой, не может быть изменена после создания привязки.</span><span class="sxs-lookup"><span data-stu-id="a5256-209">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="a5256-210">`wsFederationHttpBinding` Также предоставляет атрибут привацинотицеат для задания и получения универсального кода ресурса (URI), в котором находится уведомление о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="a5256-210">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="a5256-211">Обеспечение безопасности политики особенно важно в федеративных сценариях.</span><span class="sxs-lookup"><span data-stu-id="a5256-211">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="a5256-212">Для защиты политики от злоумышленников рекомендуется использовать определенную систему безопасности, например протокол HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a5256-212">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="a5256-213">В федеративных сценариях с использованием этой привязки политика службы потенциально содержит важные сведения, например ключ для шифрования выдаваемого маркера (SAML), тип утверждений, помещаемых в маркер, и так далее.</span><span class="sxs-lookup"><span data-stu-id="a5256-213">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="a5256-214">Если политика подделана, атакующий может обнаружить ключ выданного маркера, что приводит к дальнейшим подделкам, раскрытию сведений и другим вредоносным действиям.</span><span class="sxs-lookup"><span data-stu-id="a5256-214">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="a5256-215">Чтобы предупредить злонамеренные действия, политика должна быть получена от службы безопасным способом (например, с помощью протокола HTTPS).</span><span class="sxs-lookup"><span data-stu-id="a5256-215">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="a5256-216">Дополнительные сведения об этой привязке см. [в разделе как Создайте WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a5256-216">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="a5256-217">Пример</span><span class="sxs-lookup"><span data-stu-id="a5256-217">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsFederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="saml"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </wsFederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a5256-218">См. также</span><span class="sxs-lookup"><span data-stu-id="a5256-218">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="a5256-219">Практическое руководство. Создание WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a5256-219">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="a5256-220">Привязки</span><span class="sxs-lookup"><span data-stu-id="a5256-220">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a5256-221">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="a5256-221">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a5256-222">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="a5256-222">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a5256-223">\<Привязка ></span><span class="sxs-lookup"><span data-stu-id="a5256-223">\<binding></span></span>](../../../misc/binding.md)
