---
title: Метод ICorProfilerInfo4::RequestRevert
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e74cb663f968cc9b1b04a912307e3b4a12e86d4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748661"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="b2f7c-102">Метод ICorProfilerInfo4::RequestRevert</span><span class="sxs-lookup"><span data-stu-id="b2f7c-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="b2f7c-103">Восстанавливает исходные версии всех экземпляров указанных функций.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f7c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b2f7c-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2f7c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b2f7c-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="b2f7c-106">[in] Число функций для восстановления.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="b2f7c-107">[in] Указывает часть `moduleId` пар (`module`, `methodDef`), которые идентифицируют восстанавливаемые функции.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="b2f7c-108">[in] Указывает часть `methodId` пар (`module`, `methodDef`), которые идентифицируют восстанавливаемые функции.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="b2f7c-109">[out] Массив значений HRESULT, перечисленных в разделе «Значения HRESULT для состояния» далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="b2f7c-110">Каждое значение HRESULT указывает успех или сбой попытки восстановления исходного состояния каждой функции, указанной в параллельных массивах `moduleIds` и `methodIds`.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2f7c-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b2f7c-111">Return Value</span></span>  
 <span data-ttu-id="b2f7c-112">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b2f7c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2f7c-113">HRESULT</span></span>|<span data-ttu-id="b2f7c-114">Описание</span><span class="sxs-lookup"><span data-stu-id="b2f7c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2f7c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2f7c-115">S_OK</span></span>|<span data-ttu-id="b2f7c-116">Была предпринята попытка восстановления исходного состояния всех запросов; однако необходимо проверить массив возвращенных состояний, чтобы определить, какие функции были успешно восстановлены.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="b2f7c-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="b2f7c-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="b2f7c-118">Профилировщик должен реализовать [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) интерфейс для этого вызова, которые должны поддерживаться.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-118">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="b2f7c-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="b2f7c-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="b2f7c-120">Перекомпиляция JIT не была включена.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="b2f7c-121">Необходимо включить перекомпиляцию JIT во время инициализации с помощью [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) метод, чтобы задать `COR_PRF_ENABLE_REJIT` флаг.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="b2f7c-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b2f7c-122">E_INVALIDARG</span></span>|<span data-ttu-id="b2f7c-123">Параметр `cFunctions` имеет значение 0, либо один из параметров `moduleIds` и `methodIds` имеет значение `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="b2f7c-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b2f7c-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b2f7c-125">Среде CLR не удалось выполнить запрос, поскольку не хватило памяти.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="b2f7c-126">Значения HRESULT для состояния</span><span class="sxs-lookup"><span data-stu-id="b2f7c-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="b2f7c-127">Массив значений HRESULT для состояния</span><span class="sxs-lookup"><span data-stu-id="b2f7c-127">Status array HRESULT</span></span>|<span data-ttu-id="b2f7c-128">Описание</span><span class="sxs-lookup"><span data-stu-id="b2f7c-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="b2f7c-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2f7c-129">S_OK</span></span>|<span data-ttu-id="b2f7c-130">Соответствующая функция была успешно возвращена.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="b2f7c-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b2f7c-131">E_INVALIDARG</span></span>|<span data-ttu-id="b2f7c-132">Значение параметра `moduleID` или параметра `methodDef` — `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="b2f7c-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="b2f7c-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="b2f7c-134">Модуль еще не полностью загружен или находится в процессе выгрузки.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="b2f7c-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="b2f7c-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="b2f7c-136">Указанный модуль был создан динамически (например, с помощью `Reflection.Emit`).</span><span class="sxs-lookup"><span data-stu-id="b2f7c-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="b2f7c-137">Поэтому он не поддерживается данным методом.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="b2f7c-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="b2f7c-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="b2f7c-139">Среде CLR не удалось восстановить исходное состояние указанной функции, так как не найден соответствующий активный запрос перекомпиляции.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="b2f7c-140">Либо эта перекомпиляция никогда не запрашивалась, либо функция уже была восстановлена.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="b2f7c-141">Другое</span><span class="sxs-lookup"><span data-stu-id="b2f7c-141">Other</span></span>|<span data-ttu-id="b2f7c-142">Операционная система возвратила сбой за пределами среды CLR.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="b2f7c-143">Например, в случае сбоя системного вызова изменения защиты доступа к странице памяти будет отображаться ошибка операционной системы.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2f7c-144">Примечания</span><span class="sxs-lookup"><span data-stu-id="b2f7c-144">Remarks</span></span>  
 <span data-ttu-id="b2f7c-145">При следующем вызове любой из восстановленных функций будет запускаться исходная версия этой функции.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="b2f7c-146">Если функция уже выполняется, то будет завершено выполнение запущенной версии.</span><span class="sxs-lookup"><span data-stu-id="b2f7c-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2f7c-147">Требования</span><span class="sxs-lookup"><span data-stu-id="b2f7c-147">Requirements</span></span>  
 <span data-ttu-id="b2f7c-148">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2f7c-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2f7c-149">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b2f7c-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2f7c-150">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2f7c-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2f7c-151">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2f7c-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f7c-152">См. также</span><span class="sxs-lookup"><span data-stu-id="b2f7c-152">See also</span></span>

- [<span data-ttu-id="b2f7c-153">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="b2f7c-153">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="b2f7c-154">Интерфейсы профилирования</span><span class="sxs-lookup"><span data-stu-id="b2f7c-154">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b2f7c-155">Профилирование</span><span class="sxs-lookup"><span data-stu-id="b2f7c-155">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
