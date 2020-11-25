---
title: Метод ICorDebugManagedCallback::CreateThread
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 56ec7c56b167c29c9951638c5eee159e1d3c7ffb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721300"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="91bab-102">Метод ICorDebugManagedCallback::CreateThread</span><span class="sxs-lookup"><span data-stu-id="91bab-102">ICorDebugManagedCallback::CreateThread Method</span></span>

<span data-ttu-id="91bab-103">Уведомляет отладчик о том, что поток начал выполнение управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="91bab-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91bab-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="91bab-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91bab-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="91bab-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="91bab-106">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий поток.</span><span class="sxs-lookup"><span data-stu-id="91bab-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="91bab-107">окне Указатель на объект ICorDebugThread, представляющий поток.</span><span class="sxs-lookup"><span data-stu-id="91bab-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91bab-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="91bab-108">Remarks</span></span>  

 <span data-ttu-id="91bab-109">Поток будет размещен в первой выполняемой инструкции управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="91bab-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91bab-110">Требования</span><span class="sxs-lookup"><span data-stu-id="91bab-110">Requirements</span></span>  

 <span data-ttu-id="91bab-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91bab-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91bab-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91bab-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91bab-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91bab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91bab-114">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91bab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91bab-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="91bab-115">See also</span></span>

- [<span data-ttu-id="91bab-116">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="91bab-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
