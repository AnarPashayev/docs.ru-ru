---
title: <add> элемента <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 249227c20dd1610cba088017ae39e84d6cb683d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920211"
---
# <a name="add-of-claimtyperequirements-element"></a>\<Добавление > \<элемента > claimTypeRequirements
Задает типы обязательных и необязательных утверждений, которые могут появляться в федеративных учетных данных. Например, службы предъявляют требования к входящим учетным данным, которые должны обладать определенным набором типов утверждений.  
  
 \<системой. > ServiceModel  
\<привязки >  
\<Всфедератедбиндинг >  
\<Привязка >  
\<> безопасности  
\<> сообщения  
\<claimTypeRequirements >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|claimType|Универсальный код ресурса (URI), определяющий тип утверждения. Например, для приобретения товара с веб-узла пользователь должен представить действительную кредитную карту с достаточным кредитным лимитом. Типом утверждения будет универсальный код ресурса (URI) кредитной карты.|  
|isOptional|Логическое значение, указывающее, является ли утверждение необязательным. Если утверждение является обязательным, установите для этого атрибута значение `false`.<br /><br /> Этот атрибут можно использовать, если служба запрашивает определенные данные, но они не являются необходимыми. Например, если требуется, чтобы пользователь ввел имя, фамилию и адрес, а указание номера телефона является необязательным.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](claimtyperequirements-for-message.md)|Задает коллекцию обязательных типов утверждений. Каждый элемент имеет тип <xref:System.ServiceModel.Configuration.ClaimTypeElement>.<br /><br /> В федеративном сценарии службы предъявляют требования к входящим учетным данным. Например, входящие учетные данные должны обладать определенным набором типов утверждений. Каждый элемент в этой коллекции задает типы обязательных и необязательных утверждений, которые могут появляться в федеративных учетных данных.|  
  
## <a name="remarks"></a>Примечания  
 В федеративном сценарии службы предъявляют требования к входящим учетным данным. Например, входящие учетные данные должны обладать определенным набором типов утверждений. Это требование представлено в политике безопасности. Когда клиент запрашивает учетные данные в федеративной службе (например, CardSpace), требования помещаются в запрос маркера (RequestSecurityToken), что позволяет федеративной службе выдать учетные данные, полностью отвечающие требованиям.  
  
## <a name="example"></a>Пример  
 Следующая конфигурация добавляет два требования типа утверждения к привязке безопасности.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
