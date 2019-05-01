---
title: Метод ICorDebugInternalFrame2::GetFrameAddress
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c30115a23f7f73662c9b3f4f4a09d45478ad687
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995479"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a>Метод ICorDebugInternalFrame2::GetFrameAddress
Возвращает адрес внутреннего кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a>Параметры  
 `pAddress`  
 [out] Указатель на `CORDB_ADDRESS` для внутреннего кадра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.  
  
|HRESULT|Описание|  
|-------------|-----------------|  
|S_OK|Адрес внутреннего кадра успешно возвращен.|  
|E_FAIL|Адрес внутреннего кадра не могут быть возвращены.|  
|E_INVALIDARG|Свойство `pAddress` имеет значение `null`.|  
  
## <a name="remarks"></a>Примечания  
 Значение, возвращаемое в `pAddress` может использоваться для определения расположения внутреннего кадра относительно других фреймы в стеке. Даже на компьютерах с архитектурой IA-64 внутренний кадр существует только в стеке, и нет соответствующего указателя в резервное хранилище.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [Интерфейсы отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Отладка](../../../../docs/framework/unmanaged-api/debugging/index.md)
