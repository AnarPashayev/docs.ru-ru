---
title: Метод ICorProfilerCallback::ExceptionOSHandlerLeave
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 468c5b28bb5a574aacf623196f0c516992473707
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756229"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="77e61-102">Метод ICorProfilerCallback::ExceptionOSHandlerLeave</span><span class="sxs-lookup"><span data-stu-id="77e61-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="77e61-103">Не реализовано.</span><span class="sxs-lookup"><span data-stu-id="77e61-103">Not implemented.</span></span> <span data-ttu-id="77e61-104">Профилировщик, необходимы сведения о неуправляемых исключений необходимо получить эту информацию другим способом.</span><span class="sxs-lookup"><span data-stu-id="77e61-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e61-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77e61-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="77e61-106">Требования</span><span class="sxs-lookup"><span data-stu-id="77e61-106">Requirements</span></span>  
 <span data-ttu-id="77e61-107">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77e61-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77e61-108">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="77e61-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77e61-109">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77e61-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77e61-110">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77e61-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e61-111">См. также</span><span class="sxs-lookup"><span data-stu-id="77e61-111">See also</span></span>

- [<span data-ttu-id="77e61-112">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="77e61-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
