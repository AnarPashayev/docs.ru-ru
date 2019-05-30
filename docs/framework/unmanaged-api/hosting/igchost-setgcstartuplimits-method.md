---
title: Метод IGCHost::SetGCStartupLimits
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e65a83d1da0580436babd15e4f27e2db7a698668
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377601"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="7f401-102">Метод IGCHost::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="7f401-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="7f401-103">Задает размер сегмента и максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="7f401-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7f401-104">Начиная с .NET Framework 4.5, можно задать размер сегмента и максимально возможного поколения 0 размер значения больше, чем `DWORD` с помощью [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="7f401-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f401-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7f401-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f401-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7f401-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="7f401-107">[in] Размер сегмента, используемой системой сбора мусора.</span><span class="sxs-lookup"><span data-stu-id="7f401-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="7f401-108">[in] Максимальный размер поколения 0.</span><span class="sxs-lookup"><span data-stu-id="7f401-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f401-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="7f401-109">Remarks</span></span>  
 <span data-ttu-id="7f401-110">`SetGCStartupLimits` Метод может вызываться только один раз.</span><span class="sxs-lookup"><span data-stu-id="7f401-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="7f401-111">Эти значения нельзя изменить позже.</span><span class="sxs-lookup"><span data-stu-id="7f401-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f401-112">Требования</span><span class="sxs-lookup"><span data-stu-id="7f401-112">Requirements</span></span>  
 <span data-ttu-id="7f401-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f401-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f401-114">**Заголовок.** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="7f401-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="7f401-115">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f401-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f401-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f401-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f401-117">См. также</span><span class="sxs-lookup"><span data-stu-id="7f401-117">See also</span></span>

- [<span data-ttu-id="7f401-118">Интерфейс IGCHost</span><span class="sxs-lookup"><span data-stu-id="7f401-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
