---
title: Метод ICorDebugHeapValue3::GetThreadOwningMonitorLock
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1678f1de7c23387f028348dadbc7b61e2cdc035c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201433"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="e11e7-102">Метод ICorDebugHeapValue3::GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="e11e7-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="e11e7-103">Возвращает управляемый поток, которому принадлежит блокировка монитора для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="e11e7-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e11e7-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e11e7-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e11e7-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e11e7-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="e11e7-106">[out] Управляемый поток, которому принадлежит блокировка монитора для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="e11e7-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="e11e7-107">[out] Количество раз, этот поток необходимо снять блокировку, прежде чем он возвращается монитором.</span><span class="sxs-lookup"><span data-stu-id="e11e7-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e11e7-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e11e7-108">Return Value</span></span>  
 <span data-ttu-id="e11e7-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="e11e7-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e11e7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e11e7-110">HRESULT</span></span>|<span data-ttu-id="e11e7-111">Описание</span><span class="sxs-lookup"><span data-stu-id="e11e7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e11e7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e11e7-112">S_OK</span></span>|<span data-ttu-id="e11e7-113">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="e11e7-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="e11e7-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e11e7-114">S_FALSE</span></span>|<span data-ttu-id="e11e7-115">Не управляемый поток владеет блокировкой монитора на этот объект.</span><span class="sxs-lookup"><span data-stu-id="e11e7-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e11e7-116">Исключения</span><span class="sxs-lookup"><span data-stu-id="e11e7-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e11e7-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="e11e7-117">Remarks</span></span>  
 <span data-ttu-id="e11e7-118">Если управляемый поток владеет блокировкой монитора на этот объект:</span><span class="sxs-lookup"><span data-stu-id="e11e7-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="e11e7-119">Метод возвращает значение S_OK.</span><span class="sxs-lookup"><span data-stu-id="e11e7-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="e11e7-120">Поток выходит из объекта потока остается действительным.</span><span class="sxs-lookup"><span data-stu-id="e11e7-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="e11e7-121">Если не управляемый поток владеет блокировкой монитора на этот объект `ppThread` и `pAcquisitionCount` ничем не отличаются, и метод возвращает значение S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="e11e7-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="e11e7-122">Если `ppThread` или `pAcquisitionCount` не является допустимым указателем, результат не определен.</span><span class="sxs-lookup"><span data-stu-id="e11e7-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="e11e7-123">При возникновении ошибки таким образом, что не удается определить, который, если таковые имеются, поток владеет блокировкой монитора на этот объект, метод возвращает значение HRESULT, указывающее на сбой.</span><span class="sxs-lookup"><span data-stu-id="e11e7-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e11e7-124">Требования</span><span class="sxs-lookup"><span data-stu-id="e11e7-124">Requirements</span></span>  
 <span data-ttu-id="e11e7-125">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e11e7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e11e7-126">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e11e7-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e11e7-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e11e7-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e11e7-128">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e11e7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e11e7-129">См. также</span><span class="sxs-lookup"><span data-stu-id="e11e7-129">See also</span></span>

- [<span data-ttu-id="e11e7-130">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e11e7-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e11e7-131">Отладка</span><span class="sxs-lookup"><span data-stu-id="e11e7-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
