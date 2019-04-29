---
title: Метод IMetaDataImport::EnumUserStrings
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4be12e46851b11a5e6db60c351094a356fa61f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777933"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="2b3e2-102">Метод IMetaDataImport::EnumUserStrings</span><span class="sxs-lookup"><span data-stu-id="2b3e2-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="2b3e2-103">Перечисляет токены String, представляющие жестко заданные строки в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b3e2-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2b3e2-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b3e2-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="2b3e2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2b3e2-106">[in, out] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2b3e2-107">Это должно быть NULL при первом вызове этого метода.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="2b3e2-108">[out] Массив, используемый для хранения токенов строк.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2b3e2-109">[in] Максимальный размер массива `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="2b3e2-110">[out] Число токенов строк, возвращаемых в `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b3e2-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2b3e2-111">Return Value</span></span>  
  
|<span data-ttu-id="2b3e2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b3e2-112">HRESULT</span></span>|<span data-ttu-id="2b3e2-113">Описание</span><span class="sxs-lookup"><span data-stu-id="2b3e2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2b3e2-114">`EnumUserStrings` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2b3e2-115">Существуют маркеры для перечисления отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2b3e2-116">В этом случае `pcStrings` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b3e2-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="2b3e2-117">Remarks</span></span>  
 <span data-ttu-id="2b3e2-118">Токены строки, создаваемые [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="2b3e2-119">Этот метод предназначен для использования в обозревателе метаданных, а не с помощью компилятора.</span><span class="sxs-lookup"><span data-stu-id="2b3e2-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b3e2-120">Требования</span><span class="sxs-lookup"><span data-stu-id="2b3e2-120">Requirements</span></span>  
 <span data-ttu-id="2b3e2-121">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b3e2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b3e2-122">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2b3e2-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b3e2-123">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b3e2-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b3e2-124">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b3e2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b3e2-125">См. также</span><span class="sxs-lookup"><span data-stu-id="2b3e2-125">See also</span></span>

- [<span data-ttu-id="2b3e2-126">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="2b3e2-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2b3e2-127">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="2b3e2-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
