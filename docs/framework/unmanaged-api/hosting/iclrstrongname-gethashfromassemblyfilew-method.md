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
ms.openlocfilehash: e94bfe6151ed42886355423a838f21e13748ec61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685777"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="e142c-102">Метод ICLRStrongName::GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="e142c-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>

<span data-ttu-id="e142c-103">Создает хэш содержимого файла, указанного строкой Юникода.</span><span class="sxs-lookup"><span data-stu-id="e142c-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e142c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e142c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e142c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e142c-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="e142c-106">окне Путь к файлу для хэширования.</span><span class="sxs-lookup"><span data-stu-id="e142c-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="e142c-107">Этот параметр должен быть строкой в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="e142c-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e142c-108">[вход, выход] Константа, указывающая хэш-алгоритм.</span><span class="sxs-lookup"><span data-stu-id="e142c-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="e142c-109">Для алгоритма хэширования по умолчанию используется нуль.</span><span class="sxs-lookup"><span data-stu-id="e142c-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e142c-110">заполняет Возвращаемый буфер хэша.</span><span class="sxs-lookup"><span data-stu-id="e142c-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e142c-111">окне Запрошенный максимальный размер `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="e142c-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e142c-112">заполняет Возвращаемый размер (в байтах) для `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="e142c-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e142c-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e142c-113">Return Value</span></span>  

 <span data-ttu-id="e142c-114">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="e142c-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e142c-115">Требования</span><span class="sxs-lookup"><span data-stu-id="e142c-115">Requirements</span></span>  

 <span data-ttu-id="e142c-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e142c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e142c-117">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="e142c-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e142c-118">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e142c-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e142c-119">**.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e142c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e142c-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e142c-120">See also</span></span>

- [<span data-ttu-id="e142c-121">Метод GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="e142c-121">GetHashFromAssemblyFile Method</span></span>](iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="e142c-122">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="e142c-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
