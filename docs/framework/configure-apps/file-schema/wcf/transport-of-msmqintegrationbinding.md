---
title: <transport> из <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 3126618eca6e8317968c6eb568a04615ec8de884
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788366"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<Транспорт > из \<msmqIntegrationBinding >
Определяет параметры безопасности для транспорта интеграции очереди сообщений.  
  
 \<system.ServiceModel>  
\<привязки >  
msmqIntegrationBinding  
\<Привязка >  
\<Безопасность >  
\<Транспорт >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описываются атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Задает способ проверки подлинности сообщения транспортом MSMQ. Если задано значение `None`, атрибуту `msmqProtectionLevel` также должно быть присвоено значение `None`.<br /><br /> Допустимы следующие значения:<br /><br /> -None: Без проверки подлинности.<br />-WindowsDomain: Механизм проверки подлинности использует Active Directory для получения сертификата X.509 для SID, связанный с сообщением. Затем это используется для проверки ACL очереди, чтобы убедиться в наличии у пользователя разрешений для записи в очередь.<br />-Сертификат: Канал получает сертификат из хранилища сертификатов.<br /><br /> Значение по умолчанию - WindowsDomain. Это атрибут типа <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Задает алгоритм, который будет использоваться для шифрования сообщений при их передаче между диспетчерами очередей сообщений. Допустимы следующие значения:<br /><br /> -RC4Stream<br />-AES<br /><br /> Значение по умолчанию - RC4Stream. Это атрибут типа <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Задает способ обеспечения безопасности сообщения на уровне транспорта MSMQ. Шифрование обеспечивает целостность сообщения, а EncryptAndSign - целостность и неотрекаемость сообщения; то есть гарантируется, что сообщение на самом деле поступает от отправителя, и отправитель действительно является тем, кем называет себя.<br /><br /> -Допустимыми являются следующие:<br />-None: Нет защиты.<br />-Входа: Сообщения подписываются.<br />-EncryptAndSign: Сообщения шифруются и подписываются.<br /><br /> Значение по умолчанию - Sign. Это атрибут типа ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|— Указывает алгоритм, используемый при вычислении дайджеста в составе сигнатур. Допустимы следующие значения:<br />-MD5<br />-SHA1<br />-SHA256<br />-SHA512<br /><br /> Значение по умолчанию - SHA1. Это атрибут типа <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>Из-за конфликта проблем с MD5 и SHA1 Корпорация Майкрософт рекомендует SHA256 или выше.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<Безопасность >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Определяет параметры безопасности для привязки MSMQ.|  
  
## <a name="remarks"></a>Примечания  
 Данный элемент инкапсулирует параметры безопасности для транспорта интеграции очереди сообщений. Данные параметры одинаковы для интеграции очереди сообщений и использующих очереди транспортов. Это позволяет задать режим проверки подлинности, алгоритм шифрования, алгоритм SHA и уровень защиты.  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Защита служб и клиентов](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Привязки](../../../../../docs/framework/wcf/bindings.md)
- [Настройка привязок, предоставляемых системой](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Использование привязок для настройки служб и клиентов](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Привязка >](../../../../../docs/framework/misc/binding.md)
