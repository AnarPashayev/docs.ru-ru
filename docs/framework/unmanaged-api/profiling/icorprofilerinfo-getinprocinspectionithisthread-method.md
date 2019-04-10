---
title: Метод ICorProfilerInfo::GetInprocInspectionIThisThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24b7af4b44d51da06e9d65104f1b469ef1d83b8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219438"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="9911a-102">Метод ICorProfilerInfo::GetInprocInspectionIThisThread</span><span class="sxs-lookup"><span data-stu-id="9911a-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="9911a-103">Получает объект, который можно запросить для ICorDebugThread-интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9911a-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="9911a-104">Этот метод является устаревшим в .NET Framework версии 2.0.</span><span class="sxs-lookup"><span data-stu-id="9911a-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9911a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9911a-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9911a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9911a-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="9911a-107">[out](/cpp/atl/iunknown) объект, который можно запросить для `ICorDebugThread` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9911a-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9911a-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="9911a-108">Remarks</span></span>  
 <span data-ttu-id="9911a-109">Общеязыковой среды выполнения (CLR), службы отладки поддерживается только в процессе отладки в .NET Framework версии 1.0.</span><span class="sxs-lookup"><span data-stu-id="9911a-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="9911a-110">В процессе отладки включить профилировщик для использования для проверки часть API отладки.</span><span class="sxs-lookup"><span data-stu-id="9911a-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="9911a-111">В результате отзывов в процессе отладки удален из .NET Framework версии 2.0 и заменены набором функциональных возможностей, которые лучше соответствуют API профилирования.</span><span class="sxs-lookup"><span data-stu-id="9911a-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9911a-112">Требования</span><span class="sxs-lookup"><span data-stu-id="9911a-112">Requirements</span></span>  
 <span data-ttu-id="9911a-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9911a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9911a-114">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9911a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9911a-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9911a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9911a-116">**Версии платформы .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="9911a-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9911a-117">См. также</span><span class="sxs-lookup"><span data-stu-id="9911a-117">See also</span></span>

- [<span data-ttu-id="9911a-118">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="9911a-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
