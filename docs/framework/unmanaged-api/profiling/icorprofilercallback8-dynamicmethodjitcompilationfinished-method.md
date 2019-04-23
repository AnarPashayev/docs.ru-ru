---
title: Метод ICorProfilerCallback8::DynamicMethodJITCompilationFinished
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dbe8d4f7050b93ffb34280be6d63367ef294ae8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206594"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="a4c09-102">Метод ICorProfilerCallback8::DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="a4c09-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="a4c09-103">[Поддерживается в .NET Framework 4.7 и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="a4c09-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="a4c09-104">Уведомляет профилировщик, каждый раз, когда JIT-компиляция динамического метода завершения.</span><span class="sxs-lookup"><span data-stu-id="a4c09-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c09-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a4c09-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4c09-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a4c09-106">Parameters</span></span>  
<span data-ttu-id="a4c09-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="a4c09-107">[in] `functionId`</span></span>  
<span data-ttu-id="a4c09-108">Идентификатор функции в памяти, для которого JIT-компиляции запускается.</span><span class="sxs-lookup"><span data-stu-id="a4c09-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="a4c09-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="a4c09-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="a4c09-110">Значение, указывающее, успешно ли JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="a4c09-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="a4c09-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="a4c09-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="a4c09-112">`true` Чтобы указать, что блокировок может вызвать среды выполнения для вызывающего потока для возврата из этого обратного вызова; `false` для указания, что блокировка не повлияет на работу среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="a4c09-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="a4c09-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="a4c09-113">Remarks</span></span>  

<span data-ttu-id="a4c09-114">Этот обратный вызов активируется каждый раз, когда JIT-компиляция динамического метода завершения.</span><span class="sxs-lookup"><span data-stu-id="a4c09-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="a4c09-115">Сюда входят различные заглушки IL и LCG методы.</span><span class="sxs-lookup"><span data-stu-id="a4c09-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="a4c09-116">Его целью является предоставление модулей записи профилировщика достаточно информации для идентификации метода, скомпилированного для пользователей.</span><span class="sxs-lookup"><span data-stu-id="a4c09-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="a4c09-117">`functionId` значения не может использоваться для разрешения на их токены метаданных, так как динамические методы имеют без метаданных.</span><span class="sxs-lookup"><span data-stu-id="a4c09-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4c09-118">Требования</span><span class="sxs-lookup"><span data-stu-id="a4c09-118">Requirements</span></span>  
 <span data-ttu-id="a4c09-119">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4c09-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c09-120">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4c09-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a4c09-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4c09-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4c09-122">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c09-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c09-123">См. также</span><span class="sxs-lookup"><span data-stu-id="a4c09-123">See also</span></span>

- [<span data-ttu-id="a4c09-124">Метод DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="a4c09-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="a4c09-125">Интерфейс ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="a4c09-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
