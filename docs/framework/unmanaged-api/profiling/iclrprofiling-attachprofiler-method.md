---
title: Метод ICLRProfiling::AttachProfiler
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e3898fb836409df3b685d985d0d72ab63230a93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598698"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="22374-102">Метод ICLRProfiling::AttachProfiler</span><span class="sxs-lookup"><span data-stu-id="22374-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="22374-103">Подключает указанный профилировщик к указанному процессу.</span><span class="sxs-lookup"><span data-stu-id="22374-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22374-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="22374-104">Syntax</span></span>  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="22374-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="22374-105">Parameters</span></span>  
 `dwProfileeProcessID`  
 <span data-ttu-id="22374-106">[in] Идентификатор процесса, к которому следует подключить профилировщик.</span><span class="sxs-lookup"><span data-stu-id="22374-106">[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="22374-107">На 64-разрядном компьютере разрядность профилируемого процесса должна соответствовать разрядности инициирующего процесса, вызывающего метод `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="22374-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="22374-108">Если учетная запись пользователя, в которой вызывается метод `AttachProfiler`, имеет права администратора, целевым процессом может быть любой процесс в системе.</span><span class="sxs-lookup"><span data-stu-id="22374-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="22374-109">В противном случае целевой процесс должен принадлежать той же учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="22374-109">Otherwise, the target process must be owned by the same user account.</span></span>  
  
 `dwMillisecondsMax`  
 <span data-ttu-id="22374-110">[in] Время в миллисекундах для завершения выполнения `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="22374-110">[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="22374-111">Инициирующий процесс должен передавать интервал времени, которого заведомо будет достаточно, чтобы конкретный профилировщик завершил свою инициализацию.</span><span class="sxs-lookup"><span data-stu-id="22374-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>  
  
 `pClsidProfiler`  
 <span data-ttu-id="22374-112">[in] Указатель на идентификатор CLSID загружаемого профилировщика.</span><span class="sxs-lookup"><span data-stu-id="22374-112">[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="22374-113">Инициирующий процесс может повторно использовать эту память после возврата метода `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="22374-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>  
  
 `wszProfilerPath`  
 <span data-ttu-id="22374-114">[in] Полный путь к загружаемому DLL-файлу профилировщика.</span><span class="sxs-lookup"><span data-stu-id="22374-114">[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="22374-115">Эта строка должна содержать не более 260 символов, включая символ конца строки null.</span><span class="sxs-lookup"><span data-stu-id="22374-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="22374-116">Если в параметре `wszProfilerPath` задана пустая строка или значение null, среда CLR будет пытаться найти местоположение DLL-файла профилировщика путем поиска в реестре CLSID, на который указывает параметр `pClsidProfiler`.</span><span class="sxs-lookup"><span data-stu-id="22374-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="22374-117">[in] Указатель на данные, которые будет передаваться профилировщику [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="22374-117">[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="22374-118">Инициирующий процесс может повторно использовать эту память после возврата метода `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="22374-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="22374-119">Если параметр `pvClientData` имеет значение null, параметр `cbClientData` должен иметь значение 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="22374-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="22374-120">[in] Размер в байтах данных, на которые указывает `pvClientData`.</span><span class="sxs-lookup"><span data-stu-id="22374-120">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22374-121">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="22374-121">Return Value</span></span>  
 <span data-ttu-id="22374-122">Этот метод возвращает следующие значения HRESULT.</span><span class="sxs-lookup"><span data-stu-id="22374-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="22374-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22374-123">HRESULT</span></span>|<span data-ttu-id="22374-124">Описание</span><span class="sxs-lookup"><span data-stu-id="22374-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22374-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="22374-125">S_OK</span></span>|<span data-ttu-id="22374-126">Указанный профилировщик успешно подключен к целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="22374-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="22374-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="22374-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="22374-128">Уже существует активный профилировщик или профилировщик, подключенный к целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="22374-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="22374-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="22374-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="22374-130">Указанный профилировщик не поддерживает подключение.</span><span class="sxs-lookup"><span data-stu-id="22374-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="22374-131">Инициирующий процесс может попытаться подключить другой профилировщик.</span><span class="sxs-lookup"><span data-stu-id="22374-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="22374-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="22374-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="22374-133">Не удалось запросить подключение профилировщика, так как версия целевого процесса несовместима с текущим процессом, вызывающим метод `AttachProfiler`.</span><span class="sxs-lookup"><span data-stu-id="22374-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="22374-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="22374-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="22374-135">Пользователь инициирующего процесса не имеет доступа к целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="22374-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="22374-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="22374-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="22374-137">Пользователь инициирующего процесса не имеет привилегий, необходимых для подключения профилировщика к указанному целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="22374-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="22374-138">В журнале событий приложений могут содержаться дополнительные сведения.</span><span class="sxs-lookup"><span data-stu-id="22374-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="22374-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="22374-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="22374-140">Произошла ошибка при взаимодействии с целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="22374-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="22374-141">Обычно это происходит при завершении работы целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="22374-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="22374-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="22374-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="22374-143">Целевой процесс не существует, или в нем не запущена среда CLR, которая поддерживает подключение.</span><span class="sxs-lookup"><span data-stu-id="22374-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="22374-144">Это может указывать, что среда CLR была выгружена после вызова метода перечисления среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="22374-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="22374-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="22374-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="22374-146">Время ожидания истекло, а загрузка профилировщика не началась.</span><span class="sxs-lookup"><span data-stu-id="22374-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="22374-147">Можно повторить операцию подключения.</span><span class="sxs-lookup"><span data-stu-id="22374-147">You can retry the attach operation.</span></span> <span data-ttu-id="22374-148">Время ожидания истекает, когда метод завершения в целевом процессе выполняется дольше, чем задано в значении времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="22374-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="22374-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="22374-149">E_INVALIDARG</span></span>|<span data-ttu-id="22374-150">Как минимум один из следующих параметров имеет недопустимое значение.</span><span class="sxs-lookup"><span data-stu-id="22374-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="22374-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22374-151">E_FAIL</span></span>|<span data-ttu-id="22374-152">Произошел другой, не указанный сбой.</span><span class="sxs-lookup"><span data-stu-id="22374-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="22374-153">Другие коды ошибок</span><span class="sxs-lookup"><span data-stu-id="22374-153">Other error codes</span></span>|<span data-ttu-id="22374-154">Если профилировщик [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) метод возвращает значение HRESULT, указывающее на сбой, `AttachProfiler` возвращает то же самое значение HRESULT.</span><span class="sxs-lookup"><span data-stu-id="22374-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="22374-155">В этом случае E_NOTIMPL преобразуется в CORPROF_E_PROFILER_NOT_ATTACHABLE.</span><span class="sxs-lookup"><span data-stu-id="22374-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22374-156">Примечания</span><span class="sxs-lookup"><span data-stu-id="22374-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="22374-157">Управление памятью</span><span class="sxs-lookup"><span data-stu-id="22374-157">Memory Management</span></span>  
 <span data-ttu-id="22374-158">В соответствии с соглашениями COM объект, вызывающий метод `AttachProfiler` (например, код триггера, созданный разработчиком профилировщика), отвечает за выделение и освобождение памяти для данных, на которые указывает параметр `pvClientData`.</span><span class="sxs-lookup"><span data-stu-id="22374-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="22374-159">Когда среда CLR выполняет вызов `AttachProfiler`, создается копия памяти, на которую указывает `pvClientData`, которая затем передается в целевой процесс.</span><span class="sxs-lookup"><span data-stu-id="22374-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="22374-160">Когда среда CLR в целевом процессе получает собственную копию блока `pvClientData`, она передает этот блок в профилировщик с помощью метода `InitializeForAttach`, а затем освобождает свою копию блока `pvClientData` в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="22374-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22374-161">Требования</span><span class="sxs-lookup"><span data-stu-id="22374-161">Requirements</span></span>  
 <span data-ttu-id="22374-162">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22374-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22374-163">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22374-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22374-164">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22374-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22374-165">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22374-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22374-166">См. также</span><span class="sxs-lookup"><span data-stu-id="22374-166">See also</span></span>

- [<span data-ttu-id="22374-167">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="22374-167">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="22374-168">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="22374-168">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="22374-169">Интерфейсы профилирования</span><span class="sxs-lookup"><span data-stu-id="22374-169">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="22374-170">Профилирование</span><span class="sxs-lookup"><span data-stu-id="22374-170">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
