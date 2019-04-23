---
title: Метод IHostTaskManager::BeginDelayAbort
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 328462343669b3ea6bed2d86514ea348f6ae2b1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197975"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="45669-102">Метод IHostTaskManager::BeginDelayAbort</span><span class="sxs-lookup"><span data-stu-id="45669-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="45669-103">Уведомляет хост, что управляемый код к периоду, в котором должен не удается прервать текущую задачу.</span><span class="sxs-lookup"><span data-stu-id="45669-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45669-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="45669-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="45669-105">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="45669-105">Return Value</span></span>  
  
|<span data-ttu-id="45669-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45669-106">HRESULT</span></span>|<span data-ttu-id="45669-107">Описание</span><span class="sxs-lookup"><span data-stu-id="45669-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45669-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="45669-108">S_OK</span></span>|<span data-ttu-id="45669-109">`BeginDelayAbort` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="45669-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="45669-110">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="45669-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="45669-111">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="45669-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="45669-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="45669-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="45669-113">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="45669-113">The call timed out.</span></span>|  
|<span data-ttu-id="45669-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="45669-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="45669-115">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="45669-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="45669-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="45669-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="45669-117">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="45669-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="45669-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="45669-118">E_FAIL</span></span>|<span data-ttu-id="45669-119">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="45669-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="45669-120">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="45669-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="45669-121">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="45669-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="45669-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="45669-122">E_UNEXPECTED</span></span>|<span data-ttu-id="45669-123">`BeginDelayAbort` уже был вызван, но соответствующего вызова [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) еще не были получены.</span><span class="sxs-lookup"><span data-stu-id="45669-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45669-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="45669-124">Remarks</span></span>  
 <span data-ttu-id="45669-125">Основное приложение не должно прерывать текущую задачу до `EndDelayAbort` вызывается.</span><span class="sxs-lookup"><span data-stu-id="45669-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="45669-126">Если при вызове другой `BeginDelayAbort` устанавливается без промежуточным вызовом `EndDelayAbort`, основное приложение должно возвратить E_UNEXPECTED из `BeginDelayAbort`и не предпринимать никаких действий.</span><span class="sxs-lookup"><span data-stu-id="45669-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45669-127">Требования</span><span class="sxs-lookup"><span data-stu-id="45669-127">Requirements</span></span>  
 <span data-ttu-id="45669-128">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45669-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45669-129">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="45669-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45669-130">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45669-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45669-131">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45669-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45669-132">См. также</span><span class="sxs-lookup"><span data-stu-id="45669-132">See also</span></span>

- [<span data-ttu-id="45669-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="45669-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="45669-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="45669-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="45669-135">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="45669-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
