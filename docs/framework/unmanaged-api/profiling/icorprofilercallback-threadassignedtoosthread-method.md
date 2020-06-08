---
title: Метод ICorProfilerCallback::ThreadAssignedToOSThread
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
ms.openlocfilehash: 182a82300183046ccb4a93a79af0dd8f23848c20
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503183"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="ca4c2-102">Метод ICorProfilerCallback::ThreadAssignedToOSThread</span><span class="sxs-lookup"><span data-stu-id="ca4c2-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="ca4c2-103">Уведомляет профилировщик о том, что управляемый поток реализуется с помощью определенного потока операционной системы.</span><span class="sxs-lookup"><span data-stu-id="ca4c2-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca4c2-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ca4c2-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca4c2-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="ca4c2-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="ca4c2-106">окне Идентификатор управляемого потока.</span><span class="sxs-lookup"><span data-stu-id="ca4c2-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="ca4c2-107">окне Идентификатор потока операционной системы.</span><span class="sxs-lookup"><span data-stu-id="ca4c2-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca4c2-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="ca4c2-108">Remarks</span></span>  
 <span data-ttu-id="ca4c2-109">`ThreadAssignedToOSThread`Обратный вызов существует, чтобы профилировщик мог поддерживать точное сопоставление по волокнам потоков операционной системы с управляемыми потоками.</span><span class="sxs-lookup"><span data-stu-id="ca4c2-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca4c2-110">Требования</span><span class="sxs-lookup"><span data-stu-id="ca4c2-110">Requirements</span></span>  
 <span data-ttu-id="ca4c2-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca4c2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca4c2-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ca4c2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ca4c2-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca4c2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca4c2-114">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca4c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca4c2-115">См. также</span><span class="sxs-lookup"><span data-stu-id="ca4c2-115">See also</span></span>

- [<span data-ttu-id="ca4c2-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="ca4c2-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
