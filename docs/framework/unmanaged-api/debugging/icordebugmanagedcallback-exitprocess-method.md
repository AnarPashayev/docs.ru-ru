---
title: Метод ICorDebugManagedCallback::ExitProcess
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04b8ac6751024e64cc866fce1cfe72fb42e41200
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760440"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="2ab00-102">Метод ICorDebugManagedCallback::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="2ab00-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="2ab00-103">Уведомляет отладчик о том, что процесс завершен.</span><span class="sxs-lookup"><span data-stu-id="2ab00-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ab00-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2ab00-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ab00-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="2ab00-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="2ab00-106">[in] Указатель на объект ICorDebugProcess, представляющий процесс.</span><span class="sxs-lookup"><span data-stu-id="2ab00-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ab00-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="2ab00-107">Remarks</span></span>  
 <span data-ttu-id="2ab00-108">Не удается продолжить выполнение после `ExitProcess` событий.</span><span class="sxs-lookup"><span data-stu-id="2ab00-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="2ab00-109">Это событие вызывается асинхронно с другими событиями во время появится нужный процесс нужно остановить.</span><span class="sxs-lookup"><span data-stu-id="2ab00-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="2ab00-110">Это может произойти, если процесс прерывается во время остановки, обычно вследствие внешних.</span><span class="sxs-lookup"><span data-stu-id="2ab00-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="2ab00-111">Если среда CLR (CLR), который уже обслуживается управляемом обратном вызове, это событие будет отложено до после возвращения ответного вызова.</span><span class="sxs-lookup"><span data-stu-id="2ab00-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="2ab00-112">`ExitProcess` Это единственное событие завершения и выгрузки, гарантированно вызывается при завершении работы.</span><span class="sxs-lookup"><span data-stu-id="2ab00-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ab00-113">Требования</span><span class="sxs-lookup"><span data-stu-id="2ab00-113">Requirements</span></span>  
 <span data-ttu-id="2ab00-114">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ab00-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ab00-115">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ab00-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ab00-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ab00-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ab00-117">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ab00-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ab00-118">См. также</span><span class="sxs-lookup"><span data-stu-id="2ab00-118">See also</span></span>

- [<span data-ttu-id="2ab00-119">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="2ab00-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
