---
title: Метод IHostThreadPoolManager::GetAvailableThreads
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4f16db1d35f8a0de1c755566e27b07bf9067dfe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129198"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="4b202-102">Метод IHostThreadPoolManager::GetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="4b202-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="4b202-103">Получает количество потоков в пуле потоков, который в настоящий момент не обрабатывает рабочие элементы.</span><span class="sxs-lookup"><span data-stu-id="4b202-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b202-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4b202-104">Syntax</span></span>  
  
```  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b202-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4b202-105">Parameters</span></span>  
 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="4b202-106">[out] Указатель на число потоков в пуле потоков, которые в настоящий момент не обрабатывает рабочие элементы.</span><span class="sxs-lookup"><span data-stu-id="4b202-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b202-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4b202-107">Return Value</span></span>  
  
|<span data-ttu-id="4b202-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b202-108">HRESULT</span></span>|<span data-ttu-id="4b202-109">Описание</span><span class="sxs-lookup"><span data-stu-id="4b202-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b202-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b202-110">S_OK</span></span>|`GetAvailableThreads` <span data-ttu-id="4b202-111">успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="4b202-111">returned successfully.</span></span>|  
|<span data-ttu-id="4b202-112">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4b202-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4b202-113">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="4b202-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4b202-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4b202-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4b202-115">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="4b202-115">The call timed out.</span></span>|  
|<span data-ttu-id="4b202-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b202-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4b202-117">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="4b202-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4b202-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4b202-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4b202-119">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="4b202-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4b202-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4b202-120">E_FAIL</span></span>|<span data-ttu-id="4b202-121">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="4b202-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4b202-122">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="4b202-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4b202-123">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4b202-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4b202-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4b202-124">E_NOTIMPL</span></span>|<span data-ttu-id="4b202-125">Узел не поддерживает реализацию `GetAvailableThreads`.</span><span class="sxs-lookup"><span data-stu-id="4b202-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b202-126">Примечания</span><span class="sxs-lookup"><span data-stu-id="4b202-126">Remarks</span></span>  
 <span data-ttu-id="4b202-127">Если узел не поддерживает реализацию `GetAvailableThreads`, он должен возвращать значение HRESULT E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="4b202-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b202-128">Требования</span><span class="sxs-lookup"><span data-stu-id="4b202-128">Requirements</span></span>  
 <span data-ttu-id="4b202-129">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b202-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b202-130">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4b202-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b202-131">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b202-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4b202-132">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="4b202-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b202-133">См. также</span><span class="sxs-lookup"><span data-stu-id="4b202-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="4b202-134">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="4b202-134">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
