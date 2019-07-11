---
title: Метод IMetaDataImport::EnumSignatures
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58fa2a6d34f1f3627378c1355a1a292b665899ee
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756409"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="4fb0d-102">Метод IMetaDataImport::EnumSignatures</span><span class="sxs-lookup"><span data-stu-id="4fb0d-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="4fb0d-103">Перечисляет токены Signature, представляющие отдельные подписи в текущей области.</span><span class="sxs-lookup"><span data-stu-id="4fb0d-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fb0d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4fb0d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fb0d-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4fb0d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4fb0d-106">[in, out] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="4fb0d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4fb0d-107">Это должно быть NULL при первом вызове этого метода.</span><span class="sxs-lookup"><span data-stu-id="4fb0d-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="4fb0d-108">[out] Массив, используемый для хранения токенов подписи.</span><span class="sxs-lookup"><span data-stu-id="4fb0d-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4fb0d-109">[in] Максимальный размер массива `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="4fb0d-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="4fb0d-110">[out] Количество подписи токенов, возвращаемых в `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="4fb0d-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fb0d-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4fb0d-111">Return Value</span></span>  
  
|<span data-ttu-id="4fb0d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4fb0d-112">HRESULT</span></span>|<span data-ttu-id="4fb0d-113">Описание</span><span class="sxs-lookup"><span data-stu-id="4fb0d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4fb0d-114">`EnumSignatures` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="4fb0d-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4fb0d-115">Существуют маркеры для перечисления отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="4fb0d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="4fb0d-116">В этом случае `pcSignatures` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="4fb0d-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fb0d-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="4fb0d-117">Remarks</span></span>  
 <span data-ttu-id="4fb0d-118">Маркеры подписи, создаваемые [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="4fb0d-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fb0d-119">Требования</span><span class="sxs-lookup"><span data-stu-id="4fb0d-119">Requirements</span></span>  
 <span data-ttu-id="4fb0d-120">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fb0d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fb0d-121">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4fb0d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fb0d-122">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4fb0d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4fb0d-123">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fb0d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fb0d-124">См. также</span><span class="sxs-lookup"><span data-stu-id="4fb0d-124">See also</span></span>

- [<span data-ttu-id="4fb0d-125">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4fb0d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4fb0d-126">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4fb0d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
