---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 2458cdd4d593637c2025047d5dd510f0f89b2a0f
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423084"
---
# <a name="oneway"></a>\<oneWay >
Включает поддержку маршрутизации пакетов и использования односторонних методов для пользовательской привязки.  
  
 \<system.serviceModel>  
\<привязки >  
\<customBinding >  
\<Привязка >  
\<oneWay >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`packetRoutable`|Логическое значение, указывающее, включена ли поддержка маршрутизации пакетов. Значение по умолчанию — `false`.|  
|`MaxAcceptedChannels`|Целое число, указывающее максимальное количество принимаемых каналов.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<channelPoolSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|Объект <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>, содержащий свойства пула каналов для текущего канала.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[\<Привязка >](../../../../../docs/framework/misc/binding.md)|Определяет все возможности пользовательской привязки.|  
  
## <a name="remarks"></a>Примечания  
 Чтобы включить поддержку маршрутизации пакетов, необходим уровень одностороннего преобразования, предоставляемый данным элементом. Пользователь может создавать пользовательские привязки, которые выполняют наложение данной привязки на транспорт с поддержкой сеансов или типа «запрос-отклик», чтобы включить для него поддержку маршрутизации пакетов. Этот элемент также полезен, если необходимо предоставить односторонние методы более естественным образом. К данному уровню могут применяться дополнительные преобразования, например Composite Duplex и Reliable Messaging.  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Привязки](../../../../../docs/framework/wcf/bindings.md)
- [Расширение привязок](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Пользовательские привязки](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
