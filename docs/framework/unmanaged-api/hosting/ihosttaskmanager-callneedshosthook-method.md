---
title: Метод IHostTaskManager::CallNeedsHostHook
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a33f71ef2e0b19a33255f3745ac4d5a84cdf4ad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749738"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="dfc9f-102">Метод IHostTaskManager::CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="dfc9f-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="dfc9f-103">Ведущее приложение может указать, сможет ли среда CLR (CLR) вводить заданный вызов в неуправляемую функцию.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc9f-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dfc9f-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfc9f-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="dfc9f-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="dfc9f-106">[in] Адрес в файле сопоставленные переносимого исполняемого (PE) из неуправляемой функции, который должен вызываться.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="dfc9f-107">[out] Указатель на логическое значение, указывающее, требуется ли узел вызова связать.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfc9f-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dfc9f-108">Return Value</span></span>  
  
|<span data-ttu-id="dfc9f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dfc9f-109">HRESULT</span></span>|<span data-ttu-id="dfc9f-110">Описание</span><span class="sxs-lookup"><span data-stu-id="dfc9f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfc9f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfc9f-111">S_OK</span></span>|<span data-ttu-id="dfc9f-112">`CallNeedsHostHook` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="dfc9f-113">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dfc9f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dfc9f-114">Среда CLR не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dfc9f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dfc9f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dfc9f-116">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-116">The call timed out.</span></span>|  
|<span data-ttu-id="dfc9f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dfc9f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dfc9f-118">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dfc9f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dfc9f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dfc9f-120">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dfc9f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dfc9f-121">E_FAIL</span></span>|<span data-ttu-id="dfc9f-122">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="dfc9f-123">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dfc9f-124">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfc9f-125">Примечания</span><span class="sxs-lookup"><span data-stu-id="dfc9f-125">Remarks</span></span>  
 <span data-ttu-id="dfc9f-126">Чтобы оптимизировать выполнение кода, среда CLR выполняет анализ каждого вызова неуправляемого кода во время компиляции, чтобы определить, можно ли вызов как встроенный.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="dfc9f-127">`CallNeedsHostHook` Позволяет ведущему приложению переопределить это решение, требуя связать вызова неуправляемой функции.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="dfc9f-128">Если узлу требуется обработчик, среда выполнения не вводит вызов.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="dfc9f-129">Узел обычно требуется в случае необходимости настройки состояния с плавающей запятой, или при получении уведомления, что вызов переходит в состояние, где узел не может отслеживать запросы среды выполнения памяти или любое число блокировок.</span><span class="sxs-lookup"><span data-stu-id="dfc9f-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="dfc9f-130">Если узел требуется связать вызов, среда выполнения уведомляет основное приложение переходов в и из управляемого кода с помощью вызова [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), и [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="dfc9f-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc9f-131">Требования</span><span class="sxs-lookup"><span data-stu-id="dfc9f-131">Requirements</span></span>  
 <span data-ttu-id="dfc9f-132">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfc9f-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc9f-133">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dfc9f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfc9f-134">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dfc9f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfc9f-135">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc9f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc9f-136">См. также</span><span class="sxs-lookup"><span data-stu-id="dfc9f-136">See also</span></span>

- [<span data-ttu-id="dfc9f-137">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="dfc9f-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="dfc9f-138">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="dfc9f-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="dfc9f-139">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="dfc9f-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="dfc9f-140">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="dfc9f-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
