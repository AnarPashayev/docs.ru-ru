---
title: Метод ICorDebugHeapValue3::GetMonitorEventWaitList
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db331d75244d59aacf2207a6b83a3f337a64b989
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102795"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="e65f6-102">Метод ICorDebugHeapValue3::GetMonitorEventWaitList</span><span class="sxs-lookup"><span data-stu-id="e65f6-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="e65f6-103">Предоставляет упорядоченный список потоков, которые поставлены в очередь на события, связанного с блокировкой монитора.</span><span class="sxs-lookup"><span data-stu-id="e65f6-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65f6-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e65f6-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e65f6-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e65f6-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="e65f6-106">[out] ICorDebugThreadEnum перечислитель, который предоставляет упорядоченный список потоков.</span><span class="sxs-lookup"><span data-stu-id="e65f6-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e65f6-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e65f6-107">Return Value</span></span>  
 <span data-ttu-id="e65f6-108">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="e65f6-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e65f6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e65f6-109">HRESULT</span></span>|<span data-ttu-id="e65f6-110">Описание</span><span class="sxs-lookup"><span data-stu-id="e65f6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e65f6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e65f6-111">S_OK</span></span>|<span data-ttu-id="e65f6-112">Список не пуст.</span><span class="sxs-lookup"><span data-stu-id="e65f6-112">The list is not empty.</span></span>|  
|<span data-ttu-id="e65f6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e65f6-113">S_FALSE</span></span>|<span data-ttu-id="e65f6-114">Этот список пуст.</span><span class="sxs-lookup"><span data-stu-id="e65f6-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e65f6-115">Исключения</span><span class="sxs-lookup"><span data-stu-id="e65f6-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e65f6-116">Примечания</span><span class="sxs-lookup"><span data-stu-id="e65f6-116">Remarks</span></span>  
 <span data-ttu-id="e65f6-117">Первый поток в списке является первый поток, который гарантированно закрывалось при следующем вызове <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e65f6-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e65f6-118">Следующий поток в списке освобождается на следующий вызов и т. д.</span><span class="sxs-lookup"><span data-stu-id="e65f6-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="e65f6-119">Если список не пуст, этот метод возвращает значение S_OK.</span><span class="sxs-lookup"><span data-stu-id="e65f6-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="e65f6-120">Если список пуст, метод возвращает значение S_FALSE; в этом случае перечисление все еще действует, несмотря на то, что он пуст.</span><span class="sxs-lookup"><span data-stu-id="e65f6-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="e65f6-121">В любом случае интерфейс перечисления может использоваться только в течение текущего синхронизированного состояния.</span><span class="sxs-lookup"><span data-stu-id="e65f6-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="e65f6-122">Тем не менее выданных от него интерфейсы потока являются допустимыми, до выхода из потока.</span><span class="sxs-lookup"><span data-stu-id="e65f6-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="e65f6-123">Если `ppThreadEnum` не является допустимым указателем, результат не определен.</span><span class="sxs-lookup"><span data-stu-id="e65f6-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="e65f6-124">При возникновении ошибки таким образом, что не удается определить, что, если таковые имеются, потоки ожидают монитора, метод возвращает значение HRESULT, указывающее на сбой.</span><span class="sxs-lookup"><span data-stu-id="e65f6-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e65f6-125">Требования</span><span class="sxs-lookup"><span data-stu-id="e65f6-125">Requirements</span></span>  
 <span data-ttu-id="e65f6-126">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e65f6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e65f6-127">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e65f6-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e65f6-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e65f6-128">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e65f6-129">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e65f6-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e65f6-130">См. также</span><span class="sxs-lookup"><span data-stu-id="e65f6-130">See also</span></span>

- [<span data-ttu-id="e65f6-131">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e65f6-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e65f6-132">Отладка</span><span class="sxs-lookup"><span data-stu-id="e65f6-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
