---
title: Метод IValidator::FormatEventInfo
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31329a8674a9991a3f306eeff44ee3437ad64a5c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779436"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="44e55-102">Метод IValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="44e55-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="44e55-103">Получает сообщение об ошибке, соответствующее указанной ошибкой проверки.</span><span class="sxs-lookup"><span data-stu-id="44e55-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e55-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44e55-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44e55-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="44e55-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="44e55-106">[in] Значение HRESULT, который был передан в обработчик ошибок проверки.</span><span class="sxs-lookup"><span data-stu-id="44e55-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="44e55-107">[in] Объект `VEContext` экземпляр, содержащий контекстные сведения об ошибке проверки.</span><span class="sxs-lookup"><span data-stu-id="44e55-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="44e55-108">[in, out] Строка, содержащая сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="44e55-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="44e55-109">[in] Максимальная длина сообщения об ошибке.</span><span class="sxs-lookup"><span data-stu-id="44e55-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="44e55-110">[in] Безопасный массив, содержащий дополнительные параметры, описывающее ошибку.</span><span class="sxs-lookup"><span data-stu-id="44e55-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e55-111">Требования</span><span class="sxs-lookup"><span data-stu-id="44e55-111">Requirements</span></span>  
 <span data-ttu-id="44e55-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e55-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e55-113">**Заголовок.** IValidator.idl в файле IValidator.h</span><span class="sxs-lookup"><span data-stu-id="44e55-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="44e55-114">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44e55-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44e55-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e55-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
