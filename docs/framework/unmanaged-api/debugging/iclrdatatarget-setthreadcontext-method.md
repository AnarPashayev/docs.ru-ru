---
title: Метод ICLRDataTarget::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179132"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>Метод ICLRDataTarget::SetThreadContext
Устанавливает текущий контекст заданного потока в процессе целевого. Этот метод вызывается службами общего времени выполнения языка (CLR).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a>Параметры  
 `threadID`  
 (в) Идентификатор операционной системы потока в процессе целевого.  
  
 `contextSize`  
 (в) Размер контекста.  
  
 `context`  
 (в) Указатель на буфер, содержащий контекст.  
  
 Данные в `context` буфере будут находиться в `CONTEXT` формате структуры Win32. Контекст определяет данные регистра для процессоров, поэтому определение `CONTEXT` структуры Win32 зависит от архитектуры процессора. Обратитесь к файлу заголовка WinNT.h для `CONTEXT` определения структуры Win32.  
  
## <a name="remarks"></a>Remarks  
 Этот метод реализуется модулем записи отладчика.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** см. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** ClrData.idl, ClrData.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICLRDataTarget](iclrdatatarget-interface.md)
