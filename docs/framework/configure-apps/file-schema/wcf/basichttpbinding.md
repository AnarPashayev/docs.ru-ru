---
title: <basicHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
ms.openlocfilehash: d62746ad55b5e6a7cd9300a5f534e4ecd2d5d81e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090437"
---
# <a name="basichttpbinding"></a>\<basicHttpBinding >
Представляет привязку, которую служба Windows Communication Foundation (WCF) может использовать для настройки и предоставления конечных точек, способных связываться с веб-службами на основе ASMX, а также клиентами и другими службами, соответствующими WS-I Basic Profile 1.1.  
  
 \<system.ServiceModel>  
\<привязки >  
\<basicHttpBinding >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<basicHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           envelopeVersion="None/Soap11/Soap12"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="String"
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
                 realm="String" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`allowCookies`|Логическое значение, определяющее, принимает ли клиент файлы Cookie и распространяет ли он их на будущие запросы. Значение по умолчанию — `false`.<br /><br /> Это свойство можно использовать при взаимодействии с веб-службами ASMX, которые используют файлы Cookie. В этом случае можно быть уверенным, что файлы cookie, возвращаемые с сервера, автоматически копируются во все последующие клиентские запросы к этой службе.|  
|`bypassProxyOnLocal`|Логическое значение, определяющее, будет ли выполняться обход прокси-сервера для локальных адресов. Значение по умолчанию — `false`.<br /><br /> Интернет-ресурс является локальным, если у него локальный адрес. Локальный адрес — это задача, которая находится на одном компьютере, локальной сети или в интрасети и является, синтаксически идентифицируемый отсутствием точки (.) как URL-адреса « http://webserver/ » и « http://localhost/ ».<br /><br /> Этот атрибут определяет, будут ли конечные точки, настроенные с помощью привязки BasicHttpBinding, использовать прокси-сервер при доступе к локальным ресурсам. Если значение этого атрибута `true`, запросы к локальным интернет-ресурсам не используют прокси-сервер. Используйте имя узла (а не localhost), если необходимо, чтобы клиенты проходили через прокси-сервер при взаимодействии со службами на том же компьютере, когда для этого атрибута задано значение `true`.<br /><br /> Если атрибут имеет значение `false`, все интернет-запросы выполняются через данный прокси-сервер.|  
|`closeTimeout`|Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия. Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>. Значение по умолчанию - 00:01:00.|  
|`envelopeVersion`|Определяет версию протокола SOAP, используемого для сообщений, обрабатываемых этой привязкой. Единственным допустимым значением является «Soap11».|  
|`hostNameComparisonMode`|Задает режим сравнения имен узлов HTTP для анализа универсальных кодов ресурсов (URI). Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI). Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.|  
|`maxBufferPoolSize`|Целое значение, определяющее максимальный объем памяти, выделяемой для диспетчера буферов сообщений, получающих сообщения из канала. Значение по умолчанию - 524 288 (0x80 000) байт.<br /><br /> Диспетчер буферов сокращает затраты ресурсов на использование буферов с помощью буферного пула. Буферы требуются для обработки службой сообщений, приходящих из канала. Если в буферном пуле недостаточно памяти для обработки потока сообщений, диспетчер буферов сообщений должен выделить дополнительную память из кучи CLR, что увеличивает нагрузку по сбору мусора. Значительное выделение памяти из мусорной кучи CLR указывает на то, что размер буферного пула слишком мал и производительность можно повысить за счет выделения большего объема памяти путем увеличения значения этого атрибута.|  
|`maxBufferSize`|Целое значение, указывающее максимальный размер (в байтах) буфера, хранящего сообщения во время их обработки для конечной точки, настроенной с использованием этой привязки. Значение по умолчанию - 65 536 байт.|  
|`maxReceivedMessageSize`|Положительное целое число, определяющее максимальный размер сообщения (в байтах), включая заголовки, которое можно получить по каналу, настроенному с использованием этой привязки. Отправитель получает ошибку SOAP, если размер сообщения оказывается слишком большим для получателя. Получатель отклоняет сообщение и создает запись о событии в журнале трассировки. Значение по умолчанию - 65 536 байт.|  
|`messageEncoding`|Определяет кодировщик, используемый для кодировки сообщения SOAP. Допустимы следующие значения:<br /><br /> -Текст: Используйте кодировщик текстовых сообщений.<br />-Mtom: Используется кодировщик передачи сообщений организации 1.0 (MTOM).<br /><br /> Значение по умолчанию - Text. Это атрибут типа <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Строка, содержащая имя конфигурации привязки. Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки. Каждая привязка имеет атрибуты `name` и `namespace`, которые совместно однозначно идентифицируют привязку в метаданных службы. Кроме того, это имя является уникальным среди привязок одного типа. Начиная с версии [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] для привязок и поведений необязательно задавать имена. Дополнительные сведения о конфигурации по умолчанию и безымянных привязках и поведениях см. в разделе [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) и [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|Задает пространство имен XML привязки. Значение по умолчанию - "http://tempuri.org/Bindings". Каждая привязка имеет атрибуты `name` и `namespace`, которые совместно однозначно идентифицируют привязку в метаданных службы.|  
|`openTimeout`|Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия. Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>. Значение по умолчанию - 00:01:00.|  
|`proxyAddress`|Универсальный код ресурса (URI) содержит адрес прокси-сервера HTTP. Если для параметра `useSystemWebProxy` задано значение `true`, этот параметр должен иметь значение `null`. Значение по умолчанию — `null`.|  
|`receiveTimeout`|Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения. Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>. Значение по умолчанию - 00:10:00.|  
|`sendTimeout`|Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки. Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>. Значение по умолчанию - 00:01:00.|  
|`textEncoding`|Задает кодировку, используемую при отправке сообщений через привязку. Допустимы следующие значения:<br /><br /> -BigEndianUnicode: Юникод BigEndian.<br />-Юникод. 16-разрядная кодировка.<br />-UTF8: 8-разрядная кодировка<br /><br /> Значение по умолчанию - UTF8. Это атрибут типа <xref:System.Text.Encoding>.|  
|`transferMode`|Допустимое значение <xref:System.ServiceModel.TransferMode>, указывающее, следует ли буферизировать сообщения или передавать их потоком по запросу или отклику.|  
|`useDefaultWebProxy`|Логическое значение, определяющее, должен ли использоваться автоматически настроенный системный прокси-сервер HTTP, если он доступен. Значение по умолчанию — `true`.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<Безопасность >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Определяет параметры безопасности привязки. Это элемент типа <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки. Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<привязки >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Этот элемент содержит коллекцию стандартных и пользовательских привязок.|  
  
## <a name="remarks"></a>Примечания  
 Привязка BasicHttpBinding использует протокол HTTP в качестве транспорта для отправки сообщений протокола SOAP 1.1. Служба может использовать эту привязку для предоставления конечных точек, соответствующих профилю WS-I BP 1.1, например тех, что используют клиенты ASMX. Аналогично клиент может использовать привязку BasicHttpBinding для взаимодействия со службами, предоставляющими конечные точки, которые соответствуют требованиям профиля WS-I BP 1.1, например веб-службами ASMX или службами, настроенными с использованием привязки BasicHttpBinding.  
  
 Система безопасности отключена по умолчанию, но может быть добавлена присвоением атрибуту режима [ \<безопасности >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) дочернего элемента значение, отличное от `None`. По умолчанию используется кодировка сообщений «Text» и кодировка текста «UTF-8».  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование привязки <xref:System.ServiceModel.BasicHttpBinding>, которая обеспечивает связь по протоколу HTTP и максимальные возможности взаимодействия с веб-службами первого и второго поколений. Привязка задается в файлах конфигурации для клиента и службы. Тип привязки задан в атрибуте `binding` элемента `<endpoint>`. Если необходимо настроить основную привязку и изменить некоторые из ее параметров, необходимо определить конфигурацию привязки. Конечная точка должна ссылаться на конфигурацию привязки по имени с помощью атрибута `bindingConfiguration` элемента `<endpoint>`, как показано в следующем примере кода конфигурации службы.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a>Пример  
 Начиная с версии [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] для привязок и поведений необязательно задавать имена. Функциональные возможности из предыдущего примера можно сделать, удалив bindingConfiguration из адреса конечной точки и имя из привязки.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxReceivedMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 Дополнительные сведения о конфигурации по умолчанию и безымянных привязках и поведениях см. в разделе [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) и [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Привязки](../../../../../docs/framework/wcf/bindings.md)
- [Настройка привязок, предоставляемых системой](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Использование привязок для настройки служб и клиентов](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Привязка >](../../../../../docs/framework/misc/binding.md)
