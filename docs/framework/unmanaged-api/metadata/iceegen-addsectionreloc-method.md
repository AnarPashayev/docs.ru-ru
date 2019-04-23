---
title: Метод ICeeGen::AddSectionReloc
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d50f7488c2b231ea66c12cc4903469d9e2337fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088383"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="297b4-102">Метод ICeeGen::AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="297b4-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="297b4-103">Добавляет инструкцию .reloc базы кода.</span><span class="sxs-lookup"><span data-stu-id="297b4-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="297b4-104">Этот метод является устаревшим и не должны использоваться.</span><span class="sxs-lookup"><span data-stu-id="297b4-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="297b4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="297b4-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="297b4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="297b4-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="297b4-107">[in] Раздел кода в памяти, к которому необходимо добавить инструкцию .reloc.</span><span class="sxs-lookup"><span data-stu-id="297b4-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="297b4-108">[in] Смещение раздела.</span><span class="sxs-lookup"><span data-stu-id="297b4-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="297b4-109">[in] Раздел, к которому `offset` ссылается.</span><span class="sxs-lookup"><span data-stu-id="297b4-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="297b4-110">[in] Один из [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) значений, указывающих на вид .reloc инструкциям, чтобы добавить.</span><span class="sxs-lookup"><span data-stu-id="297b4-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="297b4-111">Требования</span><span class="sxs-lookup"><span data-stu-id="297b4-111">Requirements</span></span>  
 <span data-ttu-id="297b4-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="297b4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="297b4-113">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="297b4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="297b4-114">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="297b4-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="297b4-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="297b4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="297b4-116">См. также</span><span class="sxs-lookup"><span data-stu-id="297b4-116">See also</span></span>

- [<span data-ttu-id="297b4-117">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="297b4-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
