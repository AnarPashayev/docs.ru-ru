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
ms.openlocfilehash: a90ddd27834e7614c1827d606a9955b4d6c53127
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795980"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="68c8b-102">Перечисление CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="68c8b-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="68c8b-103">Предоставляет дополнительную информацию о событиях отладки на платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="68c8b-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c8b-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="68c8b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="68c8b-105">Участники</span><span class="sxs-lookup"><span data-stu-id="68c8b-105">Members</span></span>  
  
|<span data-ttu-id="68c8b-106">Участник</span><span class="sxs-lookup"><span data-stu-id="68c8b-106">Member</span></span>|<span data-ttu-id="68c8b-107">Описание</span><span class="sxs-lookup"><span data-stu-id="68c8b-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="68c8b-108">Указывает, что событие отладки является первичным исключением.</span><span class="sxs-lookup"><span data-stu-id="68c8b-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68c8b-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="68c8b-109">Remarks</span></span>  
 <span data-ttu-id="68c8b-110">Метод [ICorDebugProcess6::D екодивент](icordebugprocess6-decodeevent-method.md) включает `dwFlags` параметр, предоставляющий дополнительные сведения о событии отладки, значение которого зависит от целевой архитектуры.</span><span class="sxs-lookup"><span data-stu-id="68c8b-110">The [ICorDebugProcess6::DecodeEvent](icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="68c8b-111">Перечисление `CorDebugDecodeEventFlagsWindows` можно использовать с событиями отладки на платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="68c8b-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68c8b-112">Это перечисление предназначено для использования только в сценариях отладки .NET Native.</span><span class="sxs-lookup"><span data-stu-id="68c8b-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68c8b-113">Требования</span><span class="sxs-lookup"><span data-stu-id="68c8b-113">Requirements</span></span>  
 <span data-ttu-id="68c8b-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68c8b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68c8b-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68c8b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68c8b-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68c8b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68c8b-117">**.NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68c8b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c8b-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="68c8b-118">See also</span></span>

- [<span data-ttu-id="68c8b-119">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="68c8b-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
