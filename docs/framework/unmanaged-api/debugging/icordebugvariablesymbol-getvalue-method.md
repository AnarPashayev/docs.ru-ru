---
title: Метод ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 186d9eec0aa6ad9e327b1dd4d0f19e251c79ecf9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147281"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>Метод ICorDebugVariableSymbol::GetValue
Возвращает значение переменной в виде массива байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `offset`  
 [in] Начальное смещение в переменной, с которого следует читать значение. Этот параметр используется при чтении полей членов в объекте.  
  
 `cbContext`  
 [in] Размер аргумента `context` в байтах.  
  
 `context`  
 [in] Контекст потока, используемый для чтения значения.  
  
 `cbValue`  
 [in] Размер буфера `pValue` в байтах.  
  
 `pcbValue`  
 [out] Число байтов, фактически записанных в буфер `pValue`.  
  
 `pValue`  
 [out] Массив байтов, содержащий значение переменной.  
  
## <a name="remarks"></a>Примечания  
  
> [!NOTE]
>  Этот метод доступен только в машинном коде .NET.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Интерфейсы отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
