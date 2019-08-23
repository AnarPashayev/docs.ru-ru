---
title: Интерфейс ICorDebug
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afbf480d69e97662b5963706bb8c192aec0325a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966297"
---
# <a name="icordebug-interface"></a><span data-ttu-id="38515-102">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="38515-102">ICorDebug Interface</span></span>
<span data-ttu-id="38515-103">Предоставляет методы, позволяющие разработчикам отлаживать приложения в среде среды CLR.</span><span class="sxs-lookup"><span data-stu-id="38515-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38515-104">Отладка в смешанном режиме (управляемый и машинный код) не поддерживается в Windows 95, Windows 98 или Windows ME или на платформах, отличных от x86 (например, IA64 и AMD64).</span><span class="sxs-lookup"><span data-stu-id="38515-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38515-105">Методы</span><span class="sxs-lookup"><span data-stu-id="38515-105">Methods</span></span>  
  
|<span data-ttu-id="38515-106">Метод</span><span class="sxs-lookup"><span data-stu-id="38515-106">Method</span></span>|<span data-ttu-id="38515-107">Описание</span><span class="sxs-lookup"><span data-stu-id="38515-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38515-108">Метод CanLaunchOrAttach</span><span class="sxs-lookup"><span data-stu-id="38515-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="38515-109">Определяет, возможен ли запуск нового процесса или присоединение к данному процессу в контексте текущей конфигурации компьютера и среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="38515-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="38515-110">Метод CreateProcess</span><span class="sxs-lookup"><span data-stu-id="38515-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="38515-111">Запускает процесс и его основной поток под управлением отладчика.</span><span class="sxs-lookup"><span data-stu-id="38515-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="38515-112">Метод DebugActiveProcess</span><span class="sxs-lookup"><span data-stu-id="38515-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="38515-113">Присоединяет отладчик к существующему процессу.</span><span class="sxs-lookup"><span data-stu-id="38515-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="38515-114">Метод EnumerateProcesses</span><span class="sxs-lookup"><span data-stu-id="38515-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="38515-115">Возвращает перечислитель для отлаживаемых процессов.</span><span class="sxs-lookup"><span data-stu-id="38515-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="38515-116">Метод GetProcess</span><span class="sxs-lookup"><span data-stu-id="38515-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="38515-117">Возвращает объект "ICorDebugProcess" с заданным ИДЕНТИФИКАТОРом процесса.</span><span class="sxs-lookup"><span data-stu-id="38515-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="38515-118">Метод Initialize</span><span class="sxs-lookup"><span data-stu-id="38515-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="38515-119">Инициализирует `ICorDebug` объект.</span><span class="sxs-lookup"><span data-stu-id="38515-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="38515-120">Метод SetManagedHandler</span><span class="sxs-lookup"><span data-stu-id="38515-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="38515-121">Указывает объект обработчика событий для управляемых событий.</span><span class="sxs-lookup"><span data-stu-id="38515-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="38515-122">Метод SetUnmanagedHandler</span><span class="sxs-lookup"><span data-stu-id="38515-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="38515-123">Указывает объект обработчика событий для неуправляемых событий.</span><span class="sxs-lookup"><span data-stu-id="38515-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="38515-124">Метод Terminate</span><span class="sxs-lookup"><span data-stu-id="38515-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="38515-125">`ICorDebug` Завершает объект.</span><span class="sxs-lookup"><span data-stu-id="38515-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38515-126">Примечания</span><span class="sxs-lookup"><span data-stu-id="38515-126">Remarks</span></span>  
 <span data-ttu-id="38515-127">`ICorDebug`представляет цикл обработки событий для процесса отладчика.</span><span class="sxs-lookup"><span data-stu-id="38515-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="38515-128">Перед освобождением этого интерфейса отладчик должен ожидать обратного вызова [ICorDebugManagedCallback:: ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) для всех отлаживаемых процессов.</span><span class="sxs-lookup"><span data-stu-id="38515-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="38515-129">`ICorDebug` Объект является начальным объектом для управления всеми дальнейшими управляемыми отладками.</span><span class="sxs-lookup"><span data-stu-id="38515-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="38515-130">В .NET Framework версиях 1,0 и 1,1 этот объект был объектом, `CoClass` созданным из com.</span><span class="sxs-lookup"><span data-stu-id="38515-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="38515-131">В .NET Framework версии 2,0 этот объект больше `CoClass` не является объектом.</span><span class="sxs-lookup"><span data-stu-id="38515-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="38515-132">Она должна быть создана функцией [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) , которая поддерживает больше версий.</span><span class="sxs-lookup"><span data-stu-id="38515-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="38515-133">Эта новая функция создания позволяет клиентам получить определенную реализацию `ICorDebug`, которая также эмулирует определенную версию API отладки.</span><span class="sxs-lookup"><span data-stu-id="38515-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38515-134">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="38515-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38515-135">Требования</span><span class="sxs-lookup"><span data-stu-id="38515-135">Requirements</span></span>  
 <span data-ttu-id="38515-136">**Платформ** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38515-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38515-137">**Заголовок.** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="38515-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38515-138">**Библиотечная** Коргуидс. lib</span><span class="sxs-lookup"><span data-stu-id="38515-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38515-139">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38515-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38515-140">См. также</span><span class="sxs-lookup"><span data-stu-id="38515-140">See also</span></span>

- [<span data-ttu-id="38515-141">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="38515-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
