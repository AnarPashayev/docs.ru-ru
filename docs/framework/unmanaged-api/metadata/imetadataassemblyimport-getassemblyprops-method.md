---
title: Метод IMetaDataAssemblyImport::GetAssemblyProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec04588bd1cc21e585d89c734c152a86fb835b15
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772731"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="5ecab-102">Метод IMetaDataAssemblyImport::GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="5ecab-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="5ecab-103">Получает набор свойств для сборки с заданной подписью метаданных.</span><span class="sxs-lookup"><span data-stu-id="5ecab-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ecab-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5ecab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ecab-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="5ecab-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="5ecab-106">[in].</span><span class="sxs-lookup"><span data-stu-id="5ecab-106">[in].</span></span> <span data-ttu-id="5ecab-107">`mdAssembly` Токен метаданных, представляющий сборку, для которого нужно получить свойства.</span><span class="sxs-lookup"><span data-stu-id="5ecab-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="5ecab-108">[out] Указатель на открытый ключ или токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="5ecab-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="5ecab-109">[out] Число байтов в возвращаемый открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="5ecab-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="5ecab-110">[out] Указатель на алгоритм, используемый для хэширования файлов в сборке.</span><span class="sxs-lookup"><span data-stu-id="5ecab-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="5ecab-111">[out] Простое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="5ecab-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5ecab-112">[in] Размер, в расширенных символах из `szName`.</span><span class="sxs-lookup"><span data-stu-id="5ecab-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5ecab-113">[out] Число расширенных символов, фактически возвращенных в `szName`.</span><span class="sxs-lookup"><span data-stu-id="5ecab-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="5ecab-114">[out] Указатель на структуру ASSEMBLYMETADATA, которая содержит метаданные сборки.</span><span class="sxs-lookup"><span data-stu-id="5ecab-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="5ecab-115">[out] Флаги, описывающие метаданные, применяемые к сборке.</span><span class="sxs-lookup"><span data-stu-id="5ecab-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="5ecab-116">Это значение представляет собой сочетание одного или нескольких [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) значения.</span><span class="sxs-lookup"><span data-stu-id="5ecab-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ecab-117">Требования</span><span class="sxs-lookup"><span data-stu-id="5ecab-117">Requirements</span></span>  
 <span data-ttu-id="5ecab-118">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ecab-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ecab-119">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5ecab-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ecab-120">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5ecab-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ecab-121">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ecab-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ecab-122">См. также</span><span class="sxs-lookup"><span data-stu-id="5ecab-122">See also</span></span>

- [<span data-ttu-id="5ecab-123">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="5ecab-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
