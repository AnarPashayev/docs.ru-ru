---
title: Метод ICorDebugManagedCallback::EditAndContinueRemap
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
ms.openlocfilehash: 1d8aa2cca9dbbeaa9e03813b177ca59125770803
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721287"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="21e4b-102">Метод ICorDebugManagedCallback::EditAndContinueRemap</span><span class="sxs-lookup"><span data-stu-id="21e4b-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>

<span data-ttu-id="21e4b-103">Этот метод использовать не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="21e4b-103">This method has been deprecated.</span></span> <span data-ttu-id="21e4b-104">Он уведомляет отладчик о том, что событие повторного сопоставления было отправлено в интегрированную среду разработки (IDE).</span><span class="sxs-lookup"><span data-stu-id="21e4b-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e4b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="21e4b-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="21e4b-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="21e4b-106">Remarks</span></span>  

 <span data-ttu-id="21e4b-107">`EditAndContinueRemap`Метод вызывается при попыток выполнения кода в старой версии обновленной функции.</span><span class="sxs-lookup"><span data-stu-id="21e4b-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="21e4b-108">Среда CLR вызывает `EditAndContinueRemap` метод для отправки события повторного сопоставления в интегрированную среду разработки.</span><span class="sxs-lookup"><span data-stu-id="21e4b-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e4b-109">Требования</span><span class="sxs-lookup"><span data-stu-id="21e4b-109">Requirements</span></span>  

 <span data-ttu-id="21e4b-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e4b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e4b-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21e4b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21e4b-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21e4b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21e4b-113">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e4b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e4b-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="21e4b-114">See also</span></span>

- [<span data-ttu-id="21e4b-115">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="21e4b-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
