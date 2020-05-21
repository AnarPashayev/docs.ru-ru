---
title: Метод ICLRStrongName::StrongNameSignatureVerification
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
ms.openlocfilehash: d31c9c0db306aad3a7c3472ef6329f25aa6c5902
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762660"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="77ec5-102">Метод ICLRStrongName::StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="77ec5-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="77ec5-103">Возвращает значение, указывающее, содержит ли манифест сборки по указанному пути подпись строгого имени, которая проверяется в соответствии с заданными флагами.</span><span class="sxs-lookup"><span data-stu-id="77ec5-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ec5-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77ec5-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77ec5-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="77ec5-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="77ec5-106">окне Путь к переносимому исполняемому файлу (DLL или exe), для которого проверяется сборка.</span><span class="sxs-lookup"><span data-stu-id="77ec5-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="77ec5-107">окне Флаги для изменения поведения проверки.</span><span class="sxs-lookup"><span data-stu-id="77ec5-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="77ec5-108">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="77ec5-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="77ec5-109">`SN_INFLAG_FORCE_VER`(0x00000001) — принудительная проверка, даже если необходимо переопределить параметры реестра.</span><span class="sxs-lookup"><span data-stu-id="77ec5-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="77ec5-110">`SN_INFLAG_INSTALL`(0x00000002) — указывает, что это первый раз при проверке манифеста.</span><span class="sxs-lookup"><span data-stu-id="77ec5-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="77ec5-111">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) — указывает, что кэш будет разрешать доступ только тем пользователям, у которых есть права администратора.</span><span class="sxs-lookup"><span data-stu-id="77ec5-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="77ec5-112">`SN_INFLAG_USER_ACCESS`(0x00000008) — указывает, что сборка будет доступна только текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="77ec5-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="77ec5-113">`SN_INFLAG_ALL_ACCESS`(0x00000010) — указывает, что кэш не предоставляет никаких гарантий ограничения доступа.</span><span class="sxs-lookup"><span data-stu-id="77ec5-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="77ec5-114">`SN_INFLAG_RUNTIME`(0x80000000) — зарезервировано для внутренней отладки.</span><span class="sxs-lookup"><span data-stu-id="77ec5-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="77ec5-115">заполняет Флаги, указывающие, была ли проверена подпись строгого имени.</span><span class="sxs-lookup"><span data-stu-id="77ec5-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="77ec5-116">Поддерживается следующее значение:</span><span class="sxs-lookup"><span data-stu-id="77ec5-116">The following value is supported:</span></span>  
  
- <span data-ttu-id="77ec5-117">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) — это значение `false` указывает, что проверка прошла удачно из-за параметров реестра.</span><span class="sxs-lookup"><span data-stu-id="77ec5-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77ec5-118">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="77ec5-118">Return Value</span></span>  
 <span data-ttu-id="77ec5-119">`S_OK`значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="77ec5-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77ec5-120">Требования</span><span class="sxs-lookup"><span data-stu-id="77ec5-120">Requirements</span></span>  
 <span data-ttu-id="77ec5-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77ec5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77ec5-122">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="77ec5-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="77ec5-123">**Библиотека:** Включается в качестве ресурса в библиотеку MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="77ec5-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77ec5-124">**.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77ec5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ec5-125">См. также</span><span class="sxs-lookup"><span data-stu-id="77ec5-125">See also</span></span>

- [<span data-ttu-id="77ec5-126">Метод StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="77ec5-126">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="77ec5-127">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="77ec5-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
