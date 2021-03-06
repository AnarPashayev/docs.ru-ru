---
title: Метод ICorDebugController::HasQueuedCallbacks
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: bd623f8bee2feafebe80c0c7513bcfb33d6ad367
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707923"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>Метод ICorDebugController::HasQueuedCallbacks

Возвращает значение, указывающее, находятся ли в очереди управляемые обратные вызовы для указанного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>Параметры  

 `pThread`  
 окне Указатель на объект "ICorDebugThread", представляющий поток.  
  
 `pbQueued`  
 заполняет Указатель на значение, равное, `true` Если какие-либо управляемые обратные вызовы в настоящий момент поставлены в очередь для указанного потока; в противном случае — `false` .  
  
 Если для параметра задано значение NULL `pThread` , `HasQueuedCallbacks` функция возвратит, если в `true` настоящий момент в очереди есть управляемые обратные вызовы для любого потока.  
  
## <a name="remarks"></a>Комментарии  

 Обратные вызовы будут отправлены по одному, каждый раз, когда вызывается [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) . Отладчик может проверить этот флаг, если он хочет сообщить о нескольких событиях отладки, происходящих одновременно.  
  
 Когда события отладки помещаются в очередь, они уже были выполнены, поэтому отладчик должен очистить всю очередь, чтобы убедиться в состоянии отлаживаемой программы. (Вызов `ICorDebugController::Continue` для очистки очереди.) Например, если очередь содержит два события отладки в потоке *x*, а отладчик приостанавливает поток *x* после первого события отладки и затем вызывает `ICorDebugController::Continue` , второе событие отладки для потока *x* будет отправлено, хотя поток был приостановлен.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел
