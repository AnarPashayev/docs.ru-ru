---
title: Метод IMetaDataTables::GetGuid
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: f776ac59ff9bd665dc3bfde74e8a8bb0f8acc89e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702463"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="43f4d-102">Метод IMetaDataTables::GetGuid</span><span class="sxs-lookup"><span data-stu-id="43f4d-102">IMetaDataTables::GetGuid Method</span></span>

<span data-ttu-id="43f4d-103">Возвращает идентификатор GUID из строки по указанному индексу.</span><span class="sxs-lookup"><span data-stu-id="43f4d-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f4d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="43f4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43f4d-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="43f4d-105">Parameters</span></span>  

 `ixGuid`  
 <span data-ttu-id="43f4d-106">окне Индекс строки, из которой необходимо получить идентификатор GUID.</span><span class="sxs-lookup"><span data-stu-id="43f4d-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="43f4d-107">заполняет Указатель на указатель на идентификатор GUID.</span><span class="sxs-lookup"><span data-stu-id="43f4d-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43f4d-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="43f4d-108">Remarks</span></span>  

  <span data-ttu-id="43f4d-109">Мы не рекомендуем использовать этот метод, так как он не возвращает последовательные результаты.</span><span class="sxs-lookup"><span data-stu-id="43f4d-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="43f4d-110">Сведения о таблице GUID см. в документации по Common Language Infrastructure (CLI), особенно в разделе "Partition II: определение метаданных и семантика".</span><span class="sxs-lookup"><span data-stu-id="43f4d-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="43f4d-111">Документация доступна в Интернете; см. раздел [ECMA C# and Common Language Infrastructure](../../../standard/components.md#applicable-standards) Standards и [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="43f4d-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43f4d-112">Требования</span><span class="sxs-lookup"><span data-stu-id="43f4d-112">Requirements</span></span>  

 <span data-ttu-id="43f4d-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43f4d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43f4d-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="43f4d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43f4d-115">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43f4d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43f4d-116">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43f4d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f4d-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="43f4d-117">See also</span></span>

- [<span data-ttu-id="43f4d-118">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="43f4d-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="43f4d-119">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="43f4d-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
