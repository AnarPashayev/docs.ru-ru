---
title: Перечисление CorDebugBlockingReason
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ea71439c9a6c494c218a7cfc18508f4f8173b03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740382"
---
# <a name="cordebugblockingreason-enumeration"></a>Перечисление CorDebugBlockingReason
Указывает возможные причины блокировки потока на данном объекте.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`BLOCKING_NONE`|Только для внутреннего использования.|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Поток пытается получить критический раздел, связанный с блокировкой монитора на объект. Как правило, это происходит при вызове одного из <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> или <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> методы.|  
|`BLOCKING_MONITOR_EVENT`|Поток ожидает события, связанного с блокировкой монитора для объекта. Как правило, это происходит при вызове одного из <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` методы.|  
  
## <a name="remarks"></a>Примечания  
 Когда `BLOCKING_MONITOR_CRITICAL_SECTION` или `BLOCKING_MONITOR_EVENT` элемент используется в [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) структуры, `pBlockingObject` член структуры точек «ICorDebugValue» интерфейс, который представляет объект, который будет введено . Оно также реализовать [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) интерфейс.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Перечисления отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Отладка](../../../../docs/framework/unmanaged-api/debugging/index.md)
