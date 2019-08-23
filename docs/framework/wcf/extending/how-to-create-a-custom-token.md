---
title: Практическое руководство. Создание пользовательского токена
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SecurityTokenParameters class
- security [WCF], creating custom tokens
- WSSecurityTokenSerializer class
- SecurityToken class
ms.assetid: 6d892973-1558-4115-a9e1-696777776125
ms.openlocfilehash: 917278ef990842f2ce821474ffd1c6cd619ed289
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951784"
---
# <a name="how-to-create-a-custom-token"></a>Практическое руководство. Создание пользовательского токена
В этом разделе показано, как создать пользовательский маркер безопасности с помощью класса <xref:System.IdentityModel.Tokens.SecurityToken> и интегрировать его с поставщиком пользовательских маркеров безопасности и структурой проверки подлинности. Полный пример кода см. в примере [пользовательского маркера](../../../../docs/framework/wcf/samples/custom-token.md) .  
  
 *Маркер безопасности* — это, по сути, элемент XML, который используется платформой безопасности Windows Communication Foundation (WCF) для представления утверждений об отправителе в сообщении SOAP. Безопасность WCF предоставляет различные маркеры для режимов проверки подлинности, предоставляемых системой. Примером является маркер безопасности X.509, представленный классом <xref:System.IdentityModel.Tokens.X509SecurityToken>, или маркер безопасности Username, представленный классом <xref:System.IdentityModel.Tokens.UserNameSecurityToken>.  
  
 Иногда режим проверки подлинности или учетные данные не поддерживаются указанными типами. В этом случае необходимо создать пользовательский маркер безопасности, чтобы предоставить XML-представление пользовательских учетных данных в сообщение SOAP.  
  
 В следующих процедурах показано, как создать пользовательский маркер безопасности и как интегрировать его с инфраструктурой безопасности WCF. В этом разделе создается маркер кредитной карты, который используется для передачи информации о кредитной карте на сервер.  
  
 Дополнительные сведения о пользовательских учетных данных и диспетчере маркеров безопасности см [. в разделе Пошаговое руководство. Создание настраиваемых учетных данных](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)клиента и службы.  
  
 Сведения о дополнительных классах, представляющих маркеры безопасности, см. в описании пространства имен <xref:System.IdentityModel.Tokens>.  
  
## <a name="procedures"></a>Процедуры  
 Клиентскому приложению необходимо предоставить возможность указания данных кредитной карты для инфраструктуры безопасности. Эти данные делаются доступными приложению с помощью класса учетных данных клиента. Первым шагом является создание класса для представления данных кредитной карты для пользовательских учетных данных клиента.  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>Создание класса, представляющего данные кредитной карты в учетных данных клиента  
  
1. Определите новый класс, представляющий данные кредитной карты для приложения. В следующем примере создается класс с именем `CreditCardInfo`.  
  
2. Добавьте в класс соответствующие свойства, чтобы разрешить приложению указывать данные, необходимые для пользовательского маркера. В этом примере класс имеет три свойства: `CardNumber`, `CardIssuer` и `ExpirationDate`.  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 Затем необходимо создать класс, представляющий пользовательский маркер безопасности. Этот класс используется поставщиками маркеров безопасности, средством проверки подлинности и классами сериализатора для передачи сведений о маркере безопасности в инфраструктуру безопасности WCF и из нее.  
  
#### <a name="to-create-a-custom-security-token-class"></a>Создание класса пользовательского маркера безопасности  
  
1. Определите новый класс, производный от класса <xref:System.IdentityModel.Tokens.SecurityToken>. В этом примере создается класс с именем `CreditCardToken`.  
  
2. Переопределите свойство <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A>. Это свойство используется для получения локального идентификатора маркера безопасности, используемого для указания XML-представления маркера безопасности из других элементов в сообщении SOAP. В этом примере идентификатор маркера может быть передан в качестве параметра конструктора или новый случайный идентификатор может создаваться при каждом создании экземпляра маркера безопасности.  
  
3. Реализуйте свойство <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A>. Это свойство возвращает коллекцию ключей безопасности, представляемую экземпляром маркера безопасности. Такие ключи могут использоваться WCF для подписывания или шифрования частей сообщения SOAP. В этом примере маркер безопасности кредитной карты не может содержать какие-либо ключи безопасности, поэтому реализация всегда возвращает пустую коллекцию.  
  
