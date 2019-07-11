---
title: Метод ICorDebugThread3::GetActiveInternalFrames
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58aaf0445fe42d083c12541056cb362f9a994944
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765210"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="52100-102">Метод ICorDebugThread3::GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="52100-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="52100-103">Возвращает массив из внутренних кадрах ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) объектов) в стеке.</span><span class="sxs-lookup"><span data-stu-id="52100-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52100-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="52100-104">Syntax</span></span>  
  
```cpp 
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="52100-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="52100-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="52100-106">[in] Количество внутренних кадрах, ожидаемая в `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="52100-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="52100-107">[out] Указатель на `ULONG32` , содержащий количество внутренних кадров в стеке.</span><span class="sxs-lookup"><span data-stu-id="52100-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="52100-108">[in, out] Указатель на адрес массив внутренней фреймы в стеке.</span><span class="sxs-lookup"><span data-stu-id="52100-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52100-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="52100-109">Return Value</span></span>  
 <span data-ttu-id="52100-110">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="52100-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="52100-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52100-111">HRESULT</span></span>|<span data-ttu-id="52100-112">Описание</span><span class="sxs-lookup"><span data-stu-id="52100-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52100-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="52100-113">S_OK</span></span>|<span data-ttu-id="52100-114">[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) объект был успешно создан.</span><span class="sxs-lookup"><span data-stu-id="52100-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="52100-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="52100-115">E_INVALIDARG</span></span>|<span data-ttu-id="52100-116">`cInternalFrames` не равно нулю и `ppInternalFrames` — `null`, или `pcInternalFrames` является `null`.</span><span class="sxs-lookup"><span data-stu-id="52100-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="52100-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="52100-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="52100-118">`ppInternalFrames` меньше количество внутренних кадрах.</span><span class="sxs-lookup"><span data-stu-id="52100-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="52100-119">Исключения</span><span class="sxs-lookup"><span data-stu-id="52100-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52100-120">Примечания</span><span class="sxs-lookup"><span data-stu-id="52100-120">Remarks</span></span>  
 <span data-ttu-id="52100-121">Внутренние кадры — это структуры данных, помещается в стек средой выполнения для хранения временных данных.</span><span class="sxs-lookup"><span data-stu-id="52100-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="52100-122">При первом вызове `GetActiveInternalFrames`, следует задать `cInternalFrames` параметр 0 (ноль) и `ppInternalFrames` параметр значение null.</span><span class="sxs-lookup"><span data-stu-id="52100-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="52100-123">Когда `GetActiveInternalFrames` сначала возвращает `pcInternalFrames` содержит количество внутренних фреймы в стеке.</span><span class="sxs-lookup"><span data-stu-id="52100-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="52100-124">`GetActiveInternalFrames` необходимо также вызвать второй раз.</span><span class="sxs-lookup"><span data-stu-id="52100-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="52100-125">Необходимо передать правильное значение (`pcInternalFrames`) в `cInternalFrames` параметра, и задание указателя на массив подходящего размера в `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="52100-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="52100-126">Используйте [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) метод, чтобы вернуть фактические кадры стека.</span><span class="sxs-lookup"><span data-stu-id="52100-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52100-127">Требования</span><span class="sxs-lookup"><span data-stu-id="52100-127">Requirements</span></span>  
 <span data-ttu-id="52100-128">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52100-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52100-129">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52100-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52100-130">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52100-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52100-131">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52100-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52100-132">См. также</span><span class="sxs-lookup"><span data-stu-id="52100-132">See also</span></span>

- [<span data-ttu-id="52100-133">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="52100-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="52100-134">Отладка</span><span class="sxs-lookup"><span data-stu-id="52100-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
