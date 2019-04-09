---
title: Метод IGCHostControl::RequestVirtualMemLimit
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948b18832ccfc5e0fc2e42ee58e6444a581de260
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209697"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="65c3d-102">Метод IGCHostControl::RequestVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="65c3d-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="65c3d-103">Запрашивает узла, чтобы изменить ограничения виртуальной памяти.</span><span class="sxs-lookup"><span data-stu-id="65c3d-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c3d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="65c3d-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65c3d-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="65c3d-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="65c3d-106">[in] Запрошенный размер выделяемой памяти.</span><span class="sxs-lookup"><span data-stu-id="65c3d-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="65c3d-107">[in, out] Указатель на фактический размер выделенной памяти.</span><span class="sxs-lookup"><span data-stu-id="65c3d-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65c3d-108">Требования</span><span class="sxs-lookup"><span data-stu-id="65c3d-108">Requirements</span></span>  
 <span data-ttu-id="65c3d-109">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c3d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c3d-110">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65c3d-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65c3d-111">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65c3d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="65c3d-112">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="65c3d-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65c3d-113">См. также</span><span class="sxs-lookup"><span data-stu-id="65c3d-113">See also</span></span>

- [<span data-ttu-id="65c3d-114">Интерфейс IGCHostControl</span><span class="sxs-lookup"><span data-stu-id="65c3d-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
