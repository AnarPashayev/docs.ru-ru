---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 67ec30b2bf3c322b949700789ce942e4281b77a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204449"
---
# <a name="sslstreamsecurity"></a>\<sslStreamSecurity>
Представляет пользовательский элемент привязки, который поддерживает безопасность канала с помощью потока SSL.  
  
 \<system.serviceModel>  
\<привязки >  
\<customBinding >  
\<Привязка >  
\<sslStreamSecurity>  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|requireClientCertificate|Логическое значение, указывающее, требуется ли для этой привязки сертификат клиента. Значение по умолчанию — `false`.|  
|sslProtocols|Значение флага перечисления SslProtocols, указывающее, какие протоколы SslProtocols поддерживаются. Значение по умолчанию — Ssl3&#124;Tls&#124;Tls11&#124;Tls12.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<Привязка >](../../../../../docs/framework/misc/binding.md)|Определяет все возможности пользовательской привязки.|  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [Привязки](../../../../../docs/framework/wcf/bindings.md)
- [Расширение привязок](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Пользовательские привязки](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
