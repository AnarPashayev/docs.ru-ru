---
title: Метод ICorDebugExceptionDebugEvent::GetStackPointer
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9d4c0a1938edd3e2fe88ea6e418b3430f1b5cb8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163206"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="46c14-102">Метод ICorDebugExceptionDebugEvent::GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="46c14-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="46c14-103">Получает указатель стека для этого события отладки исключения.</span><span class="sxs-lookup"><span data-stu-id="46c14-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c14-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="46c14-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46c14-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="46c14-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="46c14-106">[out] Указатель на адрес указателя стека для этого события отладки исключения.</span><span class="sxs-lookup"><span data-stu-id="46c14-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="46c14-107">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="46c14-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46c14-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="46c14-108">Remarks</span></span>  
 <span data-ttu-id="46c14-109">Смысл этого указателя стека зависит от типа события, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="46c14-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="46c14-110">Тип события.</span><span class="sxs-lookup"><span data-stu-id="46c14-110">Event type</span></span>|<span data-ttu-id="46c14-111">Смысл значения `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="46c14-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="46c14-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="46c14-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="46c14-113">Указатель стека для фрейма, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="46c14-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="46c14-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="46c14-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="46c14-115">Указатель стека для фрейма пользовательского кода, ближайшего к точке вызванного исключения.</span><span class="sxs-lookup"><span data-stu-id="46c14-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="46c14-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="46c14-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="46c14-117">Указатель стека для фрейма, содержащего обработчик catch.</span><span class="sxs-lookup"><span data-stu-id="46c14-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="46c14-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="46c14-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="46c14-119">Параметр `pStackPointer` имеет значение **NULL**.</span><span class="sxs-lookup"><span data-stu-id="46c14-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="46c14-120">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="46c14-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="46c14-121">Тип события доступен из [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="46c14-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46c14-122">Требования</span><span class="sxs-lookup"><span data-stu-id="46c14-122">Requirements</span></span>  
 <span data-ttu-id="46c14-123">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c14-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c14-124">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46c14-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46c14-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46c14-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46c14-126">**Версии платформы .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46c14-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c14-127">См. также</span><span class="sxs-lookup"><span data-stu-id="46c14-127">See also</span></span>

- [<span data-ttu-id="46c14-128">Интерфейс ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="46c14-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="46c14-129">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="46c14-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