4. Переопределите свойства <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> и <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A>. Эти свойства используются WCF для определения допустимости экземпляра маркера безопасности. В этом примере для маркера безопасности кредитной карты задана только дата истечения срока действия, поэтому свойство `ValidFrom` возвращает объект <xref:System.DateTime>, представляющий дату и время создания экземпляра.  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 После создания нового типа маркера безопасности необходимо реализовать класс <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>. Реализация используется в конфигурации элемента привязки безопасности для представления нового типа маркера. Класс параметров маркера безопасности служит в качестве шаблона, который используется для сопоставления фактического маркера безопасности при обработке сообщения. Шаблон предоставляет дополнительные свойства, которые могут использоваться приложением для задания критериев, которым должен соответствовать маркер безопасности, чтобы его можно было использовать и проверять на подлинность. В следующем примере не добавляются дополнительные свойства, поэтому при поиске в инфраструктуре WCF экземпляра токена безопасности, используемого или для проверки, сопоставляется только тип маркера безопасности.  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>Создание класса параметров пользовательского маркера безопасности  
  
1. Определите новый класс, производный от класса <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>.  
  
2. Выполните метод <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A>. Скопируйте все внутренние поля, определенные в классе (при их наличии). В этом примере дополнительные поля не определены.  
  
3. Реализуйте свойство <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A>, доступное только для чтения. Это свойство возвращает значение `true`, если тип маркера безопасности, представленный данным классом, можно использовать для проверки подлинности клиента при подключении к службе. В этом примере маркер безопасности кредитной карты можно использовать для проверки подлинности клиента при подключении к службе.  
  
4. Реализуйте свойство <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A>, доступное только для чтения. Это свойство возвращает значение `true`, если тип маркера безопасности, представленный данным классом, можно использовать для проверки подлинности службы при подключении клиента. В этом примере маркер безопасности кредитной карты нельзя использовать для проверки подлинности службы при подключении клиента.  
  
5. Реализуйте свойство <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A>, доступное только для чтения. Это свойство возвращает значение `true`, если тип маркера безопасности, представленный данным классом, можно сопоставить с учетной записью Windows. В этом случае результат проверки подлинности будет представлен экземпляром класса <xref:System.Security.Principal.WindowsIdentity>. В этом примере маркер нельзя сопоставить с учетной записью Windows.  
  
6. Выполните метод <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29>. Этот метод вызывается платформой безопасности WCF, когда требуется ссылка на экземпляр маркера безопасности, представленный этим классом параметров токена безопасности. Фактический экземпляр маркера безопасности и объект <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle>, определяющий тип запрашиваемой ссылки, передаются данному методу в качестве аргументов. В этом примере маркером безопасности кредитной карты поддерживаются только внутренние ссылки. Класс <xref:System.IdentityModel.Tokens.SecurityToken> предоставляет возможность создания внутренних ссылок, поэтому для реализации не требуется дополнительный код.  
  
7. Выполните метод <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29>. Этот метод вызывается WCF для преобразования экземпляра класса параметров токена безопасности в экземпляр <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> класса. Результат используется поставщиками маркеров безопасности для создания соответствующего экземпляра маркера безопасности.  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 Токены безопасности передаются в сообщениях SOAP. Для этого требуется механизм трансляции между представлением токена безопасности, хранимого в памяти, и представлением для передачи по каналу связи. Для выполнения этой задачи WCF использует сериализатор маркеров безопасности. К каждому пользовательскому маркеру должен прилагаться сериализатор, который обеспечивает сериализацию и десериализацию пользовательского маркера безопасности из сообщения SOAP.  
  
> [!NOTE]
> Производные ключи включены по умолчанию. Если создать настраиваемый маркер безопасности и использовать его в качестве основного маркера, то WCF наследует ключ из него. При этом она вызывает сериализатор пользовательских маркеров безопасности, чтобы записать <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> для пользовательского маркера безопасности при сериализации `DerivedKeyToken` для передачи по каналу связи. При десериализации маркера в точке назначения сериализатор `DerivedKeyToken` ожидает `SecurityTokenReference` как дочерний элемент верхнего уровня, расположенный под сериализатором. Если сериализатор пользовательских маркеров безопасности не добавил элемент `SecurityTokenReference` при сериализации своего типа предложения, возникает исключение.  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>Создание сериализатора пользовательских маркеров безопасности  
  
1. Определите новый класс, производный от класса <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>.  
  
2. Переопределите метод <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29>, основанный на объекте <xref:System.Xml.XmlReader> для чтения потока XML. Этот метод возвращает значение `true`, если реализация сериализатора может десериализовать маркер безопасности при наличии его текущего элемента. В этом примере данный метод проверяет, задано ли для XML-элемента средства чтения XML правильное имя и пространство имен. В случае отрицательного результата для обработки XML-элемента вызывается базовая реализация данного метода.  
  
3. Переопределите метод <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> . Этот метод считывает содержимое XML маркера безопасности и создает для него представление, хранимое в памяти. Если метод не распознает XML-элемент, на котором основано переданное средство чтения XML, он вызывает реализацию базового класса для обработки предоставленных системой типов маркеров.  
  
