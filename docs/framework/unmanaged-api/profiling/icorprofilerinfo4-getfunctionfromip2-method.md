---
title: Метод ICorProfilerInfo4::GetFunctionFromIP2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: ea66474e809b3813faceef79a69dd8a639a72a3b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502799"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="18725-102">Метод ICorProfilerInfo4::GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="18725-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="18725-103">Сопоставляет указатель инструкции управляемого кода с JIT-повторно скомпилированной версией функции.</span><span class="sxs-lookup"><span data-stu-id="18725-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18725-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="18725-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18725-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="18725-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="18725-106">окне Указатель инструкции в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="18725-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="18725-107">заполняет Идентификатор функции.</span><span class="sxs-lookup"><span data-stu-id="18725-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="18725-108">заполняет Удостоверение JIT-повторно скомпилированной версии функции.</span><span class="sxs-lookup"><span data-stu-id="18725-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18725-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="18725-109">Remarks</span></span>  
 <span data-ttu-id="18725-110">`GetFunctionFromIP2`функция похожа на `GetFunctionFromIP` , за исключением того, что он получает JIT-перекомпилированный идентификатор вместо идентификатора функции функции, которая содержит указанный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="18725-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18725-111">`GetFunctionFromIP2`может запустить сборку мусора, тогда как это `GetFunctionFromIP` не будет.</span><span class="sxs-lookup"><span data-stu-id="18725-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="18725-112">Дополнительные сведения см. в разделе [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="18725-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18725-113">Требования</span><span class="sxs-lookup"><span data-stu-id="18725-113">Requirements</span></span>  
 <span data-ttu-id="18725-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18725-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18725-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="18725-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="18725-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18725-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18725-117">**.NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18725-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18725-118">См. также</span><span class="sxs-lookup"><span data-stu-id="18725-118">See also</span></span>

- [<span data-ttu-id="18725-119">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="18725-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
