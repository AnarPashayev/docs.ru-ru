---
title: Метод ICorProfilerCallback::UnmanagedToManagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fa7dfe101b07ae6eb8d58daad85954f0ce29b02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747052"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="b47bd-102">Метод ICorProfilerCallback::UnmanagedToManagedTransition</span><span class="sxs-lookup"><span data-stu-id="b47bd-102">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>
<span data-ttu-id="b47bd-103">Уведомляет профилировщик о переход из неуправляемого кода в управляемый код.</span><span class="sxs-lookup"><span data-stu-id="b47bd-103">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b47bd-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b47bd-104">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b47bd-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b47bd-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b47bd-106">[in] Идентификатор функции, которая вызывается.</span><span class="sxs-lookup"><span data-stu-id="b47bd-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="b47bd-107">[in] Значение [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) перечисление, указывающее, произошла ли переход из-за вызова управляемого кода из неуправляемого кода или из-за возврат из неуправляемой функции, вызываемой управляемыми.</span><span class="sxs-lookup"><span data-stu-id="b47bd-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b47bd-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="b47bd-108">Remarks</span></span>  
 <span data-ttu-id="b47bd-109">Если значение `reason` является COR_PRF_TRANSITION_RETURN и `functionId` не равно NULL, функция идентификатор является то, что неуправляемой функции и никогда не будет выполняться компиляция с помощью компилятора just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="b47bd-109">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="b47bd-110">Неуправляемые функции имеют некоторые основные сведения, связанные с ними, такие как имя и некоторые метаданные.</span><span class="sxs-lookup"><span data-stu-id="b47bd-110">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="b47bd-111">Если значение `reason` является COR_PRF_TRANSITION_CALL, может оказаться, что вызываемая функция (то есть управляемую функцию) еще не JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="b47bd-111">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b47bd-112">Требования</span><span class="sxs-lookup"><span data-stu-id="b47bd-112">Requirements</span></span>  
 <span data-ttu-id="b47bd-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b47bd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b47bd-114">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b47bd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b47bd-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b47bd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b47bd-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b47bd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b47bd-117">См. также</span><span class="sxs-lookup"><span data-stu-id="b47bd-117">See also</span></span>

- [<span data-ttu-id="b47bd-118">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b47bd-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b47bd-119">Метод ManagedToUnmanagedTransition</span><span class="sxs-lookup"><span data-stu-id="b47bd-119">ManagedToUnmanagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="b47bd-120">Использование явного вызова Pinvoke в C++ (атрибут DllImport)</span><span class="sxs-lookup"><span data-stu-id="b47bd-120">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="b47bd-121">Использование взаимодействия языка C++ (неявный PInvoke)</span><span class="sxs-lookup"><span data-stu-id="b47bd-121">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
