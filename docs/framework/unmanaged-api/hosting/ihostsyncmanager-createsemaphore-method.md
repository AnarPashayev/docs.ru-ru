---
title: Метод IHostSyncManager::CreateSemaphore
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43935829d11a925d4a3389149f5c316df15f06bb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764584"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="5a53a-102">Метод IHostSyncManager::CreateSemaphore</span><span class="sxs-lookup"><span data-stu-id="5a53a-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="5a53a-103">Создает [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) объект для выполнения (CLR) для использования в качестве semaphore для ожидания события.</span><span class="sxs-lookup"><span data-stu-id="5a53a-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a53a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5a53a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a53a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="5a53a-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="5a53a-106">[in] Исходное значение счетчика `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="5a53a-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="5a53a-107">[in] Максимальное число для `ppSemaphore`.</span><span class="sxs-lookup"><span data-stu-id="5a53a-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="5a53a-108">[out] Указатель на адрес `IHostSemaphore` экземпляра, или значение null, если не удалось создать семафор.</span><span class="sxs-lookup"><span data-stu-id="5a53a-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a53a-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5a53a-109">Return Value</span></span>  
  
|<span data-ttu-id="5a53a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a53a-110">HRESULT</span></span>|<span data-ttu-id="5a53a-111">Описание</span><span class="sxs-lookup"><span data-stu-id="5a53a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a53a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a53a-112">S_OK</span></span>|<span data-ttu-id="5a53a-113">`CreateSemaphore` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="5a53a-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="5a53a-114">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5a53a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5a53a-115">Среда CLR не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="5a53a-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5a53a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5a53a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5a53a-117">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="5a53a-117">The call timed out.</span></span>|  
|<span data-ttu-id="5a53a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5a53a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5a53a-119">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="5a53a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5a53a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5a53a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5a53a-121">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="5a53a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5a53a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5a53a-122">E_FAIL</span></span>|<span data-ttu-id="5a53a-123">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="5a53a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5a53a-124">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="5a53a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5a53a-125">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5a53a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5a53a-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5a53a-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5a53a-127">Недостаточно памяти, доступного для создания запрошенного объекта события.</span><span class="sxs-lookup"><span data-stu-id="5a53a-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a53a-128">Примечания</span><span class="sxs-lookup"><span data-stu-id="5a53a-128">Remarks</span></span>  
 <span data-ttu-id="5a53a-129">`CreateSemaphore` функция зеркал Win32, которая имеет то же имя.</span><span class="sxs-lookup"><span data-stu-id="5a53a-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="5a53a-130">`dwInitial` И `dwMax` параметры используют ту же семантику для счетчик семафора как Win32 `lInitialCount` и `lMaximumCount` параметров, соответственно.</span><span class="sxs-lookup"><span data-stu-id="5a53a-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="5a53a-131">`dwInitial` должно быть в диапазоне от нуля и `dwMax`включительно.</span><span class="sxs-lookup"><span data-stu-id="5a53a-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="5a53a-132">`dwMax` Должно быть больше нуля.</span><span class="sxs-lookup"><span data-stu-id="5a53a-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a53a-133">Требования</span><span class="sxs-lookup"><span data-stu-id="5a53a-133">Requirements</span></span>  
 <span data-ttu-id="5a53a-134">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a53a-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a53a-135">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a53a-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a53a-136">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a53a-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a53a-137">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a53a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a53a-138">См. также</span><span class="sxs-lookup"><span data-stu-id="5a53a-138">See also</span></span>

- [<span data-ttu-id="5a53a-139">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="5a53a-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="5a53a-140">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="5a53a-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="5a53a-141">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="5a53a-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
