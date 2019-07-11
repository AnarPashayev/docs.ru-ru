---
title: Метод ICorDebugManagedCallback::CreateProcess
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0eacb4b0a06fbe086935b59eba7d33135b6bef19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759712"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="d3f34-102">Метод ICorDebugManagedCallback::CreateProcess</span><span class="sxs-lookup"><span data-stu-id="d3f34-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="d3f34-103">Уведомляет отладчик присоединен процесс или запускается в первый раз.</span><span class="sxs-lookup"><span data-stu-id="d3f34-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3f34-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d3f34-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3f34-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="d3f34-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d3f34-106">[in] Указатель на объект ICorDebugProcess, представляющий процесс, которые присоединены и к работе.</span><span class="sxs-lookup"><span data-stu-id="d3f34-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3f34-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="d3f34-107">Remarks</span></span>  
 <span data-ttu-id="d3f34-108">Этот метод не вызывается до инициализации среда CLR.</span><span class="sxs-lookup"><span data-stu-id="d3f34-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="d3f34-109">Большая часть [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) методы возвращают CORDBG_E_NOTREADY перед `CreateProcess` обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="d3f34-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3f34-110">Требования</span><span class="sxs-lookup"><span data-stu-id="d3f34-110">Requirements</span></span>  
 <span data-ttu-id="d3f34-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3f34-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3f34-112">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3f34-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3f34-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3f34-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3f34-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3f34-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f34-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d3f34-115">See also</span></span>

- [<span data-ttu-id="d3f34-116">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="d3f34-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
