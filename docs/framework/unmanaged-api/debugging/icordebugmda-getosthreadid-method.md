---
title: Метод ICorDebugMDA::GetOSThreadId
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: c7ab77e9316023a97d2eafe8bcccc2b45e240cd0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207822"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="4a0ee-102">Метод ICorDebugMDA::GetOSThreadId</span><span class="sxs-lookup"><span data-stu-id="4a0ee-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="4a0ee-103">Возвращает идентификатор потока операционной системы (ОС), по которому выполняется управляемый помощник по отладке (MDA), представленный [ICorDebugMDA](icordebugmda-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4a0ee-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a0ee-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a0ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a0ee-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4a0ee-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="4a0ee-106">заполняет Указатель на идентификатор потока операционной системы.</span><span class="sxs-lookup"><span data-stu-id="4a0ee-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a0ee-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="4a0ee-107">Remarks</span></span>  
 <span data-ttu-id="4a0ee-108">Поток операционной системы используется вместо ICorDebugThread, чтобы разрешить ситуации, в которых MDA срабатывает либо в собственном потоке, либо в управляемом потоке, который еще не вошел в управляемый код.</span><span class="sxs-lookup"><span data-stu-id="4a0ee-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a0ee-109">Требования</span><span class="sxs-lookup"><span data-stu-id="4a0ee-109">Requirements</span></span>  
 <span data-ttu-id="4a0ee-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a0ee-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a0ee-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a0ee-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a0ee-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a0ee-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a0ee-113">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a0ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a0ee-114">См. также</span><span class="sxs-lookup"><span data-stu-id="4a0ee-114">See also</span></span>

- [<span data-ttu-id="4a0ee-115">Интерфейс ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="4a0ee-115">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="4a0ee-116">Диагностика ошибок посредством управляемых помощников по отладке</span><span class="sxs-lookup"><span data-stu-id="4a0ee-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
