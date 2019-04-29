---
title: Метод ICorProfilerCallback::AppDomainShutdownStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f422e99a5f6a4153368304ff0b33bbc55381575a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597860"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="9307e-102">Метод ICorProfilerCallback::AppDomainShutdownStarted</span><span class="sxs-lookup"><span data-stu-id="9307e-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="9307e-103">Уведомляет профилировщик о том, что домен приложения выгружается из процесса.</span><span class="sxs-lookup"><span data-stu-id="9307e-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9307e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9307e-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9307e-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="9307e-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="9307e-106">[in] Определяет домен, в котором хранятся сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="9307e-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9307e-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="9307e-107">Remarks</span></span>  
 <span data-ttu-id="9307e-108">Значение `appDomainId` не является допустимым для любого запроса информации после `AppDomainShutdownStarted` возвращает метод — это последняя возможность профилировщика для получения сведений о домене приложения.</span><span class="sxs-lookup"><span data-stu-id="9307e-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9307e-109">Требования</span><span class="sxs-lookup"><span data-stu-id="9307e-109">Requirements</span></span>  
 <span data-ttu-id="9307e-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9307e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9307e-111">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9307e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9307e-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9307e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9307e-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9307e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9307e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="9307e-114">See also</span></span>

- [<span data-ttu-id="9307e-115">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9307e-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
