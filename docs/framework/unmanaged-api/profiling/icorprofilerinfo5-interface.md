---
title: Интерфейс ICorProfilerInfo5
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b249605833e8fbd219495ab92bebc2eff6177eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094259"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="64042-102">Интерфейс ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="64042-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="64042-103">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="64042-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="64042-104">Подкласс [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) , предоставляющий методы для использования профилировщиками кода для взаимодействия с общеязыковой среды выполнения (CLR) для управления отслеживанием событий.</span><span class="sxs-lookup"><span data-stu-id="64042-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64042-105">Методы</span><span class="sxs-lookup"><span data-stu-id="64042-105">Methods</span></span>  
  
|<span data-ttu-id="64042-106">Метод</span><span class="sxs-lookup"><span data-stu-id="64042-106">Method</span></span>|<span data-ttu-id="64042-107">Описание</span><span class="sxs-lookup"><span data-stu-id="64042-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64042-108">Метод GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="64042-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="64042-109">Получает текущие категории событий, о которых профилировщик хочет принимать уведомления из среды CLR.</span><span class="sxs-lookup"><span data-stu-id="64042-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="64042-110">Метод SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="64042-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="64042-111">Определяет значение, указывающее типы событий, для которых профилировщик хочет принимать уведомления о событиях от среды CLR.</span><span class="sxs-lookup"><span data-stu-id="64042-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64042-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="64042-112">Remarks</span></span>  
 <span data-ttu-id="64042-113">Методы, доступные на этом интерфейсе, предназначены для замены [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) и [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) методы.</span><span class="sxs-lookup"><span data-stu-id="64042-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64042-114">Требования</span><span class="sxs-lookup"><span data-stu-id="64042-114">Requirements</span></span>  
 <span data-ttu-id="64042-115">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64042-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64042-116">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64042-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64042-117">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64042-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64042-118">См. также</span><span class="sxs-lookup"><span data-stu-id="64042-118">See also</span></span>

- [<span data-ttu-id="64042-119">Интерфейсы профилирования</span><span class="sxs-lookup"><span data-stu-id="64042-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
