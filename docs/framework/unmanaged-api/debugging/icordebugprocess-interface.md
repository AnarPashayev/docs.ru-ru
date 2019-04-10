---
title: Интерфейс ICorDebugProcess
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46d96d66f16cd956d8fab1afe00486d564e37953
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216799"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="665bc-102">Интерфейс ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="665bc-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="665bc-103">Представляет процесс, выполняющий управляемый код.</span><span class="sxs-lookup"><span data-stu-id="665bc-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="665bc-104">Этот интерфейс является подклассом ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="665bc-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="665bc-105">Методы</span><span class="sxs-lookup"><span data-stu-id="665bc-105">Methods</span></span>  
  
|<span data-ttu-id="665bc-106">Метод</span><span class="sxs-lookup"><span data-stu-id="665bc-106">Method</span></span>|<span data-ttu-id="665bc-107">Описание</span><span class="sxs-lookup"><span data-stu-id="665bc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="665bc-108">Метод ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="665bc-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="665bc-109">Очищает текущее неуправляемое исключение в данном потоке.</span><span class="sxs-lookup"><span data-stu-id="665bc-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="665bc-110">Метод EnableLogMessages</span><span class="sxs-lookup"><span data-stu-id="665bc-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="665bc-111">Включает и отключает отправку сообщений журнала в отладчик.</span><span class="sxs-lookup"><span data-stu-id="665bc-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="665bc-112">Метод EnumerateAppDomains</span><span class="sxs-lookup"><span data-stu-id="665bc-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="665bc-113">Перечисляет все домены приложений в процессе.</span><span class="sxs-lookup"><span data-stu-id="665bc-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="665bc-114">Метод EnumerateObjects</span><span class="sxs-lookup"><span data-stu-id="665bc-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="665bc-115">Не реализовано.</span><span class="sxs-lookup"><span data-stu-id="665bc-115">Not implemented.</span></span>|  
|[<span data-ttu-id="665bc-116">Метод GetHandle</span><span class="sxs-lookup"><span data-stu-id="665bc-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="665bc-117">Получает дескриптор процесса.</span><span class="sxs-lookup"><span data-stu-id="665bc-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="665bc-118">Метод GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="665bc-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="665bc-119">Получает идентификатор потока операционной системы (ОС) для внутреннего вспомогательного потока отладчика.</span><span class="sxs-lookup"><span data-stu-id="665bc-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="665bc-120">Метод GetID</span><span class="sxs-lookup"><span data-stu-id="665bc-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="665bc-121">Получает идентификатор процесса операционной системы (ОС).</span><span class="sxs-lookup"><span data-stu-id="665bc-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="665bc-122">Метод GetObject</span><span class="sxs-lookup"><span data-stu-id="665bc-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="665bc-123">Не реализовано.</span><span class="sxs-lookup"><span data-stu-id="665bc-123">Not implemented.</span></span>|  
|[<span data-ttu-id="665bc-124">Метод GetThread</span><span class="sxs-lookup"><span data-stu-id="665bc-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="665bc-125">Получает ICorDebugThread идентификатор экземпляра, имеющий указанный поток операционной системы.</span><span class="sxs-lookup"><span data-stu-id="665bc-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="665bc-126">Метод GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="665bc-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="665bc-127">Получает контекст для данного потока.</span><span class="sxs-lookup"><span data-stu-id="665bc-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="665bc-128">Метод IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="665bc-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="665bc-129">Определяет, приостановлено ли поток в результате остановки процесса отладчиком.</span><span class="sxs-lookup"><span data-stu-id="665bc-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="665bc-130">Метод IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="665bc-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="665bc-131">Определяет, является ли адрес в заглушке, вызовет переход к управляемому коду.</span><span class="sxs-lookup"><span data-stu-id="665bc-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="665bc-132">Метод ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="665bc-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="665bc-133">Задает уровень серьезности, указанный журнал коммутатора.</span><span class="sxs-lookup"><span data-stu-id="665bc-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="665bc-134">Метод ReadMemory</span><span class="sxs-lookup"><span data-stu-id="665bc-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="665bc-135">Считывает памяти из процесса.</span><span class="sxs-lookup"><span data-stu-id="665bc-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="665bc-136">Метод SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="665bc-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="665bc-137">Задает контекст для данного потока.</span><span class="sxs-lookup"><span data-stu-id="665bc-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="665bc-138">Метод ThreadForFiberCookie</span><span class="sxs-lookup"><span data-stu-id="665bc-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="665bc-139">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="665bc-139">Deprecated.</span></span>|  
|[<span data-ttu-id="665bc-140">Метод WriteMemory</span><span class="sxs-lookup"><span data-stu-id="665bc-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="665bc-141">Записывает данные в области памяти в процессе.</span><span class="sxs-lookup"><span data-stu-id="665bc-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="665bc-142">Примечания</span><span class="sxs-lookup"><span data-stu-id="665bc-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="665bc-143">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="665bc-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="665bc-144">Требования</span><span class="sxs-lookup"><span data-stu-id="665bc-144">Requirements</span></span>  
 <span data-ttu-id="665bc-145">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="665bc-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="665bc-146">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="665bc-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="665bc-147">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="665bc-147">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="665bc-148">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="665bc-148">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="665bc-149">См. также</span><span class="sxs-lookup"><span data-stu-id="665bc-149">See also</span></span>

- [<span data-ttu-id="665bc-150">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="665bc-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="665bc-151">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="665bc-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
