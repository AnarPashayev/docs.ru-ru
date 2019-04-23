---
title: Метод ICorProfilerCallback::FunctionUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1c1c9a15e9f56765710ffb2015a29b4206b3bd4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152611"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="0f0e4-102">Метод ICorProfilerCallback::FunctionUnloadStarted</span><span class="sxs-lookup"><span data-stu-id="0f0e4-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="0f0e4-103">Уведомляет профилировщик о том, что среда начала выгрузку функции.</span><span class="sxs-lookup"><span data-stu-id="0f0e4-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f0e4-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0f0e4-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="0f0e4-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="0f0e4-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="0f0e4-106">[in] Идентификатор функции, которая вызывается при выгрузке.</span><span class="sxs-lookup"><span data-stu-id="0f0e4-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f0e4-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="0f0e4-107">Remarks</span></span>  
 <span data-ttu-id="0f0e4-108">Значение `functionId` параметр больше не является допустимым, после этого метод возвращает вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="0f0e4-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f0e4-109">Требования</span><span class="sxs-lookup"><span data-stu-id="0f0e4-109">Requirements</span></span>  
 <span data-ttu-id="0f0e4-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f0e4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f0e4-111">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f0e4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f0e4-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f0e4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f0e4-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f0e4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f0e4-114">См. также</span><span class="sxs-lookup"><span data-stu-id="0f0e4-114">See also</span></span>

- [<span data-ttu-id="0f0e4-115">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0f0e4-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
