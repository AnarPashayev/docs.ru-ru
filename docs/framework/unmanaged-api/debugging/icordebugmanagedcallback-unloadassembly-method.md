---
title: Метод ICorDebugManagedCallback::UnloadAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e770602858761dbcf15c233dceebfd35be106aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214135"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="bde7f-102">Метод ICorDebugManagedCallback::UnloadAssembly</span><span class="sxs-lookup"><span data-stu-id="bde7f-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="bde7f-103">Уведомляет отладчик о выгрузке сборки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="bde7f-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bde7f-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bde7f-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bde7f-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="bde7f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bde7f-106">[in] Указатель на объект ICorDebugAppDomain, представляющий домен приложения, который содержит сборку.</span><span class="sxs-lookup"><span data-stu-id="bde7f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="bde7f-107">[in] Указатель на объект ICorDebugAssembly, представляющий сборку.</span><span class="sxs-lookup"><span data-stu-id="bde7f-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bde7f-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="bde7f-108">Remarks</span></span>  
 <span data-ttu-id="bde7f-109">Сборки не следует после этого обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="bde7f-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bde7f-110">Требования</span><span class="sxs-lookup"><span data-stu-id="bde7f-110">Requirements</span></span>  
 <span data-ttu-id="bde7f-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bde7f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bde7f-112">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bde7f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bde7f-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bde7f-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bde7f-114">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="bde7f-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bde7f-115">См. также</span><span class="sxs-lookup"><span data-stu-id="bde7f-115">See also</span></span>

- [<span data-ttu-id="bde7f-116">Метод LoadAssembly</span><span class="sxs-lookup"><span data-stu-id="bde7f-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="bde7f-117">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="bde7f-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
