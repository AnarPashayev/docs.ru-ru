---
title: Метод ICorPublishProcess::IsManaged
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29c5f96bab374d6e2d43424370bff2a4a2ab6df3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218294"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="16465-102">Метод ICorPublishProcess::IsManaged</span><span class="sxs-lookup"><span data-stu-id="16465-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="16465-103">Получает значение, указывающее, является ли процесс ссылается этот [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) известно, что есть управляемый код.</span><span class="sxs-lookup"><span data-stu-id="16465-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16465-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="16465-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16465-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="16465-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="16465-106">[out] Указатель на логическое значение, указывающее, ли процесс управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="16465-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="16465-107">Значение равно `true` Если процесс с управляемым кодом; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="16465-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16465-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="16465-108">Remarks</span></span>  
 <span data-ttu-id="16465-109">Так как текущая версия `ICorPublishProcess` разрешает доступ только к процессам, которые управляемого кода, `IsManaged` всегда возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="16465-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16465-110">Требования</span><span class="sxs-lookup"><span data-stu-id="16465-110">Requirements</span></span>  
 <span data-ttu-id="16465-111">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16465-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16465-112">**Заголовок.** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="16465-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="16465-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16465-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16465-114">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16465-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16465-115">См. также</span><span class="sxs-lookup"><span data-stu-id="16465-115">See also</span></span>

- [<span data-ttu-id="16465-116">Интерфейс ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="16465-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
