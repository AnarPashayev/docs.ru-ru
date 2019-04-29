---
title: Метод ICorDebugProcess::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e281022cd7bc9b2095fdbd3964061b811ef60e0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949036"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="bc661-102">Метод ICorDebugProcess::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="bc661-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="bc661-103">Задает контекст для данного потока в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="bc661-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc661-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bc661-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc661-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="bc661-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="bc661-106">[in] Идентификатор потока, для которого необходимо задать контекст.</span><span class="sxs-lookup"><span data-stu-id="bc661-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="bc661-107">[in] Размер массива `context`.</span><span class="sxs-lookup"><span data-stu-id="bc661-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="bc661-108">[in] Массив байтов, описывающие контекст потока.</span><span class="sxs-lookup"><span data-stu-id="bc661-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="bc661-109">Контекст задает архитектуру процессора, на котором выполняется поток.</span><span class="sxs-lookup"><span data-stu-id="bc661-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc661-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="bc661-110">Remarks</span></span>  
 <span data-ttu-id="bc661-111">Отладчик должен вызвать этот метод вместо Win32 `SetThreadContext` работать, поскольку фактически поток может находиться в состоянии «перехваченного», в котором его контекст был временно изменен.</span><span class="sxs-lookup"><span data-stu-id="bc661-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="bc661-112">Этот метод должен использоваться только в том случае, когда поток находится в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="bc661-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="bc661-113">Используйте [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) для потоков в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="bc661-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="bc661-114">Никогда не требуется изменения контекста потока во время события отладки (OOB)-каналу.</span><span class="sxs-lookup"><span data-stu-id="bc661-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="bc661-115">Данные, передаваемые должно быть структурой контекст для текущей платформы.</span><span class="sxs-lookup"><span data-stu-id="bc661-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="bc661-116">Этот метод может привести к повреждению среды выполнения при неправильном.</span><span class="sxs-lookup"><span data-stu-id="bc661-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc661-117">Требования</span><span class="sxs-lookup"><span data-stu-id="bc661-117">Requirements</span></span>  
 <span data-ttu-id="bc661-118">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc661-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc661-119">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc661-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc661-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc661-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc661-121">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc661-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
