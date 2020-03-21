---
title: Метод ICorDebugGCReferenceEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: d87f414e9dfd05a519b60efc7ecdd5328a6dd86f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178868"
---
# <a name="icordebuggcreferenceenumnext-method"></a>Метод ICorDebugGCReferenceEnum::Next
Получает указанное количество [COR_GC_REFERENCE](cor-gc-reference-structure.md) экземпляров, содержащих информацию об объектах, которые будут собраны мусором.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Параметры  
 celt  
 (в) Количество корней, которые необходимо извлечь.  
  
 Корни  
 (ваут) Массив указателей, каждый из которых указывает на [COR_GC_REFERENCE](cor-gc-reference-structure.md) объект, представляющий корень объекта, который будет собран мусором.  
  
 pceltFetched  
 (ваут) Указатель на количество [COR_GC_REFERENCE](cor-gc-reference-structure.md) объектов `roots`фактически вернулся в . Это значение может быть `null`, если параметр `celt` имеет значение 1.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>Требования  
 **Платформы:** см. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)
- [Интерфейсы отладки](debugging-interfaces.md)
