---
title: Метод ICorDebugCode::GetCode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e18097dd380ee354e5652886544d40da074f1230
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747626"
---
# <a name="icordebugcodegetcode-method"></a>Метод ICorDebugCode::GetCode
Получает весь код для указанной функции, отформатированных для Дизассемблированный код. Этот метод был объявлен устаревшим в .NET Framework версии 2.0. Используйте [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) вместо этого.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `startOffset`  
 [in] Смещение начала функции.  
  
 `endOffset`  
 [in] Смещение конца функции.  
  
 `cBufferAlloc`  
 [in] Размер `buffer` массива, в который будет возвращаться код.  
  
 `buffer`  
 [out] Массив, в которую будет возвращаться код.  
  
 `pcBufferSize`  
 [out] Число возвращаемых байтов.  
  
## <a name="remarks"></a>Примечания  
 Если код функции поделен на несколько блоков, они объединяются в порядке возрастания смещения машинного кода. Границы инструкций не проверяются.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>См. также

- [Метод GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
