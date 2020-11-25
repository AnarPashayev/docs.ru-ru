---
title: Метод ICorDebugNativeFrame::SetIP
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 65de42a0b86e4b4593b7880e9dc290ce00007a40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709262"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="c4b21-102">Метод ICorDebugNativeFrame::SetIP</span><span class="sxs-lookup"><span data-stu-id="c4b21-102">ICorDebugNativeFrame::SetIP Method</span></span>

<span data-ttu-id="c4b21-103">Задает указатель инструкции в указанном расположении смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="c4b21-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b21-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c4b21-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4b21-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="c4b21-105">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="c4b21-106">окне Положение смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="c4b21-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4b21-107">Комментарии</span><span class="sxs-lookup"><span data-stu-id="c4b21-107">Remarks</span></span>  

 <span data-ttu-id="c4b21-108">Вызывает метод, чтобы `SetIP` немедленно сделать недействительными все кадры и цепочки для текущего потока.</span><span class="sxs-lookup"><span data-stu-id="c4b21-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="c4b21-109">Если отладчику требуются сведения о кадре после вызова `SetIP` , он должен выполнить новую трассировку стека.</span><span class="sxs-lookup"><span data-stu-id="c4b21-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="c4b21-110">[ICorDebug](icordebug-interface.md) попытается удержать кадр стека в допустимом состоянии.</span><span class="sxs-lookup"><span data-stu-id="c4b21-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="c4b21-111">Однако даже если кадр находится в допустимом состоянии, то, что касается среды выполнения, могут возникнуть проблемы, например неинициализированные локальные переменные и т. д.</span><span class="sxs-lookup"><span data-stu-id="c4b21-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="c4b21-112">Вызывающий объект отвечает за выполнение согласованности выполняющейся программы.</span><span class="sxs-lookup"><span data-stu-id="c4b21-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="c4b21-113">На 64-разрядных платформах указатель инструкции не может быть перемещен из `catch` блока или `finally` .</span><span class="sxs-lookup"><span data-stu-id="c4b21-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="c4b21-114">Если `SetIP` вызывается метод для перемещения на 64-разрядной платформе, он возвращает значение HRESULT, указывающее на сбой.</span><span class="sxs-lookup"><span data-stu-id="c4b21-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4b21-115">Требования</span><span class="sxs-lookup"><span data-stu-id="c4b21-115">Requirements</span></span>  

 <span data-ttu-id="c4b21-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4b21-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4b21-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4b21-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4b21-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4b21-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4b21-119">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b21-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b21-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c4b21-120">See also</span></span>
