---
title: Метод ICorDebugILCode::GetEHClauses
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e890629f307e3d3cff11dabdb2db90a5e88ece5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995557"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="eefb8-102">Метод ICorDebugILCode::GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="eefb8-102">ICorDebugILCode::GetEHClauses Method</span></span>
<span data-ttu-id="eefb8-103">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="eefb8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="eefb8-104">Возвращает указатель на список предложений обработки исключений, определенных для этого промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="eefb8-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eefb8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eefb8-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eefb8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="eefb8-106">Parameters</span></span>  
 `cClauses`  
 <span data-ttu-id="eefb8-107">[в] Емкость хранилища массива `clauses`.</span><span class="sxs-lookup"><span data-stu-id="eefb8-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="eefb8-108">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="eefb8-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="eefb8-109">[из] Количество предложений, информация о которых записывается в массив `clauses`.</span><span class="sxs-lookup"><span data-stu-id="eefb8-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="eefb8-110">предложения</span><span class="sxs-lookup"><span data-stu-id="eefb8-110">clauses</span></span>  
 <span data-ttu-id="eefb8-111">[out] Массив [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) объектов, содержащих сведения о предложениях, определенных для этого Промежуточного обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="eefb8-111">[out] An array of [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eefb8-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="eefb8-112">Remarks</span></span>  
 <span data-ttu-id="eefb8-113">Если `cClauses` равно 0 и `pcClauses` отличается от**null**, `pcClauses` присваивается количество доступных предложений обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="eefb8-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="eefb8-114">Если значение `cClauses` не равно 0, оно обозначает емкость хранилища массива `clauses`.</span><span class="sxs-lookup"><span data-stu-id="eefb8-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="eefb8-115">Когда метод возвращает не пустое значение, `clauses` содержит максимум элементов `cClauses`, а значению `pcClauses` присваивается количество предложений, записанных в массив `clauses` на данный момент.</span><span class="sxs-lookup"><span data-stu-id="eefb8-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eefb8-116">Требования</span><span class="sxs-lookup"><span data-stu-id="eefb8-116">Requirements</span></span>  
 <span data-ttu-id="eefb8-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eefb8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eefb8-118">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eefb8-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eefb8-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eefb8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eefb8-120">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eefb8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eefb8-121">См. также</span><span class="sxs-lookup"><span data-stu-id="eefb8-121">See also</span></span>

- [<span data-ttu-id="eefb8-122">Интерфейс ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="eefb8-122">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="eefb8-123">Структура CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="eefb8-123">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [<span data-ttu-id="eefb8-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="eefb8-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
