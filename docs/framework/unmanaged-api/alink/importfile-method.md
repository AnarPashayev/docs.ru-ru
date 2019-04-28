---
title: Метод ImportFile
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e48c6c3179ced167fdc39ae4df859f161727ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753521"
---
# <a name="importfile-method"></a><span data-ttu-id="72774-102">Метод ImportFile</span><span class="sxs-lookup"><span data-stu-id="72774-102">ImportFile Method</span></span>
<span data-ttu-id="72774-103">Импортирует сборок и несвязанных модулей.</span><span class="sxs-lookup"><span data-stu-id="72774-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72774-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="72774-104">Syntax</span></span>  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="72774-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="72774-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="72774-106">Полное имя файла для импорта.</span><span class="sxs-lookup"><span data-stu-id="72774-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="72774-107">Необязательный выходной имя файла, который может использоваться для переименования файла, так как он связан в сборку.</span><span class="sxs-lookup"><span data-stu-id="72774-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="72774-108">Если значение равно TRUE, используется ImportTypes, в противном случае импорт должен выполняться вручную.</span><span class="sxs-lookup"><span data-stu-id="72774-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="72774-109">Указатель на маркер, где будет храниться уникальный идентификатор файла.</span><span class="sxs-lookup"><span data-stu-id="72774-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="72774-110">Файл может быть сборки или файла.</span><span class="sxs-lookup"><span data-stu-id="72774-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="72774-111">Получает указатель на [интерфейс IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="72774-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="72774-112">Может иметь значение NULL, если файл не является сборкой.</span><span class="sxs-lookup"><span data-stu-id="72774-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="72774-113">Указатель на количество файлов и/или области, которые были импортированы.</span><span class="sxs-lookup"><span data-stu-id="72774-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72774-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="72774-114">Return Value</span></span>  
 <span data-ttu-id="72774-115">Возвращает S_OK, если метод выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="72774-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72774-116">Требования</span><span class="sxs-lookup"><span data-stu-id="72774-116">Requirements</span></span>  
 <span data-ttu-id="72774-117">Требуется alink.h</span><span class="sxs-lookup"><span data-stu-id="72774-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72774-118">См. также</span><span class="sxs-lookup"><span data-stu-id="72774-118">See also</span></span>

- [<span data-ttu-id="72774-119">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="72774-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="72774-120">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="72774-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="72774-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="72774-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
