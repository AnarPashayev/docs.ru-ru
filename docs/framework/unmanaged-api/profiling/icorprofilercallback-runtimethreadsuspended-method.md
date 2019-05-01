---
title: Метод ICorProfilerCallback::RuntimeThreadSuspended
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0748802599926f4ec218362e6f7d086aab2d8f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041748"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="44bd7-102">Метод ICorProfilerCallback::RuntimeThreadSuspended</span><span class="sxs-lookup"><span data-stu-id="44bd7-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="44bd7-103">Уведомляет профилировщик, что указанный поток был приостановлен или будет приостановлено.</span><span class="sxs-lookup"><span data-stu-id="44bd7-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44bd7-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44bd7-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44bd7-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="44bd7-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="44bd7-106">[in] Идентификатор потока, который был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="44bd7-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44bd7-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="44bd7-107">Remarks</span></span>  
 <span data-ttu-id="44bd7-108">`RuntimeThreadSuspended` Уведомлений может произойти любое время между [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) и связанным [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) обратные вызовы.</span><span class="sxs-lookup"><span data-stu-id="44bd7-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="44bd7-109">Уведомления, которые выполняются между [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) и `RuntimeResumeStarted` для потоков, которые были запущены в неуправляемом коде и были приостановлены после входа в среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="44bd7-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="44bd7-110">Как правило этот обратный вызов происходит только в том случае, после приостановки потока.</span><span class="sxs-lookup"><span data-stu-id="44bd7-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="44bd7-111">Тем не менее если текущий выполняемый поток (поток, вызвавший этот обратный вызов) является тот, который приостанавливается, этот обратный вызов возникает непосредственно перед поток приостановлен.</span><span class="sxs-lookup"><span data-stu-id="44bd7-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44bd7-112">Требования</span><span class="sxs-lookup"><span data-stu-id="44bd7-112">Requirements</span></span>  
 <span data-ttu-id="44bd7-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44bd7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44bd7-114">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="44bd7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="44bd7-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44bd7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44bd7-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44bd7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44bd7-117">См. также</span><span class="sxs-lookup"><span data-stu-id="44bd7-117">See also</span></span>

- [<span data-ttu-id="44bd7-118">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="44bd7-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="44bd7-119">Метод RuntimeThreadResumed</span><span class="sxs-lookup"><span data-stu-id="44bd7-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
