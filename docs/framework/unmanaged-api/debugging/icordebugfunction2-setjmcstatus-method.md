---
title: Метод ICorDebugFunction2::SetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49ced1b4be888c7550c3927d1b319ab2f0bef086
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763780"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>Метод ICorDebugFunction2::SetJMCStatus
Помечает функцию, представленный этой ICorDebugFunction2 только мой код пошагового выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `bIsJustMyCode`  
 [in] Значение `true` пометить ее как код пользователя; в противном случае значение `false`.  
  
## <a name="return-values"></a>Возвращаемые значения  
  
|HRESULT|Описание|  
|-------------|-----------------|  
|`S_OK`|Функция был успешно помечен.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|Функции не могут быть помечены как пользовательский код, поскольку он не может быть отлажен.|  
  
## <a name="remarks"></a>Примечания  
 Несопоставимого только мой код будет пропускать код, не написанный пользователем. Пользовательский код должен представлять собой подмножество отлаживаемый код.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
