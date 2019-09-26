---
title: Перечисление CorDebugChainReason
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fce803544b393ac2c441779183cbf49d4c39bdae
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273980"
---
# <a name="cordebugchainreason-enumeration"></a>Перечисление CorDebugChainReason
Указывает причину или причины запуска цепочки вызовов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`CHAIN_NONE`|Цепочки вызовов не инициированы.|  
|`CHAIN_CLASS_INIT`|Цепочка была инициирована конструктором.|  
|`CHAIN_EXCEPTION_FILTER`|Цепочка была инициирована фильтром исключений.|  
|`CHAIN_SECURITY`|Цепочка была инициирована кодом, который принудительно обеспечивает безопасность.|  
|`CHAIN_CONTEXT_POLICY`|Цепочка была инициирована контекстной политикой.|  
|`CHAIN_INTERCEPTION`|Не используется.|  
|`CHAIN_PROCESS_START`|Не используется.|  
|`CHAIN_THREAD_START`|Цепочка была инициирована началом выполнения потока.|  
|`CHAIN_ENTER_MANAGED`|Цепочка была инициирована входом в управляемый код.|  
|`CHAIN_ENTER_UNMANAGED`|Цепочка была инициирована входом в неуправляемый код.|  
|`CHAIN_DEBUGGER_EVAL`|Не используется.|  
|`CHAIN_CONTEXT_SWITCH`|Не используется.|  
|`CHAIN_FUNC_EVAL`|Цепочка была инициирована оценкой функции.|  
  
## <a name="remarks"></a>Примечания  
 Используйте метод [ICorDebugChain::-Reason](icordebugchain-getreason-method.md) , чтобы определить причины инициации цепочки вызовов.  
  
## <a name="requirements"></a>Требования  
 **Платформ** См. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug. idl, CorDebug. h  
  
 **Библиотечная** Коргуидс. lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Перечисления отладки](debugging-enumerations.md)
