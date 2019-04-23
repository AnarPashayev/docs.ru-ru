---
title: Метод ICeeGen::GetMethodBuffer
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0aea6185095a30aae9197c875aa9b9ac581d406
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121541"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="b67c3-102">Метод ICeeGen::GetMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="b67c3-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="b67c3-103">Получает буфер соответствующего размера в указанный относительный виртуальный адрес метода.</span><span class="sxs-lookup"><span data-stu-id="b67c3-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="b67c3-104">Этот метод является устаревшим и не должны использоваться.</span><span class="sxs-lookup"><span data-stu-id="b67c3-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b67c3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b67c3-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b67c3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b67c3-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="b67c3-107">[in] Относительный виртуальный адрес метода, для которого необходимо вернуть в буфер.</span><span class="sxs-lookup"><span data-stu-id="b67c3-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="b67c3-108">[out] Указатель на возвращаемый буфер.</span><span class="sxs-lookup"><span data-stu-id="b67c3-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b67c3-109">Требования</span><span class="sxs-lookup"><span data-stu-id="b67c3-109">Requirements</span></span>  
 <span data-ttu-id="b67c3-110">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b67c3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b67c3-111">**Заголовок.** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b67c3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b67c3-112">**Библиотека:** Используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b67c3-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b67c3-113">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b67c3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b67c3-114">См. также</span><span class="sxs-lookup"><span data-stu-id="b67c3-114">See also</span></span>

- [<span data-ttu-id="b67c3-115">Интерфейс ICeeGen</span><span class="sxs-lookup"><span data-stu-id="b67c3-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
