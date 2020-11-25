---
title: Метод IMetaDataImport::GetPinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
ms.openlocfilehash: c34215f48190e60bd1a851f31b8b23f09491f4e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729243"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="81d99-102">Метод IMetaDataImport::GetPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="81d99-102">IMetaDataImport::GetPinvokeMap Method</span></span>

<span data-ttu-id="81d99-103">Возвращает токен ModuleRef, представляющий целевую сборку вызова PInvoke.</span><span class="sxs-lookup"><span data-stu-id="81d99-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81d99-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="81d99-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81d99-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="81d99-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="81d99-106">окне Токен FieldDef или MethodDef для получения метаданных сопоставления PInvoke для.</span><span class="sxs-lookup"><span data-stu-id="81d99-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="81d99-107">заполняет Указатель на флаги, используемые для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="81d99-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="81d99-108">Это значение является битовой маской из перечисления [CorPinvokeMap](corpinvokemap-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="81d99-108">This value is a bitmask from the [CorPinvokeMap](corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="81d99-109">заполняет Имя неуправляемой целевой библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="81d99-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="81d99-110">окне Размер в расширенных символах `szImportName` .</span><span class="sxs-lookup"><span data-stu-id="81d99-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="81d99-111">заполняет Число расширенных символов, возвращаемых в `szImportName` .</span><span class="sxs-lookup"><span data-stu-id="81d99-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="81d99-112">заполняет Указатель на токен ModuleRef, представляющий неуправляемую библиотеку целевых объектов.</span><span class="sxs-lookup"><span data-stu-id="81d99-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81d99-113">Требования</span><span class="sxs-lookup"><span data-stu-id="81d99-113">Requirements</span></span>  

 <span data-ttu-id="81d99-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81d99-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d99-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="81d99-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81d99-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81d99-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81d99-117">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d99-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d99-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="81d99-118">See also</span></span>

- [<span data-ttu-id="81d99-119">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="81d99-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="81d99-120">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="81d99-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
