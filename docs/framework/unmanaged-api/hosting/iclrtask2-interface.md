---
title: Интерфейс ICLRTask2
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518248651de6d8afdf25692c5f48da52b11eb0f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172475"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="aceef-102">Интерфейс ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="aceef-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="aceef-103">Предоставляет все функциональные возможности [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) интерфейс; Кроме того, предоставляет методы, позволяющие прерывания потоков, задержки в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="aceef-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aceef-104">Методы</span><span class="sxs-lookup"><span data-stu-id="aceef-104">Methods</span></span>  
  
|<span data-ttu-id="aceef-105">Метод</span><span class="sxs-lookup"><span data-stu-id="aceef-105">Method</span></span>|<span data-ttu-id="aceef-106">Описание</span><span class="sxs-lookup"><span data-stu-id="aceef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aceef-107">Метод BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="aceef-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="aceef-108">Задержки новые запросы прерывания потока в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="aceef-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="aceef-109">Метод EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="aceef-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="aceef-110">Позволяет новым или ожидающих запросов прерывания потока с последующим получением поток прерывает выполнение в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="aceef-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aceef-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="aceef-111">Remarks</span></span>  
 <span data-ttu-id="aceef-112">`ICLRTask2` Интерфейс наследует `ICLRTask` интерфейс и добавляет методы, позволяющие основному приложению задерживать аварийные завершения потоков, для защиты области кода, который должен работать без сбоев.</span><span class="sxs-lookup"><span data-stu-id="aceef-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="aceef-113">Вызов `BeginPreventAsyncAbort` увеличивает значение счетчика прерываний задержки потока для текущего потока и вызова `EndPreventAsyncAbort` уменьшает его.</span><span class="sxs-lookup"><span data-stu-id="aceef-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="aceef-114">Вызовы `BeginPreventAsyncAbort` и `EndPreventAsyncAbort` могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="aceef-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="aceef-115">До тех пор, пока счетчик не равно нулю, являются отложенными прерывания потока для текущего потока.</span><span class="sxs-lookup"><span data-stu-id="aceef-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="aceef-116">Если вызовы `BeginPreventAsyncAbort` и `EndPreventAsyncAbort` находятся не в паре, это можно достичь состояния, в каком потоке прерывания не доставляться к текущему потоку.</span><span class="sxs-lookup"><span data-stu-id="aceef-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="aceef-117">Задержка не учитывается для потока, который прерывает сам.</span><span class="sxs-lookup"><span data-stu-id="aceef-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="aceef-118">Функциональные возможности, предоставляемые этой функции используется внутри виртуальной машины (VM).</span><span class="sxs-lookup"><span data-stu-id="aceef-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="aceef-119">Неправильное использование этих методов может привести к непредсказуемому поведению в виртуальной Машине.</span><span class="sxs-lookup"><span data-stu-id="aceef-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="aceef-120">Например, вызов `EndPreventAsyncAbort` без предварительного вызова функции `BeginPreventAsyncAbort` удалось задать счетчик до нуля, когда Виртуальная машина увеличит его.</span><span class="sxs-lookup"><span data-stu-id="aceef-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="aceef-121">Аналогичным образом внутренний счетчик не проверяются на переполнение.</span><span class="sxs-lookup"><span data-stu-id="aceef-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="aceef-122">Если оно превышает превышено, так как увеличивается на узле и виртуальной Машины, результирующее поведение не определено.</span><span class="sxs-lookup"><span data-stu-id="aceef-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="aceef-123">Сведения об элементах, наследуемого от `ICLRTask` и о других вариантах использования этого интерфейса, см. в разделе [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="aceef-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aceef-124">Требования</span><span class="sxs-lookup"><span data-stu-id="aceef-124">Requirements</span></span>  
 <span data-ttu-id="aceef-125">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aceef-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aceef-126">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aceef-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aceef-127">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aceef-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aceef-128">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aceef-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aceef-129">См. также</span><span class="sxs-lookup"><span data-stu-id="aceef-129">See also</span></span>

- [<span data-ttu-id="aceef-130">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="aceef-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="aceef-131">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="aceef-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="aceef-132">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="aceef-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="aceef-133">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="aceef-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="aceef-134">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="aceef-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
