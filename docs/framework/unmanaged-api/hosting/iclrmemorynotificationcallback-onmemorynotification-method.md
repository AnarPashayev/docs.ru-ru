---
title: Метод ICLRMemoryNotificationCallback::OnMemoryNotification
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c933389e1398d294d79f82a69a609a77aa820f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779820"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="33e7c-102">Метод ICLRMemoryNotificationCallback::OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="33e7c-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="33e7c-103">Уведомляет общеязыковой среды выполнения (CLR) загрузки памяти на компьютере.</span><span class="sxs-lookup"><span data-stu-id="33e7c-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e7c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="33e7c-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33e7c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="33e7c-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="33e7c-106">[in] Один из [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) значений, указывающее, является нехватка памяти компьютера в настоящее время известны.</span><span class="sxs-lookup"><span data-stu-id="33e7c-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33e7c-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="33e7c-107">Return Value</span></span>  
  
|<span data-ttu-id="33e7c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33e7c-108">HRESULT</span></span>|<span data-ttu-id="33e7c-109">Описание</span><span class="sxs-lookup"><span data-stu-id="33e7c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33e7c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="33e7c-110">S_OK</span></span>|<span data-ttu-id="33e7c-111">`OnMemoryNotification` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="33e7c-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="33e7c-112">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="33e7c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="33e7c-113">Среда CLR не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="33e7c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="33e7c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="33e7c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="33e7c-115">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="33e7c-115">The call timed out.</span></span>|  
|<span data-ttu-id="33e7c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="33e7c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="33e7c-117">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="33e7c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="33e7c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="33e7c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="33e7c-119">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="33e7c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="33e7c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33e7c-120">E_FAIL</span></span>|<span data-ttu-id="33e7c-121">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="33e7c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="33e7c-122">После метод вернет значение E_FAIL, среда CLR больше не использовать в данном процессе.</span><span class="sxs-lookup"><span data-stu-id="33e7c-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="33e7c-123">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="33e7c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33e7c-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="33e7c-124">Remarks</span></span>  
 <span data-ttu-id="33e7c-125">Среда CLR регистрирует обратный вызов для `OnMemoryNotification` с помощью вызова [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="33e7c-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="33e7c-126">Среда выполнения использует сведения, возвращаемые в обратном вызове, чтобы освободить память, когда узел сообщает, что памяти недостаточно ресурсов.</span><span class="sxs-lookup"><span data-stu-id="33e7c-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33e7c-127">Вызовы `OnMemoryNotification` никогда не блокируется.</span><span class="sxs-lookup"><span data-stu-id="33e7c-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="33e7c-128">Они всегда возвращают немедленно.</span><span class="sxs-lookup"><span data-stu-id="33e7c-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33e7c-129">Требования</span><span class="sxs-lookup"><span data-stu-id="33e7c-129">Requirements</span></span>  
 <span data-ttu-id="33e7c-130">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33e7c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33e7c-131">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="33e7c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33e7c-132">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33e7c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33e7c-133">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33e7c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e7c-134">См. также</span><span class="sxs-lookup"><span data-stu-id="33e7c-134">See also</span></span>

- [<span data-ttu-id="33e7c-135">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="33e7c-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="33e7c-136">Метод RegisterMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="33e7c-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="33e7c-137">Интерфейс ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="33e7c-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
