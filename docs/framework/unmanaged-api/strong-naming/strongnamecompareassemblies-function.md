---
title: Функция StrongNameCompareAssemblies
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a49252d00f75b4d0b6325aeae0aab22f8ada5e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191384"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="cac39-102">Функция StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="cac39-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="cac39-103">Определяет, отличаются ли две сборки только подписями строгого имени.</span><span class="sxs-lookup"><span data-stu-id="cac39-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="cac39-104">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="cac39-104">This function has been deprecated.</span></span> <span data-ttu-id="cac39-105">Используйте [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) метод вместо этого.</span><span class="sxs-lookup"><span data-stu-id="cac39-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cac39-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cac39-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cac39-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="cac39-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="cac39-108">[in] Путь к первой сборки.</span><span class="sxs-lookup"><span data-stu-id="cac39-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="cac39-109">[in] Путь к вторую сборку.</span><span class="sxs-lookup"><span data-stu-id="cac39-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="cac39-110">[out] Одно из следующих значений:</span><span class="sxs-lookup"><span data-stu-id="cac39-110">[out] One of the following values:</span></span>  
  
-   `SN_CMP_DIFFERENT` <span data-ttu-id="cac39-111">(0) — указывает, что сборки содержат разные данные.</span><span class="sxs-lookup"><span data-stu-id="cac39-111">(0) - Specifies that the assemblies contain different data.</span></span>  
  
-   `SN_CMP_IDENTICAL` <span data-ttu-id="cac39-112">(1) — указывает, что сборки идентичны, включая их подписи и контрольной суммы.</span><span class="sxs-lookup"><span data-stu-id="cac39-112">(1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   `SN_CMP_SIGONLY` <span data-ttu-id="cac39-113">(2) — указывает, что сборки отличаются только подпись и контрольная сумма.</span><span class="sxs-lookup"><span data-stu-id="cac39-113">(2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cac39-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cac39-114">Return Value</span></span>  
 `true` <span data-ttu-id="cac39-115">После успешного выполнения; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="cac39-115">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cac39-116">Требования</span><span class="sxs-lookup"><span data-stu-id="cac39-116">Requirements</span></span>  
 <span data-ttu-id="cac39-117">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cac39-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cac39-118">**Заголовок.** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cac39-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cac39-119">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cac39-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="cac39-120">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="cac39-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="cac39-121">Примечания</span><span class="sxs-lookup"><span data-stu-id="cac39-121">Remarks</span></span>  
 <span data-ttu-id="cac39-122">Подпись строгого имени сборки состоит из текстовое имя сборки, версию, язык и региональные параметры и маркер открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="cac39-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="cac39-123">Если `StrongNameCompareAssemblies` функция не завершена, вызвать [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) функции для получения последнего формируемой ошибки.</span><span class="sxs-lookup"><span data-stu-id="cac39-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac39-124">См. также</span><span class="sxs-lookup"><span data-stu-id="cac39-124">See also</span></span>

- [<span data-ttu-id="cac39-125">Метод StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="cac39-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="cac39-126">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="cac39-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
