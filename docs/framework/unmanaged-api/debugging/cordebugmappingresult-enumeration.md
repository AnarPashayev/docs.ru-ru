---
title: Перечисление CorDebugMappingResult
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
ms.openlocfilehash: 0e7afa386af1bd2eebc2b58592d01b764660248f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704699"
---
# <a name="cordebugmappingresult-enumeration"></a>Перечисление CorDebugMappingResult

Предоставляет сведения о том, как было получено значение указателя инструкций.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|`MAPPING_PROLOG`|Машинный код находится в прологе, поэтому значение IP-адреса равно 0.|  
|`MAPPING_EPILOG`|Машинный код находится в заключительном фрагменте, поэтому значение IP-адреса является адресом последней инструкции метода.|  
|`MAPPING_NO_INFO`|Для метода нет доступных сведений о сопоставлении, поэтому значение IP-адреса равно 0.|  
|`MAPPING_UNMAPPED_ADDRESS`|Хотя для метода есть сведения о сопоставлении, текущий адрес не может быть сопоставлен с кодом на языке MSIL. Значение IP-адреса равно 0.|  
|`MAPPING_EXACT`|Либо метод полностью сопоставлен с кодом MSIL, либо кадр был интерпретирован, поэтому значение IP-адреса является точным.|  
|`MAPPING_APPROXIMATE`|Метод успешно сопоставлен, но значение IP-адреса может быть приблизительным.|  
  
## <a name="remarks"></a>Комментарии  

 Для получения значения указателя инструкции можно использовать метод [ICorDebugILFrame:: GetIP](icordebugilframe-getip-method.md) .  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Перечисления отладки](debugging-enumerations.md)
