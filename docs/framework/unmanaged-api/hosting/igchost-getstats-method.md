---
title: Метод IGCHost::GetStats
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14751b41809eeda5e6bd990fae368879d0f30492
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227838"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="0d7a4-102">Метод IGCHost::GetStats</span><span class="sxs-lookup"><span data-stu-id="0d7a4-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="0d7a4-103">Получает статистику для текущего состояния сборщик мусора.</span><span class="sxs-lookup"><span data-stu-id="0d7a4-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d7a4-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d7a4-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d7a4-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="0d7a4-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="0d7a4-106">[in, out] Указатель на [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) структуру, которая содержит статистические данные для текущего состояния сборщик мусора.</span><span class="sxs-lookup"><span data-stu-id="0d7a4-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d7a4-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="0d7a4-107">Remarks</span></span>  
 <span data-ttu-id="0d7a4-108">Статистику можно с помощью системы оптимального распределения помогут сборщик мусора работают.</span><span class="sxs-lookup"><span data-stu-id="0d7a4-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="0d7a4-109">Например, система распределения может определить, просмотрев статистические данные, необходимо установить дополнительную память или принудительно коллекции.</span><span class="sxs-lookup"><span data-stu-id="0d7a4-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d7a4-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0d7a4-110">Requirements</span></span>  
 <span data-ttu-id="0d7a4-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d7a4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d7a4-112">**Заголовок.** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="0d7a4-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="0d7a4-113">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d7a4-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d7a4-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d7a4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d7a4-115">См. также</span><span class="sxs-lookup"><span data-stu-id="0d7a4-115">See also</span></span>

- [<span data-ttu-id="0d7a4-116">Интерфейс IGCHost</span><span class="sxs-lookup"><span data-stu-id="0d7a4-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
