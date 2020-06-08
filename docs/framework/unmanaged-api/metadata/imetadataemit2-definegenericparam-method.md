---
title: Метод IMetaDataEmit2::DefineGenericParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: e4401ea8a70e7ace8d8efc5e0a6d29f6db51b3df
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503818"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="ebb88-102">Метод IMetaDataEmit2::DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="ebb88-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="ebb88-103">Создает определение для параметра универсального типа и получает маркер для этого параметра универсального типа.</span><span class="sxs-lookup"><span data-stu-id="ebb88-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebb88-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ebb88-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebb88-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="ebb88-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ebb88-106">окне `mdTypeDef`Токен или `mdMethodDef` , представляющий метод или конструктор, для которого необходимо определить универсальный параметр.</span><span class="sxs-lookup"><span data-stu-id="ebb88-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="ebb88-107">окне Индекс универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="ebb88-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="ebb88-108">окне Значение перечисления [корженерикпараматтр](corgenericparamattr-enumeration.md) , описывающее тип универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="ebb88-108">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="ebb88-109">окне Имя параметра.</span><span class="sxs-lookup"><span data-stu-id="ebb88-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="ebb88-110">окне Этот параметр зарезервирован для расширения в будущем.</span><span class="sxs-lookup"><span data-stu-id="ebb88-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="ebb88-111">окне Массив ограничений типа, заканчивающийся нулем.</span><span class="sxs-lookup"><span data-stu-id="ebb88-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="ebb88-112">Элементы массива должны быть `mdTypeDef` `mdTypeRef` `mdTypeSpec` маркером метаданных, или.</span><span class="sxs-lookup"><span data-stu-id="ebb88-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="ebb88-113">заполняет Токен, представляющий универсальный параметр.</span><span class="sxs-lookup"><span data-stu-id="ebb88-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebb88-114">Требования</span><span class="sxs-lookup"><span data-stu-id="ebb88-114">Requirements</span></span>  
 <span data-ttu-id="ebb88-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebb88-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebb88-116">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="ebb88-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ebb88-117">**Библиотека:** Используется в качестве ресурса в MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ebb88-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ebb88-118">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebb88-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb88-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ebb88-119">See also</span></span>

- [<span data-ttu-id="ebb88-120">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ebb88-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="ebb88-121">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ebb88-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
