---
title: Метод IMetaDataTables::GetUserStringHeapSize
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
ms.openlocfilehash: 048010f00f6581a29c6b1a3150bf5ae8822b5664
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672465"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="e0749-102">Метод IMetaDataTables::GetUserStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="e0749-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>

<span data-ttu-id="e0749-103">Возвращает размер (в байтах) кучи пользовательской строки.</span><span class="sxs-lookup"><span data-stu-id="e0749-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0749-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e0749-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0749-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e0749-105">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="e0749-106">заполняет Указатель на размер (в байтах) кучи пользовательской строки.</span><span class="sxs-lookup"><span data-stu-id="e0749-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0749-107">Требования</span><span class="sxs-lookup"><span data-stu-id="e0749-107">Requirements</span></span>  

 <span data-ttu-id="e0749-108">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0749-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0749-109">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="e0749-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0749-110">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0749-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0749-111">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0749-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0749-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e0749-112">See also</span></span>

- [<span data-ttu-id="e0749-113">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="e0749-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="e0749-114">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="e0749-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
