---
title: Метод ICorDebugManagedCallback::UnloadModule
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12e42da015864e83663d2f4d74bab2a34052d760
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995089"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="11719-102">Метод ICorDebugManagedCallback::UnloadModule</span><span class="sxs-lookup"><span data-stu-id="11719-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="11719-103">Уведомляет отладчик о выгрузке общий модуль среды выполнения языка (DLL).</span><span class="sxs-lookup"><span data-stu-id="11719-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11719-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="11719-104">Syntax</span></span>  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11719-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="11719-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="11719-106">[in] Указатель на объект ICorDebugAppDomain, который представляет домен приложения, который содержал модуля.</span><span class="sxs-lookup"><span data-stu-id="11719-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="11719-107">[in] Указатель на объект, представляющий модуль ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="11719-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11719-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="11719-108">Remarks</span></span>  
 <span data-ttu-id="11719-109">Модуль не должен использоваться после этого вызова.</span><span class="sxs-lookup"><span data-stu-id="11719-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11719-110">Требования</span><span class="sxs-lookup"><span data-stu-id="11719-110">Requirements</span></span>  
 <span data-ttu-id="11719-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11719-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11719-112">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11719-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11719-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11719-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11719-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11719-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11719-115">См. также</span><span class="sxs-lookup"><span data-stu-id="11719-115">See also</span></span>

- [<span data-ttu-id="11719-116">Метод LoadModule</span><span class="sxs-lookup"><span data-stu-id="11719-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="11719-117">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="11719-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
