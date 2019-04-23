---
title: Интерфейс ICorDebugValue
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdc889dd6b2854654bfe43b24afbe4cc19863c80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227825"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="40e76-102">Интерфейс ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="40e76-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="40e76-103">Представляет значение в отлаживаемом процессе.</span><span class="sxs-lookup"><span data-stu-id="40e76-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="40e76-104">Значение может быть чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="40e76-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40e76-105">Методы</span><span class="sxs-lookup"><span data-stu-id="40e76-105">Methods</span></span>  
  
|<span data-ttu-id="40e76-106">Метод</span><span class="sxs-lookup"><span data-stu-id="40e76-106">Method</span></span>|<span data-ttu-id="40e76-107">Описание</span><span class="sxs-lookup"><span data-stu-id="40e76-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40e76-108">Метод CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="40e76-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="40e76-109">В настоящее время этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="40e76-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="40e76-110">Метод GetAddress</span><span class="sxs-lookup"><span data-stu-id="40e76-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="40e76-111">Возвращает адрес это `ICorDebugValue` объект, который находится в отлаживаемом процессе.</span><span class="sxs-lookup"><span data-stu-id="40e76-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="40e76-112">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="40e76-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="40e76-113">Получает размер в байтах, это `ICorDebugValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="40e76-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="40e76-114">Метод GetType</span><span class="sxs-lookup"><span data-stu-id="40e76-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="40e76-115">Получает тип-примитив это `ICorDebugValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="40e76-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40e76-116">Примечания</span><span class="sxs-lookup"><span data-stu-id="40e76-116">Remarks</span></span>  
 <span data-ttu-id="40e76-117">Как правило владение объектом значение передается при возврате.</span><span class="sxs-lookup"><span data-stu-id="40e76-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="40e76-118">Получатель отвечает за удаление ссылки из объекта при его завершении с объектом.</span><span class="sxs-lookup"><span data-stu-id="40e76-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="40e76-119">В зависимости от того, где значение было получено путем значение может не остаются действительными после возобновления процесса.</span><span class="sxs-lookup"><span data-stu-id="40e76-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="40e76-120">Таким образом, как правило, значение не должно храниться во время вызова из [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="40e76-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40e76-121">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="40e76-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40e76-122">Требования</span><span class="sxs-lookup"><span data-stu-id="40e76-122">Requirements</span></span>  
 <span data-ttu-id="40e76-123">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40e76-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40e76-124">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40e76-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40e76-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40e76-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40e76-126">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40e76-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e76-127">См. также</span><span class="sxs-lookup"><span data-stu-id="40e76-127">See also</span></span>

- [<span data-ttu-id="40e76-128">Интерфейс ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="40e76-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="40e76-129">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="40e76-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
