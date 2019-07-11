---
title: Метод ICorDebugValue2::GetExactType
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c28ff84b08802246d587bfa130ae5915177932ac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764303"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="06bfa-102">Метод ICorDebugValue2::GetExactType</span><span class="sxs-lookup"><span data-stu-id="06bfa-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="06bfa-103">Получает указатель интерфейса на объект «ICorDebugType», который представляет <xref:System.Type> этого значения.</span><span class="sxs-lookup"><span data-stu-id="06bfa-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06bfa-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="06bfa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06bfa-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="06bfa-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="06bfa-106">[out] Указатель на адрес `ICorDebugType` , представляющий <xref:System.Type> значения, представленный этим объектом «ICorDebugValue2».</span><span class="sxs-lookup"><span data-stu-id="06bfa-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06bfa-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="06bfa-107">Remarks</span></span>  
 <span data-ttu-id="06bfa-108">Универсальные шаблоны с поддержкой `GetExactType` метод заменяет оба [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) и [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) методов, каждый из которых возвращают сведения о типе значения .</span><span class="sxs-lookup"><span data-stu-id="06bfa-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06bfa-109">Требования</span><span class="sxs-lookup"><span data-stu-id="06bfa-109">Requirements</span></span>  
 <span data-ttu-id="06bfa-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06bfa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06bfa-111">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06bfa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06bfa-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06bfa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06bfa-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06bfa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06bfa-114">См. также</span><span class="sxs-lookup"><span data-stu-id="06bfa-114">See also</span></span>
