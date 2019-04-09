---
title: Метод ICorProfilerFunctionControl::SetCodegenFlags
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12f91bdd264135eb0ff3a48e15611cf5a0e3c064
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104446"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="e4b7b-102">Метод ICorProfilerFunctionControl::SetCodegenFlags</span><span class="sxs-lookup"><span data-stu-id="e4b7b-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="e4b7b-103">Задает один или несколько флагов из [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) функция перекомпилировать перечисления с целью управления генерацией кода для just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="e4b7b-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4b7b-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e4b7b-104">Syntax</span></span>  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4b7b-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e4b7b-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="e4b7b-106">[in] Один или несколько флагов из [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) перечисления.</span><span class="sxs-lookup"><span data-stu-id="e4b7b-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4b7b-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="e4b7b-107">Remarks</span></span>  
 <span data-ttu-id="e4b7b-108">Профилировщик получает экземпляр этого интерфейса через [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="e4b7b-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> `SetCodegenFlags` <span data-ttu-id="e4b7b-109">позволяет профилировщику управляют созданием кода для перекомпилированной функции.</span><span class="sxs-lookup"><span data-stu-id="e4b7b-109">allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="e4b7b-110">Как и все другие JIT перекомпиляции параметры, флаги создания кода применяются ко всем экземплярам функции.</span><span class="sxs-lookup"><span data-stu-id="e4b7b-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="e4b7b-111">JIT-компилятор рассматривает эти флаги компиляции, а также другие флаги, указанные для других источников, при компиляции функции.</span><span class="sxs-lookup"><span data-stu-id="e4b7b-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="e4b7b-112">Другие источники включают отладчик, глобальные флаги задано с помощью профилировщика при запуске, с помощью [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) метод (со значениями `COR_PRF_DISABLE_INLINING` и `COR_PRF_DISABLE_OPTIMIZATIONS`) и профилировщика [ ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="e4b7b-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="e4b7b-113">JIT-компилятор предоставляет приоритет к источнику, который запрашивает наименьший объем оптимизации.</span><span class="sxs-lookup"><span data-stu-id="e4b7b-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="e4b7b-114">Например, если профилировщик указывает `COR_PRF_DISABLE_INLINING` во время запуска, но не указывает `COR_PRF_CODEGEN_DISABLE_INLINING` в [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) обратного вызова, встраивание по-прежнему отключен.</span><span class="sxs-lookup"><span data-stu-id="e4b7b-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="e4b7b-115">Аналогичным образом Если не указано профилировщик `COR_PRF_CODEGEN_DISABLE_INLINING` в `SetCodegenFlags`, но затем отключает встраивание с помощью [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) обратного вызова, встраивание отключен.</span><span class="sxs-lookup"><span data-stu-id="e4b7b-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4b7b-116">Требования</span><span class="sxs-lookup"><span data-stu-id="e4b7b-116">Requirements</span></span>  
 <span data-ttu-id="e4b7b-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4b7b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4b7b-118">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4b7b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4b7b-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4b7b-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e4b7b-120">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e4b7b-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e4b7b-121">См. также</span><span class="sxs-lookup"><span data-stu-id="e4b7b-121">See also</span></span>

- [<span data-ttu-id="e4b7b-122">Интерфейс ICorProfilerFunctionControl</span><span class="sxs-lookup"><span data-stu-id="e4b7b-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
