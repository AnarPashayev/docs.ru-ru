---
title: Метод ICLRRuntimeInfo::GetRuntimeDirectory
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
ms.openlocfilehash: 24679118e4255282f7da3ff8be2ce9c08250e181
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732051"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="4452c-102">Метод ICLRRuntimeInfo::GetRuntimeDirectory</span><span class="sxs-lookup"><span data-stu-id="4452c-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>

<span data-ttu-id="4452c-103">Возвращает каталог установки среды CLR, связанной с этим интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="4452c-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="4452c-104">Этот метод заменяет функцию [GetCORSystemDirectory](getcorsystemdirectory-function.md) , указанную в .NET Framework версиях 2,0, 3,0 и 3,5.</span><span class="sxs-lookup"><span data-stu-id="4452c-104">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4452c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4452c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4452c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4452c-106">Parameters</span></span>  

 `pwzBuffer`  
 <span data-ttu-id="4452c-107">заполняет Возвращает каталог установки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="4452c-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="4452c-108">Путь установки является полным; Например, "c:\windows\microsoft.net\framework\v1.0.3705 \\ ".</span><span class="sxs-lookup"><span data-stu-id="4452c-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="4452c-109">[вход, выход] Указывает размер `pwzBuffer` во избежание переполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="4452c-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="4452c-110">Если `pwzBuffer` параметр имеет значение null, `pchBuffer` возвращает требуемый размер `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="4452c-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4452c-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4452c-111">Return Value</span></span>  

 <span data-ttu-id="4452c-112">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="4452c-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4452c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4452c-113">HRESULT</span></span>|<span data-ttu-id="4452c-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="4452c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4452c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="4452c-115">S_OK</span></span>|<span data-ttu-id="4452c-116">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="4452c-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="4452c-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4452c-117">E_POINTER</span></span>|<span data-ttu-id="4452c-118">`pwzBuffer` или `pchBuffer` равно null.</span><span class="sxs-lookup"><span data-stu-id="4452c-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4452c-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="4452c-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4452c-120">Требования</span><span class="sxs-lookup"><span data-stu-id="4452c-120">Requirements</span></span>  

 <span data-ttu-id="4452c-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4452c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4452c-122">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="4452c-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4452c-123">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4452c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4452c-124">**.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4452c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4452c-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4452c-125">See also</span></span>

- [<span data-ttu-id="4452c-126">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="4452c-126">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="4452c-127">Размещение</span><span class="sxs-lookup"><span data-stu-id="4452c-127">Hosting</span></span>](index.md)
