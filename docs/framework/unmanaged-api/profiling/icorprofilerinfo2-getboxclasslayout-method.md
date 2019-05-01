---
title: Метод ICorProfilerInfo2::GetBoxClassLayout
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4dac7e38d1e767a3edeef932a0c0916daffe24b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049574"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="5a3b9-102">Метод ICorProfilerInfo2::GetBoxClassLayout</span><span class="sxs-lookup"><span data-stu-id="5a3b9-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="5a3b9-103">Получает сведения о расположении заданного типа значения при его упаковке.</span><span class="sxs-lookup"><span data-stu-id="5a3b9-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3b9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5a3b9-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a3b9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="5a3b9-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="5a3b9-106">[in] Идентификатор класса, который описывает тип значения, который упаковывается.</span><span class="sxs-lookup"><span data-stu-id="5a3b9-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="5a3b9-107">[out] Целое число, является смещение относительно указателя на идентификатор упакованный объект типа значения.</span><span class="sxs-lookup"><span data-stu-id="5a3b9-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a3b9-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="5a3b9-108">Remarks</span></span>  
 <span data-ttu-id="5a3b9-109">`pBufferOffset` Значение — это расположение в поле типа значения.</span><span class="sxs-lookup"><span data-stu-id="5a3b9-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="5a3b9-110">После `pBufferOffset` применяется макета класса типа значения в объект в рамке, могут использоваться для интерпретации значения объекта.</span><span class="sxs-lookup"><span data-stu-id="5a3b9-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a3b9-111">Требования</span><span class="sxs-lookup"><span data-stu-id="5a3b9-111">Requirements</span></span>  
 <span data-ttu-id="5a3b9-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a3b9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a3b9-113">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a3b9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a3b9-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a3b9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a3b9-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a3b9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a3b9-116">См. также</span><span class="sxs-lookup"><span data-stu-id="5a3b9-116">See also</span></span>

- [<span data-ttu-id="5a3b9-117">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5a3b9-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="5a3b9-118">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="5a3b9-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
