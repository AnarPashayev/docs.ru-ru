---
title: Метод ICorProfilerCallback::AppDomainShutdownFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: 722a1e0adea41a13ca25829c53372c29187b80bd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500472"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="bf516-102">Метод ICorProfilerCallback::AppDomainShutdownFinished</span><span class="sxs-lookup"><span data-stu-id="bf516-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="bf516-103">Уведомляет профилировщик о том, что домен приложения был выгружен из процесса.</span><span class="sxs-lookup"><span data-stu-id="bf516-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf516-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bf516-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf516-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="bf516-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="bf516-106">\[в] определяет домен, в котором хранятся сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="bf516-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="bf516-107">\[in] значение HRESULT, указывающее, успешно ли выгружен домен приложения.</span><span class="sxs-lookup"><span data-stu-id="bf516-107">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf516-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="bf516-108">Remarks</span></span>  
 <span data-ttu-id="bf516-109">Значение недопустимо `appDomainId` для информационного запроса после возврата метода [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bf516-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="bf516-110">Некоторые части выгрузки домена приложения могут продолжаться после `AppDomainCreationFinished` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="bf516-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="bf516-111">Ошибка HRESULT в `hrStatus` указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="bf516-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="bf516-112">Однако значение HRESULT в случае успеха в `hrStatus` указывает, что первая часть выгрузки домена приложения успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="bf516-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf516-113">Требования</span><span class="sxs-lookup"><span data-stu-id="bf516-113">Requirements</span></span>  
 <span data-ttu-id="bf516-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf516-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf516-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf516-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf516-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf516-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf516-117">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf516-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf516-118">См. также</span><span class="sxs-lookup"><span data-stu-id="bf516-118">See also</span></span>

- [<span data-ttu-id="bf516-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="bf516-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
