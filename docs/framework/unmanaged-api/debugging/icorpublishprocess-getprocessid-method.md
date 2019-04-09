---
title: Метод ICorPublishProcess::GetProcessID
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f3948e45b991e667ea90c7846ee0d6fd630c0db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165806"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="65960-102">Метод ICorPublishProcess::GetProcessID</span><span class="sxs-lookup"><span data-stu-id="65960-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="65960-103">Получает идентификатор операционной системы для этого процесса.</span><span class="sxs-lookup"><span data-stu-id="65960-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65960-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="65960-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65960-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="65960-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="65960-106">[out] Указатель на идентификатор процесса, представленный этим [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) объекта.</span><span class="sxs-lookup"><span data-stu-id="65960-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65960-107">Требования</span><span class="sxs-lookup"><span data-stu-id="65960-107">Requirements</span></span>  
 <span data-ttu-id="65960-108">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65960-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65960-109">**Заголовок.** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="65960-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="65960-110">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65960-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="65960-111">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="65960-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65960-112">См. также</span><span class="sxs-lookup"><span data-stu-id="65960-112">See also</span></span>

- [<span data-ttu-id="65960-113">Интерфейс ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="65960-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
