---
title: Метод ICorDebugVirtualUnwinder::GetContext
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3125fd5081e68237714bcb10f760b73ce7509f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119231"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="4bdac-102">Метод ICorDebugVirtualUnwinder::GetContext</span><span class="sxs-lookup"><span data-stu-id="4bdac-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="4bdac-103">Получает текущий контекст этого средства очистки.</span><span class="sxs-lookup"><span data-stu-id="4bdac-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdac-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4bdac-104">Syntax</span></span>  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bdac-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4bdac-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="4bdac-106">[in] Флаги, указывающие, какие части контекста следует возвращать (определенные в заголовке WinNt.h).</span><span class="sxs-lookup"><span data-stu-id="4bdac-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="4bdac-107">[in] Количество байтов в `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="4bdac-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="4bdac-108">[out] Указатель на число байтов, фактически записанных в `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="4bdac-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="4bdac-109">[out] Байтовый массив, содержащий текущий контекст этого средства очистки.</span><span class="sxs-lookup"><span data-stu-id="4bdac-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bdac-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4bdac-110">Return Value</span></span>  
 <span data-ttu-id="4bdac-111">Любое ошибочное значение HRESULT , полученное процессом mscordbi, считается неустранимым и приводит к возврату интерфейсами API ICorDebug значения `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="4bdac-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bdac-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="4bdac-112">Remarks</span></span>  
 <span data-ttu-id="4bdac-113">Задайте начальное значение `contextBuf` аргумент в буфере контекста, возвращенный путем вызова [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="4bdac-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bdac-114">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="4bdac-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="4bdac-115">Поскольку очистка может восстановить только подмножество регистров, например только неизменяемые регистры, контекст может не соответствовать в точности состоянию регистра во время фактического вызова метода.</span><span class="sxs-lookup"><span data-stu-id="4bdac-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bdac-116">Требования</span><span class="sxs-lookup"><span data-stu-id="4bdac-116">Requirements</span></span>  
 <span data-ttu-id="4bdac-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bdac-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bdac-118">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bdac-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bdac-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bdac-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bdac-120">**Версии платформы .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bdac-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdac-121">См. также</span><span class="sxs-lookup"><span data-stu-id="4bdac-121">See also</span></span>

- [<span data-ttu-id="4bdac-122">Интерфейс ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="4bdac-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="4bdac-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="4bdac-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
