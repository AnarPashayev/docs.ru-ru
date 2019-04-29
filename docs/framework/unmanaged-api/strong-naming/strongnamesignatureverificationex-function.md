---
title: Функция StrongNameSignatureVerificationEx
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 049b7b11473a05d74dc311ca6ee79947039b0dd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794424"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="ffacc-102">Функция StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="ffacc-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="ffacc-103">Получает значение, указывающее, содержит ли находящийся по указанному пути манифест сборки подпись строгого имени.</span><span class="sxs-lookup"><span data-stu-id="ffacc-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="ffacc-104">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ffacc-104">This function has been deprecated.</span></span> <span data-ttu-id="ffacc-105">Используйте [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="ffacc-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffacc-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ffacc-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffacc-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="ffacc-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ffacc-108">[in] Путь к переносимого исполняемого файла (.exe или .dll) для сборки, которую требуется проверить.</span><span class="sxs-lookup"><span data-stu-id="ffacc-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="ffacc-109">[in] `true` будет выполнить проверку подлинности, даже если это необходимо переопределить параметры реестра, в противном случае — `false`.</span><span class="sxs-lookup"><span data-stu-id="ffacc-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="ffacc-110">[out] `true` при подписи строгого имени проверенного; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="ffacc-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="ffacc-111">`pfWasVerified` задается значение `false` Если проверка пройдена успешно из-за параметров реестра.</span><span class="sxs-lookup"><span data-stu-id="ffacc-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffacc-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ffacc-112">Return Value</span></span>  
 <span data-ttu-id="ffacc-113">`true` Если проверка прошла успешно; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="ffacc-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffacc-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="ffacc-114">Remarks</span></span>  
 <span data-ttu-id="ffacc-115">`StrongNameSignatureVerificationEx` предоставляет возможность, аналогичную [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) функции.</span><span class="sxs-lookup"><span data-stu-id="ffacc-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="ffacc-116">Однако второй входной параметр и параметр вывода для `StrongNameSignatureVerificationEx` относятся к типу `BOOLEAN` вместо `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="ffacc-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffacc-117">Требования</span><span class="sxs-lookup"><span data-stu-id="ffacc-117">Requirements</span></span>  
 <span data-ttu-id="ffacc-118">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffacc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffacc-119">**Заголовок.** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ffacc-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ffacc-120">**Библиотека:** Включена как ресурс в mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ffacc-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="ffacc-121">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffacc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffacc-122">См. также</span><span class="sxs-lookup"><span data-stu-id="ffacc-122">See also</span></span>

- [<span data-ttu-id="ffacc-123">Метод StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="ffacc-123">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="ffacc-124">Метод StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="ffacc-124">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="ffacc-125">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ffacc-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
