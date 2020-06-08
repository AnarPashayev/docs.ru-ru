---
title: Метод ICorProfilerCallback::RemotingServerInvocationReturned
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationReturned
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned method [.NET Framework profiling]
- RemotingServerInvocationReturned method [.NET Framework profiling]
ms.assetid: a4de6805-e159-4280-99e5-3390c86166d0
topic_type:
- apiref
ms.openlocfilehash: 354736061a2c50b7db16070c3d4ff9c2548d394d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499952"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="357a6-102">Метод ICorProfilerCallback::RemotingServerInvocationReturned</span><span class="sxs-lookup"><span data-stu-id="357a6-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="357a6-103">Уведомляет профилировщик о том, что процесс завершил вызов метода в ответ на запрос удаленного вызова метода.</span><span class="sxs-lookup"><span data-stu-id="357a6-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="357a6-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="357a6-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="357a6-105">Требования</span><span class="sxs-lookup"><span data-stu-id="357a6-105">Requirements</span></span>  
 <span data-ttu-id="357a6-106">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="357a6-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="357a6-107">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="357a6-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="357a6-108">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="357a6-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="357a6-109">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="357a6-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="357a6-110">См. также</span><span class="sxs-lookup"><span data-stu-id="357a6-110">See also</span></span>

- [<span data-ttu-id="357a6-111">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="357a6-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
