---
title: Метод ICorDebug::SetUnmanagedHandler
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: 0bce14a6853c872d27057b9fffc32b54c59abf13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723393"
---
# <a name="icordebugsetunmanagedhandler-method"></a>Метод ICorDebug::SetUnmanagedHandler

Указывает объект обработчика событий для неуправляемых событий.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `pCallback`  
 окне Указатель на объект [икордебугунманажедкаллбакк](icordebugunmanagedcallback-interface.md) , представляющий обработчик событий для неуправляемых событий.  
  
## <a name="remarks"></a>Комментарии  

 Объект обработчика событий для неуправляемых событий должен быть задан после вызова метода [ICorDebug:: Initialize](icordebug-initialize-method.md) и перед вызовом [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) или [ICorDebug::D ебугактивепроцесс](icordebug-debugactiveprocess-method.md). Однако для устаревших целей не требуется задавать объект обработчика событий для неуправляемых событий до тех пор, пока не будет вызвано первое собственное событие отладки. В частности, если `ICorDebug::CreateProcess` задан флаг CREATE_SUSPENDED, события отладки машинного кода не могут быть отправлены, пока основной поток не возобновит работу.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorDebug](icordebug-interface.md)
