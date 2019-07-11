---
title: Метод IMetaDataAssemblyImport::GetExportedTypeProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8dd1daf3528bbc642033e254a809c18c3662ff1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779186"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="74693-102">Метод IMetaDataAssemblyImport::GetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="74693-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="74693-103">Получает набор свойств экспортируемого типа с заданной подписью метаданных.</span><span class="sxs-lookup"><span data-stu-id="74693-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74693-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="74693-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74693-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="74693-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="74693-106">[in] `mdExportedType` Маркер метаданных, представляющий экспортированный тип.</span><span class="sxs-lookup"><span data-stu-id="74693-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="74693-107">[out] Имя экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="74693-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="74693-108">[in] Размер в расширенные символы из `szName`.</span><span class="sxs-lookup"><span data-stu-id="74693-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="74693-109">[out] Число расширенных символов, фактически возвращенных в `szName`</span><span class="sxs-lookup"><span data-stu-id="74693-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="74693-110">[out] `mdFile`, `mdAssemblyRef`, Или `mdExportedType` токен метаданных, который содержит или разрешает доступ к свойствам экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="74693-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="74693-111">[out] Указатель на `mdTypeDef` токен, представляющий тип в файле.</span><span class="sxs-lookup"><span data-stu-id="74693-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="74693-112">[out] Указатель на флаги, описывающие метаданные, применяемые к экспортированный тип.</span><span class="sxs-lookup"><span data-stu-id="74693-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="74693-113">Флаги значение может быть один или несколько [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) значения.</span><span class="sxs-lookup"><span data-stu-id="74693-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74693-114">Требования</span><span class="sxs-lookup"><span data-stu-id="74693-114">Requirements</span></span>  
 <span data-ttu-id="74693-115">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74693-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74693-116">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74693-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74693-117">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74693-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74693-118">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74693-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74693-119">См. также</span><span class="sxs-lookup"><span data-stu-id="74693-119">See also</span></span>

- [<span data-ttu-id="74693-120">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="74693-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
