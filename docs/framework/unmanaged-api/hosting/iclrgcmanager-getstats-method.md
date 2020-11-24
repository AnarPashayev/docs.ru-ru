---
title: Метод ICLRGCManager::GetStats
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 70fe8b132f03925c41b6bc7aae8e60fea1b05202
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678302"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="ca935-102">Метод ICLRGCManager::GetStats</span><span class="sxs-lookup"><span data-stu-id="ca935-102">ICLRGCManager::GetStats Method</span></span>

<span data-ttu-id="ca935-103">Возвращает набор текущих статистических данных о системе сборки мусора среды CLR.</span><span class="sxs-lookup"><span data-stu-id="ca935-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca935-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ca935-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca935-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="ca935-105">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="ca935-106">[вход, выход] Экземпляр [COR_GC_STATS](cor-gc-stats-structure.md) , содержащий запрошенную статистику.</span><span class="sxs-lookup"><span data-stu-id="ca935-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca935-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ca935-107">Return Value</span></span>  
  
|<span data-ttu-id="ca935-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca935-108">HRESULT</span></span>|<span data-ttu-id="ca935-109">Описание:</span><span class="sxs-lookup"><span data-stu-id="ca935-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca935-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca935-110">S_OK</span></span>|<span data-ttu-id="ca935-111">`GetStats` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="ca935-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="ca935-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca935-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca935-113">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="ca935-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ca935-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ca935-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ca935-115">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="ca935-115">The call timed out.</span></span>|  
|<span data-ttu-id="ca935-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ca935-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ca935-117">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="ca935-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ca935-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ca935-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ca935-119">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="ca935-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ca935-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca935-120">E_FAIL</span></span>|<span data-ttu-id="ca935-121">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="ca935-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ca935-122">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="ca935-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ca935-123">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca935-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca935-124">Комментарии</span><span class="sxs-lookup"><span data-stu-id="ca935-124">Remarks</span></span>  

 <span data-ttu-id="ca935-125">Среда CLR вычисляет и возвращает только те статистические данные, которые указаны в `Flags` поле `pStats` .</span><span class="sxs-lookup"><span data-stu-id="ca935-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="ca935-126">Задайте в `Flags` поле одно или несколько значений перечисления [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) , чтобы указать, какие статистические данные должны быть заданы в структуре [COR_GC_STATS](cor-gc-stats-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="ca935-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="ca935-127">Пример использования таков:</span><span class="sxs-lookup"><span data-stu-id="ca935-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ca935-128">Требования</span><span class="sxs-lookup"><span data-stu-id="ca935-128">Requirements</span></span>  

 <span data-ttu-id="ca935-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca935-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca935-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ca935-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca935-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca935-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca935-132">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca935-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca935-133">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ca935-133">See also</span></span>

- [<span data-ttu-id="ca935-134">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="ca935-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="ca935-135">Структура COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="ca935-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="ca935-136">Перечисление COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="ca935-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="ca935-137">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="ca935-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="ca935-138">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="ca935-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="ca935-139">Интерфейс ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="ca935-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="ca935-140">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="ca935-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="ca935-141">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="ca935-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ca935-142">Размещение</span><span class="sxs-lookup"><span data-stu-id="ca935-142">Hosting</span></span>](index.md)
