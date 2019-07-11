---
title: Функция GetHashFromHandle
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa5d5ee469d41cca46ea05fa4111ce3abff808d4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771907"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="4f1fe-102">Функция GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="4f1fe-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="4f1fe-103">Создает хэш содержимого файла с заданным дескриптором файла с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="4f1fe-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="4f1fe-104">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="4f1fe-104">This function has been deprecated.</span></span> <span data-ttu-id="4f1fe-105">Используйте [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="4f1fe-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f1fe-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4f1fe-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f1fe-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="4f1fe-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="4f1fe-108">[in] Дескриптор файла, хэширование которого требуется выполнить.</span><span class="sxs-lookup"><span data-stu-id="4f1fe-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="4f1fe-109">[in, out] Константа, указывающая хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="4f1fe-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="4f1fe-110">Использовать нуль для алгоритма по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4f1fe-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="4f1fe-111">[out] Буфер, возвращенный хэша.</span><span class="sxs-lookup"><span data-stu-id="4f1fe-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="4f1fe-112">[in] Запрошенный максимальный размер `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4f1fe-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="4f1fe-113">[out] Размер в байтах, возвращаемого `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4f1fe-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f1fe-114">Требования</span><span class="sxs-lookup"><span data-stu-id="4f1fe-114">Requirements</span></span>  
 <span data-ttu-id="4f1fe-115">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f1fe-116">**Заголовок.** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="4f1fe-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4f1fe-117">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f1fe-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f1fe-118">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f1fe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1fe-119">См. также</span><span class="sxs-lookup"><span data-stu-id="4f1fe-119">See also</span></span>

- [<span data-ttu-id="4f1fe-120">Метод GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="4f1fe-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="4f1fe-121">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="4f1fe-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
