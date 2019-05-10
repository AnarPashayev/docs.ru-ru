---
title: Метод ICorDebugProcess5::EnumerateHandles
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6552bde30bf3363f1a5a25788fba99e473975c7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616256"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="45076-102">Метод ICorDebugProcess5::EnumerateHandles</span><span class="sxs-lookup"><span data-stu-id="45076-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="45076-103">Возвращает перечислитель для дескрипторов объектов в процессе.</span><span class="sxs-lookup"><span data-stu-id="45076-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45076-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="45076-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45076-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="45076-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="45076-106">[in] Побитовое сочетание [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) значений, определяющих тип маркеры, чтобы включить в коллекцию.</span><span class="sxs-lookup"><span data-stu-id="45076-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="45076-107">[out] Указатель на адрес [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) то есть перечислитель для объектов мусора.</span><span class="sxs-lookup"><span data-stu-id="45076-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45076-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="45076-108">Remarks</span></span>  
 <span data-ttu-id="45076-109">`EnumerateHandles` — это вспомогательная функция, которая поддерживает проверку таблицы дескрипторов.</span><span class="sxs-lookup"><span data-stu-id="45076-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="45076-110">Это похоже на [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) метода, за исключением случаев, вместо того чтобы заполнение [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) коллекции со всеми объектами, чтобы участвовать в сборе мусора, его включает только те объекты, с дескрипторами из таблицы дескрипторов.</span><span class="sxs-lookup"><span data-stu-id="45076-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="45076-111">`types` Параметр указывает типы дескрипторов для включения в коллекции.</span><span class="sxs-lookup"><span data-stu-id="45076-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="45076-112">`types` может принимать любое из следующих трех членов [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) перечисления:</span><span class="sxs-lookup"><span data-stu-id="45076-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="45076-113">`CorHandleStrongOnly` (маркеры только строгих ссылок.)</span><span class="sxs-lookup"><span data-stu-id="45076-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="45076-114">`CorHandleWeakOnly` (маркеры только слабые ссылки.)</span><span class="sxs-lookup"><span data-stu-id="45076-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="45076-115">`CorHandleAll` (все дескрипторы).</span><span class="sxs-lookup"><span data-stu-id="45076-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45076-116">Требования</span><span class="sxs-lookup"><span data-stu-id="45076-116">Requirements</span></span>  
 <span data-ttu-id="45076-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45076-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45076-118">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45076-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45076-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45076-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45076-120">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45076-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45076-121">См. также</span><span class="sxs-lookup"><span data-stu-id="45076-121">See also</span></span>

- [<span data-ttu-id="45076-122">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="45076-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="45076-123">Отладка</span><span class="sxs-lookup"><span data-stu-id="45076-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
