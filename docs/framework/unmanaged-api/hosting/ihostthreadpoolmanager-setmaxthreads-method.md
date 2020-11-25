---
title: Метод IHostThreadPoolManager::SetMaxThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
ms.openlocfilehash: 68e806daa63d13ad6c1f3b5de634c20ca02e8eb4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730723"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="5e165-102">Метод IHostThreadPoolManager::SetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="5e165-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>

<span data-ttu-id="5e165-103">Задает максимальное число потоков, которые узел может поддерживать в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="5e165-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e165-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5e165-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e165-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="5e165-105">Parameters</span></span>  

 `MaxThreads`  
 <span data-ttu-id="5e165-106">Максимальное количество рабочих потоков в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="5e165-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e165-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5e165-107">Return Value</span></span>  
  
|<span data-ttu-id="5e165-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e165-108">HRESULT</span></span>|<span data-ttu-id="5e165-109">Описание:</span><span class="sxs-lookup"><span data-stu-id="5e165-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e165-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e165-110">S_OK</span></span>|<span data-ttu-id="5e165-111">`SetMaxThreads` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="5e165-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="5e165-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e165-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e165-113">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="5e165-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5e165-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5e165-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5e165-115">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="5e165-115">The call timed out.</span></span>|  
|<span data-ttu-id="5e165-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e165-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5e165-117">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="5e165-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5e165-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5e165-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5e165-119">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="5e165-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5e165-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e165-120">E_FAIL</span></span>|<span data-ttu-id="5e165-121">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="5e165-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5e165-122">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="5e165-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5e165-123">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5e165-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5e165-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5e165-124">E_NOTIMPL</span></span>|<span data-ttu-id="5e165-125">Узел не предоставляет реализацию `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="5e165-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e165-126">Комментарии</span><span class="sxs-lookup"><span data-stu-id="5e165-126">Remarks</span></span>  

 <span data-ttu-id="5e165-127">Узел не требуется, чтобы разрешить среде CLR настраивать размер пула потоков.</span><span class="sxs-lookup"><span data-stu-id="5e165-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="5e165-128">Некоторым узлам может потребоваться монопольный контроль над пулом потоков по таким причинам, как реализация, производительность или масштабируемость.</span><span class="sxs-lookup"><span data-stu-id="5e165-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="5e165-129">В этом случае узел должен вернуть значение HRESULT, равное E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="5e165-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e165-130">Требования</span><span class="sxs-lookup"><span data-stu-id="5e165-130">Requirements</span></span>  

 <span data-ttu-id="5e165-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e165-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e165-132">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5e165-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e165-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e165-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e165-134">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e165-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e165-135">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5e165-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="5e165-136">Метод GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="5e165-136">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="5e165-137">Метод SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="5e165-137">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="5e165-138">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="5e165-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
