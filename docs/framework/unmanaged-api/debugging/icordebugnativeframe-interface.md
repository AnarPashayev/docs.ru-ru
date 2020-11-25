---
title: Интерфейс ICorDebugNativeFrame
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: 043dc0fdd5218d7bc6b80428d1eb891b3f01ee8c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695560"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="1b772-102">Интерфейс ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="1b772-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="1b772-103">Специализированная реализация ICorDebugFrame, используемая для кадров машинного кода.</span><span class="sxs-lookup"><span data-stu-id="1b772-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b772-104">Методы</span><span class="sxs-lookup"><span data-stu-id="1b772-104">Methods</span></span>  
  
|<span data-ttu-id="1b772-105">Метод</span><span class="sxs-lookup"><span data-stu-id="1b772-105">Method</span></span>|<span data-ttu-id="1b772-106">Описание</span><span class="sxs-lookup"><span data-stu-id="1b772-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b772-107">Метод CanSetIP</span><span class="sxs-lookup"><span data-stu-id="1b772-107">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="1b772-108">Возвращает значение, указывающее, может ли быть ненадежным устанавливать указатель инструкции на указанное расположение смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="1b772-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="1b772-109">Метод GetIP</span><span class="sxs-lookup"><span data-stu-id="1b772-109">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="1b772-110">Возвращает смещение кадра стека в машинный код.</span><span class="sxs-lookup"><span data-stu-id="1b772-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="1b772-111">Метод GetLocalDoubleRegisterValue</span><span class="sxs-lookup"><span data-stu-id="1b772-111">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="1b772-112">Возвращает указатель на объект ICorDebugValue, представляющий значение аргумента или локальной переменной, хранящейся в двух регистрах памяти в машинном кадре.</span><span class="sxs-lookup"><span data-stu-id="1b772-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="1b772-113">Метод GetLocalMemoryRegisterValue</span><span class="sxs-lookup"><span data-stu-id="1b772-113">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="1b772-114">Возвращает указатель на объект `ICorDebugValue` , представляющий значение локальной переменной, для которой младшие биты хранятся в указанном регистре, а старшие биты хранятся по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="1b772-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="1b772-115">Метод GetLocalMemoryValue</span><span class="sxs-lookup"><span data-stu-id="1b772-115">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="1b772-116">Возвращает указатель на объект `ICorDebugValue` , представляющий значение локальной переменной, хранящейся по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="1b772-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="1b772-117">Метод GetLocalRegisterMemoryValue</span><span class="sxs-lookup"><span data-stu-id="1b772-117">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="1b772-118">Возвращает указатель на объект `ICorDebugValue` , представляющий значение локальной переменной, для которой старшие биты хранятся в указанном регистре, а младшие биты хранятся по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="1b772-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="1b772-119">Метод GetLocalRegisterValue</span><span class="sxs-lookup"><span data-stu-id="1b772-119">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="1b772-120">Возвращает указатель на объект `ICorDebugValue` , представляющий значение аргумента или локальную переменную, хранящуюся в указанном собственном регистре.</span><span class="sxs-lookup"><span data-stu-id="1b772-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="1b772-121">Метод GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="1b772-121">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="1b772-122">Возвращает указатель на объект [ICorDebugRegisterSet](icordebugregisterset-interface.md) , представляющий набор регистров для этого объекта `ICorDebugNativeFrame` .</span><span class="sxs-lookup"><span data-stu-id="1b772-122">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="1b772-123">Метод SetIP</span><span class="sxs-lookup"><span data-stu-id="1b772-123">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="1b772-124">Задает указатель инструкции в указанном расположении смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="1b772-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b772-125">Комментарии</span><span class="sxs-lookup"><span data-stu-id="1b772-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b772-126">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="1b772-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b772-127">Требования</span><span class="sxs-lookup"><span data-stu-id="1b772-127">Requirements</span></span>  

 <span data-ttu-id="1b772-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b772-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b772-129">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b772-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b772-130">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b772-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b772-131">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b772-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b772-132">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1b772-132">See also</span></span>

- [<span data-ttu-id="1b772-133">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1b772-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
