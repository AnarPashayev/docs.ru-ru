---
title: Интерфейс ICorDebugManagedCallback2
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1ecfea208f87f53f15fcc4cdafb58341c293e43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763832"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="47640-102">Интерфейс ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="47640-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="47640-103">Предоставляет методы для поддержки обработки исключений отладчика и управляемых помощников по отладке (MDA).</span><span class="sxs-lookup"><span data-stu-id="47640-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="47640-104">`ICorDebugManagedCallback2` является логическим расширением [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="47640-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47640-105">Методы</span><span class="sxs-lookup"><span data-stu-id="47640-105">Methods</span></span>  
  
|<span data-ttu-id="47640-106">Метод</span><span class="sxs-lookup"><span data-stu-id="47640-106">Method</span></span>|<span data-ttu-id="47640-107">Описание</span><span class="sxs-lookup"><span data-stu-id="47640-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47640-108">Метод ChangeConnection</span><span class="sxs-lookup"><span data-stu-id="47640-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="47640-109">Уведомляет отладчик о том, что изменился набор задач, связанных с указанным соединением.</span><span class="sxs-lookup"><span data-stu-id="47640-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="47640-110">Метод CreateConnection</span><span class="sxs-lookup"><span data-stu-id="47640-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="47640-111">Уведомляет отладчик для создания нового соединения.</span><span class="sxs-lookup"><span data-stu-id="47640-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="47640-112">Метод DestroyConnection</span><span class="sxs-lookup"><span data-stu-id="47640-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="47640-113">Уведомляет отладчик о том, что указанное соединение было прервано.</span><span class="sxs-lookup"><span data-stu-id="47640-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="47640-114">Метод Exception</span><span class="sxs-lookup"><span data-stu-id="47640-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="47640-115">Уведомляет отладчик о начале поиска обработчика исключений.</span><span class="sxs-lookup"><span data-stu-id="47640-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="47640-116">Метод ExceptionUnwind</span><span class="sxs-lookup"><span data-stu-id="47640-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="47640-117">Предоставляет уведомление о состоянии во время процесса очистки исключения.</span><span class="sxs-lookup"><span data-stu-id="47640-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="47640-118">Метод FunctionRemapComplete</span><span class="sxs-lookup"><span data-stu-id="47640-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="47640-119">Уведомляет отладчик, что выполнение кода переключил до новой версии редактируемой функции.</span><span class="sxs-lookup"><span data-stu-id="47640-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="47640-120">Метод FunctionRemapOpportunity</span><span class="sxs-lookup"><span data-stu-id="47640-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="47640-121">Уведомляет отладчик о том, что выполнение кода достигнет точки последовательности в старой версии редактируемой функции.</span><span class="sxs-lookup"><span data-stu-id="47640-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="47640-122">Метод MDANotification</span><span class="sxs-lookup"><span data-stu-id="47640-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="47640-123">Предоставляет уведомление, что при выполнении кода было обнаружено сообщение управляемого помощника MDA, отладке.</span><span class="sxs-lookup"><span data-stu-id="47640-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47640-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="47640-124">Remarks</span></span>  
 <span data-ttu-id="47640-125">`ICorDebugManagedCallback2` Интерфейс расширяет `ICorDebugManagedCallback` интерфейс для обработки новых событий отладки, представленные в .NET Framework версии 2.0.</span><span class="sxs-lookup"><span data-stu-id="47640-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="47640-126">Отладчик должен реализовать `ICorDebugManagedCallback2` при отладке приложений .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="47640-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="47640-127">Экземпляр `ICorDebugManagedCallback` или `ICorDebugManagedCallback2` передается в качестве объекта обратного вызова для [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="47640-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47640-128">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="47640-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47640-129">Требования</span><span class="sxs-lookup"><span data-stu-id="47640-129">Requirements</span></span>  
 <span data-ttu-id="47640-130">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47640-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47640-131">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47640-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47640-132">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47640-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47640-133">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47640-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47640-134">См. также</span><span class="sxs-lookup"><span data-stu-id="47640-134">See also</span></span>

- [<span data-ttu-id="47640-135">Диагностика ошибок посредством помощников по отладке управляемого кода</span><span class="sxs-lookup"><span data-stu-id="47640-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="47640-136">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="47640-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="47640-137">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="47640-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
