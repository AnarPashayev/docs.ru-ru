---
title: Метод ICLRStrongName::StrongNameTokenFromPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e595904eacebdd42467fc4e0550db77578c075c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169732"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="46985-102">Метод ICLRStrongName::StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="46985-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="46985-103">Возвращает токен, представляющий открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="46985-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="46985-104">Маркер строгого имени — это сокращенная форма открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="46985-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46985-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="46985-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46985-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="46985-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="46985-107">[in] Структура типа [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) , содержащий открытую часть пары ключей, использованного для создания подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="46985-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="46985-108">[in] Размер в байтах из `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="46985-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="46985-109">[out] Токен строгое имя, соответствующее ключу, переданный в `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="46985-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="46985-110">Среда CLR выделяет память, в котором для возврата токена.</span><span class="sxs-lookup"><span data-stu-id="46985-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="46985-111">Вызывающий объект должен освободить эту память с помощью [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="46985-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="46985-112">[out] Размер в байтах, возвращенный строгое имя маркера.</span><span class="sxs-lookup"><span data-stu-id="46985-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46985-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="46985-113">Return Value</span></span>  
 `S_OK` <span data-ttu-id="46985-114">Если метод успешно завершена; в противном случае — значение HRESULT, указывающее на сбой (см. в разделе [часто встречающихся значений HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) список).</span><span class="sxs-lookup"><span data-stu-id="46985-114">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46985-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="46985-115">Remarks</span></span>  
 <span data-ttu-id="46985-116">Маркер строгого имени — это сокращенная форма открытого ключа, который используется для экономии места, при сохранении информации ключа в метаданных.</span><span class="sxs-lookup"><span data-stu-id="46985-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="46985-117">В частности маркеры строгого имени используются в ссылках сборок для ссылки на зависимые сборки.</span><span class="sxs-lookup"><span data-stu-id="46985-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46985-118">Требования</span><span class="sxs-lookup"><span data-stu-id="46985-118">Requirements</span></span>  
 <span data-ttu-id="46985-119">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46985-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46985-120">**Заголовок.** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="46985-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="46985-121">**Библиотека:** Включена как ресурс в mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="46985-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 **<span data-ttu-id="46985-122">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="46985-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="46985-123">См. также</span><span class="sxs-lookup"><span data-stu-id="46985-123">See also</span></span>

- [<span data-ttu-id="46985-124">Метод StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="46985-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="46985-125">Структура PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="46985-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="46985-126">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="46985-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
