---
title: Метод ICLRTask2::BeginPreventAsyncAbort
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a43fef7f6dfa6dbe0bb9f1c4caec2c9c224b93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213588"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="dbbde-102">Метод ICLRTask2::BeginPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="dbbde-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="dbbde-103">Новый поток задержки запросов в прерывания потока в текущем потоке прерывания.</span><span class="sxs-lookup"><span data-stu-id="dbbde-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbbde-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dbbde-104">Syntax</span></span>  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dbbde-105">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dbbde-105">Return Value</span></span>  
 <span data-ttu-id="dbbde-106">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="dbbde-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dbbde-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbbde-107">HRESULT</span></span>|<span data-ttu-id="dbbde-108">Описание</span><span class="sxs-lookup"><span data-stu-id="dbbde-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbbde-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbbde-109">S_OK</span></span>|<span data-ttu-id="dbbde-110">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="dbbde-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="dbbde-111">ЗНАЧЕНИЕ HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="dbbde-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="dbbde-112">Метод был вызван для потока, который не является текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="dbbde-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbbde-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="dbbde-113">Remarks</span></span>  
 <span data-ttu-id="dbbde-114">Вызов этого метода увеличивает счетчик прерываний задержки потока для текущего потока на единицу.</span><span class="sxs-lookup"><span data-stu-id="dbbde-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="dbbde-115">Вызовы `BeginPreventAsyncAbort` и [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="dbbde-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="dbbde-116">До тех пор, пока счетчик не равно нулю, являются отложенными прерывания потока для текущего потока.</span><span class="sxs-lookup"><span data-stu-id="dbbde-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="dbbde-117">Если этот вызов не объединен с вызовом `EndPreventAsyncAbort` метод, можно достичь состояния, в каком потоке прерывания не удается доставить к текущему потоку.</span><span class="sxs-lookup"><span data-stu-id="dbbde-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="dbbde-118">Задержка не учитывается для потока, который прерывает сам.</span><span class="sxs-lookup"><span data-stu-id="dbbde-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="dbbde-119">Функциональные возможности, предоставляемые этой функции используется внутри виртуальной машины (VM).</span><span class="sxs-lookup"><span data-stu-id="dbbde-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="dbbde-120">Неправильное использование этих методов может привести к непредсказуемому поведению в виртуальной Машине.</span><span class="sxs-lookup"><span data-stu-id="dbbde-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="dbbde-121">Например, вызов `EndPreventAsyncAbort` без предварительного вызова функции `BeginPreventAsyncAbort` удалось задать счетчик до нуля, когда Виртуальная машина увеличит его.</span><span class="sxs-lookup"><span data-stu-id="dbbde-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="dbbde-122">Аналогичным образом внутренний счетчик не проверяются на переполнение.</span><span class="sxs-lookup"><span data-stu-id="dbbde-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="dbbde-123">Если оно превышает превышено, так как увеличивается на узле и виртуальной Машины, результирующее поведение не определено.</span><span class="sxs-lookup"><span data-stu-id="dbbde-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbbde-124">Требования</span><span class="sxs-lookup"><span data-stu-id="dbbde-124">Requirements</span></span>  
 <span data-ttu-id="dbbde-125">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbbde-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbbde-126">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbbde-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbbde-127">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbbde-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbbde-128">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbbde-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbde-129">См. также</span><span class="sxs-lookup"><span data-stu-id="dbbde-129">See also</span></span>

- [<span data-ttu-id="dbbde-130">Метод EndPreventAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="dbbde-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="dbbde-131">Интерфейс ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="dbbde-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [<span data-ttu-id="dbbde-132">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="dbbde-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="dbbde-133">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="dbbde-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="dbbde-134">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="dbbde-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="dbbde-135">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="dbbde-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
