---
title: Функция GetHashFromFile
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5774b7cdcfedfc407b626ab5052f5b4a77461e9b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155913"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="ea2ad-102">Функция GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="ea2ad-102">GetHashFromFile Function</span></span>
<span data-ttu-id="ea2ad-103">Создает хэш содержимого указанного файла.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="ea2ad-104">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-104">This function has been deprecated.</span></span> <span data-ttu-id="ea2ad-105">Используйте [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2ad-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ea2ad-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea2ad-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea2ad-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="ea2ad-108">[in] Имя файла для хеширования.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ea2ad-109">[in, out] Алгоритм, используемый при создании хеша.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="ea2ad-110">Допустимыми являются алгоритмы, определенные интерфейсом Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="ea2ad-111">Если `piHashAlg` имеет значение 0, CALG_SHA 1 используется алгоритм по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ea2ad-112">[out] Массив байтов, содержащий созданный хэш.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ea2ad-113">[in] Максимальный размер буфера, `pbHash` указывает.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ea2ad-114">[out] Размер в байтах, возвращаемого `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea2ad-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="ea2ad-115">Remarks</span></span>  
 <span data-ttu-id="ea2ad-116">Эта функция совпадает со значением [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), за исключением того, что спецификация имени файла — ANSI, а не в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="ea2ad-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea2ad-117">Требования</span><span class="sxs-lookup"><span data-stu-id="ea2ad-117">Requirements</span></span>  
 <span data-ttu-id="ea2ad-118">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea2ad-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea2ad-119">**Заголовок.** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ea2ad-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ea2ad-120">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea2ad-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea2ad-121">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea2ad-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2ad-122">См. также</span><span class="sxs-lookup"><span data-stu-id="ea2ad-122">See also</span></span>

- [<span data-ttu-id="ea2ad-123">Метод GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="ea2ad-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="ea2ad-124">Метод GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="ea2ad-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="ea2ad-125">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ea2ad-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
