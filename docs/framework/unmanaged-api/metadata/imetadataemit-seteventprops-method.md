---
title: Метод IMetaDataEmit::SetEventProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 271ecd7e757340becccb7bf52362487a2b277299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737180"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="211d3-102">Метод IMetaDataEmit::SetEventProps</span><span class="sxs-lookup"><span data-stu-id="211d3-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="211d3-103">Задает или обновляет указанный компонент события, определенного с помощью предыдущего вызова [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="211d3-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="211d3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="211d3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="211d3-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="211d3-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="211d3-106">[in] Токен события.</span><span class="sxs-lookup"><span data-stu-id="211d3-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="211d3-107">[in] Флаги событий.</span><span class="sxs-lookup"><span data-stu-id="211d3-107">[in] Event flags.</span></span> <span data-ttu-id="211d3-108">Это битовая маска `CorEventAttr` значения.</span><span class="sxs-lookup"><span data-stu-id="211d3-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="211d3-109">[in] Токен для класса событий.</span><span class="sxs-lookup"><span data-stu-id="211d3-109">[in] The token for the event class.</span></span> <span data-ttu-id="211d3-110">Это может быть либо `mdTypeDef` или `mdTypeRef` токена.</span><span class="sxs-lookup"><span data-stu-id="211d3-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="211d3-111">[in] Метод, используемый для подписки на событие, или значение null.</span><span class="sxs-lookup"><span data-stu-id="211d3-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="211d3-112">[in] Метод, используемый для отказа от подписки на событие, или значение null.</span><span class="sxs-lookup"><span data-stu-id="211d3-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="211d3-113">[in] Метод, используемый (с помощью производного класса) для вызова события.</span><span class="sxs-lookup"><span data-stu-id="211d3-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="211d3-114">[in] Массив маркеров для других методов, связанный с событием.</span><span class="sxs-lookup"><span data-stu-id="211d3-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="211d3-115">Последний элемент массива должен быть `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="211d3-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="211d3-116">Требования</span><span class="sxs-lookup"><span data-stu-id="211d3-116">Requirements</span></span>  
 <span data-ttu-id="211d3-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="211d3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="211d3-118">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="211d3-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="211d3-119">**Библиотека:** Используется как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="211d3-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="211d3-120">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="211d3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="211d3-121">См. также</span><span class="sxs-lookup"><span data-stu-id="211d3-121">See also</span></span>

- [<span data-ttu-id="211d3-122">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="211d3-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="211d3-123">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="211d3-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
