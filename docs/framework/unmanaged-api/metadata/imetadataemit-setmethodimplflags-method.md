---
title: Метод IMetaDataEmit::SetMethodImplFlags
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a437ff11114ea8d577b2fc3b81cd981cebb8c8d6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751065"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="af625-102">Метод IMetaDataEmit::SetMethodImplFlags</span><span class="sxs-lookup"><span data-stu-id="af625-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="af625-103">Задает или обновляет подпись метаданных реализации унаследованного метода, на который ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="af625-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af625-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="af625-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af625-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="af625-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="af625-106">[in] Токен, метод должен быть изменен.</span><span class="sxs-lookup"><span data-stu-id="af625-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="af625-107">[in] Сочетание значений [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) перечисления, которое указывает возможности реализации метода.</span><span class="sxs-lookup"><span data-stu-id="af625-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af625-108">Требования</span><span class="sxs-lookup"><span data-stu-id="af625-108">Requirements</span></span>  
 <span data-ttu-id="af625-109">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af625-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af625-110">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="af625-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af625-111">**Библиотека:** Используется как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af625-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af625-112">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af625-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af625-113">См. также</span><span class="sxs-lookup"><span data-stu-id="af625-113">See also</span></span>

- [<span data-ttu-id="af625-114">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="af625-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="af625-115">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="af625-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
