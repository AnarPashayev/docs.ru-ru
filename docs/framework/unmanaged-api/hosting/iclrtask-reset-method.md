---
title: Метод ICLRTask::Reset
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13bf7342157de48e0183537afea2f2e53d1498dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300311"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="bd303-102">Метод ICLRTask::Reset</span><span class="sxs-lookup"><span data-stu-id="bd303-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="bd303-103">Информирует общеязыковой среды выполнения (CLR), что узел завершения задачи и обеспечивает работу CLR для повторного использования текущего [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) экземпляра для представления другой задачи.</span><span class="sxs-lookup"><span data-stu-id="bd303-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd303-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bd303-104">Syntax</span></span>  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd303-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="bd303-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="bd303-106">[in] `true`, если среда выполнения должна Сброс всех связанных с потоком статических значений дополняет сведения о безопасности и языковой стандарт, связанные с текущим `ICLRTask` экземпляра; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="bd303-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="bd303-107">Если значение равно `true`, среда выполнения сбрасывает данные, хранящиеся с помощью <xref:System.Threading.Thread.AllocateDataSlot%2A> или <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd303-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd303-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="bd303-108">Return Value</span></span>  
  
|<span data-ttu-id="bd303-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd303-109">HRESULT</span></span>|<span data-ttu-id="bd303-110">Описание</span><span class="sxs-lookup"><span data-stu-id="bd303-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd303-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd303-111">S_OK</span></span>|`Reset` <span data-ttu-id="bd303-112">успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="bd303-112">returned successfully.</span></span>|  
|<span data-ttu-id="bd303-113">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bd303-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bd303-114">Среда CLR не был загружен в процесс или находится в состоянии, в котором он не может выполнять управляемый код или обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="bd303-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="bd303-115">успешно</span><span class="sxs-lookup"><span data-stu-id="bd303-115">successfully</span></span>|  
|<span data-ttu-id="bd303-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bd303-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bd303-117">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="bd303-117">The call timed out.</span></span>|  
|<span data-ttu-id="bd303-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bd303-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bd303-119">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="bd303-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bd303-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bd303-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bd303-121">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="bd303-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bd303-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bd303-122">E_FAIL</span></span>|<span data-ttu-id="bd303-123">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="bd303-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bd303-124">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="bd303-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bd303-125">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bd303-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd303-126">Примечания</span><span class="sxs-lookup"><span data-stu-id="bd303-126">Remarks</span></span>  
 <span data-ttu-id="bd303-127">Среда CLR может повторно использовать ранее созданный `ICLRTask` экземпляры, чтобы избежать создания новых экземпляров каждый раз при выполнении новой задачи.</span><span class="sxs-lookup"><span data-stu-id="bd303-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="bd303-128">Узел включает эту функцию, вызвав `ICLRTask::Reset` вместо [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) после его завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="bd303-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="bd303-129">В следующем списке перечислены обычный жизненный цикл `ICLRTask` экземпляр:</span><span class="sxs-lookup"><span data-stu-id="bd303-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="bd303-130">Среда выполнения создает новый `ICLRTask` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="bd303-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="bd303-131">Среда выполнения вызывает [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) для получения ссылки на текущую задачу узла.</span><span class="sxs-lookup"><span data-stu-id="bd303-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="bd303-132">Среда выполнения вызывает [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) должен быть сопоставлен новому экземпляру задачи.</span><span class="sxs-lookup"><span data-stu-id="bd303-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="bd303-133">Задача выполняет и завершается.</span><span class="sxs-lookup"><span data-stu-id="bd303-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="bd303-134">Узел уничтожает задачи путем вызова `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="bd303-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 `Reset` <span data-ttu-id="bd303-135">изменяет этот сценарий следующим образом.</span><span class="sxs-lookup"><span data-stu-id="bd303-135">alters this scenario in two ways.</span></span> <span data-ttu-id="bd303-136">В шаге 5 выше, сервер вызывает функцию `Reset` для сброса задачи в исходное состояние и затем разрывает связь между `ICLRTask` экземпляр из сопоставленного ему [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) экземпляра.</span><span class="sxs-lookup"><span data-stu-id="bd303-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="bd303-137">При желании также можно кэшировать узла `IHostTask` экземпляра для повторного использования.</span><span class="sxs-lookup"><span data-stu-id="bd303-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="bd303-138">На шаге 1 выше, среда выполнения извлекает перезапущен `ICLRTask` из кэша вместо создания нового экземпляра.</span><span class="sxs-lookup"><span data-stu-id="bd303-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="bd303-139">Этот подход работает также в том случае, когда узел также имеет пул повторно используемых рабочих задач.</span><span class="sxs-lookup"><span data-stu-id="bd303-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="bd303-140">Когда узел Удаляет один из его `IHostTask` экземпляры, она окончательно удаляет соответствующие `ICLRTask` путем вызова `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="bd303-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd303-141">Требования</span><span class="sxs-lookup"><span data-stu-id="bd303-141">Requirements</span></span>  
 <span data-ttu-id="bd303-142">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd303-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd303-143">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bd303-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd303-144">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd303-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="bd303-145">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="bd303-145">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bd303-146">См. также</span><span class="sxs-lookup"><span data-stu-id="bd303-146">See also</span></span>

- [<span data-ttu-id="bd303-147">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="bd303-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="bd303-148">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="bd303-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="bd303-149">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="bd303-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="bd303-150">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="bd303-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
