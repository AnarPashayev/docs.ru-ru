---
title: Метод IMetaDataEmit::SetPinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a6fd0a9ae798fa5071d9b4b9fac1f8b3c759a20
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750873"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="07f22-102">Метод IMetaDataEmit::SetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="07f22-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="07f22-103">Задает или изменяет функции сигнатуры метода PInvoke, в соответствии с определением предыдущего вызова [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span><span class="sxs-lookup"><span data-stu-id="07f22-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07f22-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07f22-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07f22-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="07f22-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="07f22-106">[in] `mdToken` Какие сопоставление информация относится.</span><span class="sxs-lookup"><span data-stu-id="07f22-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="07f22-107">[in] Флаги, используемые PInvoke для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="07f22-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="07f22-108">Это битовая маска `CorPinvokeMap` значения.</span><span class="sxs-lookup"><span data-stu-id="07f22-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="07f22-109">[in] Имя целевого объекта экспорта в неуправляемой библиотеке DLL.</span><span class="sxs-lookup"><span data-stu-id="07f22-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="07f22-110">[in] `mdModuleRef` Маркеров для целевого объекта неуправляемые библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="07f22-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07f22-111">Требования</span><span class="sxs-lookup"><span data-stu-id="07f22-111">Requirements</span></span>  
 <span data-ttu-id="07f22-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07f22-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07f22-113">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="07f22-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07f22-114">**Библиотека:** Используется как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07f22-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07f22-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07f22-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f22-116">См. также</span><span class="sxs-lookup"><span data-stu-id="07f22-116">See also</span></span>

- [<span data-ttu-id="07f22-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="07f22-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="07f22-118">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="07f22-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
