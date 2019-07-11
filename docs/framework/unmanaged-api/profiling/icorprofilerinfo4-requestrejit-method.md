---
title: Метод ICorProfilerInfo4::RequestReJIT
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f4ad89c821e9b8e9b52e3369a347eae27ab2231
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748673"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="8016d-102">Метод ICorProfilerInfo4::RequestReJIT</span><span class="sxs-lookup"><span data-stu-id="8016d-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="8016d-103">Запрашивает перекомпиляцию JIT всех экземпляров указанных функций.</span><span class="sxs-lookup"><span data-stu-id="8016d-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8016d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8016d-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8016d-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="8016d-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="8016d-106">[in] Число функций для перекомпиляции.</span><span class="sxs-lookup"><span data-stu-id="8016d-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="8016d-107">[in] Указывает часть `moduleId` пар (`module`, `methodDef`), которые идентифицируют перекомпилируемые функции.</span><span class="sxs-lookup"><span data-stu-id="8016d-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="8016d-108">[in] Указывает часть `methodId` пар (`module`, `methodDef`), которые идентифицируют перекомпилируемые функции.</span><span class="sxs-lookup"><span data-stu-id="8016d-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8016d-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8016d-109">Return Value</span></span>  
 <span data-ttu-id="8016d-110">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="8016d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8016d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8016d-111">HRESULT</span></span>|<span data-ttu-id="8016d-112">Описание</span><span class="sxs-lookup"><span data-stu-id="8016d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8016d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8016d-113">S_OK</span></span>|<span data-ttu-id="8016d-114">Была предпринята попытка пометить все методы для перекомпиляции JIT.</span><span class="sxs-lookup"><span data-stu-id="8016d-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="8016d-115">Профилировщик должен реализовать [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) метод, чтобы определить, какие методы были успешно помечены для перекомпиляции JIT.</span><span class="sxs-lookup"><span data-stu-id="8016d-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="8016d-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="8016d-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="8016d-117">Профилировщик должен реализовать [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) интерфейс для этого вызова, которые должны поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="8016d-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="8016d-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="8016d-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="8016d-119">Перекомпиляция JIT не была включена.</span><span class="sxs-lookup"><span data-stu-id="8016d-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="8016d-120">Необходимо включить перекомпиляцию JIT во время инициализации с помощью [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) метод, чтобы задать `COR_PRF_ENABLE_REJIT` флаг.</span><span class="sxs-lookup"><span data-stu-id="8016d-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="8016d-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8016d-121">E_INVALIDARG</span></span>|<span data-ttu-id="8016d-122">Параметр `cFunctions` имеет значение 0, либо один из параметров `moduleIds` и `methodIds` имеет значение `NULL`.</span><span class="sxs-lookup"><span data-stu-id="8016d-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="8016d-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8016d-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8016d-124">Среде CLR не удалось выполнить запрос, поскольку не хватило памяти.</span><span class="sxs-lookup"><span data-stu-id="8016d-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8016d-125">Примечания</span><span class="sxs-lookup"><span data-stu-id="8016d-125">Remarks</span></span>  
 <span data-ttu-id="8016d-126">Вызовите `RequestReJIT`, чтобы среда выполнения перекомпилировала указанный набор функций.</span><span class="sxs-lookup"><span data-stu-id="8016d-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="8016d-127">Профилировщик кода затем можно использовать [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) интерфейс изменений в код, создаваемый при перекомпиляции функций.</span><span class="sxs-lookup"><span data-stu-id="8016d-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="8016d-128">Это не влияет на функции, выполняющиеся в текущий момент; только на будущие вызовы функций.</span><span class="sxs-lookup"><span data-stu-id="8016d-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="8016d-129">Если любая из указанных функций уже подверглась перекомпиляции JIT ранее, то запрос перекомпиляции эквивалентен восстановлению исходного состояния и перекомпиляции этой функции.</span><span class="sxs-lookup"><span data-stu-id="8016d-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="8016d-130">Для сохранения возможности восстановления исходного состояния, когда JIT-компилятор компилирует исходную версию функции, он рассматривает только исходные версии вызывающих ее объектов для встраиваемых решений.</span><span class="sxs-lookup"><span data-stu-id="8016d-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="8016d-131">Когда JIT-компилятор перекомпилирует функцию, он рассматривает текущие версии (перекомпилированные или исходные) ее  вызывающих объектов для встраивания.</span><span class="sxs-lookup"><span data-stu-id="8016d-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="8016d-132">Профилировщик обычно вызывает `RequestReJIT` в ответ на ввод пользователя, запрашивающего инструментирование профилировщиком одного или нескольких методов.</span><span class="sxs-lookup"><span data-stu-id="8016d-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="8016d-133">Обычно `RequestReJIT` приостанавливает среду выполнения для выполнения некоторых операций и потенциально может инициировать сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="8016d-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="8016d-134">Таким образом, профилировщик должен вызывать `RequestReJIT` из потока, созданного им ранее, а не из потока, созданного средой CLR, который в текущий момент выполняет обратный вызов профилировщика.</span><span class="sxs-lookup"><span data-stu-id="8016d-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8016d-135">Требования</span><span class="sxs-lookup"><span data-stu-id="8016d-135">Requirements</span></span>  
 <span data-ttu-id="8016d-136">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8016d-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8016d-137">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8016d-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8016d-138">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8016d-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8016d-139">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8016d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8016d-140">См. также</span><span class="sxs-lookup"><span data-stu-id="8016d-140">See also</span></span>

- [<span data-ttu-id="8016d-141">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="8016d-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="8016d-142">Интерфейсы профилирования</span><span class="sxs-lookup"><span data-stu-id="8016d-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="8016d-143">Профилирование</span><span class="sxs-lookup"><span data-stu-id="8016d-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
