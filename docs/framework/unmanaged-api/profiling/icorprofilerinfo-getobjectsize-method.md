---
title: Метод ICorProfilerInfo::GetObjectSize
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d366a0093ca82d2e5b3c40729777a1b6c0766bda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092205"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="b9d89-102">Метод ICorProfilerInfo::GetObjectSize</span><span class="sxs-lookup"><span data-stu-id="b9d89-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="b9d89-103">Возвращает размер указанного объекта.</span><span class="sxs-lookup"><span data-stu-id="b9d89-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d89-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b9d89-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9d89-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b9d89-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="b9d89-106">[in] Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="b9d89-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="b9d89-107">[out] Указатель на размер объекта в байтах.</span><span class="sxs-lookup"><span data-stu-id="b9d89-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9d89-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="b9d89-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9d89-109">Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="b9d89-109">This method is obsolete.</span></span> <span data-ttu-id="b9d89-110">Он возвращает COR_E_OVERFLOW для объектов, размер которых превышает 4 ГБ на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="b9d89-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="b9d89-111">Используйте [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="b9d89-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="b9d89-112">Разные объекты одного типа часто имеют одинаковый размер.</span><span class="sxs-lookup"><span data-stu-id="b9d89-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="b9d89-113">Тем не менее некоторые типы, например массивы или строки, возможно другого размера для каждого объекта.</span><span class="sxs-lookup"><span data-stu-id="b9d89-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="b9d89-114">Размер, возвращенный `GetObjectSize` метод не имеет любых заполнений выравнивания, которые могут появиться после объект находится в куче сбора мусора.</span><span class="sxs-lookup"><span data-stu-id="b9d89-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="b9d89-115">Если вы используете `GetObjectSize` метод для перехода от объекта к объекту в куче сбора мусора, добавить выравнивание, заполнение вручную, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="b9d89-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="b9d89-116">На 32-разрядной Windows COR_PRF_GC_GEN_0 COR_PRF_GC_GEN_1 и COR_PRF_GC_GEN_2 4-байтового выравнивания, а COR_PRF_GC_LARGE_OBJECT_HEAP использует 8-байтового выравнивания.</span><span class="sxs-lookup"><span data-stu-id="b9d89-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="b9d89-117">На 64-разрядной Windows выравнивание всегда равен 8 байтам.</span><span class="sxs-lookup"><span data-stu-id="b9d89-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9d89-118">Требования</span><span class="sxs-lookup"><span data-stu-id="b9d89-118">Requirements</span></span>  
 <span data-ttu-id="b9d89-119">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9d89-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9d89-120">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9d89-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9d89-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9d89-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b9d89-122">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b9d89-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b9d89-123">См. также</span><span class="sxs-lookup"><span data-stu-id="b9d89-123">See also</span></span>

- [<span data-ttu-id="b9d89-124">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b9d89-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
