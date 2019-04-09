---
title: Метод IHostTask::Join
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4373fc4e8a4c414c40e8d3c5547b5998b9300348
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170774"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="53100-102">Метод IHostTask::Join</span><span class="sxs-lookup"><span data-stu-id="53100-102">IHostTask::Join Method</span></span>
<span data-ttu-id="53100-103">Блокирует вызывающий задачу до выполнения задачи, представленный текущим [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) завершения экземпляра, по истечении указанного интервала времени, или [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) вызывается.</span><span class="sxs-lookup"><span data-stu-id="53100-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53100-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="53100-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53100-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="53100-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="53100-106">[in] Интервал времени в миллисекундах для ожидания завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="53100-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="53100-107">Если это время истекает до завершения задачи, задача вызова разблокируется.</span><span class="sxs-lookup"><span data-stu-id="53100-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="53100-108">[in] Один из [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) значения.</span><span class="sxs-lookup"><span data-stu-id="53100-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="53100-109">Значение WAIT_ALERTABLE указывает узлу задачи, если в `Alert` вызывается перед `milliseconds` пройдет указанное время.</span><span class="sxs-lookup"><span data-stu-id="53100-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53100-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="53100-110">Return Value</span></span>  
  
|<span data-ttu-id="53100-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53100-111">HRESULT</span></span>|<span data-ttu-id="53100-112">Описание</span><span class="sxs-lookup"><span data-stu-id="53100-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53100-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="53100-113">S_OK</span></span>|`Join` <span data-ttu-id="53100-114">успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="53100-114">returned successfully.</span></span>|  
|<span data-ttu-id="53100-115">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53100-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53100-116">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="53100-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="53100-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53100-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53100-118">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="53100-118">The call timed out.</span></span>|  
|<span data-ttu-id="53100-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53100-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53100-120">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="53100-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53100-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53100-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53100-122">Событие было отменено с сохранением заблокированный поток или волокон ожидал, или текущий `IHostTask` экземпляра не связан с задачей.</span><span class="sxs-lookup"><span data-stu-id="53100-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="53100-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53100-123">E_FAIL</span></span>|<span data-ttu-id="53100-124">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="53100-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53100-125">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="53100-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53100-126">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="53100-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53100-127">Требования</span><span class="sxs-lookup"><span data-stu-id="53100-127">Requirements</span></span>  
 <span data-ttu-id="53100-128">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53100-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53100-129">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53100-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53100-130">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53100-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="53100-131">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="53100-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="53100-132">См. также</span><span class="sxs-lookup"><span data-stu-id="53100-132">See also</span></span>

- [<span data-ttu-id="53100-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="53100-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="53100-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="53100-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="53100-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="53100-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="53100-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="53100-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="53100-137">Перечисление WAIT_OPTION</span><span class="sxs-lookup"><span data-stu-id="53100-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)
