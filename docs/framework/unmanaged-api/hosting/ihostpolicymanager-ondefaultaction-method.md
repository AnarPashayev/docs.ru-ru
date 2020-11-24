---
title: Метод IHostPolicyManager::OnDefaultAction
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: a22f16c14514b90ce888fafc0ea554bd9f90cb11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684087"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="c9195-102">Метод IHostPolicyManager::OnDefaultAction</span><span class="sxs-lookup"><span data-stu-id="c9195-102">IHostPolicyManager::OnDefaultAction Method</span></span>

<span data-ttu-id="c9195-103">Уведомляет основное приложение о том, что среда CLR собирается выполнить действие по умолчанию, заданное вызовом метода [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) в ответ на прерывание или <xref:System.AppDomain> выгрузку потока.</span><span class="sxs-lookup"><span data-stu-id="c9195-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9195-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c9195-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9195-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="c9195-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="c9195-106">окне Одно из значений [еклроператион](eclroperation-enumeration.md) , указывающее тип события, на которое отвечает среда CLR.</span><span class="sxs-lookup"><span data-stu-id="c9195-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="c9195-107">окне Одно из значений [еполициактион](epolicyaction-enumeration.md) , указывающее действие, которое среда CLR принимает в ответ на событие.</span><span class="sxs-lookup"><span data-stu-id="c9195-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9195-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c9195-108">Return Value</span></span>  
  
|<span data-ttu-id="c9195-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9195-109">HRESULT</span></span>|<span data-ttu-id="c9195-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="c9195-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9195-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9195-111">S_OK</span></span>|<span data-ttu-id="c9195-112">`OnDefaultAction` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="c9195-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="c9195-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9195-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9195-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="c9195-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="c9195-115">успешность</span><span class="sxs-lookup"><span data-stu-id="c9195-115">successfully</span></span>|  
|<span data-ttu-id="c9195-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9195-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9195-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="c9195-117">The call timed out.</span></span>|  
|<span data-ttu-id="c9195-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9195-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9195-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="c9195-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9195-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9195-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9195-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="c9195-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9195-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9195-122">E_FAIL</span></span>|<span data-ttu-id="c9195-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="c9195-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9195-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="c9195-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9195-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c9195-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9195-126">Требования</span><span class="sxs-lookup"><span data-stu-id="c9195-126">Requirements</span></span>  

 <span data-ttu-id="c9195-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9195-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9195-128">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c9195-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9195-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9195-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9195-130">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9195-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9195-131">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c9195-131">See also</span></span>

- [<span data-ttu-id="c9195-132">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="c9195-132">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="c9195-133">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="c9195-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="c9195-134">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="c9195-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="c9195-135">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="c9195-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
