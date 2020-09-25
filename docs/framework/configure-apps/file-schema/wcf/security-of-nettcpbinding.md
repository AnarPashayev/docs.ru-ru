---
title: <security> из <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: d39e3e5e655817aa91c5301274a860a00a6ab7ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169990"
---
# <a name="security-of-nettcpbinding"></a>\<security> из \<netTcpBinding>

Определяет параметры безопасности для привязки.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  

 В следующих разделах описываются атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|mode|Необязательный элемент. Задает тип применяемого механизма обеспечения безопасности. Ниже приведены допустимые значения. Значение по умолчанию — `Transport`.<br /><br /> Это атрибут типа <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Атрибут mode  
  
|Значение|Описание|  
|-----------|-----------------|  
|Отсутствуют|Режим безопасности отключен.|  
|Транспорт|Безопасность транспорта обеспечивается с помощью TLS через TCP или SPNego. Может потребоваться настроить службу с использованием SSL-сертификатов. Этот режим позволяет контролировать уровень защиты.|  
|Сообщение|Безопасность обеспечивается с помощью средств безопасности сообщений SOAP. По умолчанию текст сообщений SOAP шифруется и подписывается. Этот режим предоставляет множество функций, таких как сведения о доступности учетных данных службы для клиентов за пределами диапазона, об используемом наборе алгоритмов и об уровне защиты, применяемом к тексту сообщения. Проверка подлинности клиента выполняется один раз за сеанс, и результаты проверки сохраняются в кэше на протяжении всего сеанса.|  
|TransportWithMessageCredential|Безопасность транспорта связана с безопасностью сообщения. Безопасность транспорта обеспечивается протоколом TLS через TCP, или SPNego, и гарантирует целостность, конфиденциальность и проверку подлинности сервера. Безопасность сообщений SOAP представляет проверку подлинности клиента. По умолчанию проверка подлинности клиента выполняется один раз за сеанс, и результаты проверки сохраняются в кэше на протяжении всего сеанса.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|Определяет параметры безопасности для данного транспорта. Это элемент типа <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<message>](message-element-of-nettcpbinding.md)|Определяет параметры безопасности сообщения. Это элемент типа <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|binding|Элемент Binding объекта [\<netTcpBinding>](nettcpbinding.md) .|  
  
## <a name="remarks"></a>Remarks  

 Каждая из стандартных привязок предоставляет параметры для управления требованиями безопасности перемещения. Эти параметры, как правило, включают режим безопасности, определяющий, используется ли безопасность уровня сообщения или уровня транспорта, а также выбор типа учетных данных клиента. На основании предоставленного выбора параметров создается стек каналов с соответствующей безопасностью.  
  
 Предоставляемые системой привязки, поставляемые Windows Communication Foundation (WCF), представляют собой набор, отвечающий требованиям наиболее распространенных сценариев. Каждая из этих привязок позволяет задавать требования безопасности для некоторых конкретных целевых сценариев.  
  
 Элемент конфигурации предоставляет спецификации безопасности для `netTcpBinding`. Это безопасная, надежная и оптимизированная привязка, пригодная для обмена данными между компьютерами. По умолчанию она создает стек связи среды выполнения, поддерживающий протокол TCP для доставки сообщений и безопасность Windows для безопасности сообщений и проверки подлинности, WS-ReliableMessaging для надежности, а также кодирование двоичных сообщений.  
  
## <a name="see-also"></a>См. также раздел

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Защита служб и клиентов](../../../wcf/feature-details/securing-services-and-clients.md)
- [Привязки](../../../wcf/bindings.md)
- [Настройка привязок, предоставляемых системой](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Использование привязок для настройки служб и клиентов](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
