---
title: Функция CertVerifyAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d8ab96c758b946684af78bfa21822fdaf96530a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786969"
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="69f1c-102">Функция CertVerifyAuthenticodeLicense</span><span class="sxs-lookup"><span data-stu-id="69f1c-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="69f1c-103">Проверяет правильность лицензии Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="69f1c-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f1c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="69f1c-104">Syntax</span></span>  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69f1c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="69f1c-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="69f1c-106">[в] Лицензия Authenticode XrML должна быть проверена.</span><span class="sxs-lookup"><span data-stu-id="69f1c-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="69f1c-107">См. структуру [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="69f1c-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="69f1c-108">[в] Необязательно.</span><span class="sxs-lookup"><span data-stu-id="69f1c-108">[in] Optional.</span></span> <span data-ttu-id="69f1c-109">Комбинация следующих значений:</span><span class="sxs-lookup"><span data-stu-id="69f1c-109">A combination of following values:</span></span>  
  
- <span data-ttu-id="69f1c-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="69f1c-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
- <span data-ttu-id="69f1c-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="69f1c-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
- <span data-ttu-id="69f1c-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="69f1c-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
- <span data-ttu-id="69f1c-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="69f1c-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
- <span data-ttu-id="69f1c-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="69f1c-114">AXL_LIFETIME_SIGNING</span></span>  
  
- <span data-ttu-id="69f1c-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="69f1c-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="69f1c-116">[из] Для получения сведений о подписавшем.</span><span class="sxs-lookup"><span data-stu-id="69f1c-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="69f1c-117">Если лицензия не подписана, переменной `dwError` присваивается значение TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="69f1c-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="69f1c-118">Он отвечает за освобождение ресурсов с помощью функции [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) после использования.</span><span class="sxs-lookup"><span data-stu-id="69f1c-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="69f1c-119">См. раздел [Структура AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="69f1c-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="69f1c-120">[из] Для получения сведений об отметке времени (если есть).</span><span class="sxs-lookup"><span data-stu-id="69f1c-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="69f1c-121">Если отметки времени для лицензии не установлены, переменной `dwError` присваивается значение TRUST_E_NOSIGNATURE.</span><span class="sxs-lookup"><span data-stu-id="69f1c-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="69f1c-122">Он отвечает за освобождение ресурсов с помощью функции [цертфриаусентикодетиместамперинфо](certfreeauthenticodetimestamperinfo-function.md) после использования.</span><span class="sxs-lookup"><span data-stu-id="69f1c-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="69f1c-123">См. раздел [Структура AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md).</span><span class="sxs-lookup"><span data-stu-id="69f1c-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69f1c-124">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="69f1c-124">Return Value</span></span>  
 <span data-ttu-id="69f1c-125">Возвращает значение `S_OK` в случае успешного выполнения.</span><span class="sxs-lookup"><span data-stu-id="69f1c-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="69f1c-126">В противном случае возвращается код ошибки.</span><span class="sxs-lookup"><span data-stu-id="69f1c-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f1c-127">См. также</span><span class="sxs-lookup"><span data-stu-id="69f1c-127">See also</span></span>

- [<span data-ttu-id="69f1c-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="69f1c-128">Authenticode</span></span>](index.md)
- [<span data-ttu-id="69f1c-129">Метод GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="69f1c-129">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="69f1c-130">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="69f1c-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
