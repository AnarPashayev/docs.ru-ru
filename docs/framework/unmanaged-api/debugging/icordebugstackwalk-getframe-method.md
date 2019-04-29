---
title: Метод ICorDebugStackWalk::GetFrame
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 253a25fdfc1f00adbc20388660caf6c227030a1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782737"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="eca56-102">Метод ICorDebugStackWalk::GetFrame</span><span class="sxs-lookup"><span data-stu-id="eca56-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="eca56-103">Получает текущий кадр [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) объекта.</span><span class="sxs-lookup"><span data-stu-id="eca56-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca56-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eca56-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eca56-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="eca56-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="eca56-106">[in] Указатель на адрес объекта созданный кадр, который представляет текущий кадр стека.</span><span class="sxs-lookup"><span data-stu-id="eca56-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eca56-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eca56-107">Return Value</span></span>  
 <span data-ttu-id="eca56-108">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="eca56-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="eca56-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eca56-109">HRESULT</span></span>|<span data-ttu-id="eca56-110">Описание</span><span class="sxs-lookup"><span data-stu-id="eca56-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eca56-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eca56-111">S_OK</span></span>|<span data-ttu-id="eca56-112">Среда выполнения успешно возвращено текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="eca56-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="eca56-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eca56-113">E_FAIL</span></span>|<span data-ttu-id="eca56-114">Текущий кадр не возвращен.</span><span class="sxs-lookup"><span data-stu-id="eca56-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="eca56-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="eca56-115">S_FALSE</span></span>|<span data-ttu-id="eca56-116">Текущий кадр является кадром стека.</span><span class="sxs-lookup"><span data-stu-id="eca56-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="eca56-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="eca56-117">E_INVALIDARG</span></span>|<span data-ttu-id="eca56-118">Параметр `pFrame` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="eca56-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="eca56-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="eca56-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="eca56-120">Указатель кадра уже находится в конце стека; Таким образом может осуществляться без дополнительных кадров.</span><span class="sxs-lookup"><span data-stu-id="eca56-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="eca56-121">Исключения</span><span class="sxs-lookup"><span data-stu-id="eca56-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eca56-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="eca56-122">Remarks</span></span>  
 <span data-ttu-id="eca56-123">`ICorDebugStackWalk` Возвращает только фактические кадры стека.</span><span class="sxs-lookup"><span data-stu-id="eca56-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="eca56-124">Используйте [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) метод для возврата внутренних кадрах.</span><span class="sxs-lookup"><span data-stu-id="eca56-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="eca56-125">(Внутренние кадры — это структуры данных, помещается в стек средой выполнения для хранения временных данных.)</span><span class="sxs-lookup"><span data-stu-id="eca56-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eca56-126">Требования</span><span class="sxs-lookup"><span data-stu-id="eca56-126">Requirements</span></span>  
 <span data-ttu-id="eca56-127">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eca56-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eca56-128">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eca56-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eca56-129">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eca56-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eca56-130">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eca56-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca56-131">См. также</span><span class="sxs-lookup"><span data-stu-id="eca56-131">See also</span></span>

- [<span data-ttu-id="eca56-132">Интерфейс ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="eca56-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="eca56-133">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="eca56-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="eca56-134">Отладка</span><span class="sxs-lookup"><span data-stu-id="eca56-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
