---
title: Метод IMetaDataImport::EnumModuleRefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d66d24da05bc3b8f0c3d0a828456d7c61613d219
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188315"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="76821-102">Метод IMetaDataImport::EnumModuleRefs</span><span class="sxs-lookup"><span data-stu-id="76821-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="76821-103">Перечисляет токены ModuleRef, представляющие импортируемые модули.</span><span class="sxs-lookup"><span data-stu-id="76821-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76821-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="76821-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76821-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="76821-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="76821-106">[in, out] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="76821-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="76821-107">Это должно быть NULL при первом вызове этого метода.</span><span class="sxs-lookup"><span data-stu-id="76821-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="76821-108">[out] Массив, используемый для хранения токены ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="76821-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="76821-109">[in] Максимальный размер массива `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="76821-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="76821-110">[out] Количество токены ModuleRef, возвращаемых в `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="76821-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76821-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="76821-111">Return Value</span></span>  
  
|<span data-ttu-id="76821-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76821-112">HRESULT</span></span>|<span data-ttu-id="76821-113">Описание</span><span class="sxs-lookup"><span data-stu-id="76821-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="76821-114">`EnumModuleRefs` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="76821-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="76821-115">Существуют маркеры для перечисления отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="76821-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="76821-116">В этом случае `pcModuleRefs` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="76821-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76821-117">Требования</span><span class="sxs-lookup"><span data-stu-id="76821-117">Requirements</span></span>  
 <span data-ttu-id="76821-118">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76821-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76821-119">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="76821-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76821-120">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="76821-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76821-121">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76821-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76821-122">См. также</span><span class="sxs-lookup"><span data-stu-id="76821-122">See also</span></span>

- [<span data-ttu-id="76821-123">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="76821-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="76821-124">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="76821-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
