---
title: Метод IHostAssemblyManager::GetAssemblyStore
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35e38949ce945d93216daffd3c0d91dad6c8739b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763195"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="fbd57-102">Метод IHostAssemblyManager::GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="fbd57-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="fbd57-103">Получает указатель интерфейса на [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , представляющий список сборок, загруженных приложением.</span><span class="sxs-lookup"><span data-stu-id="fbd57-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbd57-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fbd57-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbd57-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="fbd57-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="fbd57-106">[out] Указатель функции `IHostAssemblyStore` экземпляра, или значение null, если узел не реализует `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="fbd57-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbd57-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fbd57-107">Return Value</span></span>  
  
|<span data-ttu-id="fbd57-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbd57-108">HRESULT</span></span>|<span data-ttu-id="fbd57-109">Описание</span><span class="sxs-lookup"><span data-stu-id="fbd57-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbd57-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fbd57-110">S_OK</span></span>|<span data-ttu-id="fbd57-111">`GetAssemblyStore` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="fbd57-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="fbd57-112">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fbd57-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fbd57-113">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="fbd57-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fbd57-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fbd57-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fbd57-115">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="fbd57-115">The call timed out.</span></span>|  
|<span data-ttu-id="fbd57-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fbd57-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fbd57-117">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="fbd57-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fbd57-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fbd57-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fbd57-119">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="fbd57-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fbd57-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fbd57-120">E_FAIL</span></span>|<span data-ttu-id="fbd57-121">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="fbd57-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fbd57-122">Когда метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="fbd57-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fbd57-123">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fbd57-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fbd57-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="fbd57-124">E_NOINTERFACE</span></span>|<span data-ttu-id="fbd57-125">Узел не поддерживает реализацию `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="fbd57-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbd57-126">Примечания</span><span class="sxs-lookup"><span data-stu-id="fbd57-126">Remarks</span></span>  
 <span data-ttu-id="fbd57-127">`IHostAssemblyStore` Предоставляет методы, позволяющие узлу для привязки к сборкам и модулям независимо от среды CLR.</span><span class="sxs-lookup"><span data-stu-id="fbd57-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="fbd57-128">Узлы обычно предоставляют хранилища можно разрешить сборок, загружаемых из форматов, отличных от файловой системы.</span><span class="sxs-lookup"><span data-stu-id="fbd57-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbd57-129">Если узел не реализует `IHostAssemblyStore`, `GetAssemblyStore` должен возвращать значение HRESULT E_NOINTERFACE модели, а также следует задать `ppAssemblyStore` значение null.</span><span class="sxs-lookup"><span data-stu-id="fbd57-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbd57-130">Требования</span><span class="sxs-lookup"><span data-stu-id="fbd57-130">Requirements</span></span>  
 <span data-ttu-id="fbd57-131">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbd57-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbd57-132">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fbd57-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbd57-133">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fbd57-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbd57-134">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbd57-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbd57-135">См. также</span><span class="sxs-lookup"><span data-stu-id="fbd57-135">See also</span></span>

- [<span data-ttu-id="fbd57-136">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="fbd57-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="fbd57-137">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="fbd57-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
