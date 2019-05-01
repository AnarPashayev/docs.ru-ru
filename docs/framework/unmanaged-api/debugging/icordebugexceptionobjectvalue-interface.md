---
title: Интерфейс ICorDebugExceptionObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5328442ceaee05b3f81466b785f04a361d456a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995921"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="75bc7-102">Интерфейс ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="75bc7-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="75bc7-103">Расширяет интерфейс «ICorDebugObjectValue», чтобы предоставить сведения о трассировке стека из управляемого объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="75bc7-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75bc7-104">Методы</span><span class="sxs-lookup"><span data-stu-id="75bc7-104">Methods</span></span>  
  
|<span data-ttu-id="75bc7-105">Метод</span><span class="sxs-lookup"><span data-stu-id="75bc7-105">Method</span></span>|<span data-ttu-id="75bc7-106">Описание</span><span class="sxs-lookup"><span data-stu-id="75bc7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75bc7-107">Метод EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="75bc7-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="75bc7-108">Получает перечислитель для стека вызовов, внедренных в объект исключения.</span><span class="sxs-lookup"><span data-stu-id="75bc7-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75bc7-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="75bc7-109">Remarks</span></span>  
 <span data-ttu-id="75bc7-110">Вызов `QueryInterface` проходит успешно для управляемых объектов, которые являются производными от <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75bc7-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75bc7-111">Требования</span><span class="sxs-lookup"><span data-stu-id="75bc7-111">Requirements</span></span>  
 <span data-ttu-id="75bc7-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75bc7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75bc7-113">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75bc7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75bc7-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75bc7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75bc7-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75bc7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75bc7-116">См. также</span><span class="sxs-lookup"><span data-stu-id="75bc7-116">See also</span></span>

- [<span data-ttu-id="75bc7-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="75bc7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="75bc7-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="75bc7-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
