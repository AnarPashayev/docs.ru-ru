---
title: Метод ICorDebugNativeFrame2::IsChild
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550d25e995bdfe010fb1aa664a7c9882a775f4d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757171"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="2f61c-102">Метод ICorDebugNativeFrame2::IsChild</span><span class="sxs-lookup"><span data-stu-id="2f61c-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="2f61c-103">Определяет, является ли текущий кадр дочерним.</span><span class="sxs-lookup"><span data-stu-id="2f61c-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f61c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2f61c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f61c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="2f61c-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="2f61c-106">[out] Логическое значение, указывающее, является ли текущий кадр дочерним.</span><span class="sxs-lookup"><span data-stu-id="2f61c-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f61c-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2f61c-107">Return Value</span></span>  
 <span data-ttu-id="2f61c-108">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="2f61c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2f61c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f61c-109">HRESULT</span></span>|<span data-ttu-id="2f61c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="2f61c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f61c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f61c-111">S_OK</span></span>|<span data-ttu-id="2f61c-112">Состояние дочернего был успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="2f61c-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="2f61c-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f61c-113">E_FAIL</span></span>|<span data-ttu-id="2f61c-114">Состояние дочернего не могут быть возвращены.</span><span class="sxs-lookup"><span data-stu-id="2f61c-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="2f61c-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2f61c-115">E_INVALIDARG</span></span>|<span data-ttu-id="2f61c-116">Параметр `pIsChild` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="2f61c-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2f61c-117">Исключения</span><span class="sxs-lookup"><span data-stu-id="2f61c-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f61c-118">Примечания</span><span class="sxs-lookup"><span data-stu-id="2f61c-118">Remarks</span></span>  
 <span data-ttu-id="2f61c-119">`IsChild` Возвращает метод `true` Если объект кадра, для которого вызван метод является потомком другого кадра.</span><span class="sxs-lookup"><span data-stu-id="2f61c-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="2f61c-120">Если это так, используйте [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) метод для проверки, является ли кадр родительской.</span><span class="sxs-lookup"><span data-stu-id="2f61c-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f61c-121">Требования</span><span class="sxs-lookup"><span data-stu-id="2f61c-121">Requirements</span></span>  
 <span data-ttu-id="2f61c-122">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f61c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f61c-123">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f61c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f61c-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f61c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f61c-125">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f61c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f61c-126">См. также</span><span class="sxs-lookup"><span data-stu-id="2f61c-126">See also</span></span>

- [<span data-ttu-id="2f61c-127">Интерфейс ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="2f61c-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="2f61c-128">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="2f61c-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2f61c-129">Отладка</span><span class="sxs-lookup"><span data-stu-id="2f61c-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
