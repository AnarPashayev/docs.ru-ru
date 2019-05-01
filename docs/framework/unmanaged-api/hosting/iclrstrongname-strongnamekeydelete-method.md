---
title: Метод ICLRStrongName::StrongNameKeyDelete
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 412aa8fd30294ac9681a5edd02bb4bdfe25b3fab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993061"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="a8588-102">Метод ICLRStrongName::StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="a8588-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="a8588-103">Удаляет указанный контейнер ключей.</span><span class="sxs-lookup"><span data-stu-id="a8588-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8588-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a8588-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8588-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="a8588-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="a8588-106">[in] Имя контейнера ключа для удаления.</span><span class="sxs-lookup"><span data-stu-id="a8588-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8588-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a8588-107">Return Value</span></span>  
 <span data-ttu-id="a8588-108">`S_OK` Если метод успешно завершена; в противном случае — значение HRESULT, указывающее на сбой (см. в разделе [часто встречающихся значений HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) список).</span><span class="sxs-lookup"><span data-stu-id="a8588-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8588-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="a8588-109">Remarks</span></span>  
 <span data-ttu-id="a8588-110">Используйте [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) метод, чтобы импортировать пару открытого и закрытого ключей в контейнере.</span><span class="sxs-lookup"><span data-stu-id="a8588-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8588-111">Требования</span><span class="sxs-lookup"><span data-stu-id="a8588-111">Requirements</span></span>  
 <span data-ttu-id="a8588-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8588-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8588-113">**Заголовок.** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a8588-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a8588-114">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8588-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8588-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8588-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8588-116">См. также</span><span class="sxs-lookup"><span data-stu-id="a8588-116">See also</span></span>

- [<span data-ttu-id="a8588-117">Метод StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="a8588-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="a8588-118">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a8588-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
