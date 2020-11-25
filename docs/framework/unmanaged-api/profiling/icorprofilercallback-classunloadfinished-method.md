---
title: Метод ICorProfilerCallback::ClassUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 114d5d58d0d9098944299aefd0cb99a70c5da09d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700266"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="0e627-102">Метод ICorProfilerCallback::ClassUnloadFinished</span><span class="sxs-lookup"><span data-stu-id="0e627-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>

<span data-ttu-id="0e627-103">Уведомляет профилировщик о завершении выгрузки класса.</span><span class="sxs-lookup"><span data-stu-id="0e627-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e627-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0e627-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e627-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="0e627-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="0e627-106">\[в] определяет класс, который был выгружен.</span><span class="sxs-lookup"><span data-stu-id="0e627-106">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="0e627-107">\[in] значение HRESULT, указывающее, успешно ли выгружен класс.</span><span class="sxs-lookup"><span data-stu-id="0e627-107">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="0e627-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="0e627-108">Remarks</span></span>  

 <span data-ttu-id="0e627-109">Некоторые части выгрузки класса могут продолжаться после `ClassUnloadFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="0e627-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="0e627-110">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="0e627-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="0e627-111">Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть выгрузки класса успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="0e627-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e627-112">Требования</span><span class="sxs-lookup"><span data-stu-id="0e627-112">Requirements</span></span>  

 <span data-ttu-id="0e627-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e627-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e627-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0e627-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0e627-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e627-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e627-116">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e627-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e627-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0e627-117">See also</span></span>

- [<span data-ttu-id="0e627-118">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0e627-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0e627-119">Метод ClassUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="0e627-119">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
