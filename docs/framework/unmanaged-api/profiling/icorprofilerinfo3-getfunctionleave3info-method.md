---
title: Метод ICorProfilerInfo3::GetFunctionLeave3Info
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: f365a95b0859f4f97dab96ec85af6d7dfb96d8e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721625"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="c9a21-102">Метод ICorProfilerInfo3::GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="c9a21-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>

<span data-ttu-id="c9a21-103">Предоставляет кадр стека и возвращаемое значение функции, о которой сообщается профилировщику функцией [функции FunctionLeave3WithInfo](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="c9a21-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="c9a21-104">Этот метод может быть вызван только во время обратного вызова `FunctionLeave3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="c9a21-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9a21-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c9a21-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9a21-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c9a21-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="c9a21-107">окне Возвращаемое значение `FunctionID` функции.</span><span class="sxs-lookup"><span data-stu-id="c9a21-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="c9a21-108">[in] Непрозрачный дескриптор, представляющий сведения об указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="c9a21-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="c9a21-109">Профилировщик должен предоставлять те же `eltInfo` данные, что и профилировщик, с помощью функции [FunctionLeave3WithInfo](functionleave3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="c9a21-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="c9a21-110">[out] Непрозрачный дескриптор, представляющий универсальные сведения об указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="c9a21-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="c9a21-111">Этот дескриптор допустим только во время обратного вызова `FunctionLeave3WithInfo`, в котором профилировщик вызывал метод `GetFunctionLeave3Info`.</span><span class="sxs-lookup"><span data-stu-id="c9a21-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="c9a21-112">заполняет Указатель на структуру [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , которая содержит значение, возвращаемое функцией.</span><span class="sxs-lookup"><span data-stu-id="c9a21-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="c9a21-113">Чтобы получить доступ к сведениям о возвращаемом значении, `COR_PRF_ENABLE_FUNCTION_RETVAL` необходимо установить флаг.</span><span class="sxs-lookup"><span data-stu-id="c9a21-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="c9a21-114">Профилировщик может использовать [метод ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий.</span><span class="sxs-lookup"><span data-stu-id="c9a21-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9a21-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="c9a21-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9a21-116">Требования</span><span class="sxs-lookup"><span data-stu-id="c9a21-116">Requirements</span></span>  

 <span data-ttu-id="c9a21-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9a21-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9a21-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9a21-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9a21-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9a21-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9a21-120">**.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9a21-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a21-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c9a21-121">See also</span></span>

- [<span data-ttu-id="c9a21-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9a21-122">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="c9a21-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9a21-123">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="c9a21-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9a21-124">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="c9a21-125">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="c9a21-125">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c9a21-126">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c9a21-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c9a21-127">Профилирование</span><span class="sxs-lookup"><span data-stu-id="c9a21-127">Profiling</span></span>](index.md)
