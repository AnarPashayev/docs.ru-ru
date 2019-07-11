---
title: Метод ICLRPolicyManager::SetTimeoutAndAction
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c58c14dbc11272a40de01140db72ac3605bfbc67
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757260"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="26556-102">Метод ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="26556-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="26556-103">Задает значение времени ожидания для указанной операции и указывает действие политики, которое займет общеязыковой среды выполнения (CLR), при выполнении этой операции.</span><span class="sxs-lookup"><span data-stu-id="26556-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26556-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26556-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26556-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="26556-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="26556-106">[in] Один из [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) значений, указывающее операцию, для которого требуется задать время ожидания и политики `action`.</span><span class="sxs-lookup"><span data-stu-id="26556-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="26556-107">Поддерживаются следующие значения:</span><span class="sxs-lookup"><span data-stu-id="26556-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="26556-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="26556-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="26556-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="26556-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="26556-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="26556-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="26556-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="26556-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="26556-112">[in] Новое значение времени ожидания в миллисекундах.</span><span class="sxs-lookup"><span data-stu-id="26556-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="26556-113">Значение БЕСКОНЕЧНОГО причины `operation` никогда не для времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="26556-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="26556-114">[in] Один из [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) значений, указывающий действие политики, что когда должна выполнять среда CLR `operation` происходит.</span><span class="sxs-lookup"><span data-stu-id="26556-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26556-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="26556-115">Return Value</span></span>  
  
|<span data-ttu-id="26556-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26556-116">HRESULT</span></span>|<span data-ttu-id="26556-117">Описание</span><span class="sxs-lookup"><span data-stu-id="26556-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26556-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="26556-118">S_OK</span></span>|<span data-ttu-id="26556-119">`SetTimeoutAndAction` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="26556-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="26556-120">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="26556-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="26556-121">Среда CLR не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="26556-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="26556-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="26556-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="26556-123">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="26556-123">The call timed out.</span></span>|  
|<span data-ttu-id="26556-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="26556-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="26556-125">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="26556-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="26556-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="26556-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="26556-127">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="26556-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="26556-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26556-128">E_FAIL</span></span>|<span data-ttu-id="26556-129">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="26556-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="26556-130">После метод вернет значение E_FAIL, среда CLR больше не использовать в данном процессе.</span><span class="sxs-lookup"><span data-stu-id="26556-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="26556-131">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="26556-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="26556-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="26556-132">E_INVALIDARG</span></span>|<span data-ttu-id="26556-133">Невозможно задать время ожидания для указанного `operation`, или задано недопустимое значение `action`.</span><span class="sxs-lookup"><span data-stu-id="26556-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26556-134">Примечания</span><span class="sxs-lookup"><span data-stu-id="26556-134">Remarks</span></span>  
 <span data-ttu-id="26556-135">`SetTimeoutAndAction` Инкапсулирует возможности [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) и [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) методов и может быть вызван вместо последовательных вызовов к этим двум методам.</span><span class="sxs-lookup"><span data-stu-id="26556-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="26556-136">Не все значения действия политики можно указать как поведение времени ожидания для операций среды CLR.</span><span class="sxs-lookup"><span data-stu-id="26556-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="26556-137">См. в разделе "Примечания" разделы, посвященные эти два метода для допустимых значений.</span><span class="sxs-lookup"><span data-stu-id="26556-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26556-138">Требования</span><span class="sxs-lookup"><span data-stu-id="26556-138">Requirements</span></span>  
 <span data-ttu-id="26556-139">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26556-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26556-140">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="26556-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26556-141">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26556-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26556-142">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26556-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26556-143">См. также</span><span class="sxs-lookup"><span data-stu-id="26556-143">See also</span></span>

- [<span data-ttu-id="26556-144">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="26556-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="26556-145">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="26556-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="26556-146">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="26556-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="26556-147">Метод SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="26556-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="26556-148">ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="26556-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
