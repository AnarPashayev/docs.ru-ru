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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d59450540b680d6004c47fd646769e38c806024
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994621"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="1f050-102">Интерфейс ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="1f050-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="1f050-103">Специализированная реализация ICorDebugFrame, используемый для кадров машинного кода.</span><span class="sxs-lookup"><span data-stu-id="1f050-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1f050-104">Методы</span><span class="sxs-lookup"><span data-stu-id="1f050-104">Methods</span></span>  
  
|<span data-ttu-id="1f050-105">Метод</span><span class="sxs-lookup"><span data-stu-id="1f050-105">Method</span></span>|<span data-ttu-id="1f050-106">Описание</span><span class="sxs-lookup"><span data-stu-id="1f050-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1f050-107">Метод CanSetIP</span><span class="sxs-lookup"><span data-stu-id="1f050-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="1f050-108">Получает значение, указывающее, является ли он безопасным задать указатель инструкций в указанное расположение смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="1f050-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="1f050-109">Метод GetIP</span><span class="sxs-lookup"><span data-stu-id="1f050-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="1f050-110">Получает смещение кадра стека в машинный код.</span><span class="sxs-lookup"><span data-stu-id="1f050-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="1f050-111">Метод GetLocalDoubleRegisterValue</span><span class="sxs-lookup"><span data-stu-id="1f050-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="1f050-112">Получает указатель на интерфейс ICorDebugValue, представляющий значение аргумента или локальной переменной, хранящихся в двух регистрах памяти фрейм машинного кода.</span><span class="sxs-lookup"><span data-stu-id="1f050-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="1f050-113">Метод GetLocalMemoryRegisterValue</span><span class="sxs-lookup"><span data-stu-id="1f050-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="1f050-114">Возвращает указатель на `ICorDebugValue` , представляющий значение локальной переменной, которой младшие бита хранятся в указанном регистре, а старшие бита хранятся по адресу указанной области памяти.</span><span class="sxs-lookup"><span data-stu-id="1f050-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="1f050-115">Метод GetLocalMemoryValue</span><span class="sxs-lookup"><span data-stu-id="1f050-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="1f050-116">Возвращает указатель на `ICorDebugValue` , представляющий значение, хранящееся в указанной области памяти адрес локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="1f050-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="1f050-117">Метод GetLocalRegisterMemoryValue</span><span class="sxs-lookup"><span data-stu-id="1f050-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="1f050-118">Возвращает указатель на `ICorDebugValue` , представляющий значение локальной переменной, которой старшие бита хранятся в указанном регистре, а младшие бита хранятся по указанному адресу памяти</span><span class="sxs-lookup"><span data-stu-id="1f050-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="1f050-119">Метод GetLocalRegisterValue</span><span class="sxs-lookup"><span data-stu-id="1f050-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="1f050-120">Возвращает указатель на `ICorDebugValue` , представляющий значение аргумента или локальной переменной, хранящейся в указанном машинном регистре.</span><span class="sxs-lookup"><span data-stu-id="1f050-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="1f050-121">Метод GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="1f050-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="1f050-122">Возвращает указатель на [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) , представляющий набор для данного регистров `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="1f050-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="1f050-123">Метод SetIP</span><span class="sxs-lookup"><span data-stu-id="1f050-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="1f050-124">Задает указатель инструкций в указанное расположение смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="1f050-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f050-125">Примечания</span><span class="sxs-lookup"><span data-stu-id="1f050-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f050-126">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="1f050-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f050-127">Требования</span><span class="sxs-lookup"><span data-stu-id="1f050-127">Requirements</span></span>  
 <span data-ttu-id="1f050-128">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f050-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f050-129">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f050-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f050-130">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f050-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f050-131">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f050-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f050-132">См. также</span><span class="sxs-lookup"><span data-stu-id="1f050-132">See also</span></span>

- [<span data-ttu-id="1f050-133">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1f050-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
