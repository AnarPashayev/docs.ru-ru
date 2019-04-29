---
title: Интерфейс ICorDebugArrayValue
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67fd1a9174b04e42b53f2b866a1dfdd504362aa9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645621"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="c96ca-102">Интерфейс ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="c96ca-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="c96ca-103">Подкласс ICorDebugHeapValue, который представляет одномерный или многомерный массив.</span><span class="sxs-lookup"><span data-stu-id="c96ca-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c96ca-104">Методы</span><span class="sxs-lookup"><span data-stu-id="c96ca-104">Methods</span></span>  
  
|<span data-ttu-id="c96ca-105">Метод</span><span class="sxs-lookup"><span data-stu-id="c96ca-105">Method</span></span>|<span data-ttu-id="c96ca-106">Описание</span><span class="sxs-lookup"><span data-stu-id="c96ca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c96ca-107">Метод GetBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="c96ca-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="c96ca-108">Получает базовый индекс каждого измерения в массиве.</span><span class="sxs-lookup"><span data-stu-id="c96ca-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="c96ca-109">Метод GetCount</span><span class="sxs-lookup"><span data-stu-id="c96ca-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="c96ca-110">Получает общее число элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="c96ca-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="c96ca-111">Метод GetDimensions</span><span class="sxs-lookup"><span data-stu-id="c96ca-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="c96ca-112">Возвращает размерность массива.</span><span class="sxs-lookup"><span data-stu-id="c96ca-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="c96ca-113">Метод GetElement</span><span class="sxs-lookup"><span data-stu-id="c96ca-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="c96ca-114">Получает значение, представляющее данный элемент в массиве.</span><span class="sxs-lookup"><span data-stu-id="c96ca-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="c96ca-115">Метод GetElementAtPosition</span><span class="sxs-lookup"><span data-stu-id="c96ca-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="c96ca-116">Получает элемент в заданной позиции, обработка массива в виде — отсчитываемый от нуля одномерный массив.</span><span class="sxs-lookup"><span data-stu-id="c96ca-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="c96ca-117">Метод GetElementType</span><span class="sxs-lookup"><span data-stu-id="c96ca-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="c96ca-118">Получает простой тип элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="c96ca-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="c96ca-119">Метод GetRank</span><span class="sxs-lookup"><span data-stu-id="c96ca-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="c96ca-120">Получает число измерений в массиве.</span><span class="sxs-lookup"><span data-stu-id="c96ca-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="c96ca-121">Метод HasBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="c96ca-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="c96ca-122">Определяет, имеет ли массив базовые индексы.</span><span class="sxs-lookup"><span data-stu-id="c96ca-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c96ca-123">Примечания</span><span class="sxs-lookup"><span data-stu-id="c96ca-123">Remarks</span></span>  
 <span data-ttu-id="c96ca-124">`ICorDebugArrayValue` поддерживает одномерных и многомерных массивов.</span><span class="sxs-lookup"><span data-stu-id="c96ca-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c96ca-125">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="c96ca-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c96ca-126">Требования</span><span class="sxs-lookup"><span data-stu-id="c96ca-126">Requirements</span></span>  
 <span data-ttu-id="c96ca-127">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c96ca-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c96ca-128">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c96ca-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c96ca-129">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c96ca-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c96ca-130">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c96ca-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96ca-131">См. также</span><span class="sxs-lookup"><span data-stu-id="c96ca-131">See also</span></span>

- [<span data-ttu-id="c96ca-132">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c96ca-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
