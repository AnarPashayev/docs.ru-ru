---
title: Структура COR_ARRAY_LAYOUT
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
ms.openlocfilehash: 2ca6c89a671c4d7882e7cefdb820d07ac5636530
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727410"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="86e7f-102">Структура COR_ARRAY_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="86e7f-102">COR_ARRAY_LAYOUT Structure</span></span>

<span data-ttu-id="86e7f-103">Предоставляет сведения о расположении объекта массива в памяти.</span><span class="sxs-lookup"><span data-stu-id="86e7f-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e7f-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="86e7f-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;
    ULONG32 rankSize;
    ULONG32 numRanks;
    ULONG32 rankOffset;
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="86e7f-105">Члены</span><span class="sxs-lookup"><span data-stu-id="86e7f-105">Members</span></span>  
  
|<span data-ttu-id="86e7f-106">Член</span><span class="sxs-lookup"><span data-stu-id="86e7f-106">Member</span></span>|<span data-ttu-id="86e7f-107">Описание</span><span class="sxs-lookup"><span data-stu-id="86e7f-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="86e7f-108">Идентификатор типа объектов, содержащихся в массиве.</span><span class="sxs-lookup"><span data-stu-id="86e7f-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="86e7f-109">Значение перечисления Корелементтипе, указывающее, является ли компонент ссылкой для сборки мусора, классом значения или примитивом.</span><span class="sxs-lookup"><span data-stu-id="86e7f-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="86e7f-110">Смещение к первому элементу в массиве.</span><span class="sxs-lookup"><span data-stu-id="86e7f-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="86e7f-111">Размер каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="86e7f-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="86e7f-112">Смещение к числу элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="86e7f-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="86e7f-113">Размер ранга в байтах.</span><span class="sxs-lookup"><span data-stu-id="86e7f-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="86e7f-114">Число рангов в массиве.</span><span class="sxs-lookup"><span data-stu-id="86e7f-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="86e7f-115">Смещение, с которого начинается ранжирование.</span><span class="sxs-lookup"><span data-stu-id="86e7f-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86e7f-116">Комментарии</span><span class="sxs-lookup"><span data-stu-id="86e7f-116">Remarks</span></span>  

 <span data-ttu-id="86e7f-117">`rankSize`Поле задает размер ранга в многомерном массиве.</span><span class="sxs-lookup"><span data-stu-id="86e7f-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="86e7f-118">Точны также для одномерных массивов.</span><span class="sxs-lookup"><span data-stu-id="86e7f-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="86e7f-119">Значение `numRanks` равно 1 для одномерного массива и `N` многомерного массива `N` измерений.</span><span class="sxs-lookup"><span data-stu-id="86e7f-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86e7f-120">Требования</span><span class="sxs-lookup"><span data-stu-id="86e7f-120">Requirements</span></span>  

 <span data-ttu-id="86e7f-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86e7f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86e7f-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86e7f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86e7f-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86e7f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86e7f-124">**.NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86e7f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e7f-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="86e7f-125">See also</span></span>

- [<span data-ttu-id="86e7f-126">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="86e7f-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="86e7f-127">Отладка</span><span class="sxs-lookup"><span data-stu-id="86e7f-127">Debugging</span></span>](index.md)
