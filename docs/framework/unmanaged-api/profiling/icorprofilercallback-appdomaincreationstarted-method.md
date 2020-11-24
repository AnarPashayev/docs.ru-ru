---
title: Метод ICorProfilerCallback::AppDomainCreationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: 901546c80c3bee32afddfa8e8cffbd2b679bc43b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685400"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="3b3e1-102">Метод ICorProfilerCallback::AppDomainCreationStarted</span><span class="sxs-lookup"><span data-stu-id="3b3e1-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>

<span data-ttu-id="3b3e1-103">Уведомляет профилировщик о создании домена приложения.</span><span class="sxs-lookup"><span data-stu-id="3b3e1-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b3e1-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3b3e1-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b3e1-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="3b3e1-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="3b3e1-106">\[в] определяет создаваемый домен.</span><span class="sxs-lookup"><span data-stu-id="3b3e1-106">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="3b3e1-107">Комментарии</span><span class="sxs-lookup"><span data-stu-id="3b3e1-107">Remarks</span></span>  

 <span data-ttu-id="3b3e1-108">Идентификатор не является допустимым для запроса информации до вызова метода [ICorProfilerCallback:: аппдомаинкреатионфинишед](icorprofilercallback-appdomaincreationfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3b3e1-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b3e1-109">Требования</span><span class="sxs-lookup"><span data-stu-id="3b3e1-109">Requirements</span></span>  

 <span data-ttu-id="3b3e1-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b3e1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b3e1-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3b3e1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b3e1-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b3e1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b3e1-113">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b3e1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b3e1-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3b3e1-114">See also</span></span>

- [<span data-ttu-id="3b3e1-115">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="3b3e1-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
