---
title: Метод IHostTaskManager::EndThreadAffinity
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: 2e857f951a837e1385d02dfc810fc12cfefd0d2b
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841962"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="cc581-102">Метод IHostTaskManager::EndThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="cc581-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="cc581-103">Уведомляет узел о выходе управляемого кода за время, в течение которого текущая задача не должна быть перемещена в другой поток операционной системы, после предыдущего вызова [IHostTaskManager:: BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="cc581-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc581-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cc581-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cc581-105">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cc581-105">Return Value</span></span>  
  
|<span data-ttu-id="cc581-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc581-106">HRESULT</span></span>|<span data-ttu-id="cc581-107">Описание</span><span class="sxs-lookup"><span data-stu-id="cc581-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc581-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc581-108">S_OK</span></span>|<span data-ttu-id="cc581-109">`EndThreadAffinity`успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="cc581-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="cc581-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc581-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc581-111">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="cc581-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc581-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc581-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc581-113">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="cc581-113">The call timed out.</span></span>|  
|<span data-ttu-id="cc581-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc581-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc581-115">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="cc581-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc581-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc581-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc581-117">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="cc581-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc581-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc581-118">E_FAIL</span></span>|<span data-ttu-id="cc581-119">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="cc581-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc581-120">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="cc581-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc581-121">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cc581-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cc581-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="cc581-122">E_UNEXPECTED</span></span>|<span data-ttu-id="cc581-123">`EndThreadAffinity`был вызван без ранее соответствующего вызова `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="cc581-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc581-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="cc581-124">Remarks</span></span>  
 <span data-ttu-id="cc581-125">Среда CLR выполняет соответствующий вызов `BeginThreadAffinity` в текущей задаче перед вызовом метода `EndThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="cc581-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="cc581-126">В отсутствие такого соответствующего вызова реализация [IHostTaskManager](ihosttaskmanager-interface.md) должна возвращать E_UNEXPECTED и не предпринимать никаких действий.</span><span class="sxs-lookup"><span data-stu-id="cc581-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc581-127">Требования</span><span class="sxs-lookup"><span data-stu-id="cc581-127">Requirements</span></span>  
 <span data-ttu-id="cc581-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc581-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc581-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc581-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc581-130">**Библиотека:** Включается в качестве ресурса в библиотеку MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cc581-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc581-131">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc581-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc581-132">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="cc581-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="cc581-133">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="cc581-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="cc581-134">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="cc581-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="cc581-135">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="cc581-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="cc581-136">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="cc581-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
