---
title: Метод ICorDebugProcess::GetHelperThreadID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: 77cc658e28c7a69d8c4aeeed2f3e7ea40f0d2af6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724576"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="69f14-102">Метод ICorDebugProcess::GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="69f14-102">ICorDebugProcess::GetHelperThreadID Method</span></span>

<span data-ttu-id="69f14-103">Получает идентификатор потока операционной системы (ОС) внутреннего вспомогательного потока отладчика.</span><span class="sxs-lookup"><span data-stu-id="69f14-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f14-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="69f14-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69f14-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="69f14-105">Parameters</span></span>  

 `pThreadID`  
 <span data-ttu-id="69f14-106">заполняет Указатель на идентификатор потока операционной системы внутреннего вспомогательного потока отладчика.</span><span class="sxs-lookup"><span data-stu-id="69f14-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69f14-107">Комментарии</span><span class="sxs-lookup"><span data-stu-id="69f14-107">Remarks</span></span>  

 <span data-ttu-id="69f14-108">Во время управляемой и неуправляемой отладки следует следить за тем, чтобы поток с указанным ИДЕНТИФИКАТОРом оставался в работоспособном режиме, если он достигнет точки останова, размещенной отладчиком.</span><span class="sxs-lookup"><span data-stu-id="69f14-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="69f14-109">Отладчику также может потребоваться скрыть этот поток от пользователя.</span><span class="sxs-lookup"><span data-stu-id="69f14-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="69f14-110">Если в процессе еще не существует вспомогательного потока, `GetHelperThreadID` метод возвращает ноль в \* `pThreadID` .</span><span class="sxs-lookup"><span data-stu-id="69f14-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="69f14-111">Невозможно кэшировать идентификатор потока вспомогательного потока, так как он может измениться со временем.</span><span class="sxs-lookup"><span data-stu-id="69f14-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="69f14-112">Необходимо повторно запросить идентификатор потока при каждом событии остановки.</span><span class="sxs-lookup"><span data-stu-id="69f14-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="69f14-113">Идентификатор потока вспомогательного потока отладчика будет правильным для каждого неуправляемого события [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) , что позволяет отладчику определить идентификатор потока вспомогательного потока и скрыть его от пользователя.</span><span class="sxs-lookup"><span data-stu-id="69f14-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="69f14-114">Поток, идентифицированный в виде вспомогательного потока во время неуправляемого `ICorDebugManagedCallback::CreateThread` события, никогда не будет запускать управляемый пользовательский код.</span><span class="sxs-lookup"><span data-stu-id="69f14-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69f14-115">Требования</span><span class="sxs-lookup"><span data-stu-id="69f14-115">Requirements</span></span>  

 <span data-ttu-id="69f14-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69f14-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69f14-117">**Заголовок:** CorDebug. idl.</span><span class="sxs-lookup"><span data-stu-id="69f14-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="69f14-118">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="69f14-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="69f14-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69f14-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69f14-120">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69f14-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
