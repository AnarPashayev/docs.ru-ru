---
title: Метод ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
ms.openlocfilehash: 62aad8339b34a4831211a45bd645906d73393d25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727150"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="6765e-102">Метод ICorProfilerInfo2::GetClassFromTokenAndTypeArgs</span><span class="sxs-lookup"><span data-stu-id="6765e-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>

<span data-ttu-id="6765e-103">Возвращает объект `ClassID` типа, используя указанный токен метаданных и `ClassID` значения любых аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="6765e-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6765e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6765e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6765e-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="6765e-105">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="6765e-106">окне Идентификатор модуля, в котором находится тип.</span><span class="sxs-lookup"><span data-stu-id="6765e-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="6765e-107">окне `mdTypeDef` Токен метаданных, ссылающийся на тип.</span><span class="sxs-lookup"><span data-stu-id="6765e-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="6765e-108">окне Число параметров типа для данного типа.</span><span class="sxs-lookup"><span data-stu-id="6765e-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="6765e-109">Для типов, не являющихся универсальными, это значение должно быть равно нулю.</span><span class="sxs-lookup"><span data-stu-id="6765e-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="6765e-110">окне Массив `ClassID` значений, каждый из которых является аргументом типа.</span><span class="sxs-lookup"><span data-stu-id="6765e-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="6765e-111">Значение `typeArgs` может быть равно null, если `cTypeArgs` имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="6765e-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="6765e-112">заполняет Указатель на объект `ClassID` указанного типа.</span><span class="sxs-lookup"><span data-stu-id="6765e-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6765e-113">Комментарии</span><span class="sxs-lookup"><span data-stu-id="6765e-113">Remarks</span></span>  

 <span data-ttu-id="6765e-114">Вызов `GetClassFromTokenAndTypeArgs` метода с помощью `mdTypeRef` вместо `mdTypeDef` токена метаданных может иметь непредсказуемые результаты; вызывающие объекты должны разрешить объект `mdTypeRef` в `mdTypeDef` при передаче.</span><span class="sxs-lookup"><span data-stu-id="6765e-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="6765e-115">Если тип еще не загружен, вызов инициирует `GetClassFromTokenAndTypeArgs` загрузку, что является опасной операцией во многих контекстах.</span><span class="sxs-lookup"><span data-stu-id="6765e-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="6765e-116">Например, вызов этого метода во время загрузки модулей или других типов может привести к бесконечному циклу, так как среда выполнения пытается циклически загружать вещи.</span><span class="sxs-lookup"><span data-stu-id="6765e-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="6765e-117">Как правило, использование параметра `GetClassFromTokenAndTypeArgs` не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="6765e-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="6765e-118">Если профилировщики заинтересованы в событиях для определенного типа, они должны хранить и для `ModuleID` `mdTypeDef` этого типа, а также использовать [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) для проверки того `ClassID` , относится ли данный тип к требуемому типу.</span><span class="sxs-lookup"><span data-stu-id="6765e-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6765e-119">Требования</span><span class="sxs-lookup"><span data-stu-id="6765e-119">Requirements</span></span>  

 <span data-ttu-id="6765e-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6765e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6765e-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6765e-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6765e-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6765e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6765e-123">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6765e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6765e-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6765e-124">See also</span></span>

- [<span data-ttu-id="6765e-125">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="6765e-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="6765e-126">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="6765e-126">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
