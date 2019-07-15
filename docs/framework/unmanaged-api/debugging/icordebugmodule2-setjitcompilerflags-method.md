---
title: Метод ICorDebugModule2::SetJITCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 114f4ff261d9612a81d17bf5b3df2f87323f77f2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764201"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>Метод ICorDebugModule2::SetJITCompilerFlags
Задает флаги, определяющие компиляции этого ICorDebugModule2 just-in-time (JIT).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `dwFlags`  
 [in] Побитовое сочетание [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) значений перечисления.  
  
## <a name="remarks"></a>Примечания  
 Если `dwFlags` значение является недопустимым, `SetJITCompilerFlags` метод завершится с ошибкой.  
  
 `SetJITCompilerFlags` Метод может вызываться только в пределах [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) обратного вызова для этого модуля. Пытается вызвать его после `ICorDebugManagedCallback::LoadModule` обратного вызова доставки будет ошибкой.  
  
 Изменить и продолжить в 64-разрядной или платформах операционных системах Win9x не поддерживается. Таким образом при вызове метода `SetJITCompilerFlags` метод на любой из этих двух платформ с флагом CORDEBUG_JIT_ENABLE_ENC, установленным `dwFlags`, `SetJITCompilerFlags` метод и всех методах, используемых для изменения и продолжить, такие как [ICorDebugModule2:: Метод ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), завершится ошибкой.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
