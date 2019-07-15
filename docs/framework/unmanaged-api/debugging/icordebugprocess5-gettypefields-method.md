---
title: Метод ICorDebugProcess5::GetTypeFields
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d413b17da0b6f241f9078bfeb3bd035d4d07a81
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767627"
---
# <a name="icordebugprocess5gettypefields-method"></a>Метод ICorDebugProcess5::GetTypeFields
Сведения о полях, которые принадлежат к типу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `id`  
 [in] Идентификатор типа которого извлекаются поля.  
  
 `celt`  
 [in] Число [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) объектов, которой требуется извлечь сведения о которой поля.  
  
 `fields`  
 [out] Массив [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) объектов, которые предоставляют сведения о полях, которые принадлежат к типу.  
  
 `pceltNeeded`  
 [out] Указатель на число [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) объекты, включенные в `fields`.  
  
## <a name="remarks"></a>Примечания  
 `celt` Параметр, который указывает количество полей, сведения о поле, данный метод использует для заполнения `fields`, должен соответствовать значению `COR_TYPE_LAYOUT::numFields` поля.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Интерфейсы отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
