---
title: Метод ICorDebugThread::GetRegisterSet
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8769293364c111754f4bfe9360a0dca93c0ba13c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770602"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="7a73a-102">Метод ICorDebugThread::GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="7a73a-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="7a73a-103">Получает указатель интерфейса на набор регистров, которая связана с активной части данного объекта ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="7a73a-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a73a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7a73a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a73a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="7a73a-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="7a73a-106">[out] Указатель на адрес [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) интерфейс, представляющий регистра набор для активной части данного потока.</span><span class="sxs-lookup"><span data-stu-id="7a73a-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a73a-107">Требования</span><span class="sxs-lookup"><span data-stu-id="7a73a-107">Requirements</span></span>  
 <span data-ttu-id="7a73a-108">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a73a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a73a-109">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a73a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a73a-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a73a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a73a-111">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a73a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
