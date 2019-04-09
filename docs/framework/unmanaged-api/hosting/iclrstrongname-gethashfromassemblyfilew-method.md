---
title: Метод ICLRStrongName::GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 578dd7941ad7a2cf1d39a3aeed7fa823eb7efa79
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162170"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="3d8de-102">Метод ICLRStrongName::GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="3d8de-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="3d8de-103">Создает хэш содержимого файла, указанного строкой Юникода.</span><span class="sxs-lookup"><span data-stu-id="3d8de-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d8de-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3d8de-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d8de-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d8de-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="3d8de-106">[in] Путь к файлу, хэширование которого требуется выполнить.</span><span class="sxs-lookup"><span data-stu-id="3d8de-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="3d8de-107">Этот параметр должен быть строкой Юникода.</span><span class="sxs-lookup"><span data-stu-id="3d8de-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="3d8de-108">[in, out] Константа, указывающая хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="3d8de-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="3d8de-109">Использовать нуль для хэш-алгоритм по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3d8de-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="3d8de-110">[out] Буфер, возвращенный хэша.</span><span class="sxs-lookup"><span data-stu-id="3d8de-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="3d8de-111">[in] Запрошенный максимальный размер `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="3d8de-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="3d8de-112">[out] Размер в байтах, возвращенное `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="3d8de-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d8de-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3d8de-113">Return Value</span></span>  
 `S_OK` <span data-ttu-id="3d8de-114">Если метод успешно завершена; в противном случае — значение HRESULT, указывающее на сбой (см. в разделе [часто встречающихся значений HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) список).</span><span class="sxs-lookup"><span data-stu-id="3d8de-114">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d8de-115">Требования</span><span class="sxs-lookup"><span data-stu-id="3d8de-115">Requirements</span></span>  
 <span data-ttu-id="3d8de-116">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d8de-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d8de-117">**Заголовок.** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3d8de-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3d8de-118">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d8de-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3d8de-119">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3d8de-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d8de-120">См. также</span><span class="sxs-lookup"><span data-stu-id="3d8de-120">See also</span></span>

- [<span data-ttu-id="3d8de-121">Метод GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="3d8de-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="3d8de-122">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="3d8de-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
