---
title: Метод ICLRSyncManager::CreateRWLockOwnerIterator
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c742410da8e7dbce53b53978516ab94243455849
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763715"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="9b0a9-102">Метод ICLRSyncManager::CreateRWLockOwnerIterator</span><span class="sxs-lookup"><span data-stu-id="9b0a9-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="9b0a9-103">Запросы, которые среда CLR (CLR) создают итератор для узла для определения набора задач, ожидающих блокировки чтения и записи.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0a9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9b0a9-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b0a9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="9b0a9-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="9b0a9-106">[in] Файл cookie, связанный с блокировкой требуемой чтения записи.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="9b0a9-107">[out] Указатель на итератор, который может быть передан [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) и [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) методы.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b0a9-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9b0a9-108">Return Value</span></span>  
  
|<span data-ttu-id="9b0a9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b0a9-109">HRESULT</span></span>|<span data-ttu-id="9b0a9-110">Описание</span><span class="sxs-lookup"><span data-stu-id="9b0a9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b0a9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b0a9-111">S_OK</span></span>|<span data-ttu-id="9b0a9-112">`CreateRWLockOwnerIterator` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="9b0a9-113">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9b0a9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9b0a9-114">Среда CLR не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9b0a9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9b0a9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9b0a9-116">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-116">The call timed out.</span></span>|  
|<span data-ttu-id="9b0a9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9b0a9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9b0a9-118">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9b0a9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9b0a9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9b0a9-120">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9b0a9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9b0a9-121">E_FAIL</span></span>|<span data-ttu-id="9b0a9-122">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9b0a9-123">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9b0a9-124">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9b0a9-125">ЗНАЧЕНИЕ HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="9b0a9-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="9b0a9-126">`CreateRWLockOwnerIterator` был вызван в потоке, который выполняется в данный момент управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b0a9-127">Примечания</span><span class="sxs-lookup"><span data-stu-id="9b0a9-127">Remarks</span></span>  
 <span data-ttu-id="9b0a9-128">Обычно вызывать узлы `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, и `GetRWLockOwnerNext` методов во время обнаружения взаимоблокировок.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="9b0a9-129">Узел отвечает за то, что блокировка чтения или записи действительна, так как среда CLR не предпринимает попытки сохранения блокировка чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="9b0a9-130">Несколько стратегий доступны для узла обеспечить правильность блокировки:</span><span class="sxs-lookup"><span data-stu-id="9b0a9-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="9b0a9-131">Узел может блокировать вызовы снятия блокировки чтения и записи (например, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) гарантией того, что этот блок не приводит к взаимоблокировке.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="9b0a9-132">Узел может блокировать выход из режима ожидания для объекта события, связанного с блокировкой чтения записи, еще раз, гарантируя, что этот блок не приводит к взаимоблокировке.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b0a9-133">`CreateRWLockOwnerIterator` должен вызываться только в потоках, которые в данный момент неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="9b0a9-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b0a9-134">Требования</span><span class="sxs-lookup"><span data-stu-id="9b0a9-134">Requirements</span></span>  
 <span data-ttu-id="9b0a9-135">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b0a9-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b0a9-136">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b0a9-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b0a9-137">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b0a9-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b0a9-138">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b0a9-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0a9-139">См. также</span><span class="sxs-lookup"><span data-stu-id="9b0a9-139">See also</span></span>

- [<span data-ttu-id="9b0a9-140">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="9b0a9-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="9b0a9-141">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="9b0a9-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
