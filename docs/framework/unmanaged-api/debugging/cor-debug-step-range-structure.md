---
title: Структура COR_DEBUG_STEP_RANGE
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bda8079cff8f5e8fafade03a02c3dfe8798c5ca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740772"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="cdd2a-102">Структура COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="cdd2a-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="cdd2a-103">Содержит сведения о смещении для диапазона кода.</span><span class="sxs-lookup"><span data-stu-id="cdd2a-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="cdd2a-104">Эта структура используется [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="cdd2a-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdd2a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cdd2a-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="cdd2a-106">Участники</span><span class="sxs-lookup"><span data-stu-id="cdd2a-106">Members</span></span>  
  
|<span data-ttu-id="cdd2a-107">Член</span><span class="sxs-lookup"><span data-stu-id="cdd2a-107">Member</span></span>|<span data-ttu-id="cdd2a-108">Описание</span><span class="sxs-lookup"><span data-stu-id="cdd2a-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="cdd2a-109">Смещение начала диапазона.</span><span class="sxs-lookup"><span data-stu-id="cdd2a-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="cdd2a-110">Смещение конца диапазона.</span><span class="sxs-lookup"><span data-stu-id="cdd2a-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cdd2a-111">Требования</span><span class="sxs-lookup"><span data-stu-id="cdd2a-111">Requirements</span></span>  
 <span data-ttu-id="cdd2a-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdd2a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdd2a-113">**Заголовок.** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="cdd2a-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="cdd2a-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdd2a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdd2a-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdd2a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd2a-116">См. также</span><span class="sxs-lookup"><span data-stu-id="cdd2a-116">See also</span></span>

- [<span data-ttu-id="cdd2a-117">Метод StepRange</span><span class="sxs-lookup"><span data-stu-id="cdd2a-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="cdd2a-118">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="cdd2a-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="cdd2a-119">Отладка</span><span class="sxs-lookup"><span data-stu-id="cdd2a-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
