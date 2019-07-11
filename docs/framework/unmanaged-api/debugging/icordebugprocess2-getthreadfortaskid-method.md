---
title: Метод ICorDebugProcess2::GetThreadForTaskID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85040a31966a92ead6ca4786f62852f17923056
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736924"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="330e2-102">Метод ICorDebugProcess2::GetThreadForTaskID</span><span class="sxs-lookup"><span data-stu-id="330e2-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="330e2-103">Получает поток, на котором выполняется задача с указанным идентификатором.</span><span class="sxs-lookup"><span data-stu-id="330e2-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="330e2-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="330e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="330e2-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="330e2-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="330e2-106">[in] Идентификатор задачи.</span><span class="sxs-lookup"><span data-stu-id="330e2-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="330e2-107">[out] Указатель на адрес ICorDebugThread2 объект, представляющий поток, который требуется получить.</span><span class="sxs-lookup"><span data-stu-id="330e2-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="330e2-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="330e2-108">Remarks</span></span>  
 <span data-ttu-id="330e2-109">Основное приложение может задать идентификатор задачи с помощью [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="330e2-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="330e2-110">Требования</span><span class="sxs-lookup"><span data-stu-id="330e2-110">Requirements</span></span>  
 <span data-ttu-id="330e2-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="330e2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="330e2-112">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="330e2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="330e2-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="330e2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="330e2-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="330e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
