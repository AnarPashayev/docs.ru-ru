---
title: <wsDualHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 8fd758258a34fd63882c3d06b49cbe53bd2d105d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915129"
---
# <a name="wsdualhttpbinding"></a>\<wsDualHttpBinding >
Определяет безопасную, надежную привязку с возможностью взаимодействия, которая подходит для дуплексных контрактов службы или связи посредством посредников протокола SOAP.  
  
 \<системой. > ServiceModel  
\<привязки >  
\<wsDualHttpBinding >  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описываются атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|bypassProxyOnLocal|Логическое значение, определяющее, будет ли выполняться обход прокси-сервера для локальных адресов. Значение по умолчанию — `false`.|  
|clientBaseAddress|Универсальный код ресурса (URI), задающий базовый адрес, который клиент прослушивает для получения сообщений ответа от службы. Если значение задано, для прослушивания используется этот адрес (плюс per-channelGUID). Если значение не задано, базовый адрес клиента создается в соответствии с транспортом. Значение по умолчанию — `null`.|  
|closeTimeout|Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия. Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>. Значение по умолчанию - 00:01:00.|  
|hostnameComparisonMode|Задает режим сравнения имен узлов HTTP для анализа универсальных кодов ресурсов (URI). Это атрибут типа <xref:System.ServiceModel.HostNameComparisonMode>, который указывает, используется ли имя узла для доступа к службе при сравнении по универсальному коду ресурсов (URI). Значение по умолчанию — <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, при котором имя узла в найденном соответствии не используется.|  
|maxBufferPoolSize|Целое число, задающее максимальный размер буферного пула для этой привязки. Значение по умолчанию - 524 288 байт (512 * 1024). Многие элементы Windows Communication Foundation (WCF) используют буферы. При создании буферов и их уничтожении после каждого использования расходуется слишком много ресурсов; при сборке мусора для буферов также расходуется слишком много ресурсов. Буферные пулы позволяют брать буфер из пула, использовать его, а затем возвращать обратно, когда он больше не требуется. Это позволяет избежать излишней нагрузки, связанной с созданием и уничтожением буферов.|  
|maxReceivedMessageSize|Положительное целое число, задающее, в байтах, максимальный размер сообщения (включая заголовки), которое можно получить по каналу, настроенному с использованием этой привязки. Отправитель сообщения, превышающего это ограничение, получит ошибку SOAP. Получатель отклоняет сообщение и создает запись о событии в журнале трассировки. Значение по умолчанию — 65536.|  
|messageEncoding|Определяет кодировщик, используемый для кодировки сообщения. Допустимы следующие значения:<br /><br /> Полнотекстовым Использование кодировщика текстовых сообщений.<br />MTOM Используйте кодировщик обмена сообщениями с механизмом 1,0 (MTOM).<br />— Значение по умолчанию — Text.<br /><br /> Это атрибут типа <xref:System.ServiceModel.WSMessageEncoding>.|  
|имя|Строка, содержащая имя конфигурации привязки. Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки. Начиная с версии [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] для привязок и поведений необязательно задавать имена. Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия. Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>. Значение по умолчанию - 00:01:00.|  
|proxyAddress|Универсальный код ресурса (URI), задающий адрес прокси-сервера HTTP. Если параметр `useDefaultWebProxy` имеет значение `true`, данный параметр должен иметь значение `null`. Значение по умолчанию — `null`.|  
|receiveTimeout|Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения. Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>. Значение по умолчанию - 00:01:00.|  
|sendTimeout|Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки. Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>. Значение по умолчанию - 00:01:00.|  
|textEncoding|Задает кодировку, используемую при отправке сообщений через привязку. Допустимы следующие значения:<br /><br /> BigEndianUnicode Кодировка байтов Юникода.<br />Юникод 16-разрядная кодировка.<br />ОБРАТНО 8-разрядная кодировка<br /><br /> Значение по умолчанию - UTF8. Это атрибут типа <xref:System.Text.Encoding>.|  
|transactionFlow|Логическое значение, определяющее, поддерживает ли привязка потоковые спецификации WS-Transactions. Значение по умолчанию — `false`.|  
|useDefaultWebProxy|Логическое значение, указывающее, должен ли использоваться автоматически настроенный системный прокси-сервер HTTP. Если данный атрибут имеет значение `null`, прокси-адрес должен быть равен `true` (то есть не задан). Значение по умолчанию — `true`.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<> безопасности](security-of-wsdualhttpbinding.md)|Определяет параметры безопасности привязки. Это элемент типа <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.|  
|[\<Реадеркуотас >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Определяет ограничения по сложности сообщений SOAP, которые могут обрабатываться конечными точками, настроенными с использованием этой привязки. Это элемент типа <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Указывает, устанавливаются ли между конечными точками канала надежные сеансы.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<привязки >](bindings.md)|Этот элемент содержит коллекцию стандартных и пользовательских привязок.|  
  
## <a name="remarks"></a>Примечания  
 Объект `WSDualHttpBinding` предоставляет такую же поддержку протоколам веб-служб, как и объект `WSHttpBinding`, но применяется для дуплексных контрактов. `WSDualHttpBinding` поддерживает только безопасность SOAP и требует надежного обмена сообщениями. Для этой привязки необходимо, чтобы клиент имел открытый универсальный код ресурса (URI), предоставляющий конечную точку обратного вызова для службы. Это обеспечивается атрибутом `clientBaseAddress`. Двойная привязка предоставляет службе IP-адрес клиента. Клиенту следует использовать механизм безопасности, чтобы гарантировать, что подключение выполняется только к доверенным службам.  
  
 Эту привязку можно использовать для надежной связи посредством одного или нескольких посредников протокола SOAP.  
  
 По умолчанию эта привязка создает стек времени выполнения с WS-ReliableMessaging для надежности, WS-Security для безопасности и проверки подлинности сообщений, HTTP для доставки сообщений и кодировкой сообщений Text/XML.  
  
## <a name="example"></a>Пример  
  
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
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>
- [Привязки](../../../wcf/bindings.md)
- [Настройка привязок, предоставляемых системой](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Использование привязок для настройки служб и клиентов](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Привязка >](../../../misc/binding.md)
