---
title: Функция StrongNameTokenFromAssemblyEx
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 566bba09f6bfac2f7616dc5caf32ef431f2e1e67
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719805"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="9de2a-102">Функция StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="9de2a-102">StrongNameTokenFromAssemblyEx Function</span></span>

<span data-ttu-id="9de2a-103">Создает маркер строгого имени из указанного файла сборки и возвращает открытый ключ, который представляет маркер.</span><span class="sxs-lookup"><span data-stu-id="9de2a-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="9de2a-104">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="9de2a-104">This function has been deprecated.</span></span> <span data-ttu-id="9de2a-105">Используйте вместо этого метод [метод iclrstrongname:: StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9de2a-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9de2a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9de2a-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9de2a-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="9de2a-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="9de2a-108">окне Путь к переносимому исполняемому файлу (PE) для сборки.</span><span class="sxs-lookup"><span data-stu-id="9de2a-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="9de2a-109">заполняет Возвращенный маркер строгого имени.</span><span class="sxs-lookup"><span data-stu-id="9de2a-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="9de2a-110">заполняет Размер (в байтах) маркера строгого имени.</span><span class="sxs-lookup"><span data-stu-id="9de2a-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="9de2a-111">заполняет Возвращаемый открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="9de2a-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="9de2a-112">заполняет Размер открытого ключа в байтах.</span><span class="sxs-lookup"><span data-stu-id="9de2a-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9de2a-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9de2a-113">Return Value</span></span>  

 <span data-ttu-id="9de2a-114">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="9de2a-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9de2a-115">Комментарии</span><span class="sxs-lookup"><span data-stu-id="9de2a-115">Remarks</span></span>  

 <span data-ttu-id="9de2a-116">Маркер строгого имени — это сокращенная форма открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="9de2a-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="9de2a-117">Маркер представляет собой 64-разрядный хэш, созданный из открытого ключа, используемого для подписания сборки.</span><span class="sxs-lookup"><span data-stu-id="9de2a-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="9de2a-118">Токен является частью строгого имени сборки и может быть считан из метаданных сборки.</span><span class="sxs-lookup"><span data-stu-id="9de2a-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="9de2a-119">После извлечения ключа и создания маркера следует вызвать функцию [StrongNameFreeBuffer](strongnamefreebuffer-function.md) , чтобы освободить выделенную память.</span><span class="sxs-lookup"><span data-stu-id="9de2a-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="9de2a-120">Если `StrongNameTokenFromAssemblyEx` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="9de2a-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9de2a-121">Требования</span><span class="sxs-lookup"><span data-stu-id="9de2a-121">Requirements</span></span>  

 <span data-ttu-id="9de2a-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9de2a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9de2a-123">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="9de2a-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9de2a-124">**Библиотека:** Включается в качестве ресурса в mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9de2a-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="9de2a-125">**.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9de2a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9de2a-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9de2a-126">See also</span></span>

- [<span data-ttu-id="9de2a-127">Метод StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="9de2a-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="9de2a-128">Метод StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="9de2a-128">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="9de2a-129">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9de2a-129">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
