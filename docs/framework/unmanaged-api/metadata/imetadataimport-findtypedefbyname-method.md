---
title: Метод IMetaDataImport::FindTypeDefByName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
ms.openlocfilehash: df1516a916b2b48080e4f94937fba063926330ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711303"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="33f04-102">Метод IMetaDataImport::FindTypeDefByName</span><span class="sxs-lookup"><span data-stu-id="33f04-102">IMetaDataImport::FindTypeDefByName Method</span></span>

<span data-ttu-id="33f04-103">Возвращает указатель на маркер метаданных TypeDef для <xref:System.Type> с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="33f04-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33f04-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="33f04-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33f04-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="33f04-105">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="33f04-106">окне Имя типа, для которого требуется получить маркер TypeDef.</span><span class="sxs-lookup"><span data-stu-id="33f04-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="33f04-107">окне Токен TypeDef или TypeRef, представляющий включающий класс.</span><span class="sxs-lookup"><span data-stu-id="33f04-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="33f04-108">Если искомый тип не является вложенным классом, присвойте этому параметру значение NULL.</span><span class="sxs-lookup"><span data-stu-id="33f04-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="33f04-109">заполняет Указатель на соответствующий маркер TypeDef.</span><span class="sxs-lookup"><span data-stu-id="33f04-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33f04-110">Требования</span><span class="sxs-lookup"><span data-stu-id="33f04-110">Requirements</span></span>  

 <span data-ttu-id="33f04-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33f04-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33f04-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="33f04-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33f04-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33f04-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33f04-114">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33f04-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f04-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="33f04-115">See also</span></span>

- [<span data-ttu-id="33f04-116">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="33f04-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="33f04-117">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="33f04-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
