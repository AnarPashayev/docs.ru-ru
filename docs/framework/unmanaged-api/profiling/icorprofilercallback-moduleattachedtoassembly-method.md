---
title: Метод ICorProfilerCallback::ModuleAttachedToAssembly
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3345e2e87ba41f750031deed2d15e13dbe4f06c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769291"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="66a80-102">Метод ICorProfilerCallback::ModuleAttachedToAssembly</span><span class="sxs-lookup"><span data-stu-id="66a80-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="66a80-103">Уведомляет профилировщик, что модуль присоединяется к ее родительской сборки.</span><span class="sxs-lookup"><span data-stu-id="66a80-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a80-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="66a80-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66a80-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="66a80-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="66a80-106">[in] Идентификатор модуля, который присоединяется.</span><span class="sxs-lookup"><span data-stu-id="66a80-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="66a80-107">[in] Идентификатор родительской сборки, к которой подключен модуль.</span><span class="sxs-lookup"><span data-stu-id="66a80-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66a80-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="66a80-108">Remarks</span></span>  
 <span data-ttu-id="66a80-109">Модуль может быть загружен посредством таблицы адресов импорта (IAT), посредством вызова `LoadLibrary`, или с помощью ссылки на метаданные.</span><span class="sxs-lookup"><span data-stu-id="66a80-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="66a80-110">Таким образом загрузчик распространенных языковой среды выполнения (CLR) имеет несколько путей кода для определения сборки, в котором находится модуль.</span><span class="sxs-lookup"><span data-stu-id="66a80-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="66a80-111">Таким образом, возможна после того как [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) вызывается, модуль не знает, какие сборки в и получение идентификатора родительской сборки не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="66a80-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="66a80-112">`ModuleAttachedToAssembly` При присоединении к ее родительской сборки и ее родительской сборки, можно получить идентификатор модуля, вызывается метод.</span><span class="sxs-lookup"><span data-stu-id="66a80-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66a80-113">Требования</span><span class="sxs-lookup"><span data-stu-id="66a80-113">Requirements</span></span>  
 <span data-ttu-id="66a80-114">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a80-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66a80-115">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66a80-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66a80-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66a80-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66a80-117">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a80-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a80-118">См. также</span><span class="sxs-lookup"><span data-stu-id="66a80-118">See also</span></span>

- [<span data-ttu-id="66a80-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="66a80-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
