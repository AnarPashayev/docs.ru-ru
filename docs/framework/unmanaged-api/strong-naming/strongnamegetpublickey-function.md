---
title: Функция StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e38a85b688d66e9f44bd8026bb4c9e141a6eb7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229294"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="0ecf5-102">Функция StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="0ecf5-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="0ecf5-103">Получает открытый ключ из пары закрытого и открытого ключей.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="0ecf5-104">Пару ключей можно указать как имя контейнера ключей в поставщике служб шифрования (CSP) или как коллекция необработанных байтов.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="0ecf5-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-105">This function has been deprecated.</span></span> <span data-ttu-id="0ecf5-106">Используйте [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ecf5-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0ecf5-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ecf5-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="0ecf5-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="0ecf5-109">[in] Имя контейнера ключа, который содержит пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="0ecf5-110">Если `pbKeyBlob` имеет значение null, `szKeyContainer` необходимо указать допустимый контейнер в CSP.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="0ecf5-111">В этом случае `StrongNameGetPublicKey` извлекает открытый ключ из пары ключей, хранящихся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="0ecf5-112">Если `pbKeyBlob` не равно null, предполагается, что пары ключей должен содержаться в ключевых большой двоичный объект (BLOB).</span><span class="sxs-lookup"><span data-stu-id="0ecf5-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="0ecf5-113">Ключи должны быть Rivest-Шамир-Adleman 1024-разрядный (RSA) ключи подписывания.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="0ecf5-114">Другие типы ключей не поддерживаются в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="0ecf5-115">[in] Указатель на пару открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="0ecf5-116">Эта пара имеет формат, созданные Win32 `CryptExportKey` функции.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="0ecf5-117">Если `pbKeyBlob` имеет значение null, контейнере ключей `szKeyContainer` предполагается, что содержит пару ключей.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="0ecf5-118">[in] Размер в байтах из `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="0ecf5-119">[out] Возвращаемый открытый ключ BLOB-ОБЪЕКТОВ.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="0ecf5-120">`ppbPublicKeyBlob` Параметра выделяется, среда CLR и возвращается вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="0ecf5-121">Вызывающий объект должен освободить память с помощью [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) функции.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="0ecf5-122">[out] Размер возвращаемого большой двоичный объект открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ecf5-123">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0ecf5-123">Return Value</span></span>  
 `true` <span data-ttu-id="0ecf5-124">После успешного выполнения; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-124">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ecf5-125">Примечания</span><span class="sxs-lookup"><span data-stu-id="0ecf5-125">Remarks</span></span>  
 <span data-ttu-id="0ecf5-126">Открытый ключ, содержащийся в [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) структуры.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="0ecf5-127">Если `StrongNameGetPublicKey` функция не завершена, вызвать [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) функции для получения последнего формируемой ошибки.</span><span class="sxs-lookup"><span data-stu-id="0ecf5-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ecf5-128">Требования</span><span class="sxs-lookup"><span data-stu-id="0ecf5-128">Requirements</span></span>  
 <span data-ttu-id="0ecf5-129">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ecf5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ecf5-130">**Заголовок.** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0ecf5-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0ecf5-131">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ecf5-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="0ecf5-132">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0ecf5-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0ecf5-133">См. также</span><span class="sxs-lookup"><span data-stu-id="0ecf5-133">See also</span></span>

- [<span data-ttu-id="0ecf5-134">Метод StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="0ecf5-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="0ecf5-135">Метод StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="0ecf5-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="0ecf5-136">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="0ecf5-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="0ecf5-137">Структура PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="0ecf5-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
