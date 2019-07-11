---
title: Метод IHostSecurityManager::RevertToSelf
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f098d8462229a405d5775203368478c7ee7e9f3c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769401"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="d21ba-102">Метод IHostSecurityManager::RevertToSelf</span><span class="sxs-lookup"><span data-stu-id="d21ba-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="d21ba-103">Завершает олицетворение удостоверения текущего пользователя и возвращает исходный маркер потока.</span><span class="sxs-lookup"><span data-stu-id="d21ba-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d21ba-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d21ba-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d21ba-105">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d21ba-105">Return Value</span></span>  
  
|<span data-ttu-id="d21ba-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d21ba-106">HRESULT</span></span>|<span data-ttu-id="d21ba-107">Описание</span><span class="sxs-lookup"><span data-stu-id="d21ba-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d21ba-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d21ba-108">S_OK</span></span>|<span data-ttu-id="d21ba-109">`RevertToSelf` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="d21ba-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="d21ba-110">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d21ba-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d21ba-111">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="d21ba-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d21ba-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d21ba-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d21ba-113">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="d21ba-113">The call timed out.</span></span>|  
|<span data-ttu-id="d21ba-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d21ba-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d21ba-115">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="d21ba-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d21ba-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d21ba-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d21ba-117">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="d21ba-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d21ba-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d21ba-118">E_FAIL</span></span>|<span data-ttu-id="d21ba-119">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="d21ba-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d21ba-120">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="d21ba-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d21ba-121">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d21ba-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d21ba-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="d21ba-122">Remarks</span></span>  
 <span data-ttu-id="d21ba-123">`RevertToSelf` вызывается для возвращения исходный маркер потока, после предыдущего вызова [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="d21ba-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d21ba-124">Требования</span><span class="sxs-lookup"><span data-stu-id="d21ba-124">Requirements</span></span>  
 <span data-ttu-id="d21ba-125">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d21ba-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d21ba-126">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d21ba-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d21ba-127">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d21ba-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d21ba-128">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d21ba-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d21ba-129">См. также</span><span class="sxs-lookup"><span data-stu-id="d21ba-129">See also</span></span>

- [<span data-ttu-id="d21ba-130">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="d21ba-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="d21ba-131">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="d21ba-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="d21ba-132">Метод ImpersonateLoggedOnUser</span><span class="sxs-lookup"><span data-stu-id="d21ba-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
