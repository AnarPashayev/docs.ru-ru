---
title: Метод ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73321a28b1c61775d08e2c60ee2b9a863b8250dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121684"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="45c3f-102">Метод ICorProfilerInfo3::SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="45c3f-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="45c3f-103">Задает реализуемые профилировщиком функции, которые будут вызываться в [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), и [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) функции.</span><span class="sxs-lookup"><span data-stu-id="45c3f-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45c3f-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="45c3f-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45c3f-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="45c3f-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="45c3f-106">[in] Указатель на реализацию для использования в качестве `FunctionEnter3` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="45c3f-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="45c3f-107">[in] Указатель на реализацию для использования в качестве `FunctionLeave3` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="45c3f-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="45c3f-108">[in] Указатель на реализацию для использования в качестве `FunctionTailcall3` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="45c3f-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45c3f-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="45c3f-109">Remarks</span></span>  
 <span data-ttu-id="45c3f-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), и [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) обработчики не предоставляют стека кадра и проверка аргументов.</span><span class="sxs-lookup"><span data-stu-id="45c3f-110">[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="45c3f-111">Доступ к этим сведениям `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, и/или `COR_PRF_ENABLE_FRAME_INFO` флаги должны быть заданы.</span><span class="sxs-lookup"><span data-stu-id="45c3f-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="45c3f-112">Можно использовать профилировщик [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) метод, чтобы задать флаги событий, а затем используйте [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) метода для регистрации вашей Реализация этой функции.</span><span class="sxs-lookup"><span data-stu-id="45c3f-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="45c3f-113">Одновременно может быть активным только один набор обратных вызовов, и новая версия имеет более высокий приоритет.</span><span class="sxs-lookup"><span data-stu-id="45c3f-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="45c3f-114">Таким образом Если профилировщик вызывает оба [метод SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) и `SetEnterLeaveFunctionHooks3` метода `SetEnterLeaveFunctionHooks3` используется.</span><span class="sxs-lookup"><span data-stu-id="45c3f-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="45c3f-115">`SetEnterLeaveFunctionHooks3` Метод может вызываться только из профилировщика [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="45c3f-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45c3f-116">Требования</span><span class="sxs-lookup"><span data-stu-id="45c3f-116">Requirements</span></span>  
 <span data-ttu-id="45c3f-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45c3f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45c3f-118">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45c3f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45c3f-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45c3f-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="45c3f-120">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="45c3f-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45c3f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="45c3f-121">See also</span></span>

- [<span data-ttu-id="45c3f-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="45c3f-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="45c3f-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="45c3f-123">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="45c3f-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="45c3f-124">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="45c3f-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="45c3f-125">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="45c3f-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="45c3f-126">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="45c3f-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="45c3f-127">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="45c3f-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="45c3f-128">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="45c3f-129">Глобальные статические функции профилирования</span><span class="sxs-lookup"><span data-stu-id="45c3f-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [<span data-ttu-id="45c3f-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="45c3f-130">ICorProfilerInfo3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="45c3f-131">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="45c3f-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="45c3f-132">Профилирование</span><span class="sxs-lookup"><span data-stu-id="45c3f-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
