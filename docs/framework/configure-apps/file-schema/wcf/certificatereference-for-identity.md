---
title: <certificateReference> для <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 3b7779ac00c2fca6300c12ac18ff2d5f6b868424
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704340"
---
# <a name="certificatereference-for-identity"></a>\<certificateReference > для \<identity >
Задает параметры для проверки сертификата X.509. Защищенный клиент Windows Communication Foundation (WCF), подключающийся к конечной точке с использованием этого удостоверения, проверяет, что утверждения, представленные сервером, содержат идентификационное утверждение, используемое для конструирования этого удостоверения.  
  
 \<удостоверение >  
\<certificateReference >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|findValue|Задает значение для поиска в хранилище сертификатов X.509. Тип, указанный в этом атрибуте, должен отвечать требованиям заданного значения `X509FindType`. Значение по умолчанию - пустая строка.|  
|isChainIncluded|Логическое значение, определяющее, выполнена ли проверка с использованием цепочки сертификатов.|  
|storeLocation|Задает расположение хранилища сертификатов, которое клиент может использовать для проверки сертификата сервера.<br /><br /> Допустимы следующие значения:<br /><br /> -LocalMachine: Хранилище сертификатов, назначенное локальному компьютеру.<br />-CurrentUser: Хранилище сертификатов, назначенное текущему пользователю.<br /><br /> Значение по умолчанию - LocalMachine.<br /><br /> Это атрибут типа <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Задает имя открываемого хранилища сертификатов X.509.<br /><br /> Допустимы следующие значения:<br /><br /> -AddressBook: Хранилище сертификатов для других пользователей.<br />-AuthRoot: Хранилище сертификатов для сторонних сертификации (ЦС).<br />-CertificateAuthority: Хранилище сертификатов для промежуточных центров сертификации.<br />-Запрещается использовать следующее: Хранилище сертификатов для отозванных сертификатов.<br />— My: Хранилище сертификатов для личных сертификатов.<br />-Root: Хранилище сертификатов для доверенных корневых центров сертификации.<br />-TrustedPeople: Хранилище сертификатов для непосредственно доверенных лиц и ресурсов.<br />-TrustedPublisher: Хранилище сертификатов для непосредственно доверенных издателей.<br /><br /> Значение по умолчанию - «My».<br /><br /> Это атрибут типа <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Определяет тип выполняемого поиска X.509. Тип, указанный в атрибуте `findValue`, должен отвечать требованиям заданного значения X509FindType.<br /><br /> Допустимы следующие значения:<br /><br /> -FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-FindByTimeValid<br />-FindByTimeNotYetValid<br />-FindByTemplateName<br />-FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-FindBySubjectKeyIdentifier<br /><br /> Значение по умолчанию - FindBySubjectDistinguishedName.<br /><br /> Это атрибут типа <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<удостоверение >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Задает параметры, которые обеспечивают проверку подлинности конечной точки другими конечными точками, с которыми происходит обмен сообщениями.|  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
