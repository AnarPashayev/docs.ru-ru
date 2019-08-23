---
title: Метод ICLRRuntimeInfo::GetVersionString
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a886106e5da49e7124dac5c8ea7416859aa441da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929844"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="1b1d3-102">Метод ICLRRuntimeInfo::GetVersionString</span><span class="sxs-lookup"><span data-stu-id="1b1d3-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="1b1d3-103">Возвращает сведения о версии среды CLR, связанные с заданным интерфейсом [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1b1d3-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="1b1d3-104">Этот метод заменяет следующие функции:</span><span class="sxs-lookup"><span data-stu-id="1b1d3-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="1b1d3-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="1b1d3-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
- [<span data-ttu-id="1b1d3-106">жетрекуестедрунтимеверсион</span><span class="sxs-lookup"><span data-stu-id="1b1d3-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="1b1d3-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1b1d3-107">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b1d3-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="1b1d3-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="1b1d3-109">заполняет Версия компиляции .NET Framework в формате "v*A*. *Б* [. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="1b1d3-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="1b1d3-110">*A*, *B*и *X* — это десятичные числа, соответствующие основной версии, дополнительной версии и номеру сборки.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="1b1d3-111">*X* является необязательным.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-111">*X* is optional.</span></span> <span data-ttu-id="1b1d3-112">Если значение *X* отсутствует, конечная точка отсутствует.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b1d3-113">Этот параметр должен соответствовать имени каталога для .NET Framework версии, как показано в разделе К:\виндовс\микрософт.нет\фрамеворк.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="1b1d3-114">Примеры значений: "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" и "v 4.0. *x*", где *x* зависит от установленного номера сборки.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="1b1d3-115">Обратите внимание, что префикс "v" является обязательным.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="1b1d3-116">[вход, выход] Указывает размер `pwzBuffer` во избежание переполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="1b1d3-117">Если `pwzBuffer` имеет `null`значение `pchBuffer` , функция возвращает требуемый `pwzBuffer` размер, чтобы разрешить предварительное выделение.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b1d3-118">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1b1d3-118">Return Value</span></span>  
 <span data-ttu-id="1b1d3-119">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1b1d3-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b1d3-120">HRESULT</span></span>|<span data-ttu-id="1b1d3-121">Описание</span><span class="sxs-lookup"><span data-stu-id="1b1d3-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b1d3-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b1d3-122">S_OK</span></span>|<span data-ttu-id="1b1d3-123">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="1b1d3-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1b1d3-124">E_POINTER</span></span>|<span data-ttu-id="1b1d3-125">`pwzBuffer` или `pchBuffer` равно null.</span><span class="sxs-lookup"><span data-stu-id="1b1d3-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b1d3-126">Требования</span><span class="sxs-lookup"><span data-stu-id="1b1d3-126">Requirements</span></span>  
 <span data-ttu-id="1b1d3-127">**Платформ** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1d3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1d3-128">**Заголовок.** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="1b1d3-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1b1d3-129">**Библиотечная** Включается в качестве ресурса в библиотеку MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1b1d3-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b1d3-130">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1d3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1d3-131">См. также</span><span class="sxs-lookup"><span data-stu-id="1b1d3-131">See also</span></span>

- [<span data-ttu-id="1b1d3-132">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="1b1d3-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="1b1d3-133">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="1b1d3-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1b1d3-134">Интерфейсы размещения CLR, добавленные в версиях .NET Framework 4 и 4.5</span><span class="sxs-lookup"><span data-stu-id="1b1d3-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="1b1d3-135">Размещение</span><span class="sxs-lookup"><span data-stu-id="1b1d3-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
