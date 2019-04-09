---
title: Метод IMetaDataAssemblyEmit::DefineFile
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5693da3b5e6d883efd9ad8a5a409a5dba8dd8b6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203435"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="8e3b8-102">Метод IMetaDataAssemblyEmit::DefineFile</span><span class="sxs-lookup"><span data-stu-id="8e3b8-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="8e3b8-103">Создает структуру метаданных `File`, содержащую метаданные для сборки, на которую ссылается данная сборка, и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="8e3b8-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e3b8-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8e3b8-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e3b8-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="8e3b8-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="8e3b8-106">[in] Имя файла для использования.</span><span class="sxs-lookup"><span data-stu-id="8e3b8-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="8e3b8-107">[in] Указатель на данные хэша, связанные со сборкой.</span><span class="sxs-lookup"><span data-stu-id="8e3b8-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="8e3b8-108">[in] Размер в байтах `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="8e3b8-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="8e3b8-109">[in] Побитовое сочетание `FileFlags` значения, которые определяют параметры свойств.</span><span class="sxs-lookup"><span data-stu-id="8e3b8-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="8e3b8-110">[out] Указатель на возвращенный `File` токена.</span><span class="sxs-lookup"><span data-stu-id="8e3b8-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e3b8-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="8e3b8-111">Remarks</span></span>  
 <span data-ttu-id="8e3b8-112">Один `File` структура метаданных должны быть определены для каждого файла, который был частью этой сборки во время построения, за исключением файла, содержащего метаданные.</span><span class="sxs-lookup"><span data-stu-id="8e3b8-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e3b8-113">Требования</span><span class="sxs-lookup"><span data-stu-id="8e3b8-113">Requirements</span></span>  
 <span data-ttu-id="8e3b8-114">**Платформа:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e3b8-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e3b8-115">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8e3b8-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e3b8-116">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8e3b8-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="8e3b8-117">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="8e3b8-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e3b8-118">См. также</span><span class="sxs-lookup"><span data-stu-id="8e3b8-118">See also</span></span>

- [<span data-ttu-id="8e3b8-119">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="8e3b8-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
