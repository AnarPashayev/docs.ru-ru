---
title: Метод IMetaDataImport::ResetEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa5a446ba7bfd70330601c7cbc129800761cdb7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782620"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="db1bb-102">Метод IMetaDataImport::ResetEnum</span><span class="sxs-lookup"><span data-stu-id="db1bb-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="db1bb-103">Возвращает заданный перечислитель в указанную позицию.</span><span class="sxs-lookup"><span data-stu-id="db1bb-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db1bb-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="db1bb-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db1bb-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="db1bb-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="db1bb-106">[in] Перечислитель для сброса.</span><span class="sxs-lookup"><span data-stu-id="db1bb-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="db1bb-107">[in] Новое положение, по которому следует вставить перечислитель.</span><span class="sxs-lookup"><span data-stu-id="db1bb-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db1bb-108">Требования</span><span class="sxs-lookup"><span data-stu-id="db1bb-108">Requirements</span></span>  
 <span data-ttu-id="db1bb-109">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db1bb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db1bb-110">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db1bb-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db1bb-111">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db1bb-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db1bb-112">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db1bb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db1bb-113">См. также</span><span class="sxs-lookup"><span data-stu-id="db1bb-113">See also</span></span>

- [<span data-ttu-id="db1bb-114">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="db1bb-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="db1bb-115">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="db1bb-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
