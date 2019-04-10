---
title: Интерфейс ICLRMemoryNotificationCallback
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c98ece9d60571034f3298f15897b10c4d8fb06f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212158"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="ea730-102">Интерфейс ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="ea730-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="ea730-103">Позволяет узлу отчетов об условиях нехватки памяти с помощью подхода, аналогичную Win32 `CreateMemoryResourceNotification` функции.</span><span class="sxs-lookup"><span data-stu-id="ea730-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea730-104">Методы</span><span class="sxs-lookup"><span data-stu-id="ea730-104">Methods</span></span>  
  
|<span data-ttu-id="ea730-105">Метод</span><span class="sxs-lookup"><span data-stu-id="ea730-105">Method</span></span>|<span data-ttu-id="ea730-106">Описание</span><span class="sxs-lookup"><span data-stu-id="ea730-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea730-107">Метод OnMemoryNotification</span><span class="sxs-lookup"><span data-stu-id="ea730-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="ea730-108">Уведомляет общеязыковой среды выполнения (CLR) загрузки памяти на компьютере.</span><span class="sxs-lookup"><span data-stu-id="ea730-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea730-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="ea730-109">Remarks</span></span>  
 <span data-ttu-id="ea730-110">На узле используется `ICLRMemoryNotificationCallback` интерфейс для запроса, что среда CLR освободить ресурсы памяти.</span><span class="sxs-lookup"><span data-stu-id="ea730-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea730-111">Требования</span><span class="sxs-lookup"><span data-stu-id="ea730-111">Requirements</span></span>  
 <span data-ttu-id="ea730-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea730-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea730-113">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ea730-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea730-114">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea730-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ea730-115">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ea730-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ea730-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ea730-116">See also</span></span>

- [<span data-ttu-id="ea730-117">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="ea730-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="ea730-118">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="ea730-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
