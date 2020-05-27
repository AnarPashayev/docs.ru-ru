---
title: Метод IManagedObject::GetObjectIdentity
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
ms.openlocfilehash: 1b40ed8e107d30c22b4ade25d29376b1b74583d1
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842417"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="c6ebe-102">Метод IManagedObject::GetObjectIdentity</span><span class="sxs-lookup"><span data-stu-id="c6ebe-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="c6ebe-103">Возвращает удостоверение этого управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="c6ebe-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ebe-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c6ebe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6ebe-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="c6ebe-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="c6ebe-106">заполняет Указатель на идентификатор GUID процесса, в котором находится объект.</span><span class="sxs-lookup"><span data-stu-id="c6ebe-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="c6ebe-107">заполняет Указатель на идентификатор домена приложения объекта.</span><span class="sxs-lookup"><span data-stu-id="c6ebe-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="c6ebe-108">заполняет Указатель на индекс объекта в классической таблице v-таблицы COM.</span><span class="sxs-lookup"><span data-stu-id="c6ebe-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6ebe-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="c6ebe-109">Remarks</span></span>  
 <span data-ttu-id="c6ebe-110">Удостоверение управляемого объекта включает идентификатор GUID процесса, идентификатор домена приложения и индекс объекта в классической таблице v-таблицы COM.</span><span class="sxs-lookup"><span data-stu-id="c6ebe-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ebe-111">Требования</span><span class="sxs-lookup"><span data-stu-id="c6ebe-111">Requirements</span></span>  
 <span data-ttu-id="c6ebe-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6ebe-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6ebe-113">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c6ebe-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6ebe-114">**Библиотека:** Включается в качестве ресурса в библиотеку MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c6ebe-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6ebe-115">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6ebe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ebe-116">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="c6ebe-116">See also</span></span>

- [<span data-ttu-id="c6ebe-117">Интерфейс IManagedObject</span><span class="sxs-lookup"><span data-stu-id="c6ebe-117">IManagedObject Interface</span></span>](imanagedobject-interface.md)
