---
title: Метод ICorDebugThread::SetDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15e18888e307a14c4396966afc0a623e1acba104
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332815"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="47853-102">Метод ICorDebugThread::SetDebugState</span><span class="sxs-lookup"><span data-stu-id="47853-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="47853-103">Устанавливает флаги, описывающие состояние отладки этого ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="47853-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47853-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="47853-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47853-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="47853-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="47853-106">окне Побитовое сочетание значений перечисления Кордебугсреадстате, определяющих состояние отладки этого потока.</span><span class="sxs-lookup"><span data-stu-id="47853-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47853-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="47853-107">Remarks</span></span>  
 <span data-ttu-id="47853-108">`SetDebugState` задает текущее состояние отладки потока.</span><span class="sxs-lookup"><span data-stu-id="47853-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="47853-109">("Текущее состояние отладки" представляет состояние отладки, если процесс должен быть продолжен, а не фактическое текущее состояние.) Нормальное значение для этого параметра — THREAD_RUN.</span><span class="sxs-lookup"><span data-stu-id="47853-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="47853-110">Только отладчик может повлиять на состояние отладки потока.</span><span class="sxs-lookup"><span data-stu-id="47853-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="47853-111">Состояния отладки продолжают выполняться, поэтому, если вы хотите, чтобы поток THREAD_SUSPENDed над несколькими, вы можете установить его один раз, а затем не беспокоиться о нем.</span><span class="sxs-lookup"><span data-stu-id="47853-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="47853-112">Приостановка потоков и возобновление процесса могут привести к взаимоблокировке, хотя обычно маловероятно.</span><span class="sxs-lookup"><span data-stu-id="47853-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="47853-113">Это встроенное качество потоков и процессов, а именно-проектирование.</span><span class="sxs-lookup"><span data-stu-id="47853-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="47853-114">Отладчик может асинхронно приостанавливать и возобновлять потоки, чтобы нарушить взаимоблокировку.</span><span class="sxs-lookup"><span data-stu-id="47853-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="47853-115">Если пользовательское состояние потока включает USER_UNSAFE_POINT, поток может блокировать сборку мусора (GC).</span><span class="sxs-lookup"><span data-stu-id="47853-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="47853-116">Это означает, что приостановленный поток имеет намного более высокий шанс возникновения взаимоблокировки.</span><span class="sxs-lookup"><span data-stu-id="47853-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="47853-117">Это может не влиять на события отладки, уже поставленные в очередь.</span><span class="sxs-lookup"><span data-stu-id="47853-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="47853-118">Таким образом, отладчик должен очистить всю очередь событий (вызвав [ICorDebugController:: хаскуеуедкаллбаккс](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) перед приостановкой или возобновлением потоков.</span><span class="sxs-lookup"><span data-stu-id="47853-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="47853-119">В противном случае он может получить события в потоке, который предположительно уже приостановлен.</span><span class="sxs-lookup"><span data-stu-id="47853-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47853-120">Требования</span><span class="sxs-lookup"><span data-stu-id="47853-120">Requirements</span></span>  
 <span data-ttu-id="47853-121">**Платформ** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47853-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47853-122">**Заголовок.** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="47853-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47853-123">**Библиотечная** Коргуидс. lib</span><span class="sxs-lookup"><span data-stu-id="47853-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47853-124">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47853-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
