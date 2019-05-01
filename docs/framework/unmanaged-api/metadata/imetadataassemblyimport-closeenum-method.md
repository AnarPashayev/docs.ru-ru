---
title: Метод IMetaDataAssemblyImport::CloseEnum
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::CloseEnum
helpviewer_keywords:
- CloseEnum method, IMetaDataAssemblyImport interface [.NET Framework metadata]
- IMetaDataAssemblyImport::CloseEnum method [.NET Framework metadata]
ms.assetid: c9df4087-12b3-46d9-b075-9067dd7805df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cc0a4f52747cbc88a26f4b9aaff6642b6c1d62f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044713"
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="ab2d7-102">Метод IMetaDataAssemblyImport::CloseEnum</span><span class="sxs-lookup"><span data-stu-id="ab2d7-102">IMetaDataAssemblyImport::CloseEnum Method</span></span>
<span data-ttu-id="ab2d7-103">Освобождает ссылку на экземпляр указанного перечисления.</span><span class="sxs-lookup"><span data-stu-id="ab2d7-103">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab2d7-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ab2d7-104">Syntax</span></span>  
  
```  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab2d7-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="ab2d7-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ab2d7-106">[in] Экземпляр перечисления, будет закрыта.</span><span class="sxs-lookup"><span data-stu-id="ab2d7-106">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab2d7-107">Требования</span><span class="sxs-lookup"><span data-stu-id="ab2d7-107">Requirements</span></span>  
 <span data-ttu-id="ab2d7-108">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab2d7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab2d7-109">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab2d7-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab2d7-110">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab2d7-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab2d7-111">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab2d7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab2d7-112">См. также</span><span class="sxs-lookup"><span data-stu-id="ab2d7-112">See also</span></span>

- [<span data-ttu-id="ab2d7-113">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="ab2d7-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
