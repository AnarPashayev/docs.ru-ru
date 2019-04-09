---
title: Метод IMetaDataImport::EnumMethodsWithName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f15ee906fb20cb60272cee3deffa68dbe852f689
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200185"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="932cf-102">Метод IMetaDataImport::EnumMethodsWithName</span><span class="sxs-lookup"><span data-stu-id="932cf-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="932cf-103">Перечисляет методы с заданным именем, определяемые по типу, на который ссылается указанный токен TypeDef.</span><span class="sxs-lookup"><span data-stu-id="932cf-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="932cf-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="932cf-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="932cf-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="932cf-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="932cf-106">[in, out] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="932cf-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="932cf-107">Это должно быть NULL при первом вызове этого метода.</span><span class="sxs-lookup"><span data-stu-id="932cf-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="932cf-108">[in] Токен TypeDef, представляющий тип, методы которого для перечисления.</span><span class="sxs-lookup"><span data-stu-id="932cf-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="932cf-109">[in] Имя, которое ограничивает область перечисления.</span><span class="sxs-lookup"><span data-stu-id="932cf-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="932cf-110">[out] Массив, используемый для хранения токенов MethodDef.</span><span class="sxs-lookup"><span data-stu-id="932cf-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="932cf-111">[in] Максимальный размер массива `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="932cf-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="932cf-112">[out] Количество токены MethodDef, возвращаемых в `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="932cf-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="932cf-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="932cf-113">Remarks</span></span>  
 <span data-ttu-id="932cf-114">Этот метод перечисляет поля и методы, но не свойства или события.</span><span class="sxs-lookup"><span data-stu-id="932cf-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="932cf-115">В отличие от [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` отбрасывает все маркеры метод, у которых нет указанного имени.</span><span class="sxs-lookup"><span data-stu-id="932cf-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="932cf-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="932cf-116">Return Value</span></span>  
  
|<span data-ttu-id="932cf-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="932cf-117">HRESULT</span></span>|<span data-ttu-id="932cf-118">Описание</span><span class="sxs-lookup"><span data-stu-id="932cf-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName` <span data-ttu-id="932cf-119">успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="932cf-119">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="932cf-120">Существуют маркеры для перечисления отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="932cf-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="932cf-121">В этом случае `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="932cf-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="932cf-122">Требования</span><span class="sxs-lookup"><span data-stu-id="932cf-122">Requirements</span></span>  
 <span data-ttu-id="932cf-123">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="932cf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="932cf-124">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="932cf-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="932cf-125">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="932cf-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="932cf-126">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="932cf-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="932cf-127">См. также</span><span class="sxs-lookup"><span data-stu-id="932cf-127">See also</span></span>

- [<span data-ttu-id="932cf-128">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="932cf-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="932cf-129">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="932cf-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
