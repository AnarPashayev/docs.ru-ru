---
title: Метод ICorRuntimeHost::GetDefaultDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: 673c32c86c808c36db6454b8a9f0d8e68f9b1258
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720637"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="71e1c-102">Метод ICorRuntimeHost::GetDefaultDomain</span><span class="sxs-lookup"><span data-stu-id="71e1c-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>

<span data-ttu-id="71e1c-103">Возвращает указатель интерфейса типа <xref:System._AppDomain?displayProperty=nameWithType> , представляющий домен по умолчанию для текущего процесса.</span><span class="sxs-lookup"><span data-stu-id="71e1c-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71e1c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="71e1c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71e1c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="71e1c-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="71e1c-106">заполняет Указатель интерфейса типа <xref:System._AppDomain?displayProperty=nameWithType> на <xref:System.AppDomain> экземпляр, представляющий домен приложения по умолчанию для процесса.</span><span class="sxs-lookup"><span data-stu-id="71e1c-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="71e1c-107">Этот указатель типизирован `IUnknown` , поэтому вызывающие объекты должны, как правило, вызывать `QueryInterface` для получения указателя интерфейса типа <xref:System._AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="71e1c-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71e1c-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="71e1c-108">Return Value</span></span>  
  
|<span data-ttu-id="71e1c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71e1c-109">HRESULT</span></span>|<span data-ttu-id="71e1c-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="71e1c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71e1c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="71e1c-111">S_OK</span></span>|<span data-ttu-id="71e1c-112">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="71e1c-112">The operation was successful.</span></span>|  
|<span data-ttu-id="71e1c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="71e1c-113">S_FALSE</span></span>|<span data-ttu-id="71e1c-114">Не удалось завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="71e1c-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="71e1c-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71e1c-115">E_FAIL</span></span>|<span data-ttu-id="71e1c-116">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="71e1c-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="71e1c-117">Если метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="71e1c-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="71e1c-118">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="71e1c-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="71e1c-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71e1c-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71e1c-120">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="71e1c-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71e1c-121">Требования</span><span class="sxs-lookup"><span data-stu-id="71e1c-121">Requirements</span></span>  

 <span data-ttu-id="71e1c-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71e1c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71e1c-123">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="71e1c-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71e1c-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="71e1c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71e1c-125">**.NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="71e1c-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e1c-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="71e1c-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="71e1c-127">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="71e1c-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
