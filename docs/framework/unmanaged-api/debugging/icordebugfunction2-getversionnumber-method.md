---
title: Метод ICorDebugFunction2::GetVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995617"
---
# <a name="icordebugfunction2getversionnumber-method"></a>Метод ICorDebugFunction2::GetVersionNumber
Получает версию "Изменить и продолжить" этой функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `pnVersion`  
 [out] Указатель на целое число, — это номер версии, представленный этим объектом ICorDebugFunction2 функции.  
  
## <a name="remarks"></a>Примечания  
 Среда выполнения отслеживает этой информации на количестве изменений, произошедших в каждый модуль во время сеанса отладки. Номер версии функции входит более количества редактирования, которая представлена функция. Исходная версия функции — версии 1. Номер увеличивается для модуля, каждый раз [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) вызывается для этого модуля. Таким образом Если тело функции был заменен в первый и третий вызов `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` может возвращать версии 1, 2 или 4 для этой функции, но не в версии 3. (Эта функция будет иметь нет версии 3.)  
  
 Номер версии отслеживается отдельно для каждого модуля. Таким образом при выполнении четырех изменений в 1 модуль и модуль 2 следующее изменение на модуле 1 присвоит номер версии 6 ко всем функциям, измененный в 1 модуль. Если данное изменение затрагивает 2 модуля, функции в модуле 2 Получите номер версии 2.  
  
 Получить номер версии, `GetVersionNumber` метод может быть ниже, чем у полученных [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).  
  
 [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) метод выполняет те же функции, как `ICorDebugFunction2::GetVersionNumber`.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
