---
title: Метод ICorProfilerCallback::COMClassicVTableDestroyed
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
ms.openlocfilehash: aa02b4def015d5badfd0003e08bea5289fe58e17
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700188"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="b5d9b-102">Метод ICorProfilerCallback::COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="b5d9b-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>

<span data-ttu-id="b5d9b-103">Уведомляет профилировщик о том, что виртуальная таблица COM-взаимодействия удалена.</span><span class="sxs-lookup"><span data-stu-id="b5d9b-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5d9b-104">Этот обратный вызов, скорее всего, никогда не происходит, так как уничтожение vtable происходит очень близко к завершению работы.</span><span class="sxs-lookup"><span data-stu-id="b5d9b-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5d9b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b5d9b-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5d9b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b5d9b-106">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="b5d9b-107">\[in] идентификатор класса, для которого была создана эта таблица vtable.</span><span class="sxs-lookup"><span data-stu-id="b5d9b-107">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="b5d9b-108">\[in] идентификатор интерфейса, реализуемого классом.</span><span class="sxs-lookup"><span data-stu-id="b5d9b-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="b5d9b-109">Это значение может быть равно NULL, если интерфейс является только внутренним.</span><span class="sxs-lookup"><span data-stu-id="b5d9b-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="b5d9b-110">\[in] указатель на начало таблицы vtable.</span><span class="sxs-lookup"><span data-stu-id="b5d9b-110">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5d9b-111">Комментарии</span><span class="sxs-lookup"><span data-stu-id="b5d9b-111">Remarks</span></span>  

 <span data-ttu-id="b5d9b-112">Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="b5d9b-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b5d9b-113">Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.</span><span class="sxs-lookup"><span data-stu-id="b5d9b-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b5d9b-114">Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.</span><span class="sxs-lookup"><span data-stu-id="b5d9b-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5d9b-115">Требования</span><span class="sxs-lookup"><span data-stu-id="b5d9b-115">Requirements</span></span>  

 <span data-ttu-id="b5d9b-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5d9b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5d9b-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b5d9b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5d9b-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5d9b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5d9b-119">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5d9b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d9b-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b5d9b-120">See also</span></span>

- [<span data-ttu-id="b5d9b-121">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b5d9b-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b5d9b-122">Метод COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="b5d9b-122">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
