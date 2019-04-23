---
title: Метод ICorDebug::SetUnmanagedHandler
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c234b3953130f53d7e6b583cd92670149a70689b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168874"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="34bc0-102">Метод ICorDebug::SetUnmanagedHandler</span><span class="sxs-lookup"><span data-stu-id="34bc0-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="34bc0-103">Указывает объект обработчика событий для неуправляемых событий.</span><span class="sxs-lookup"><span data-stu-id="34bc0-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34bc0-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="34bc0-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34bc0-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="34bc0-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="34bc0-106">[in] Указатель на [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) объект, представляющий обработчик событий для неуправляемых событий.</span><span class="sxs-lookup"><span data-stu-id="34bc0-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34bc0-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="34bc0-107">Remarks</span></span>  
 <span data-ttu-id="34bc0-108">Обработчик событий объекта для неуправляемых событий необходимо задать после вызова [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) и перед любыми вызовами [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) или [ICorDebug::DebugActiveProcess ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="34bc0-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="34bc0-109">Тем не менее для обратной совместимости, вы не должны задать объект обработчика событий для неуправляемых событий до первого события отладки машинного кода.</span><span class="sxs-lookup"><span data-stu-id="34bc0-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="34bc0-110">В частности Если `ICorDebug::CreateProcess` установлен флаг CREATE_SUSPENDED, события, которые не удалось доставить, пока основной поток не будет возобновлена отладки машинного кода.</span><span class="sxs-lookup"><span data-stu-id="34bc0-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34bc0-111">Требования</span><span class="sxs-lookup"><span data-stu-id="34bc0-111">Requirements</span></span>  
 <span data-ttu-id="34bc0-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34bc0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34bc0-113">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34bc0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34bc0-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34bc0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34bc0-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34bc0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34bc0-116">См. также</span><span class="sxs-lookup"><span data-stu-id="34bc0-116">See also</span></span>

- [<span data-ttu-id="34bc0-117">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="34bc0-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
