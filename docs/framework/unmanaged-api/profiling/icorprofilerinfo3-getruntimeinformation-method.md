---
title: Метод ICorProfilerInfo3::GetRuntimeInformation
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a13e3e525c7f019e7dc49111b88ac374345830af
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164935"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="648d4-102">Метод ICorProfilerInfo3::GetRuntimeInformation</span><span class="sxs-lookup"><span data-stu-id="648d4-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="648d4-103">Предоставляет сведения о среда CLR (CLR) профилируемым версии.</span><span class="sxs-lookup"><span data-stu-id="648d4-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="648d4-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="648d4-104">Syntax</span></span>  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="648d4-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="648d4-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="648d4-106">[out] Идентификатор представителем работающего экземпляра среды CLR в процессе.</span><span class="sxs-lookup"><span data-stu-id="648d4-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="648d4-107">Так же, как это `ClrInstanceID` сообщает, трассировка событий для события при запуске Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="648d4-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="648d4-108">[out] Тип среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="648d4-108">[out] The runtime type.</span></span> <span data-ttu-id="648d4-109">Этот параметр возвращает `COR_PRF_DESKTOP_CLR` для настольной версии среды CLR, или `COR_PRF_CORE_CLR` для основную версию среды CLR, используемую в Silverlight.</span><span class="sxs-lookup"><span data-stu-id="648d4-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="648d4-110">[out] Основной номер версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="648d4-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="648d4-111">[out] Дополнительный номер версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="648d4-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="648d4-112">[out] Номер версии сборки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="648d4-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="648d4-113">[out] Номер версии среды CLR, связанный с обновлением программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="648d4-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="648d4-114">[in] Длина в символах, буфера, `szVersionString` указывает.</span><span class="sxs-lookup"><span data-stu-id="648d4-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="648d4-115">[out] Длина в символах, из `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="648d4-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="648d4-116">[out] Строка версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="648d4-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="648d4-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="648d4-117">Remarks</span></span>  
 <span data-ttu-id="648d4-118">Можно передать значение null для любого параметра.</span><span class="sxs-lookup"><span data-stu-id="648d4-118">You may pass null for any parameter.</span></span> <span data-ttu-id="648d4-119">Тем не менее `pcchVersionString` не может иметь значение null Если `szVersionString` также имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="648d4-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="648d4-120">Требования</span><span class="sxs-lookup"><span data-stu-id="648d4-120">Requirements</span></span>  
 <span data-ttu-id="648d4-121">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="648d4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="648d4-122">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="648d4-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="648d4-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="648d4-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="648d4-124">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="648d4-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="648d4-125">См. также</span><span class="sxs-lookup"><span data-stu-id="648d4-125">See also</span></span>

- [<span data-ttu-id="648d4-126">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="648d4-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="648d4-127">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="648d4-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="648d4-128">Профилирование</span><span class="sxs-lookup"><span data-stu-id="648d4-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
