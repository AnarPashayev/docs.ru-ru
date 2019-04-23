---
title: Метод ICorProfilerInfo::IsArrayClass
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 350221ae205636cef82581f3fe11367006dd8b2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072176"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="a6e8a-102">Метод ICorProfilerInfo::IsArrayClass</span><span class="sxs-lookup"><span data-stu-id="a6e8a-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="a6e8a-103">Определяет, является ли указанный класс класса массива.</span><span class="sxs-lookup"><span data-stu-id="a6e8a-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6e8a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a6e8a-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6e8a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6e8a-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="a6e8a-106">[in] Идентификатор класса, который необходимо проверить.</span><span class="sxs-lookup"><span data-stu-id="a6e8a-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="a6e8a-107">[out] Указатель на значение CorElementType перечисления, указывающее тип элементов массива.</span><span class="sxs-lookup"><span data-stu-id="a6e8a-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="a6e8a-108">[out] Указатель на идентификатор класса для элементов массива, если они доступны.</span><span class="sxs-lookup"><span data-stu-id="a6e8a-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="a6e8a-109">[out] Указатель на целое число, указывающее ранг (то есть число измерений) массива.</span><span class="sxs-lookup"><span data-stu-id="a6e8a-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6e8a-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="a6e8a-110">Remarks</span></span>  
 <span data-ttu-id="a6e8a-111">Если класс является классом массива, `IsArrayClass` метод возвращает значение S_OK HRESULT и значения для всех ненулевых выходных параметров.</span><span class="sxs-lookup"><span data-stu-id="a6e8a-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="a6e8a-112">В противном случае возвращается значение S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="a6e8a-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6e8a-113">Требования</span><span class="sxs-lookup"><span data-stu-id="a6e8a-113">Requirements</span></span>  
 <span data-ttu-id="a6e8a-114">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6e8a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6e8a-115">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6e8a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6e8a-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6e8a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6e8a-117">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6e8a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e8a-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a6e8a-118">See also</span></span>

- [<span data-ttu-id="a6e8a-119">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a6e8a-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
