---
title: Метод IHostMemoryManager::AcquiredVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
ms.openlocfilehash: 58fce616ae05dcc622369a706f010f91d657389f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700630"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="414ed-102">Метод IHostMemoryManager::AcquiredVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="414ed-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>

<span data-ttu-id="414ed-103">Уведомляет узел о том, что среда CLR получила указанную память из операционной системы.</span><span class="sxs-lookup"><span data-stu-id="414ed-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="414ed-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="414ed-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="414ed-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="414ed-105">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="414ed-106">окне Начальный адрес памяти.</span><span class="sxs-lookup"><span data-stu-id="414ed-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="414ed-107">окне Размер памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="414ed-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="414ed-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="414ed-108">Remarks</span></span>  

 <span data-ttu-id="414ed-109">`AcquiredVirtualAddressSpace`Метод является методом обратного вызова и должен быть реализован модулем записи размещающего приложения.</span><span class="sxs-lookup"><span data-stu-id="414ed-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="414ed-110">Он вызывается средой CLR.</span><span class="sxs-lookup"><span data-stu-id="414ed-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="414ed-111">Требования</span><span class="sxs-lookup"><span data-stu-id="414ed-111">Requirements</span></span>  

 <span data-ttu-id="414ed-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="414ed-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="414ed-113">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="414ed-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="414ed-114">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="414ed-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="414ed-115">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="414ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="414ed-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="414ed-116">See also</span></span>

- [<span data-ttu-id="414ed-117">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="414ed-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
