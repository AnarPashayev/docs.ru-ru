---
title: Метод IValidator::Validate
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1fba06360a0c31e0a7fa3e61de9793bad14650fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127508"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="19be1-102">Метод IValidator::Validate</span><span class="sxs-lookup"><span data-stu-id="19be1-102">IValidator::Validate Method</span></span>
<span data-ttu-id="19be1-103">Проверяет указанный переносимого исполняемого (PE) или файл Microsoft промежуточного языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="19be1-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19be1-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="19be1-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19be1-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="19be1-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="19be1-106">[in] Указатель на `IVEHandler` экземпляр, который обрабатывает ошибки проверки.</span><span class="sxs-lookup"><span data-stu-id="19be1-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="19be1-107">[in] Указатель на область приложений, в котором загружается файл.</span><span class="sxs-lookup"><span data-stu-id="19be1-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="19be1-108">[in] Побитовое сочетание [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) значений, указывающее, проверки, которые должны выполняться.</span><span class="sxs-lookup"><span data-stu-id="19be1-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="19be1-109">[in] Максимальное количество ошибок, чтобы разрешить перед выходом из проверки.</span><span class="sxs-lookup"><span data-stu-id="19be1-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="19be1-110">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="19be1-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="19be1-111">[in] Строка, указывающая имя файла для проверки.</span><span class="sxs-lookup"><span data-stu-id="19be1-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="19be1-112">[in] Указатель на буфер памяти, в которой будет храниться файл.</span><span class="sxs-lookup"><span data-stu-id="19be1-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="19be1-113">[in] Размер в байтах файла для проверки.</span><span class="sxs-lookup"><span data-stu-id="19be1-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19be1-114">Требования</span><span class="sxs-lookup"><span data-stu-id="19be1-114">Requirements</span></span>  
 <span data-ttu-id="19be1-115">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19be1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19be1-116">**Заголовок.** IValidator.idl в файле IValidator.h</span><span class="sxs-lookup"><span data-stu-id="19be1-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="19be1-117">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19be1-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19be1-118">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19be1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
