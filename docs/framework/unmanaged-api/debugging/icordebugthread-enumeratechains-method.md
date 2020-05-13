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
ms.openlocfilehash: 711fccd65379bc3e5e178869e7220dd84fd07fbe
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379705"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="e9797-102">Метод ICorDebugThread::EnumerateChains</span><span class="sxs-lookup"><span data-stu-id="e9797-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="e9797-103">Получает указатель интерфейса на перечислитель Икордебугчаиненум, который содержит все цепочки стека в этом объекте ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="e9797-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9797-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e9797-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9797-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e9797-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="e9797-106">заполняет Указатель на адрес `ICorDebugChainEnum` объекта, который допускает перечисление всех цепочек стека в этом потоке, начиная с активной (то есть самой последней) цепочки.</span><span class="sxs-lookup"><span data-stu-id="e9797-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9797-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="e9797-107">Remarks</span></span>  
 <span data-ttu-id="e9797-108">Цепочка стека представляет физический стек вызовов для потока.</span><span class="sxs-lookup"><span data-stu-id="e9797-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="e9797-109">В следующих случаях создается граница цепочки стеков:</span><span class="sxs-lookup"><span data-stu-id="e9797-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="e9797-110">Переход с управляемого на неуправляемый или неуправляемый на управляемый.</span><span class="sxs-lookup"><span data-stu-id="e9797-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="e9797-111">Переключение контекста.</span><span class="sxs-lookup"><span data-stu-id="e9797-111">A context switch.</span></span>  
  
- <span data-ttu-id="e9797-112">Перехват пользовательского потока отладчиком.</span><span class="sxs-lookup"><span data-stu-id="e9797-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="e9797-113">В простом случае для потока, в котором выполняется исключительно управляемый код в одном контексте, между потоками и цепочками стеков будет существовать соответствие "один к одному".</span><span class="sxs-lookup"><span data-stu-id="e9797-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="e9797-114">Отладчик может захотеть перераспределить физические стеки вызовов всех потоков на логические стеки вызовов.</span><span class="sxs-lookup"><span data-stu-id="e9797-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="e9797-115">Это может привести к сортировке всех цепочек потоков по связям "Вызывающий/вызываемый" и их перегруппировку.</span><span class="sxs-lookup"><span data-stu-id="e9797-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9797-116">Требования</span><span class="sxs-lookup"><span data-stu-id="e9797-116">Requirements</span></span>  
 <span data-ttu-id="e9797-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9797-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9797-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9797-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9797-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9797-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9797-120">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9797-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
