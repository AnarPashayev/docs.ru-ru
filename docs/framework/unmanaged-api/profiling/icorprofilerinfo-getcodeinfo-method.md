---
title: Метод ICorProfilerInfo::GetCodeInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d069446ecb0b630870f0d2c9c4bdc23232c40c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120696"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="c5dfc-102">Метод ICorProfilerInfo::GetCodeInfo</span><span class="sxs-lookup"><span data-stu-id="c5dfc-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="c5dfc-103">Получает экстент машинного кода, связанного с указанным идентификатором функции.</span><span class="sxs-lookup"><span data-stu-id="c5dfc-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="c5dfc-104">Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="c5dfc-104">This method is obsolete.</span></span> <span data-ttu-id="c5dfc-105">Используйте [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="c5dfc-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5dfc-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c5dfc-106">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5dfc-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="c5dfc-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c5dfc-108">[in] Идентификатор функции, с которым связан машинный код.</span><span class="sxs-lookup"><span data-stu-id="c5dfc-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="c5dfc-109">[out] Указатель на массив байтов, составляющих машинный код функции.</span><span class="sxs-lookup"><span data-stu-id="c5dfc-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="c5dfc-110">[out] Указатель на целое число, задающее размер машинного кода в байтах.</span><span class="sxs-lookup"><span data-stu-id="c5dfc-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5dfc-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="c5dfc-111">Remarks</span></span>  
 <span data-ttu-id="c5dfc-112">Для оптимизации производительности среда выполнения в .NET Framework версии 2.0 разделяет предварительно скомпилированный машинный код функции на несколько областей.</span><span class="sxs-lookup"><span data-stu-id="c5dfc-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="c5dfc-113">Следовательно, метод `GetCodeInfo` является устаревшим в .NET Framework 2.0, так как он не может обработать экстент машинного кода функции.</span><span class="sxs-lookup"><span data-stu-id="c5dfc-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="c5dfc-114">Профилировщики следует переключить на использование более универсального метода `ICorProfilerInfo2::GetCodeInfo2`.</span><span class="sxs-lookup"><span data-stu-id="c5dfc-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="c5dfc-115">Эта функция использует буферы, выделенные вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="c5dfc-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5dfc-116">Требования</span><span class="sxs-lookup"><span data-stu-id="c5dfc-116">Requirements</span></span>  
 <span data-ttu-id="c5dfc-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5dfc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5dfc-118">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5dfc-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5dfc-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5dfc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5dfc-120">**Версии платформы .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="c5dfc-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5dfc-121">См. также</span><span class="sxs-lookup"><span data-stu-id="c5dfc-121">See also</span></span>

- [<span data-ttu-id="c5dfc-122">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="c5dfc-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="c5dfc-123">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c5dfc-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="c5dfc-124">Профилирование</span><span class="sxs-lookup"><span data-stu-id="c5dfc-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
