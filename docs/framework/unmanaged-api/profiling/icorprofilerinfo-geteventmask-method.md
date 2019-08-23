---
title: Метод ICorProfilerInfo::GetEventMask
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fea50b9d42511540197c80d4ba402834b216830
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957947"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="68809-102">Метод ICorProfilerInfo::GetEventMask</span><span class="sxs-lookup"><span data-stu-id="68809-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="68809-103">Получает текущие категории событий, о которых профилировщик хочет получать уведомления из среды CLR.</span><span class="sxs-lookup"><span data-stu-id="68809-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68809-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="68809-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68809-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="68809-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="68809-106">[из] Указатель на 4-байтовое значение, определяющее категории событий.</span><span class="sxs-lookup"><span data-stu-id="68809-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="68809-107">Каждый бит управляет отдельной возможностью, поведением или типом события.</span><span class="sxs-lookup"><span data-stu-id="68809-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="68809-108">Биты описаны в перечислении [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="68809-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68809-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="68809-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68809-110">Вместо этого метода следует вызвать метод [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="68809-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="68809-111">Несмотря на `SetEventMask` то, что метод поддерживается, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) предоставляет дополнительные функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="68809-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68809-112">Требования</span><span class="sxs-lookup"><span data-stu-id="68809-112">Requirements</span></span>  
 <span data-ttu-id="68809-113">**Платформ** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68809-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68809-114">**Заголовок.** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="68809-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="68809-115">**Библиотечная** Коргуидс. lib</span><span class="sxs-lookup"><span data-stu-id="68809-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68809-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68809-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68809-117">См. также</span><span class="sxs-lookup"><span data-stu-id="68809-117">See also</span></span>

- [<span data-ttu-id="68809-118">Метод GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="68809-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="68809-119">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="68809-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
