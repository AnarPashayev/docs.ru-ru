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
ms.openlocfilehash: 28c0aa37bdcae2a09a4d53f920efd3ffe7117bd3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145175"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="f87b3-102">Метод IMetaDataEmit::SetMethodImplFlags</span><span class="sxs-lookup"><span data-stu-id="f87b3-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="f87b3-103">Задает или обновляет подпись метаданных реализации унаследованного метода, на который ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="f87b3-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f87b3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f87b3-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f87b3-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="f87b3-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="f87b3-106">[in] Токен, метод должен быть изменен.</span><span class="sxs-lookup"><span data-stu-id="f87b3-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="f87b3-107">[in] Сочетание значений [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) перечисления, которое указывает возможности реализации метода.</span><span class="sxs-lookup"><span data-stu-id="f87b3-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f87b3-108">Требования</span><span class="sxs-lookup"><span data-stu-id="f87b3-108">Requirements</span></span>  
 <span data-ttu-id="f87b3-109">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f87b3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f87b3-110">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f87b3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f87b3-111">**Библиотека:** Используется как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f87b3-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f87b3-112">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f87b3-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f87b3-113">См. также</span><span class="sxs-lookup"><span data-stu-id="f87b3-113">See also</span></span>

- [<span data-ttu-id="f87b3-114">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f87b3-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f87b3-115">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f87b3-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
