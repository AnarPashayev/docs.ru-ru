---
title: Метод ICLRAssemblyReferenceList::IsAssemblyReferenceInList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6a95a636623f0b4ea75706039194572ecf1bbe0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136205"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="607e6-102">Метод ICLRAssemblyReferenceList::IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="607e6-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="607e6-103">Получает значение, указывающее, ссылается ли заданный указатель на сборку в списке.</span><span class="sxs-lookup"><span data-stu-id="607e6-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="607e6-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="607e6-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="607e6-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="607e6-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="607e6-106">[in] Указатель интерфейса на сборку, который требуется найти.</span><span class="sxs-lookup"><span data-stu-id="607e6-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="607e6-107">Допустимые значения имеют тип `IAssemblyName` или `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="607e6-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="607e6-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="607e6-108">Return Value</span></span>  
  
|<span data-ttu-id="607e6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="607e6-109">HRESULT</span></span>|<span data-ttu-id="607e6-110">Описание</span><span class="sxs-lookup"><span data-stu-id="607e6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="607e6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="607e6-111">S_OK</span></span>|<span data-ttu-id="607e6-112">Строка отображается в списке.</span><span class="sxs-lookup"><span data-stu-id="607e6-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="607e6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="607e6-113">S_FALSE</span></span>|<span data-ttu-id="607e6-114">Строка не отображается в списке.</span><span class="sxs-lookup"><span data-stu-id="607e6-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="607e6-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="607e6-115">E_FAIL</span></span>|<span data-ttu-id="607e6-116">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="607e6-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="607e6-117">После метод вернет значение E_FAIL, среда CLR больше не использовать в данном процессе.</span><span class="sxs-lookup"><span data-stu-id="607e6-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="607e6-118">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="607e6-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="607e6-119">Требования</span><span class="sxs-lookup"><span data-stu-id="607e6-119">Requirements</span></span>  
 <span data-ttu-id="607e6-120">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="607e6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="607e6-121">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="607e6-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="607e6-122">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="607e6-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="607e6-123">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="607e6-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="607e6-124">См. также</span><span class="sxs-lookup"><span data-stu-id="607e6-124">See also</span></span>

- [<span data-ttu-id="607e6-125">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="607e6-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="607e6-126">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="607e6-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="607e6-127">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="607e6-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="607e6-128">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="607e6-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
