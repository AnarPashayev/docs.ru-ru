---
title: Метод ICorDebugChain::GetCallee
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: ba9a4e32216fd6fad285397bfc48fbc54f602b88
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894647"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="519aa-102">Метод ICorDebugChain::GetCallee</span><span class="sxs-lookup"><span data-stu-id="519aa-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="519aa-103">Возвращает цепочку, вызванную этой цепочкой.</span><span class="sxs-lookup"><span data-stu-id="519aa-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="519aa-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="519aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="519aa-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="519aa-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="519aa-106">заполняет Указатель на адрес объекта ICorDebugChain, который представляет вызываемую цепочку.</span><span class="sxs-lookup"><span data-stu-id="519aa-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="519aa-107">Если эта цепочка выполняется в данный момент (то есть если эта цепочка не ожидает возврата вызванной цепочки), `ppChain` будет иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="519aa-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="519aa-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="519aa-108">Remarks</span></span>  
 <span data-ttu-id="519aa-109">Эта цепочка будет ожидать возврата вызванной цепочки перед возобновлением выполнения.</span><span class="sxs-lookup"><span data-stu-id="519aa-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="519aa-110">Вызываемая цепочка может находиться в другом потоке в случае маршалинга вызовов между потоками.</span><span class="sxs-lookup"><span data-stu-id="519aa-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="519aa-111">Требования</span><span class="sxs-lookup"><span data-stu-id="519aa-111">Requirements</span></span>  
 <span data-ttu-id="519aa-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="519aa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="519aa-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="519aa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="519aa-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="519aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="519aa-115">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="519aa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
