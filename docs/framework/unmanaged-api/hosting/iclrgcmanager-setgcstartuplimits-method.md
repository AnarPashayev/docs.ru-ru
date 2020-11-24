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
ms.openlocfilehash: 169d344975762b97f89e8dc32d72f2b9c95fea11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678185"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="e0f56-102">Метод ICLRGCManager::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="e0f56-102">ICLRGCManager::SetGCStartupLimits Method</span></span>

<span data-ttu-id="e0f56-103">Задает размер сегмента сборки мусора и максимальный размер поколения 0 для системы сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="e0f56-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e0f56-104">Начиная с .NET Framework 4,5 можно задать размер сегмента и максимальный размер поколения 0 в значениях, превышающих `DWORD` использование метода [ICLRGCManager2:: SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e0f56-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0f56-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e0f56-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0f56-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e0f56-106">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="e0f56-107">окне Указанный размер сегмента сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="e0f56-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="e0f56-108">Минимальный размер сегмента — 4 МБ.</span><span class="sxs-lookup"><span data-stu-id="e0f56-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="e0f56-109">Размер сегментов можно увеличить с шагом в 1 МБ или больше.</span><span class="sxs-lookup"><span data-stu-id="e0f56-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="e0f56-110">окне Указанный максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="e0f56-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="e0f56-111">Минимальный размер поколения 0 — 64 КБ.</span><span class="sxs-lookup"><span data-stu-id="e0f56-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0f56-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e0f56-112">Return Value</span></span>  
  
|<span data-ttu-id="e0f56-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0f56-113">HRESULT</span></span>|<span data-ttu-id="e0f56-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="e0f56-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0f56-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0f56-115">S_OK</span></span>|<span data-ttu-id="e0f56-116">`SetGCStartupLimits` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="e0f56-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="e0f56-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0f56-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0f56-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="e0f56-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0f56-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0f56-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0f56-120">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="e0f56-120">The call timed out.</span></span>|  
|<span data-ttu-id="e0f56-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0f56-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0f56-122">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="e0f56-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0f56-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0f56-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0f56-124">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="e0f56-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0f56-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0f56-125">E_FAIL</span></span>|<span data-ttu-id="e0f56-126">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="e0f56-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0f56-127">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="e0f56-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0f56-128">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e0f56-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0f56-129">Комментарии</span><span class="sxs-lookup"><span data-stu-id="e0f56-129">Remarks</span></span>  

 <span data-ttu-id="e0f56-130">Значения, которые `SetGCStartupLimits` задаются, можно указать только один раз.</span><span class="sxs-lookup"><span data-stu-id="e0f56-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="e0f56-131">Последующие вызовы метода `SetGCStartupLimits` игнорируются.</span><span class="sxs-lookup"><span data-stu-id="e0f56-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0f56-132">Требования</span><span class="sxs-lookup"><span data-stu-id="e0f56-132">Requirements</span></span>  

 <span data-ttu-id="e0f56-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0f56-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0f56-134">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e0f56-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0f56-135">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0f56-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0f56-136">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0f56-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f56-137">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e0f56-137">See also</span></span>

- [<span data-ttu-id="e0f56-138">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="e0f56-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="e0f56-139">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="e0f56-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="e0f56-140">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="e0f56-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="e0f56-141">Интерфейс ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="e0f56-141">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
