---
title: Метод IMetaDataDispenserEx::GetOption
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe9bc9aea4ceb0f5b5c03416f43894b482c3294e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136634"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="cf575-102">Метод IMetaDataDispenserEx::GetOption</span><span class="sxs-lookup"><span data-stu-id="cf575-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="cf575-103">Получает значение указанного параметра в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="cf575-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="cf575-104">Параметр определяет, как обрабатываются вызовы к текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="cf575-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf575-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cf575-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf575-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cf575-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="cf575-107">[in] Указатель на идентификатор GUID, который задает параметр, который требуется получить.</span><span class="sxs-lookup"><span data-stu-id="cf575-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="cf575-108">См. в разделе "Примечания" для получения списка поддерживаемых идентификаторов GUID.</span><span class="sxs-lookup"><span data-stu-id="cf575-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="cf575-109">[out] Значение возвращаемого параметра.</span><span class="sxs-lookup"><span data-stu-id="cf575-109">[out] The value of the returned option.</span></span> <span data-ttu-id="cf575-110">Тип этого значения будет вариант указанного параметра типа.</span><span class="sxs-lookup"><span data-stu-id="cf575-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf575-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="cf575-111">Remarks</span></span>  
 <span data-ttu-id="cf575-112">Ниже приведены идентификаторы GUID, которые поддерживаются для этого метода.</span><span class="sxs-lookup"><span data-stu-id="cf575-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="cf575-113">Описание, см. в разделе [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="cf575-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="cf575-114">Если `optionId` находится не в этом списке, этот метод возвращает значение HRESULT `E_INVALIDARG`, указывающее, неверный параметр.</span><span class="sxs-lookup"><span data-stu-id="cf575-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="cf575-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="cf575-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="cf575-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="cf575-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="cf575-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="cf575-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="cf575-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="cf575-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="cf575-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="cf575-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="cf575-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="cf575-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="cf575-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="cf575-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf575-122">Требования</span><span class="sxs-lookup"><span data-stu-id="cf575-122">Requirements</span></span>  
 <span data-ttu-id="cf575-123">**Платформа:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf575-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf575-124">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf575-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf575-125">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf575-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf575-126">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf575-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf575-127">См. также</span><span class="sxs-lookup"><span data-stu-id="cf575-127">See also</span></span>

- [<span data-ttu-id="cf575-128">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="cf575-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="cf575-129">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="cf575-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
