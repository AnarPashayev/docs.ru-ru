---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 3bcf205964a22cdb418d0158e5ee6439169538ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273988"
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior

ServiceThrottlingBehavior  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>Методы  

 Класс ServiceThrottlingBehavior не определяет никаких методов.  
  
## <a name="properties"></a>Свойства  

 Класс ServiceThrottlingBehavior имеет следующие свойства.  
  
### <a name="maxconcurrentcalls"></a>MaxConcurrentCalls  

 Тип данных: sint32  
  
 Тип доступа: только для чтения  
  
 Максимальное количество сообщений, которые могут одновременно обрабатываться во всех объектах диспетчера в узле ServiceHost.  
  
### <a name="maxconcurrentinstances"></a>MaxConcurrentInstances  

 Тип данных: sint32  
  
 Тип доступа: только для чтения  
  
 Максимальное число объектов службы, которые могут выполняться одновременно.  
  
### <a name="maxconcurrentsessions"></a>MaxConcurrentSessions  

 Тип данных: sint32  
  
 Тип доступа: только для чтения  
  
 Максимальное число сеансов, одновременно принимаемых узлом.  
  
## <a name="requirements"></a>Требования  
  
|MOF|Объявлено в файле Servicemodel.mof.|  
|---------|-----------------------------------|  
|Пространство имен|Определено в root\ServiceModel.|  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
