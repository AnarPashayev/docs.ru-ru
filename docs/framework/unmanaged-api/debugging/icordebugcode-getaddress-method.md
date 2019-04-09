---
title: Метод ICorDebugCode::GetAddress
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11ced90b88f083eb69b06d197d64a8ef4252f9d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141502"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="09ee9-102">Метод ICorDebugCode::GetAddress</span><span class="sxs-lookup"><span data-stu-id="09ee9-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="09ee9-103">Возвращает относительный виртуальный адрес (RVA) сегмента кода, представляющий этот интерфейс «ICorDebugCode».</span><span class="sxs-lookup"><span data-stu-id="09ee9-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ee9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="09ee9-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09ee9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="09ee9-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="09ee9-106">[out] Указатель на относительный виртуальный адрес сегмента кода.</span><span class="sxs-lookup"><span data-stu-id="09ee9-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ee9-107">Требования</span><span class="sxs-lookup"><span data-stu-id="09ee9-107">Requirements</span></span>  
 <span data-ttu-id="09ee9-108">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09ee9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ee9-109">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09ee9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09ee9-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09ee9-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="09ee9-111">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="09ee9-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="09ee9-112">См. также</span><span class="sxs-lookup"><span data-stu-id="09ee9-112">See also</span></span>
