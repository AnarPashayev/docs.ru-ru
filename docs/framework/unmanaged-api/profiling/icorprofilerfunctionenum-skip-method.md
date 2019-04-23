---
title: Метод ICorProfilerFunctionEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e334c75afee60591db2b4e1f45cf0ec753ee2e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141656"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="be8e7-102">Метод ICorProfilerFunctionEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="be8e7-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="be8e7-103">Перемещает курсор перечислителя из текущей позиции, пропуская указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="be8e7-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be8e7-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="be8e7-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be8e7-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="be8e7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="be8e7-106">[in] Число элементов, которые нужно пропустить.</span><span class="sxs-lookup"><span data-stu-id="be8e7-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be8e7-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="be8e7-107">Return Value</span></span>  
 <span data-ttu-id="be8e7-108">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="be8e7-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="be8e7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be8e7-109">HRESULT</span></span>|<span data-ttu-id="be8e7-110">Описание</span><span class="sxs-lookup"><span data-stu-id="be8e7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be8e7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="be8e7-111">S_OK</span></span>|<span data-ttu-id="be8e7-112">`celt` элементы были пропущены.</span><span class="sxs-lookup"><span data-stu-id="be8e7-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="be8e7-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="be8e7-113">S_FALSE</span></span>|<span data-ttu-id="be8e7-114">Менее `celt` элементы были пропущены, который указывает, что никакие элементы.</span><span class="sxs-lookup"><span data-stu-id="be8e7-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be8e7-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="be8e7-115">Remarks</span></span>  
 <span data-ttu-id="be8e7-116">Новое положение курсора этот перечислитель является (текущей позиции) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="be8e7-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be8e7-117">Требования</span><span class="sxs-lookup"><span data-stu-id="be8e7-117">Requirements</span></span>  
 <span data-ttu-id="be8e7-118">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be8e7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be8e7-119">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be8e7-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be8e7-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be8e7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be8e7-121">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be8e7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be8e7-122">См. также</span><span class="sxs-lookup"><span data-stu-id="be8e7-122">See also</span></span>

- [<span data-ttu-id="be8e7-123">Интерфейс ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="be8e7-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="be8e7-124">Интерфейсы профилирования</span><span class="sxs-lookup"><span data-stu-id="be8e7-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