4. Переопределите метод <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> . Этот метод возвращает значение `true`, если он может преобразовать хранимое в памяти представление маркера (переданное в качестве аргумента) в XML-представление. Если преобразование невозможно, он вызывает реализацию базового класса.  
  
5. Переопределите метод <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> . Этот метод преобразует хранимое в памяти представление маркера безопасности в XML-представление. Если преобразование невозможно, он вызывает реализацию базового класса.  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 После выполнения четырех вышеуказанных процедур следует интегрировать пользовательский маркер безопасности с поставщиком маркеров безопасности, структурой проверки подлинности маркеров безопасности, диспетчером маркеров безопасности, а также с учетными данными клиента и службы.  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>Интеграция пользовательского маркера безопасности с поставщиком маркеров безопасности  
  
1. Поставщик маркеров безопасности создает, изменяет (при необходимости) и возвращает экземпляр маркера. Чтобы создать пользовательский поставщик для пользовательского маркера безопасности, создайте класс, наследуемый от класса <xref:System.IdentityModel.Selectors.SecurityTokenProvider>. В следующем примере переопределяется метод <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> для возврата экземпляра `CreditCardToken`. Дополнительные сведения о настраиваемых поставщиках маркеров безопасности см [. в разделе как Создайте настраиваемого поставщика](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)маркеров безопасности.  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>Интеграция пользовательского маркера безопасности со структурой проверки подлинности маркеров безопасности  
  
1. Структура проверки подлинности маркеров безопасности проверяет содержимое маркера безопасности при его извлечении из сообщения. Чтобы создать пользовательскую структуру проверки подлинности для пользовательского маркера безопасности, создайте класс, наследуемый от класса <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>. В следующем примере демонстрируется метод переопределения <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A>. Дополнительные сведения о настраиваемых средствах проверки подлинности [маркеров безопасности см. в разделе как Создайте настраиваемую проверку подлинности](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)маркеров безопасности.  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>Интеграция пользовательского маркера безопасности с диспетчером маркеров безопасности  
  
1. Диспетчер маркеров безопасности создает соответствующие экземпляры поставщика, структуры проверки подлинности и сериализатора маркеров безопасности. Чтобы создать диспетчер пользовательских маркеров, создайте класс, наследуемый от класса <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>. Основные методы класса используют <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> для создания соответствующего поставщика и клиента или учетных данных службы. Дополнительные сведения о настраиваемых диспетчерах маркеров безопасности см [. в разделе Пошаговое руководство. Создание настраиваемых учетных данных](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)клиента и службы.  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>Интеграция пользовательского маркера безопасности с пользовательскими учетными данными клиента и службы  
  
1. Учетные данные клиента и службы необходимо добавить для предоставления интерфейса API приложению, чтобы обеспечить возможность указания данных пользовательского маркера, которые используются инфраструктурой пользовательских маркеров безопасности, предварительно созданной для предоставления и проверки подлинности содержимого пользовательских маркеров безопасности. В следующих образцах показано, как это можно сделать. Дополнительные сведения о настраиваемых учетных данных клиента и службы [см. в разделе Пошаговое руководство. Создание настраиваемых учетных данных](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)клиента и службы.  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 Класс параметров настраиваемого маркера безопасности, созданный ранее, используется для информирования платформы безопасности WCF о том, что при взаимодействии со службой должен использоваться настраиваемый маркер безопасности. В следующей процедуре показано, как это можно сделать.  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>Интеграция пользовательского маркера безопасности с привязкой  
  
1. Класс параметров пользовательского маркера безопасности необходимо задать в одной из коллекций параметров маркера, предоставляемых классом <xref:System.ServiceModel.Channels.SecurityBindingElement>. В следующем примере используется коллекция, возвращаемая методом `SignedEncrypted`. Код добавляет пользовательский маркер кредитной карты в каждое сообщение, передаваемое клиентом службе; при этом содержимое автоматически подписывается и шифруется.  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 В этом разделе показаны различные фрагменты кода, необходимые для реализации и использования пользовательского токена. Чтобы просмотреть полный пример того, как все эти фрагменты кода соответствуют друг другу, см. [Пользовательский токен](../../../../docs/framework/wcf/samples/custom-token.md).  
  
## <a name="see-also"></a>См. также

- <xref:System.IdentityModel.Tokens.SecurityToken>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>
- <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>
- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Пошаговое руководство: Создание настраиваемых учетных данных клиента и службы](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [Практическое руководство. Создание настраиваемого средства проверки подлинности маркеров безопасности](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Практическое руководство. Создание пользовательского поставщика маркеров безопасности](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
