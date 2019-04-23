---
title: Метод ICorProfilerModuleEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d246acbf314a83ca3f8113e9a2fb223ac0ebcafe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223710"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="de7e7-102">Метод ICorProfilerModuleEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="de7e7-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="de7e7-103">Возвращает число управляемых модулей, загруженных в приложение.</span><span class="sxs-lookup"><span data-stu-id="de7e7-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de7e7-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="de7e7-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de7e7-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="de7e7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="de7e7-106">[out] Число модулей среды выполнения в коллекции.</span><span class="sxs-lookup"><span data-stu-id="de7e7-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de7e7-107">Требования</span><span class="sxs-lookup"><span data-stu-id="de7e7-107">Requirements</span></span>  
 <span data-ttu-id="de7e7-108">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de7e7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de7e7-109">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="de7e7-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de7e7-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de7e7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de7e7-111">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de7e7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7e7-112">См. также</span><span class="sxs-lookup"><span data-stu-id="de7e7-112">See also</span></span>

- [<span data-ttu-id="de7e7-113">Интерфейс ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="de7e7-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="de7e7-114">Интерфейсы профилирования</span><span class="sxs-lookup"><span data-stu-id="de7e7-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
