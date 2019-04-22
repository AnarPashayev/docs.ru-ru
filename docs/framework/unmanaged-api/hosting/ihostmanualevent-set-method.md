---
title: Метод IHostManualEvent::Set
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 674745636033f42eb8fb67babf6f5a3f013491c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093505"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="e9135-102">Метод IHostManualEvent::Set</span><span class="sxs-lookup"><span data-stu-id="e9135-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="e9135-103">Задает текущий [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) экземпляр сигнальное состояние.</span><span class="sxs-lookup"><span data-stu-id="e9135-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9135-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e9135-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e9135-105">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e9135-105">Return Value</span></span>  
  
|<span data-ttu-id="e9135-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9135-106">HRESULT</span></span>|<span data-ttu-id="e9135-107">Описание</span><span class="sxs-lookup"><span data-stu-id="e9135-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9135-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9135-108">S_OK</span></span>|<span data-ttu-id="e9135-109">`Set` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="e9135-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="e9135-110">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9135-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9135-111">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="e9135-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9135-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9135-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9135-113">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="e9135-113">The call timed out.</span></span>|  
|<span data-ttu-id="e9135-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9135-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9135-115">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="e9135-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9135-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9135-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9135-117">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="e9135-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9135-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9135-118">E_FAIL</span></span>|<span data-ttu-id="e9135-119">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="e9135-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9135-120">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="e9135-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9135-121">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e9135-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9135-122">Требования</span><span class="sxs-lookup"><span data-stu-id="e9135-122">Requirements</span></span>  
 <span data-ttu-id="e9135-123">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9135-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9135-124">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9135-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9135-125">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9135-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9135-126">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9135-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9135-127">См. также</span><span class="sxs-lookup"><span data-stu-id="e9135-127">See also</span></span>

- [<span data-ttu-id="e9135-128">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="e9135-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e9135-129">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="e9135-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="e9135-130">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="e9135-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e9135-131">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="e9135-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="e9135-132">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="e9135-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
