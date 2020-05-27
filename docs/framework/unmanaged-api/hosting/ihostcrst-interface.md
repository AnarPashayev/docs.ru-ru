---
title: Интерфейс IHostCrst
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: e8cb1486ccea11ba6edcf7bbb781a9bf210b496d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804906"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="2e794-102">Интерфейс IHostCrst</span><span class="sxs-lookup"><span data-stu-id="2e794-102">IHostCrst Interface</span></span>
<span data-ttu-id="2e794-103">Служит в качестве представления критической секции для потоков в основном приложении.</span><span class="sxs-lookup"><span data-stu-id="2e794-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e794-104">Методы</span><span class="sxs-lookup"><span data-stu-id="2e794-104">Methods</span></span>  
  
|<span data-ttu-id="2e794-105">Метод</span><span class="sxs-lookup"><span data-stu-id="2e794-105">Method</span></span>|<span data-ttu-id="2e794-106">Описание</span><span class="sxs-lookup"><span data-stu-id="2e794-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e794-107">Метод Enter</span><span class="sxs-lookup"><span data-stu-id="2e794-107">Enter Method</span></span>](ihostcrst-enter-method.md)|<span data-ttu-id="2e794-108">Входит в критическую секцию.</span><span class="sxs-lookup"><span data-stu-id="2e794-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="2e794-109">Метод Leave</span><span class="sxs-lookup"><span data-stu-id="2e794-109">Leave Method</span></span>](ihostcrst-leave-method.md)|<span data-ttu-id="2e794-110">Оставляет критическую секцию.</span><span class="sxs-lookup"><span data-stu-id="2e794-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="2e794-111">Метод SetSpinCount</span><span class="sxs-lookup"><span data-stu-id="2e794-111">SetSpinCount Method</span></span>](ihostcrst-setspincount-method.md)|<span data-ttu-id="2e794-112">Задает счетчик счетчиков для критической секции.</span><span class="sxs-lookup"><span data-stu-id="2e794-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="2e794-113">Метод TryEnter</span><span class="sxs-lookup"><span data-stu-id="2e794-113">TryEnter Method</span></span>](ihostcrst-tryenter-method.md)|<span data-ttu-id="2e794-114">Пытается войти в критическую секцию и немедленно сообщает об успешном или неуспешном завершении.</span><span class="sxs-lookup"><span data-stu-id="2e794-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e794-115">Замечания</span><span class="sxs-lookup"><span data-stu-id="2e794-115">Remarks</span></span>  
 <span data-ttu-id="2e794-116">`IHostCrst`позволяет среде CLR взаимодействовать непосредственно с представлением критического раздела узла, а не использовать функции Win32, такие как `EnterCriticalSection` или `LeaveCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="2e794-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e794-117">Требования</span><span class="sxs-lookup"><span data-stu-id="2e794-117">Requirements</span></span>  
 <span data-ttu-id="2e794-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e794-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e794-119">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e794-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e794-120">**Библиотека:** Включается в качестве ресурса в библиотеку MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e794-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e794-121">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e794-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e794-122">См. также статью</span><span class="sxs-lookup"><span data-stu-id="2e794-122">See also</span></span>

- [<span data-ttu-id="2e794-123">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="2e794-123">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2e794-124">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="2e794-124">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="2e794-125">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="2e794-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
