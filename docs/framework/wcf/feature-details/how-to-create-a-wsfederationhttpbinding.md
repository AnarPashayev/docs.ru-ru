---
title: Практическое руководство. Создание WSFederationHttpBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: 3a6564683a856c8d1eb47b1569f156e0b6d5cc67
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636408"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Практическое руководство. Создание WSFederationHttpBinding

В Windows Communication Foundation (WCF), <xref:System.ServiceModel.WSFederationHttpBinding> класс ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) в конфигурации) предоставляет механизм для предоставления федеративной службы. т. е. к службе, требующей проверки подлинности клиентов с использованием маркера безопасности, выданного службой маркеров безопасности. В этом разделе показано, как настраивать привязку <xref:System.ServiceModel.WSFederationHttpBinding> в коде и в конфигурации. После создания привязки можно настроить конечную точку на использование этой привязки.

 Ниже перечислены основные шаги.

1. Выберите режим безопасности. Привязка <xref:System.ServiceModel.WSFederationHttpBinding> поддерживает режим `Message`, обеспечивающий сквозную защиту на уровне сообщений даже при нескольких переходах, а также режим `TransportWithMessageCredential`, который повышает производительность в случаях, когда клиент и служба могут напрямую подключаться друг к другу с помощью протокола HTTPS.

    > [!NOTE]
    > Кроме того, привязка <xref:System.ServiceModel.WSFederationHttpBinding> поддерживает режим безопасности `None`. Этот режим небезопасен и поддерживается только в целях отладки. Если конечная точка службы развертывается с <xref:System.ServiceModel.WSFederationHttpBinding> его задан режим безопасности `None`, полученный привязки клиента (созданные [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) является <xref:System.ServiceModel.WSHttpBinding> с режим безопасности `None`.

     В отличие от других предоставляемых системой привязок, при использовании привязки `WSFederationHttpBinding` нет необходимости выбирать тип учетных данных клиента. Это связано с тем, что типом учетных данных клиента всегда является выданный токен. WCF получает маркер от заданного издателя и передает этот маркер службе проверки подлинности клиента.

2. В федеративных клиентах присвойте свойству <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> URL-адрес службы маркеров безопасности. Задайте в качестве свойства <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> привязку, которая должна использоваться для взаимодействия со службой маркеров безопасности.

3. Необязательный параметр. Задайте в качестве свойства <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> универсальный код ресурса (URI) типа маркера. В федеративных службах укажите ожидаемый службой тип маркера. В федеративных клиентах укажите тип маркера, запрашиваемый клиентом у службы маркеров безопасности.

     Если тип маркера не задан, клиенты создают маркеры безопасности запросов (RST) WS-Trust без универсального кода ресурса (URI) типа маркера, а служба по умолчанию ожидает проверки подлинности клиента с использованием маркера SAML 1.1.

     URI для маркера SAML 1.1 `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. Необязательный параметр. В федеративных службах присвойте свойству <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> URL-адрес метаданных службы маркеров безопасности. Конечная точка метаданных позволяет клиентам службы выбрать соответствующую пару «привязка - конечная точка», если служба настроена на публикацию метаданных. Дополнительные сведения о публикации метаданных см. в разделе [публикация метаданных](publishing-metadata.md).

 Можно также задать другие свойства, в том числе тип ключа, используемого в качестве ключа проверки в выданном маркере, набор алгоритмов для взаимодействия между клиентом и службой, необходимость согласования или явного задания учетных данных службы, конкретные утверждения, которые служба ожидает получить в выданном маркере, а также любые дополнительные элементы XML, которые необходимо добавить в запрос, отправляемый клиентом службе маркеров безопасности.

> [!NOTE]
>  Свойство `NegotiateServiceCredential` используется только в том случае, если `SecurityMode` имеет значение `Message`. Если `SecurityMode` имеет значение `TransportWithMessageCredential`, свойство `NegotiateServiceCredential` игнорируется.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Настройка привязки WSFederationHttpBinding в коде

1. Создайте экземпляр класса <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Присвойте свойству <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> значение <xref:System.ServiceModel.WSFederationHttpSecurityMode> или <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> в зависимости от необходимости. Если набор алгоритмов, в отличных от <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> требуется, задайте <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> присваивается значение, взятое из <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.

3. Задайте свойство <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> в зависимости от необходимости.

4. Задайте <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> свойства <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` или.`AsymmetricKey` При необходимости.

5. Присвойте свойству <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> соответствующее значение. Если значение не задано, по умолчанию используется WCF `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`, который соответствует маркерам SAML 1.1.

6. Является обязательным для клиента, если не задан локальный издатель; для службы является необязательным. Создайте объект <xref:System.ServiceModel.EndpointAddress>, содержащий адрес и сведения об удостоверении службы маркеров безопасности и присвойте экземпляр <xref:System.ServiceModel.EndpointAddress> свойству <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A>.

7. Является обязательным для клиента, если не задан локальный издатель; для службы не используется. Создание <xref:System.ServiceModel.Channels.Binding> для `SecurityTokenService` и назначить <xref:System.ServiceModel.Channels.Binding> экземпляр <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> свойство.

8. Не используется для клиента; является необязательным для службы. Создайте экземпляр <xref:System.ServiceModel.EndpointAddress> для метаданных службы маркеров безопасности и присвойте его свойству `IssuerMetadataAddress`.

9. Является необязательным как для клиента, так и для службы. Создайте и добавьте один или более экземпляров <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> в коллекцию, возвращаемую свойством <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>.

10. Является необязательным как для клиента, так и для службы. Создайте и добавьте один или более экземпляров <xref:System.Xml.XmlElement> в коллекцию, возвращаемую свойством <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Создание федеративной конечной точки в конфигурации

1. Создание [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) как дочерний [ \<привязки >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) элемент в файле конфигурации приложения.

2. Создание [ \<привязки >](../../../../docs/framework/misc/binding.md) как дочерний элемент элемента [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) и задайте `name` атрибут соответствующее значение.

3. Создание `<security>` как дочерний элемент элемента [ \<привязки >](../../../../docs/framework/misc/binding.md) элемент.

4. Задайте для атрибута `mode` элемента `<security>` значение `Message` или `TransportWithMessageCredential` в зависимости от необходимости.

5. Создайте элемент `<message>`, являющийся дочерним для элемента `<security>`.

6. Необязательный параметр. Задайте соответствующее значение атрибута `algorithmSuite` элемента `<message>`. Значение по умолчанию — `Basic256`.

7. Необязательный параметр. Если требуется асимметричный ключ проверки, задайте для атрибута `issuedKeyType` элемента `<message>` значение `AsymmetricKey`. Значение по умолчанию — `SymmetricKey`.

8. Необязательный параметр. Задайте значение атрибута `issuedTokenType` элемента `<message>`.

9. Является обязательным для клиента, если не задан локальный издатель; для службы является необязательным. Создайте элемент `<issuer>`, являющийся дочерним для элемента `<message>`.

10. Задайте атрибут `address` элемента `<issuer>` и укажите адрес, по которому служба маркеров безопасности принимает запросы маркеров.

11. Необязательный параметр. Добавьте дочерний элемент `<identity>` и задайте удостоверение службы маркеров безопасности.

12. Дополнительные сведения см. в разделе [службы идентификации и проверки подлинности](service-identity-and-authentication.md).

13. Является обязательным для клиента, если не задан локальный издатель; для службы не используется. Создание [ \<привязки >](../../../../docs/framework/misc/binding.md) элемент в разделе привязок, который может использоваться для взаимодействия со службой маркеров безопасности. Дополнительные сведения о создании привязки см. в разделе [как: Указание привязки службы в конфигурации](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. Укажите привязку, созданную на предыдущем этапе, задав атрибуты `binding` и `bindingConfiguration` элемента `<issuer>`.

15. Не используется для клиента; является необязательным для службы. Создание `<issuerMetadata>` как дочерний элемент элемента <`message`> элемента. Затем в атрибуте `address` элемента `<issuerMetadata>` укажите адрес, по которому служба маркеров безопасности должна опубликовать свои метаданные. Добавьте дочерний элемент `<identity>` и задайте удостоверение службы маркеров безопасности (необязательно).

16. Является необязательным как для клиента, так и для службы. Добавьте элемент `<claimTypeRequirements>` в качестве дочернего элемента для элемента `<message>`. Задать обязательные и необязательные утверждения, использующая службы, добавив [ \<Добавить >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) элементы `<claimTypeRequirements>` элемента и указания утверждения типа с `claimType` атрибута. С помощью атрибута `isOptional` укажите, является ли то или иное утверждение обязательным.

## <a name="example"></a>Пример

Ниже приведен пример кода принудительной настройки привязки `WSFederationHttpBinding`.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>См. также

- [Федерация](federation.md)
- [Пример федерации](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Практическое руководство. Отключения безопасных сеансов в WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
