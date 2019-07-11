---
title: Метод ICorDebugThread::EnumerateChains
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f0ed843f72d3f1e1575da15776a94a9097fd02
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771098"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="25f78-102">Метод ICorDebugThread::EnumerateChains</span><span class="sxs-lookup"><span data-stu-id="25f78-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="25f78-103">Получает указатель интерфейса на перечислитель ICorDebugChainEnum, содержащий всех цепочек стека в этом объекте ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="25f78-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25f78-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="25f78-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25f78-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="25f78-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="25f78-106">[out] Указатель на адрес `ICorDebugChainEnum` связан объект, который позволяет перечисления всех стека в этом потоке, начиная с цепочке активный (то есть последнее).</span><span class="sxs-lookup"><span data-stu-id="25f78-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25f78-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="25f78-107">Remarks</span></span>  
 <span data-ttu-id="25f78-108">Цепочка стека представляет физический стек вызова для потока.</span><span class="sxs-lookup"><span data-stu-id="25f78-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="25f78-109">Следующих обстоятельствах создания цепочки границы стека:</span><span class="sxs-lookup"><span data-stu-id="25f78-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="25f78-110">Управляемого и неуправляемого или неуправляемого в управляемый переход.</span><span class="sxs-lookup"><span data-stu-id="25f78-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="25f78-111">Переключение контекста.</span><span class="sxs-lookup"><span data-stu-id="25f78-111">A context switch.</span></span>  
  
- <span data-ttu-id="25f78-112">Объект отладчика захват пользовательского потока.</span><span class="sxs-lookup"><span data-stu-id="25f78-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="25f78-113">В простом случае для потока, на котором выполняется только управляемый код в одном контексте однозначное соответствие будет существовать между потоками и цепочек стека.</span><span class="sxs-lookup"><span data-stu-id="25f78-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="25f78-114">Отладчик может потребоваться изменить расположение физических стеков вызова всех потоков в логические стеки вызовов.</span><span class="sxs-lookup"><span data-stu-id="25f78-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="25f78-115">Будет включать в себя сортировку цепочки всех потоков и их связей "Вызывающий/вызываемый" и перегруппирование.</span><span class="sxs-lookup"><span data-stu-id="25f78-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25f78-116">Требования</span><span class="sxs-lookup"><span data-stu-id="25f78-116">Requirements</span></span>  
 <span data-ttu-id="25f78-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25f78-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25f78-118">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25f78-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25f78-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25f78-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25f78-120">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25f78-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
