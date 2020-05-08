---
title: Метод ICorDebugArrayValue::GetElementType
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementType
helpviewer_keywords:
- ICorDebugArrayValue::GetElementType method [.NET Framework debugging]
- GetElementType method [.NET Framework debugging]
ms.assetid: ed71961e-ae9b-4dfc-9554-06637696d697
topic_type:
- apiref
ms.openlocfilehash: 8b5a6f4447730ebc6e4b23d3cd06df85b2d7fee6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895007"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="440ce-102">Метод ICorDebugArrayValue::GetElementType</span><span class="sxs-lookup"><span data-stu-id="440ce-102">ICorDebugArrayValue::GetElementType Method</span></span>
<span data-ttu-id="440ce-103">Возвращает значение, указывающее простой тип элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="440ce-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="440ce-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="440ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="440ce-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="440ce-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="440ce-106">заполняет Указатель на значение перечисления Корелементтипе, указывающее тип.</span><span class="sxs-lookup"><span data-stu-id="440ce-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="440ce-107">Требования</span><span class="sxs-lookup"><span data-stu-id="440ce-107">Requirements</span></span>  
 <span data-ttu-id="440ce-108">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="440ce-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="440ce-109">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="440ce-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="440ce-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="440ce-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="440ce-111">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="440ce-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
