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
ms.openlocfilehash: cd337ca6d7b03ad22f178c9c7084cfa2585da73c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782752"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="53b52-102">Метод ICorProfilerInfo::GetObjectSize</span><span class="sxs-lookup"><span data-stu-id="53b52-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="53b52-103">Возвращает размер указанного объекта.</span><span class="sxs-lookup"><span data-stu-id="53b52-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53b52-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="53b52-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53b52-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="53b52-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="53b52-106">[in] Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="53b52-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="53b52-107">[out] Указатель на размер объекта в байтах.</span><span class="sxs-lookup"><span data-stu-id="53b52-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53b52-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="53b52-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="53b52-109">Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="53b52-109">This method is obsolete.</span></span> <span data-ttu-id="53b52-110">Он возвращает COR_E_OVERFLOW для объектов, размер которых превышает 4 ГБ на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="53b52-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="53b52-111">Используйте [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="53b52-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="53b52-112">Разные объекты одного типа часто имеют одинаковый размер.</span><span class="sxs-lookup"><span data-stu-id="53b52-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="53b52-113">Тем не менее некоторые типы, например массивы или строки, возможно другого размера для каждого объекта.</span><span class="sxs-lookup"><span data-stu-id="53b52-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="53b52-114">Размер, возвращенный `GetObjectSize` метод не имеет любых заполнений выравнивания, которые могут появиться после объект находится в куче сбора мусора.</span><span class="sxs-lookup"><span data-stu-id="53b52-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="53b52-115">Если вы используете `GetObjectSize` метод для перехода от объекта к объекту в куче сбора мусора, добавить выравнивание, заполнение вручную, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="53b52-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="53b52-116">На 32-разрядной Windows COR_PRF_GC_GEN_0 COR_PRF_GC_GEN_1 и COR_PRF_GC_GEN_2 4-байтового выравнивания, а COR_PRF_GC_LARGE_OBJECT_HEAP использует 8-байтового выравнивания.</span><span class="sxs-lookup"><span data-stu-id="53b52-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="53b52-117">На 64-разрядной Windows выравнивание всегда равен 8 байтам.</span><span class="sxs-lookup"><span data-stu-id="53b52-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53b52-118">Требования</span><span class="sxs-lookup"><span data-stu-id="53b52-118">Requirements</span></span>  
 <span data-ttu-id="53b52-119">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53b52-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53b52-120">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53b52-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53b52-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53b52-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53b52-122">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53b52-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b52-123">См. также</span><span class="sxs-lookup"><span data-stu-id="53b52-123">See also</span></span>

- [<span data-ttu-id="53b52-124">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="53b52-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
