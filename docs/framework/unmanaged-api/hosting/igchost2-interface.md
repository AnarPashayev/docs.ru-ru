---
title: Интерфейс IGCHost2
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75bef91eb70c8109653741452362cd2e85f625ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946111"
---
# <a name="igchost2-interface"></a><span data-ttu-id="5fe0d-102">Интерфейс IGCHost2</span><span class="sxs-lookup"><span data-stu-id="5fe0d-102">IGCHost2 Interface</span></span>
<span data-ttu-id="5fe0d-103">Предоставляет методы для получения информации о сборщик мусора, а также для управления некоторыми аспектами сбора мусора.</span><span class="sxs-lookup"><span data-stu-id="5fe0d-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fe0d-104">Для разработки новых приложений мы рекомендуем использовать [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="5fe0d-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5fe0d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="5fe0d-105">Methods</span></span>  
  
|<span data-ttu-id="5fe0d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="5fe0d-106">Method</span></span>|<span data-ttu-id="5fe0d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="5fe0d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5fe0d-108">Метод SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="5fe0d-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="5fe0d-109">Задает размер сегмента и максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="5fe0d-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="5fe0d-110">Позволяет поколения 0 и размера сегментов, размер которых превышает `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="5fe0d-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5fe0d-111">Требования</span><span class="sxs-lookup"><span data-stu-id="5fe0d-111">Requirements</span></span>  
 <span data-ttu-id="5fe0d-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fe0d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fe0d-113">**Заголовок.** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="5fe0d-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="5fe0d-114">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5fe0d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fe0d-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fe0d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe0d-116">См. также</span><span class="sxs-lookup"><span data-stu-id="5fe0d-116">See also</span></span>

- [<span data-ttu-id="5fe0d-117">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="5fe0d-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="5fe0d-118">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="5fe0d-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="5fe0d-119">Кокласс CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="5fe0d-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
