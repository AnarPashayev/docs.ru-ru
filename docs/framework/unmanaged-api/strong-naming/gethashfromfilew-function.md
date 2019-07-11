---
title: Функция GetHashFromFileW
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77b164cdec0dd224042e4de3265d14a4991d60ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771890"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="e866e-102">Функция GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="e866e-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="e866e-103">Создает хэш содержимого файла, указанного строкой Юникода.</span><span class="sxs-lookup"><span data-stu-id="e866e-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="e866e-104">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="e866e-104">This function has been deprecated.</span></span> <span data-ttu-id="e866e-105">Используйте [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="e866e-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e866e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e866e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="e866e-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="e866e-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e866e-108">[in] Имя файла для хеширования Юникода.</span><span class="sxs-lookup"><span data-stu-id="e866e-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e866e-109">[in, out] Алгоритм, используемый при создании хеша.</span><span class="sxs-lookup"><span data-stu-id="e866e-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="e866e-110">Допустимыми являются алгоритмы, определенные интерфейсом Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="e866e-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="e866e-111">Если `piHashAlg` имеет значение 0, CALG_SHA 1 используется алгоритм по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e866e-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e866e-112">[out] Массив байтов, содержащий созданный хэш.</span><span class="sxs-lookup"><span data-stu-id="e866e-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e866e-113">[in] Максимальный размер буфера, на которые указывают `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e866e-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e866e-114">[out] Размер в байтах из `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e866e-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e866e-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="e866e-115">Remarks</span></span>  
 <span data-ttu-id="e866e-116">Эта функция совпадает со значением [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), за исключением того, что спецификация имени файла — Юникод вместо ANSI.</span><span class="sxs-lookup"><span data-stu-id="e866e-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e866e-117">Требования</span><span class="sxs-lookup"><span data-stu-id="e866e-117">Requirements</span></span>  
 <span data-ttu-id="e866e-118">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e866e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e866e-119">**Заголовок.** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e866e-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e866e-120">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e866e-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e866e-121">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e866e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e866e-122">См. также</span><span class="sxs-lookup"><span data-stu-id="e866e-122">See also</span></span>

- [<span data-ttu-id="e866e-123">Метод GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="e866e-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="e866e-124">Метод GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="e866e-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="e866e-125">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="e866e-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
