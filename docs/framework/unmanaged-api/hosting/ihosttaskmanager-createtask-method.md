---
title: Метод IHostTaskManager::CreateTask
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eddb11ab56bae5243ea7d00614090bbfe774f71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789452"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="f2e40-102">Метод IHostTaskManager::CreateTask</span><span class="sxs-lookup"><span data-stu-id="f2e40-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="f2e40-103">Запросы на создание новой задачи.</span><span class="sxs-lookup"><span data-stu-id="f2e40-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2e40-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f2e40-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2e40-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="f2e40-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="f2e40-106">[in] Запрошенный размер в байтах, запрошенной стека, или 0 (ноль) для размера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f2e40-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="f2e40-107">[in] Указатель на функцию будет выполнять задача.</span><span class="sxs-lookup"><span data-stu-id="f2e40-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="f2e40-108">[in] Указатель на данные пользователя должны быть переданы функции, или значение null, если функция не принимает никаких параметров.</span><span class="sxs-lookup"><span data-stu-id="f2e40-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="f2e40-109">[out] Указатель на адрес [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) экземпляра, созданные в узле, или значение null, если задача не может быть создана.</span><span class="sxs-lookup"><span data-stu-id="f2e40-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="f2e40-110">Задача остается в приостановленном состоянии, пока она запущена явным образом с помощью вызова [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="f2e40-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2e40-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f2e40-111">Return Value</span></span>  
  
|<span data-ttu-id="f2e40-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2e40-112">HRESULT</span></span>|<span data-ttu-id="f2e40-113">Описание</span><span class="sxs-lookup"><span data-stu-id="f2e40-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2e40-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2e40-114">S_OK</span></span>|<span data-ttu-id="f2e40-115">`CreateTask` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="f2e40-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="f2e40-116">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f2e40-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f2e40-117">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="f2e40-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f2e40-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f2e40-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f2e40-119">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="f2e40-119">The call timed out.</span></span>|  
|<span data-ttu-id="f2e40-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f2e40-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f2e40-121">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="f2e40-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f2e40-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f2e40-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f2e40-123">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="f2e40-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f2e40-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2e40-124">E_FAIL</span></span>|<span data-ttu-id="f2e40-125">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="f2e40-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f2e40-126">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="f2e40-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f2e40-127">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f2e40-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f2e40-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f2e40-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f2e40-129">Недостаточно памяти, доступного для создания требуемой задачи.</span><span class="sxs-lookup"><span data-stu-id="f2e40-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2e40-130">Примечания</span><span class="sxs-lookup"><span data-stu-id="f2e40-130">Remarks</span></span>  
 <span data-ttu-id="f2e40-131">Среда CLR вызывает `CreateTask` для запроса, создание новой задачи.</span><span class="sxs-lookup"><span data-stu-id="f2e40-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="f2e40-132">Основное приложение возвращает указатель интерфейса на `IHostTask` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="f2e40-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="f2e40-133">Возвращаемая задача должна отложен до явным образом она запущена с помощью вызова `IHostTask::Start`.</span><span class="sxs-lookup"><span data-stu-id="f2e40-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2e40-134">Требования</span><span class="sxs-lookup"><span data-stu-id="f2e40-134">Requirements</span></span>  
 <span data-ttu-id="f2e40-135">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2e40-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2e40-136">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f2e40-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2e40-137">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2e40-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2e40-138">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2e40-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e40-139">См. также</span><span class="sxs-lookup"><span data-stu-id="f2e40-139">See also</span></span>

- [<span data-ttu-id="f2e40-140">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="f2e40-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f2e40-141">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="f2e40-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f2e40-142">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="f2e40-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f2e40-143">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="f2e40-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
