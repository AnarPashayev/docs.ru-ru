---
title: Метод ICorDebugObjectValue::GetClass
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06e9c7af1c4a769bfb45a8e9f805d97b3bad94aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174191"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="edfe3-102">Метод ICorDebugObjectValue::GetClass</span><span class="sxs-lookup"><span data-stu-id="edfe3-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="edfe3-103">Возвращает класс значение этого объекта.</span><span class="sxs-lookup"><span data-stu-id="edfe3-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edfe3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="edfe3-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edfe3-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="edfe3-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="edfe3-106">[out] Указатель на адрес объекта «ICorDebugClass», который представляет класс объекта значение объекта, представленный этим объектом «ICorDebugObjectValue».</span><span class="sxs-lookup"><span data-stu-id="edfe3-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edfe3-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="edfe3-107">Remarks</span></span>  
 <span data-ttu-id="edfe3-108">`GetClass` И [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) методы возвращают сведения о типе значения; они оба заменяемые поддержкой универсальных типов [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="edfe3-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edfe3-109">Требования</span><span class="sxs-lookup"><span data-stu-id="edfe3-109">Requirements</span></span>  
 <span data-ttu-id="edfe3-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edfe3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edfe3-111">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edfe3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edfe3-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edfe3-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="edfe3-113">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="edfe3-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="edfe3-114">См. также</span><span class="sxs-lookup"><span data-stu-id="edfe3-114">See also</span></span>
