---
title: Метод ICorDebugNativeFrame::SetIP
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 65de42a0b86e4b4593b7880e9dc290ce00007a40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709262"
---
# <a name="icordebugnativeframesetip-method"></a>Метод ICorDebugNativeFrame::SetIP

Задает указатель инструкции в указанном расположении смещения в машинном коде.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `nOffset`  
 окне Положение смещения в машинном коде.  
  
## <a name="remarks"></a>Комментарии  

 Вызывает метод, чтобы `SetIP` немедленно сделать недействительными все кадры и цепочки для текущего потока. Если отладчику требуются сведения о кадре после вызова `SetIP` , он должен выполнить новую трассировку стека.  
  
 [ICorDebug](icordebug-interface.md) попытается удержать кадр стека в допустимом состоянии. Однако даже если кадр находится в допустимом состоянии, то, что касается среды выполнения, могут возникнуть проблемы, например неинициализированные локальные переменные и т. д. Вызывающий объект отвечает за выполнение согласованности выполняющейся программы.  
  
 На 64-разрядных платформах указатель инструкции не может быть перемещен из `catch` блока или `finally` . Если `SetIP` вызывается метод для перемещения на 64-разрядной платформе, он возвращает значение HRESULT, указывающее на сбой.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел
