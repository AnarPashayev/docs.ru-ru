---
title: Метод IMetaDataAssemblyImport::GetFileProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f3883b0cd1b7aca6265b738eace483c81eb37b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760141"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="e4ba2-102">Метод IMetaDataAssemblyImport::GetFileProps</span><span class="sxs-lookup"><span data-stu-id="e4ba2-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="e4ba2-103">Получает свойства файла с заданной подписью метаданных.</span><span class="sxs-lookup"><span data-stu-id="e4ba2-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ba2-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e4ba2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4ba2-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e4ba2-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="e4ba2-106">[in] `mdFile` Маркер метаданных, представляющий файл, для которого нужно получить свойства.</span><span class="sxs-lookup"><span data-stu-id="e4ba2-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="e4ba2-107">[out] Простое имя файла.</span><span class="sxs-lookup"><span data-stu-id="e4ba2-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e4ba2-108">[in] Размер, в расширенных символах из `szName`.</span><span class="sxs-lookup"><span data-stu-id="e4ba2-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="e4ba2-109">[out] Число расширенных символов, фактически возвращенных в `szName`.</span><span class="sxs-lookup"><span data-stu-id="e4ba2-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="e4ba2-110">[out] Указатель на хэш-значения.</span><span class="sxs-lookup"><span data-stu-id="e4ba2-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="e4ba2-111">Это хэш, с помощью алгоритма SHA-1, файла.</span><span class="sxs-lookup"><span data-stu-id="e4ba2-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="e4ba2-112">[out] Число расширенных символов в возвращенное хэш-значение.</span><span class="sxs-lookup"><span data-stu-id="e4ba2-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="e4ba2-113">[out] Указатель на флаги, описывающие метаданные, применяемые к файлу.</span><span class="sxs-lookup"><span data-stu-id="e4ba2-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="e4ba2-114">Значение флагов представляет собой сочетание одного или нескольких [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) значения.</span><span class="sxs-lookup"><span data-stu-id="e4ba2-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4ba2-115">Требования</span><span class="sxs-lookup"><span data-stu-id="e4ba2-115">Requirements</span></span>  
 <span data-ttu-id="e4ba2-116">**Платформа:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4ba2-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4ba2-117">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e4ba2-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4ba2-118">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4ba2-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4ba2-119">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4ba2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ba2-120">См. также</span><span class="sxs-lookup"><span data-stu-id="e4ba2-120">See also</span></span>

- [<span data-ttu-id="e4ba2-121">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="e4ba2-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
