---
title: Метод IMetaDataEmit::SetClassLayout
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: a18583ce807ffa672811f3a0cd1e744233f6eb30
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008837"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="a75ad-102">Метод IMetaDataEmit::SetClassLayout</span><span class="sxs-lookup"><span data-stu-id="a75ad-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="a75ad-103">Завершает компоновку полей для класса, который был определен при предыдущем вызове [метода дефинетипедеф](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="a75ad-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a75ad-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a75ad-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a75ad-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="a75ad-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a75ad-106">окне `mdTypeDef`Токен, указывающий класс для размещения.</span><span class="sxs-lookup"><span data-stu-id="a75ad-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="a75ad-107">окне Размер упаковки: 1, 2, 4, 8 или 16 байт.</span><span class="sxs-lookup"><span data-stu-id="a75ad-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="a75ad-108">Размер упаковки — это число байтов между смежными полями.</span><span class="sxs-lookup"><span data-stu-id="a75ad-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="a75ad-109">окне Массив структур [COR_FIELD_OFFSET](cor-field-offset-structure.md) , каждый из которых задает поле класса и смещение поля в пределах класса.</span><span class="sxs-lookup"><span data-stu-id="a75ad-109">[in] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="a75ad-110">Завершите массив с помощью `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="a75ad-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="a75ad-111">окне Размер класса в байтах.</span><span class="sxs-lookup"><span data-stu-id="a75ad-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a75ad-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="a75ad-112">Remarks</span></span>  
 <span data-ttu-id="a75ad-113">Класс изначально определяется путем вызова метода [IMetaDataEmit::D ефинетипедеф](imetadataemit-definetypedef-method.md) и указания одного из трех макетов для полей класса: Automatic, последовательный или явный.</span><span class="sxs-lookup"><span data-stu-id="a75ad-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="a75ad-114">Как правило, вы используете автоматическую разметку и позволяете среде выполнения выбрать лучший способ размещения полей.</span><span class="sxs-lookup"><span data-stu-id="a75ad-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="a75ad-115">Однако может потребоваться, чтобы поля были размещены в соответствии с расположением, используемым неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="a75ad-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="a75ad-116">В этом случае выберите последовательный или явный макет и вызов `SetClassLayout` , чтобы завершить компоновку полей:</span><span class="sxs-lookup"><span data-stu-id="a75ad-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="a75ad-117">Последовательный макет: укажите размер упаковки.</span><span class="sxs-lookup"><span data-stu-id="a75ad-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="a75ad-118">Поле выстраивается в соответствии с его естественным размером или упаковочным размером, в зависимости от того, что приводит к уменьшению смещения поля.</span><span class="sxs-lookup"><span data-stu-id="a75ad-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="a75ad-119">Задайте `rFieldOffsets` и `ulClassSize` равным нулю.</span><span class="sxs-lookup"><span data-stu-id="a75ad-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="a75ad-120">Явный макет. либо укажите смещение каждого поля, либо укажите размер класса и размер упаковки.</span><span class="sxs-lookup"><span data-stu-id="a75ad-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a75ad-121">Требования</span><span class="sxs-lookup"><span data-stu-id="a75ad-121">Requirements</span></span>  
 <span data-ttu-id="a75ad-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a75ad-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a75ad-123">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a75ad-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a75ad-124">**Библиотека:** Используется в качестве ресурса в MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a75ad-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a75ad-125">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a75ad-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75ad-126">См. также статью</span><span class="sxs-lookup"><span data-stu-id="a75ad-126">See also</span></span>

- [<span data-ttu-id="a75ad-127">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a75ad-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a75ad-128">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a75ad-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
