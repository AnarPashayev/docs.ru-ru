---
title: Метод ICorProfilerAssemblyReferenceProvider::AddAssemblyReference
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09ce4f3a293e7870ddadf4ad6ee2c15de10f4594
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200575"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="d2f17-102">Метод ICorProfilerAssemblyReferenceProvider::AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="d2f17-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="d2f17-103">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="d2f17-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d2f17-104">Информирует общеязыковой среды выполнения (CLR) ссылки на сборку, которую профилировщик планирует добавить в [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="d2f17-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2f17-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d2f17-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2f17-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d2f17-106">Parameters</span></span>  
 <span data-ttu-id="d2f17-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="d2f17-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="d2f17-108">Указатель на [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) структуру, которая предоставляет среде CLR сведения о ссылку на сборку, которую ей следует учитывать при выполнении обхода замыкания.</span><span class="sxs-lookup"><span data-stu-id="d2f17-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2f17-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="d2f17-109">Remarks</span></span>  
 <span data-ttu-id="d2f17-110">Профилировщик вызывает этот метод для каждой целевой сборки, он планирует ссылаться из сборки, указанной в `wszAssemblyPath` аргумент [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="d2f17-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="d2f17-111">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) интерфейс объект передается в профилировщик [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) обратного вызова, а также путь к сборке и имени в `wszAssemblyPath` аргумент.</span><span class="sxs-lookup"><span data-stu-id="d2f17-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2f17-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d2f17-112">Requirements</span></span>  
 <span data-ttu-id="d2f17-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2f17-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2f17-114">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d2f17-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2f17-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2f17-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d2f17-116">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d2f17-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d2f17-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d2f17-117">See also</span></span>

- [<span data-ttu-id="d2f17-118">Интерфейс ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="d2f17-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="d2f17-119">Метод GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="d2f17-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="d2f17-120">Метод ModuleLoadFinished</span><span class="sxs-lookup"><span data-stu-id="d2f17-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
