---
title: Метод ICorDebugEval::NewString
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db609bdee7975b6c067271f99529e2cf2240f720
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989031"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="86681-102">Метод ICorDebugEval::NewString</span><span class="sxs-lookup"><span data-stu-id="86681-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="86681-103">Выделяет новый экземпляр строки с указанным содержимым.</span><span class="sxs-lookup"><span data-stu-id="86681-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86681-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="86681-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86681-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="86681-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="86681-106">[in] Указатель на содержимое для строки.</span><span class="sxs-lookup"><span data-stu-id="86681-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86681-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="86681-107">Remarks</span></span>  
 <span data-ttu-id="86681-108">Строка всегда создается в домене приложения, в котором в настоящее время выполняется поток.</span><span class="sxs-lookup"><span data-stu-id="86681-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86681-109">Требования</span><span class="sxs-lookup"><span data-stu-id="86681-109">Requirements</span></span>  
 <span data-ttu-id="86681-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86681-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86681-111">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86681-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86681-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86681-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86681-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86681-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
