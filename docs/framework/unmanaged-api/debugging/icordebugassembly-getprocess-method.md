---
title: Метод ICorDebugAssembly::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: e8662535fb6f1aa812130d96e67678baa3c41a52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734040"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="0409d-102">Метод ICorDebugAssembly::GetProcess</span><span class="sxs-lookup"><span data-stu-id="0409d-102">ICorDebugAssembly::GetProcess Method</span></span>

<span data-ttu-id="0409d-103">Возвращает указатель интерфейса на процесс, в котором выполняется данный экземпляр ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="0409d-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0409d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0409d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0409d-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="0409d-105">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="0409d-106">заполняет Указатель на интерфейс ICorDebugProcess, представляющий процесс.</span><span class="sxs-lookup"><span data-stu-id="0409d-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0409d-107">Требования</span><span class="sxs-lookup"><span data-stu-id="0409d-107">Requirements</span></span>  

 <span data-ttu-id="0409d-108">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0409d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0409d-109">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0409d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0409d-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0409d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0409d-111">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0409d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
