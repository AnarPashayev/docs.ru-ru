---
title: Метод ICorDebugProcess::WriteMemory
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
ms.openlocfilehash: 18416954517c3cac09d013b8075bd097305a1dca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673973"
---
# <a name="icordebugprocesswritememory-method"></a>Метод ICorDebugProcess::WriteMemory

Записывает данные в область памяти в этом процессе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a>Параметры  

 `address`  
 окне `CORDB_ADDRESS` Значение, являющееся базовым адресом области памяти, в которую записываются данные. Перед передачей данных система проверяет, что область памяти указанного размера, начиная с базового адреса, доступна для записи. Если он недоступен, метод завершается ошибкой.  
  
 `size`  
 окне Число байтов, записываемых в область памяти.  
  
 `buffer`  
 окне Буфер, содержащий записываемые данные.  
  
 `written`  
 заполняет Указатель на переменную, которая получает число байтов, записанных в область памяти в этом процессе. Если `written` аргумент имеет значение null, этот параметр игнорируется.  
  
## <a name="remarks"></a>Комментарии  

 Данные автоматически записываются за любые точки останова. В .NET Framework версии 2,0 отладчики машинного кода не должны использовать этот метод для вставки точек останова в поток инструкций. Вместо этого используйте [ICorDebugProcess2:: сетунманажедбреакпоинт](icordebugprocess2-setunmanagedbreakpoint-method.md) .  
  
 `WriteMemory`Метод следует использовать только за пределами управляемого кода. Этот метод может повредить среду выполнения при неправильном использовании.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
