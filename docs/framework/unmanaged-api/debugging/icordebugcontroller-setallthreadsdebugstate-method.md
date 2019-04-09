---
title: Метод ICorDebugController::SetAllThreadsDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 280dc3f0271d7326fe4c22b813abebfd4d45c89e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138480"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="7dd68-102">Метод ICorDebugController::SetAllThreadsDebugState</span><span class="sxs-lookup"><span data-stu-id="7dd68-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="7dd68-103">Задает состояние отладки все управляемые потоки в процессе.</span><span class="sxs-lookup"><span data-stu-id="7dd68-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd68-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7dd68-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dd68-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="7dd68-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="7dd68-106">[in] Значение перечисления «CorDebugThreadState», которое указывает состояние потока для отладки.</span><span class="sxs-lookup"><span data-stu-id="7dd68-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="7dd68-107">[in] Указатель на объект «ICorDebugThread», который представляет поток, который требуется исключить из параметра состояние отладки.</span><span class="sxs-lookup"><span data-stu-id="7dd68-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="7dd68-108">Если это значение равно null, ни один поток не исключен.</span><span class="sxs-lookup"><span data-stu-id="7dd68-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dd68-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="7dd68-109">Remarks</span></span>  
 <span data-ttu-id="7dd68-110">`SetAllThreadsDebugState` Метод может повлиять на потоки, которые не видны через [метод EnumerateThreads](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), поэтому потоки, которые были приостановлены с `SetAllThreadsDebugState` метод потребуется возобновления, с `SetAllThreadsDebugState` метод.</span><span class="sxs-lookup"><span data-stu-id="7dd68-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dd68-111">Требования</span><span class="sxs-lookup"><span data-stu-id="7dd68-111">Requirements</span></span>  
 <span data-ttu-id="7dd68-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dd68-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dd68-113">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7dd68-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7dd68-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dd68-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7dd68-115">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7dd68-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7dd68-116">См. также</span><span class="sxs-lookup"><span data-stu-id="7dd68-116">See also</span></span>
