---
title: Метод ICLRGCManager::SetGCStartupLimits
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ffbe29db96cbb6162adc3b4cc77b45dcef27a46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117291"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="e185c-102">Метод ICLRGCManager::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="e185c-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="e185c-103">Задает размер сегмент сборки мусора и максимальный размер в систему сбора мусора поколения 0.</span><span class="sxs-lookup"><span data-stu-id="e185c-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e185c-104">Начиная с [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], можно задать размер сегмента и максимально возможного поколения 0 размер значения больше, чем `DWORD` с помощью [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="e185c-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e185c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e185c-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e185c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e185c-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="e185c-107">[in] Указанный размер сегмент сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="e185c-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="e185c-108">Минимальный размер сегмента составляет 4 МБ.</span><span class="sxs-lookup"><span data-stu-id="e185c-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="e185c-109">Сегменты можно увеличить с шагом 1 МБ или больше.</span><span class="sxs-lookup"><span data-stu-id="e185c-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="e185c-110">[in] Заданный максимальный размер поколения 0.</span><span class="sxs-lookup"><span data-stu-id="e185c-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="e185c-111">Минимальное поколения 0 размер составляет 64 КБ.</span><span class="sxs-lookup"><span data-stu-id="e185c-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e185c-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e185c-112">Return Value</span></span>  
  
|<span data-ttu-id="e185c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e185c-113">HRESULT</span></span>|<span data-ttu-id="e185c-114">Описание</span><span class="sxs-lookup"><span data-stu-id="e185c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e185c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e185c-115">S_OK</span></span>|<span data-ttu-id="e185c-116">`SetGCStartupLimits` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="e185c-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="e185c-117">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e185c-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e185c-118">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="e185c-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e185c-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e185c-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e185c-120">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="e185c-120">The call timed out.</span></span>|  
|<span data-ttu-id="e185c-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e185c-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e185c-122">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="e185c-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e185c-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e185c-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e185c-124">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="e185c-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e185c-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e185c-125">E_FAIL</span></span>|<span data-ttu-id="e185c-126">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="e185c-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e185c-127">После метод вернет значение E_FAIL, среда CLR больше не использовать в данном процессе.</span><span class="sxs-lookup"><span data-stu-id="e185c-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e185c-128">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e185c-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e185c-129">Примечания</span><span class="sxs-lookup"><span data-stu-id="e185c-129">Remarks</span></span>  
 <span data-ttu-id="e185c-130">Значения, `SetGCStartupLimits` наборы, которые можно указать только один раз.</span><span class="sxs-lookup"><span data-stu-id="e185c-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="e185c-131">Последующие вызовы `SetGCStartupLimits` игнорируются.</span><span class="sxs-lookup"><span data-stu-id="e185c-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e185c-132">Требования</span><span class="sxs-lookup"><span data-stu-id="e185c-132">Requirements</span></span>  
 <span data-ttu-id="e185c-133">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e185c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e185c-134">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e185c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e185c-135">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e185c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e185c-136">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e185c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e185c-137">См. также</span><span class="sxs-lookup"><span data-stu-id="e185c-137">See also</span></span>

- [<span data-ttu-id="e185c-138">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="e185c-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="e185c-139">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="e185c-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="e185c-140">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e185c-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e185c-141">Интерфейс ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="e185c-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
