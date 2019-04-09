---
title: Метод IHostTaskManager::ReverseLeaveRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cd3012d966c777749eb800b8986974a4e8d401f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154171"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="3d81d-102">Метод IHostTaskManager::ReverseLeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="3d81d-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="3d81d-103">Уведомляет ведущее приложение, что элемент управления является оставляя общеязыковой среды выполнения (CLR) и неуправляемой функции, которая, в свою очередь, была вызвана из управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="3d81d-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d81d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3d81d-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3d81d-105">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3d81d-105">Return Value</span></span>  
  
|<span data-ttu-id="3d81d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d81d-106">HRESULT</span></span>|<span data-ttu-id="3d81d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="3d81d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d81d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d81d-108">S_OK</span></span>|`ReverseLeaveRuntime` <span data-ttu-id="3d81d-109">успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="3d81d-109">returned successfully.</span></span>|  
|<span data-ttu-id="3d81d-110">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3d81d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3d81d-111">Среда CLR не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="3d81d-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3d81d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3d81d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3d81d-113">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="3d81d-113">The call timed out.</span></span>|  
|<span data-ttu-id="3d81d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d81d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3d81d-115">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="3d81d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3d81d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3d81d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3d81d-117">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="3d81d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3d81d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3d81d-118">E_FAIL</span></span>|<span data-ttu-id="3d81d-119">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="3d81d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3d81d-120">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="3d81d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3d81d-121">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3d81d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3d81d-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3d81d-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3d81d-123">Недостаточно памяти для завершения выделения запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="3d81d-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d81d-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="3d81d-124">Remarks</span></span>  
 <span data-ttu-id="3d81d-125">Среда CLR вызывает `ReverseLeaveRuntime` для информирования, возвращая текущая выполняющаяся задача основного элемента управления в неуправляемую функцию, которая в свою очередь, была вызвана из управляемого кода посредством вызова.</span><span class="sxs-lookup"><span data-stu-id="3d81d-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="3d81d-126">Каждый вызов `ReverseLeaveRuntime` совпадает с соответствующим вызовом метода [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="3d81d-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d81d-127">Требования</span><span class="sxs-lookup"><span data-stu-id="3d81d-127">Requirements</span></span>  
 <span data-ttu-id="3d81d-128">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d81d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d81d-129">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3d81d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d81d-130">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d81d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3d81d-131">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3d81d-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d81d-132">См. также</span><span class="sxs-lookup"><span data-stu-id="3d81d-132">See also</span></span>

- [<span data-ttu-id="3d81d-133">Метод CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="3d81d-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="3d81d-134">Метод EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="3d81d-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="3d81d-135">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="3d81d-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="3d81d-136">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="3d81d-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="3d81d-137">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="3d81d-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="3d81d-138">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="3d81d-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="3d81d-139">Метод LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="3d81d-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
- [<span data-ttu-id="3d81d-140">Подробный обзор вызова неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="3d81d-140">A Closer Look at Platform Invoke</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))
