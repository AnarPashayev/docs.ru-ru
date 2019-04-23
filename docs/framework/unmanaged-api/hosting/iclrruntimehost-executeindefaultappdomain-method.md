---
title: Метод ICLRRuntimeHost::ExecuteInDefaultAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e6805dc67f7ec5ceb8c67d77462a0200b6c0317
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205914"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="5fe7a-102">Метод ICLRRuntimeHost::ExecuteInDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="5fe7a-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="5fe7a-103">Вызывает указанный метод заданного типа в указанной управляемой сборки.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe7a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5fe7a-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fe7a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="5fe7a-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="5fe7a-106">[in] Путь к <xref:System.Reflection.Assembly> , определяющий <xref:System.Type> метод которого должен вызываться.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="5fe7a-107">[in] Имя <xref:System.Type> , определяющий вызываемый метод.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="5fe7a-108">[in] Имя вызываемого метода.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="5fe7a-109">[in] Параметр строки для передачи в метод.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="5fe7a-110">[out] Целочисленное значение, возвращенное вызванным методом.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fe7a-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5fe7a-111">Return Value</span></span>  
  
|<span data-ttu-id="5fe7a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5fe7a-112">HRESULT</span></span>|<span data-ttu-id="5fe7a-113">Описание</span><span class="sxs-lookup"><span data-stu-id="5fe7a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5fe7a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5fe7a-114">S_OK</span></span>|<span data-ttu-id="5fe7a-115">`ExecuteInDefaultAppDomain` успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="5fe7a-116">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5fe7a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5fe7a-117">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5fe7a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5fe7a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5fe7a-119">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-119">The call timed out.</span></span>|  
|<span data-ttu-id="5fe7a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5fe7a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5fe7a-121">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5fe7a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5fe7a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5fe7a-123">Событие было отменено с сохранением заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5fe7a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5fe7a-124">E_FAIL</span></span>|<span data-ttu-id="5fe7a-125">Неизвестный Разрушительный сбой.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5fe7a-126">Если метод вернет значение E_FAIL, список отзыва Сертификатов больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="5fe7a-127">Последующие вызовы к размещению методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fe7a-128">Примечания</span><span class="sxs-lookup"><span data-stu-id="5fe7a-128">Remarks</span></span>  
 <span data-ttu-id="5fe7a-129">Вызванный метод должен иметь следующую сигнатуру:</span><span class="sxs-lookup"><span data-stu-id="5fe7a-129">The invoked method must have the following signature:</span></span>  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="5fe7a-130">где `pwzMethodName` представляет имя вызываемого метода, и `pwzArgument` представляет строковое значение, передаваемое как параметр этому методу.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="5fe7a-131">Если HRESULT имеет значение S_OK, `pReturnValue` присваивается целочисленное значение, возвращенное вызванным методом.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="5fe7a-132">В противном случае `pReturnValue` не задано.</span><span class="sxs-lookup"><span data-stu-id="5fe7a-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fe7a-133">Требования</span><span class="sxs-lookup"><span data-stu-id="5fe7a-133">Requirements</span></span>  
 <span data-ttu-id="5fe7a-134">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fe7a-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fe7a-135">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5fe7a-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5fe7a-136">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5fe7a-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fe7a-137">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fe7a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe7a-138">См. также</span><span class="sxs-lookup"><span data-stu-id="5fe7a-138">See also</span></span>

- [<span data-ttu-id="5fe7a-139">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="5fe7a-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
