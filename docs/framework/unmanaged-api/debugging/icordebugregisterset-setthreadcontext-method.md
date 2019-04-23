---
title: Метод ICorDebugRegisterSet::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b1ea34c187de99d23b05b5e1a30c53bc54a6c0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197403"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="07993-102">Метод ICorDebugRegisterSet::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="07993-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="07993-103">`SetThreadContext` не реализуется в .NET Framework версии 2.0.</span><span class="sxs-lookup"><span data-stu-id="07993-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="07993-104">Этот метод не вызывается.</span><span class="sxs-lookup"><span data-stu-id="07993-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07993-105">С помощью операции более высокого уровня [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) для задания контекста потока.</span><span class="sxs-lookup"><span data-stu-id="07993-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07993-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07993-106">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="07993-107">Требования</span><span class="sxs-lookup"><span data-stu-id="07993-107">Requirements</span></span>  
 <span data-ttu-id="07993-108">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07993-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07993-109">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07993-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07993-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07993-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07993-111">**Версии платформы .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="07993-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07993-112">См. также</span><span class="sxs-lookup"><span data-stu-id="07993-112">See also</span></span>

- [<span data-ttu-id="07993-113">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="07993-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="07993-114">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="07993-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
