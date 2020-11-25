---
title: Метод IMetaDataImport::CountEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: f2470cd7112adff35ef49c21a155072fcd4008be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727293"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="99cb0-102">Метод IMetaDataImport::CountEnum</span><span class="sxs-lookup"><span data-stu-id="99cb0-102">IMetaDataImport::CountEnum Method</span></span>

<span data-ttu-id="99cb0-103">Возвращает количество элементов в перечислении, полученных указанным перечислителем.</span><span class="sxs-lookup"><span data-stu-id="99cb0-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99cb0-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="99cb0-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99cb0-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="99cb0-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="99cb0-106">окне Маркер для перечислителя.</span><span class="sxs-lookup"><span data-stu-id="99cb0-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="99cb0-107">заполняет Число перечисленных элементов.</span><span class="sxs-lookup"><span data-stu-id="99cb0-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99cb0-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="99cb0-108">Remarks</span></span>  

 <span data-ttu-id="99cb0-109">Маркер, заданный параметром, `hEnum` получается из предыдущего `Enum` вызова *имени* (например, [IMetaDataImport:: EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="99cb0-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99cb0-110">Требования</span><span class="sxs-lookup"><span data-stu-id="99cb0-110">Requirements</span></span>  

 <span data-ttu-id="99cb0-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99cb0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99cb0-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="99cb0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99cb0-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99cb0-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99cb0-114">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99cb0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cb0-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="99cb0-115">See also</span></span>

- [<span data-ttu-id="99cb0-116">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="99cb0-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="99cb0-117">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="99cb0-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
