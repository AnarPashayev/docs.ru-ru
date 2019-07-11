---
title: Метод ICorDebugFunction2::GetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed2364c7c47aed1430a86aeee3daabf6b94cbf3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754479"
---
# <a name="icordebugfunction2getjmcstatus-method"></a>Метод ICorDebugFunction2::GetJMCStatus
Получает значение, указывающее, отмечена ли функция, представляемая этим объектом ICorDebugFunction2 как пользовательский код.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `pbIsJustMyCode`  
 [out] Указатель на логическое значение, которое является `true`, если эта функция помечается как код пользователя; в противном случае значение равно `false`.  
  
## <a name="remarks"></a>Примечания  
 Если функция, представленный данным `ICorDebugFunction2` невозможна, `pbIsJustMyCode` всегда будет `false`.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
