---
title: Метод ICorDebugMDA::GetFlags
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a35e9f7cf43105db05408f285cd89dbd839a4cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093492"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="44a8c-102">Метод ICorDebugMDA::GetFlags</span><span class="sxs-lookup"><span data-stu-id="44a8c-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="44a8c-103">Получает флаги, связанные с управляемый помощник по отладке (MDA), представленный [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="44a8c-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44a8c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44a8c-104">Syntax</span></span>  
  
```  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44a8c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="44a8c-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="44a8c-106">[in] Побитовое сочетание [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) значений перечисления, определяющих параметры флагов данный MDA.</span><span class="sxs-lookup"><span data-stu-id="44a8c-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44a8c-107">Требования</span><span class="sxs-lookup"><span data-stu-id="44a8c-107">Requirements</span></span>  
 <span data-ttu-id="44a8c-108">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44a8c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44a8c-109">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44a8c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44a8c-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44a8c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44a8c-111">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44a8c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a8c-112">См. также</span><span class="sxs-lookup"><span data-stu-id="44a8c-112">See also</span></span>

- [<span data-ttu-id="44a8c-113">Интерфейс ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="44a8c-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="44a8c-114">Диагностика ошибок посредством помощников по отладке управляемого кода</span><span class="sxs-lookup"><span data-stu-id="44a8c-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
