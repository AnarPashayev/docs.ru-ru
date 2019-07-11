---
title: Функция StrongNameGetBlobFromImage
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b076c39ccf40ca5b613cab94ecc75716158d97a9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780129"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="7dd97-102">Функция StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="7dd97-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="7dd97-103">Получает двоичное представление образа сборки по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="7dd97-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="7dd97-104">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="7dd97-104">This function has been deprecated.</span></span> <span data-ttu-id="7dd97-105">Используйте [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="7dd97-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd97-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7dd97-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dd97-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="7dd97-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="7dd97-108">[in] Адрес памяти, сопоставленной сборки манифеста.</span><span class="sxs-lookup"><span data-stu-id="7dd97-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7dd97-109">[in] Размер в байтах, изображения в `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="7dd97-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="7dd97-110">[in] Буфер, содержащий двоичное представление изображения.</span><span class="sxs-lookup"><span data-stu-id="7dd97-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="7dd97-111">[in, out] Максимальный размер в байтах, запрошенную `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="7dd97-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="7dd97-112">По возвращении фактический размер в байтах из `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="7dd97-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7dd97-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7dd97-113">Return Value</span></span>  
 <span data-ttu-id="7dd97-114">`true` После успешного выполнения; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="7dd97-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dd97-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="7dd97-115">Remarks</span></span>  
 <span data-ttu-id="7dd97-116">Если `StrongNameGetBlobFromImage` функция не завершена, вызвать [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) функции для получения последнего формируемой ошибки.</span><span class="sxs-lookup"><span data-stu-id="7dd97-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dd97-117">Требования</span><span class="sxs-lookup"><span data-stu-id="7dd97-117">Requirements</span></span>  
 <span data-ttu-id="7dd97-118">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dd97-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dd97-119">**Заголовок.** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="7dd97-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="7dd97-120">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7dd97-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7dd97-121">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dd97-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd97-122">См. также</span><span class="sxs-lookup"><span data-stu-id="7dd97-122">See also</span></span>

- [<span data-ttu-id="7dd97-123">Метод StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="7dd97-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="7dd97-124">Метод StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="7dd97-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="7dd97-125">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7dd97-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
