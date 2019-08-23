---
title: Метод IHostTaskManager::ReverseEnterRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e5beabb5ac1b5a4b2a34ae8e18b7fad7c86504
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959054"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="a5fa5-102">Метод IHostTaskManager::ReverseEnterRuntime</span><span class="sxs-lookup"><span data-stu-id="a5fa5-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="a5fa5-103">Уведомляет узел о том, что в среде CLR выполняется вызов из неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5fa5-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a5fa5-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a5fa5-105">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a5fa5-105">Return Value</span></span>  
  
|<span data-ttu-id="a5fa5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5fa5-106">HRESULT</span></span>|<span data-ttu-id="a5fa5-107">Описание</span><span class="sxs-lookup"><span data-stu-id="a5fa5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5fa5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5fa5-108">S_OK</span></span>|<span data-ttu-id="a5fa5-109">`ReverseEnterRuntime`успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="a5fa5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a5fa5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a5fa5-111">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a5fa5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a5fa5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a5fa5-113">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-113">The call timed out.</span></span>|  
|<span data-ttu-id="a5fa5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a5fa5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a5fa5-115">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a5fa5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a5fa5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a5fa5-117">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a5fa5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a5fa5-118">E_FAIL</span></span>|<span data-ttu-id="a5fa5-119">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a5fa5-120">Когда метод возвращает значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a5fa5-121">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a5fa5-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a5fa5-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a5fa5-123">Недостаточно памяти для завершения запрошенного выделения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5fa5-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="a5fa5-124">Remarks</span></span>  
 <span data-ttu-id="a5fa5-125">Если вызов среды CLR выполняется из последовательности, порожденной в управляемом коде, каждый вызов `ReverseEnterRuntime` соответствует вызову [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="a5fa5-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5fa5-126">Вызовы могут исходить из неуправляемого кода без вложения.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="a5fa5-127">В этом случае нет вызова [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [леаверунтиме](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) `ReverseLeaveRuntime`или, `ReverseEnterRuntime` а число вызовов не равно числу вызовов `ReverseLeaveRuntime`.</span><span class="sxs-lookup"><span data-stu-id="a5fa5-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5fa5-128">Требования</span><span class="sxs-lookup"><span data-stu-id="a5fa5-128">Requirements</span></span>  
 <span data-ttu-id="a5fa5-129">**Платформ** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5fa5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5fa5-130">**Заголовок.** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a5fa5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5fa5-131">**Библиотечная** Включается в качестве ресурса в библиотеку MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a5fa5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5fa5-132">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5fa5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fa5-133">См. также</span><span class="sxs-lookup"><span data-stu-id="a5fa5-133">See also</span></span>

- [<span data-ttu-id="a5fa5-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="a5fa5-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a5fa5-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="a5fa5-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a5fa5-136">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="a5fa5-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a5fa5-137">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="a5fa5-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
