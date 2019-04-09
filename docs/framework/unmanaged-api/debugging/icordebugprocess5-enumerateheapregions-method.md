---
title: Метод ICorDebugProcess5::EnumerateHeapRegions
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61e30cf4ffe45578f7ad37de8295d227dbf313c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103965"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="1a0dc-102">Метод ICorDebugProcess5::EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="1a0dc-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="1a0dc-103">Возвращает перечислитель для диапазона памяти управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="1a0dc-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a0dc-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1a0dc-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a0dc-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="1a0dc-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="1a0dc-106">[out] Указатель на адрес [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) объект интерфейса, который является перечислителем для диапазонов адресов памяти, в котором находятся объекты в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="1a0dc-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a0dc-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="1a0dc-107">Remarks</span></span>  
 <span data-ttu-id="1a0dc-108">Перед вызовом `ICorDebugProcess5::EnumerateHeapRegions` метод следует вызывать [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) метод и проверьте значение `areGCStructuresValid` поле возвращенного [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Объект, чтобы убедиться, что в ее текущем состоянии куче сбора мусора является перечислимым.</span><span class="sxs-lookup"><span data-stu-id="1a0dc-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="1a0dc-109">Кроме того `ICorDebugProcess5::EnumerateHeapRegions` возвращает метод `E_FAIL` при присоединении слишком раннем этапе жизни процесса, прежде чем памяти регионах создаются.</span><span class="sxs-lookup"><span data-stu-id="1a0dc-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="1a0dc-110">Этот метод гарантированно перечисления всех областей памяти, которые могут содержать управляемые объекты, но это не гарантирует, что управляемые объекты располагаются в этих регионах.</span><span class="sxs-lookup"><span data-stu-id="1a0dc-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="1a0dc-111">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) объект коллекции могут быть пустой или зарезервированный памяти регионы.</span><span class="sxs-lookup"><span data-stu-id="1a0dc-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="1a0dc-112">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) объект интерфейс является производным от ICorDebugEnum интерфейс, который позволяет перечислять стандартный перечислитель [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) объектов.</span><span class="sxs-lookup"><span data-stu-id="1a0dc-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="1a0dc-113">Каждый [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) объект предоставляет сведения о диапазоне памяти конкретного сегмента, а также поколение объектов, в этом сегменте.</span><span class="sxs-lookup"><span data-stu-id="1a0dc-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a0dc-114">Требования</span><span class="sxs-lookup"><span data-stu-id="1a0dc-114">Requirements</span></span>  
 <span data-ttu-id="1a0dc-115">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a0dc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a0dc-116">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a0dc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a0dc-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a0dc-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1a0dc-118">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1a0dc-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a0dc-119">См. также</span><span class="sxs-lookup"><span data-stu-id="1a0dc-119">See also</span></span>

- [<span data-ttu-id="1a0dc-120">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="1a0dc-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="1a0dc-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1a0dc-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
