---
title: Метод ICorDebugFunction::GetCurrentVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea615eacb30fd4e7a0fd7d730094c2ab4f9dc285
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988732"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="ad0ed-102">Метод ICorDebugFunction::GetCurrentVersionNumber</span><span class="sxs-lookup"><span data-stu-id="ad0ed-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="ad0ed-103">Получает номер версии последней правки, внесенной в функцию, представленный этим объектом ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="ad0ed-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad0ed-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ad0ed-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad0ed-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="ad0ed-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="ad0ed-106">[out] Указатель на целочисленное значение, — это номер версии последней правки этой функции.</span><span class="sxs-lookup"><span data-stu-id="ad0ed-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad0ed-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="ad0ed-107">Remarks</span></span>  
 <span data-ttu-id="ad0ed-108">Номер версии последней правки этой функции может быть больше, чем номер версии самой функции.</span><span class="sxs-lookup"><span data-stu-id="ad0ed-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="ad0ed-109">Использовать [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) метод или [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) метод для извлечения номер версии функции.</span><span class="sxs-lookup"><span data-stu-id="ad0ed-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad0ed-110">Требования</span><span class="sxs-lookup"><span data-stu-id="ad0ed-110">Requirements</span></span>  
 <span data-ttu-id="ad0ed-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad0ed-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad0ed-112">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad0ed-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad0ed-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad0ed-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad0ed-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad0ed-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
