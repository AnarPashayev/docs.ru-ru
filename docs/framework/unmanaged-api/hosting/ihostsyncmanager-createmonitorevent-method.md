---
title: Метод IHostSyncManager::CreateMonitorEvent
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b0e32ab46b3e8ba5120da4b16a10db85f105a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127690"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="27fa9-102">Метод IHostSyncManager::CreateMonitorEvent</span><span class="sxs-lookup"><span data-stu-id="27fa9-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="27fa9-103">Создает объект наблюдаемое событие автоматического сброса.</span><span class="sxs-lookup"><span data-stu-id="27fa9-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27fa9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="27fa9-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27fa9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="27fa9-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="27fa9-106">[in] Файл cookie должен быть сопоставлен объект события.</span><span class="sxs-lookup"><span data-stu-id="27fa9-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="27fa9-107">[out] Указатель на адрес [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) экземпляра, или значение null, если не удалось создать объект события.</span><span class="sxs-lookup"><span data-stu-id="27fa9-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27fa9-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="27fa9-108">Return Value</span></span>  
  
|<span data-ttu-id="27fa9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27fa9-109">HRESULT</span></span>|<span data-ttu-id="27fa9-110">Описание</span><span class="sxs-lookup"><span data-stu-id="27fa9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27fa9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="27fa9-111">S_OK</span></span>|<span data-ttu-id="27fa9-112">`CreateMonitorEvent` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="27fa9-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="27fa9-113">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="27fa9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="27fa9-114">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="27fa9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="27fa9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="27fa9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="27fa9-116">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="27fa9-116">The call timed out.</span></span>|  
|<span data-ttu-id="27fa9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="27fa9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="27fa9-118">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="27fa9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="27fa9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="27fa9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="27fa9-120">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="27fa9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="27fa9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="27fa9-121">E_FAIL</span></span>|<span data-ttu-id="27fa9-122">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="27fa9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="27fa9-123">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="27fa9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="27fa9-124">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="27fa9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="27fa9-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="27fa9-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="27fa9-126">Недостаточно памяти, доступного для создания запрошенного объекта события.</span><span class="sxs-lookup"><span data-stu-id="27fa9-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27fa9-127">Примечания</span><span class="sxs-lookup"><span data-stu-id="27fa9-127">Remarks</span></span>  
 <span data-ttu-id="27fa9-128">`CreateMonitorEvent` Возвращает `IHostAutoEvent` , среда CLR использует в своей реализации управляемых <xref:System.Threading.Monitor?displayProperty=nameWithType> типа.</span><span class="sxs-lookup"><span data-stu-id="27fa9-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="27fa9-129">Этот метод отражает Win32 `CreateEvent` функции со значением `false` указанный для `bManualReset` параметра.</span><span class="sxs-lookup"><span data-stu-id="27fa9-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="27fa9-130">Узел может использовать куки-файл, чтобы определить, какая задача ожидает монитор, вызвав [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="27fa9-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27fa9-131">Требования</span><span class="sxs-lookup"><span data-stu-id="27fa9-131">Requirements</span></span>  
 <span data-ttu-id="27fa9-132">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27fa9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27fa9-133">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="27fa9-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27fa9-134">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27fa9-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27fa9-135">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27fa9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27fa9-136">См. также</span><span class="sxs-lookup"><span data-stu-id="27fa9-136">See also</span></span>

- [<span data-ttu-id="27fa9-137">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="27fa9-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="27fa9-138">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="27fa9-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="27fa9-139">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="27fa9-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
