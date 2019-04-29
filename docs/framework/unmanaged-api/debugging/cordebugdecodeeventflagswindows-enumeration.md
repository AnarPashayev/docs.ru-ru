---
title: Перечисление CorDebugDecodeEventFlagsWindows
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d4e006a03db5b16de93dfd07ec7b964db4bfc1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609221"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="ef7c0-102">Перечисление CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="ef7c0-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="ef7c0-103">Предоставляет дополнительную информацию о событиях отладки на платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="ef7c0-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef7c0-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ef7c0-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="ef7c0-105">Участники</span><span class="sxs-lookup"><span data-stu-id="ef7c0-105">Members</span></span>  
  
|<span data-ttu-id="ef7c0-106">Член</span><span class="sxs-lookup"><span data-stu-id="ef7c0-106">Member</span></span>|<span data-ttu-id="ef7c0-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ef7c0-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="ef7c0-108">Указывает, что событие отладки является первичным исключением.</span><span class="sxs-lookup"><span data-stu-id="ef7c0-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef7c0-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="ef7c0-109">Remarks</span></span>  
 <span data-ttu-id="ef7c0-110">[ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) метод включает `dwFlags` параметра, предоставляющий дополнительные сведения о событии отладки, и значение которого зависит от целевой архитектуры.</span><span class="sxs-lookup"><span data-stu-id="ef7c0-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="ef7c0-111">Перечисление `CorDebugDecodeEventFlagsWindows` можно использовать с событиями отладки на платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="ef7c0-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef7c0-112">Это перечисление предназначено для использования только в сценариях отладки .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ef7c0-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef7c0-113">Требования</span><span class="sxs-lookup"><span data-stu-id="ef7c0-113">Requirements</span></span>  
 <span data-ttu-id="ef7c0-114">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef7c0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef7c0-115">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef7c0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef7c0-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef7c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef7c0-117">**Версии платформы .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef7c0-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef7c0-118">См. также</span><span class="sxs-lookup"><span data-stu-id="ef7c0-118">See also</span></span>

- [<span data-ttu-id="ef7c0-119">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="ef7c0-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
