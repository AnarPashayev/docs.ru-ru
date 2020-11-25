---
title: Метод IMetaDataAssemblyImport::FindManifestResourceByName
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
ms.openlocfilehash: 152f62fddee3eaa7fa14e454e6eb7ea2547265ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731583"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="3fa2e-102">Метод IMetaDataAssemblyImport::FindManifestResourceByName</span><span class="sxs-lookup"><span data-stu-id="3fa2e-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>

<span data-ttu-id="3fa2e-103">Возвращает указатель на ресурс манифеста с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="3fa2e-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fa2e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3fa2e-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="3fa2e-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="3fa2e-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="3fa2e-106">[in] Имя ресурса.</span><span class="sxs-lookup"><span data-stu-id="3fa2e-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="3fa2e-107">заполняет Массив, используемый для хранения `mdManifestResource` маркеров метаданных, каждый из которых представляет ресурс манифеста.</span><span class="sxs-lookup"><span data-stu-id="3fa2e-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fa2e-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="3fa2e-108">Remarks</span></span>  

 <span data-ttu-id="3fa2e-109">`FindManifestResourceByName`Метод использует стандартные правила, используемые средой CLR для разрешения ссылок.</span><span class="sxs-lookup"><span data-stu-id="3fa2e-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fa2e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="3fa2e-110">Requirements</span></span>  

 <span data-ttu-id="3fa2e-111">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fa2e-111">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fa2e-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="3fa2e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fa2e-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3fa2e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fa2e-114">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fa2e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa2e-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3fa2e-115">See also</span></span>

- [<span data-ttu-id="3fa2e-116">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="3fa2e-116">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="3fa2e-117">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="3fa2e-117">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
