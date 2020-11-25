---
title: Перечисление CLR_DEBUGGING_PROCESS_FLAGS
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
ms.openlocfilehash: dd148d23d6e29f03052d3bbf1fcd5d02fb332a0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729854"
---
# <a name="clr_debugging_process_flags-enumeration"></a>Перечисление CLR_DEBUGGING_PROCESS_FLAGS

Предоставляет значения, используемые методом [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Эта среда выполнения имеет управляемое событие отладчика, не являющегося перехватываться, для отправки. Различия между событиями "перехват" и "не перехватывать" см. в разделе "Примечания".|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|Управляемое событие, которое является ожидающим, является <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> запросом.|  
  
## <a name="remarks"></a>Комментарии  

 К событиям перехвата относятся процесс, домен приложения, сборка, модуль и уведомления о создании потоков, которые переводят отладчик в текущее состояние после его присоединения к процессу. События, не относящиеся к перехвату, которые обозначаются `CLR_DEBUGGING_MANAGED_EVENT_PENDING` флагом, включают все остальные события отладчика, такие как исключения и уведомления помощника по отладке управляемого кода (MDA).  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`Флаг позволяет среде выполнения отличать незавершенное исключение и запрос на присоединение управляемого отладчика, который может быть отменен.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** Метахост. idl, Метахост. h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Перечисления отладки](debugging-enumerations.md)
- [Отладка](index.md)
