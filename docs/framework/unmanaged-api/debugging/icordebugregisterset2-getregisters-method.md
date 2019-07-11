---
title: Метод ICorDebugRegisterSet2::GetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c1b90390689e709ee131935bd6417fa6b273eb2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769981"
---
# <a name="icordebugregisterset2getregisters-method"></a>Метод ICorDebugRegisterSet2::GetRegisters
Получает значение каждого из регистров (для платформы, на котором в настоящее время выполняется код), указанный данной битовой маской.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `maskCount`  
 [in] Размер в байтах из `mask` массива.  
  
 `mask`  
 [in] Массив байтов, каждый бит соответствует регистру. Если бит равен 1, соответствующий регистр будет извлечено.  
  
 `regCount`  
 [in] Количество значений регистров требуется получить.  
  
 `regBuffer`  
 [out] Массив `CORDB_REGISTER` объектов, каждый из которых получает значение регистра.  
  
## <a name="remarks"></a>Примечания  
 `GetRegisters` Метод возвращает массив значений из регистров, которые определяются маски. Массив не содержит значения, регистров, маска не задано. Таким образом, размер `regBuffer` массива должно быть равно количеству 1 в маске. Если значение `regCount` слишком мал для количество регистрами, указанными в маске, значения регистры с более будет усечен из набора. Если `regCount` слишком велик, неиспользуемые `regBuffer` элементы будут изменены.  
  
 Если маска указывает недоступный регистр, для этого регистра возвращается неопределенное значение.  
  
 `ICorDebugRegisterSet2::GetRegisters` Метод необходим для платформ, которые имеют более 64 регистров. Например IA64 имеет 128 регистров общего назначения и 128 регистров с плавающей запятой, поэтому вам потребуется больше 64 бита в битовой маске.  
  
 Если у вас более чем 64 регистры, как в случае на платформах, например x86, `GetRegisters` метод фактически переводит байты в `mask` массив байтов, в `ULONG64` , а затем вызывает [ICorDebugRegisterSet:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) метод, который принимает `ULONG64` маски.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [Интерфейс ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
