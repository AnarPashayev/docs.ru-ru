---
title: Метод ICorDebugChain::GetActiveFrame
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c14b48a29993a65a0a0ab9fcb63bcb1e0d882042
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645374"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="3534f-102">Метод ICorDebugChain::GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="3534f-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="3534f-103">Получает активный (то есть самой последней) кадра в цепочке.</span><span class="sxs-lookup"><span data-stu-id="3534f-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3534f-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3534f-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3534f-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="3534f-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="3534f-106">[out] Указатель на адрес ICorDebugFrame объект, представляющий активный (то есть самой последней) кадра в цепочке.</span><span class="sxs-lookup"><span data-stu-id="3534f-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3534f-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="3534f-107">Remarks</span></span>  
 <span data-ttu-id="3534f-108">Если нет кадров управляемого стека, `ppFrame` задано значение null.</span><span class="sxs-lookup"><span data-stu-id="3534f-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="3534f-109">Если активная рамка не доступен, вызов будет успешным и `ppFrame` будет иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="3534f-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="3534f-110">Активные кадры будет недоступен для цепочек, инициирована из-за CHAIN_ENTER_UNMANAGED, а также для некоторых цепей, инициированных из-за CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="3534f-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="3534f-111">См. в разделе перечисление CorDebugChainReason.</span><span class="sxs-lookup"><span data-stu-id="3534f-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3534f-112">Требования</span><span class="sxs-lookup"><span data-stu-id="3534f-112">Requirements</span></span>  
 <span data-ttu-id="3534f-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3534f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3534f-114">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3534f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3534f-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3534f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3534f-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3534f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
