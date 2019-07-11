---
title: Метод ICorProfilerInfo::GetModuleMetaData
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e63cf698e41e70084c9b71bdf58d7ac60723d53
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782788"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="cd7d9-102">Метод ICorProfilerInfo::GetModuleMetaData</span><span class="sxs-lookup"><span data-stu-id="cd7d9-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="cd7d9-103">Получает экземпляр интерфейса метаданных, который сопоставляется указанного модуля.</span><span class="sxs-lookup"><span data-stu-id="cd7d9-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd7d9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cd7d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd7d9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="cd7d9-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="cd7d9-106">[in] Идентификатор модуля, с которым будет сопоставлен экземпляр интерфейса.</span><span class="sxs-lookup"><span data-stu-id="cd7d9-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="cd7d9-107">[in] Значение [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) перечисления, указывающее режим для открытия файлов манифеста.</span><span class="sxs-lookup"><span data-stu-id="cd7d9-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="cd7d9-108">Только `ofRead`, `ofWrite` и `ofNoTransform` bits являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="cd7d9-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="cd7d9-109">[in] Ссылка на идентификатор (GUID) интерфейс метаданных, экземпляр которого будут извлекаться.</span><span class="sxs-lookup"><span data-stu-id="cd7d9-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="cd7d9-110">См. в разделе [интерфейсы метаданных](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) список интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="cd7d9-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="cd7d9-111">[out] Указатель на адрес метаданных экземпляра интерфейса.</span><span class="sxs-lookup"><span data-stu-id="cd7d9-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd7d9-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="cd7d9-112">Remarks</span></span>  
 <span data-ttu-id="cd7d9-113">Существует возможность запросить метаданные для открытия в режиме чтения/записи, но это приведет к замедлению выполнения программы, поскольку изменения метаданных не могут быть оптимизированы, как от компилятора.</span><span class="sxs-lookup"><span data-stu-id="cd7d9-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="cd7d9-114">Некоторые модули (например, модули ресурсов) имеют без метаданных.</span><span class="sxs-lookup"><span data-stu-id="cd7d9-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="cd7d9-115">В таком случае `GetModuleMetaData` возвратит значение HRESULT S_FALSE, и значение null в \*`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="cd7d9-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd7d9-116">Требования</span><span class="sxs-lookup"><span data-stu-id="cd7d9-116">Requirements</span></span>  
 <span data-ttu-id="cd7d9-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd7d9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd7d9-118">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd7d9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd7d9-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd7d9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd7d9-120">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd7d9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7d9-121">См. также</span><span class="sxs-lookup"><span data-stu-id="cd7d9-121">See also</span></span>

- [<span data-ttu-id="cd7d9-122">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="cd7d9-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
