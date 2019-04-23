---
title: Метод ICLRDomainManager::SetAppDomainManagerType
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cfef7d929d40996716a02a4db51630827011a68
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183252"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="7992d-102">Метод ICLRDomainManager::SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="7992d-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="7992d-103">Указывает тип, производный от <xref:System.AppDomainManager?displayProperty=nameWithType> класс диспетчера домена приложения, который будет использоваться для инициализации домена приложения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="7992d-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7992d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7992d-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7992d-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="7992d-105">Parameters</span></span>  
 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="7992d-106">[in] Отображаемое имя сборки, содержащей тип диспетчера домена приложения; Например: «AdMgrExample, версия = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3».</span><span class="sxs-lookup"><span data-stu-id="7992d-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="7992d-107">[in] Имя типа диспетчера домена приложения, включая пространство имен.</span><span class="sxs-lookup"><span data-stu-id="7992d-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="7992d-108">[in] Сочетание [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) значений перечисления, предоставляющая сведения о диспетчера доменов приложений.</span><span class="sxs-lookup"><span data-stu-id="7992d-108">[in] A combination of [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7992d-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7992d-109">Return Value</span></span>  
 <span data-ttu-id="7992d-110">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="7992d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7992d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7992d-111">HRESULT</span></span>|<span data-ttu-id="7992d-112">Описание</span><span class="sxs-lookup"><span data-stu-id="7992d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7992d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7992d-113">S_OK</span></span>|<span data-ttu-id="7992d-114">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="7992d-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7992d-115">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7992d-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7992d-116">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7992d-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7992d-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="7992d-117">Remarks</span></span>  
 <span data-ttu-id="7992d-118">В настоящее время единственное определенное значение для `dwInitializeDomainFlags` — `eInitializeNewDomainFlags_NoSecurityChanges`, которое сообщает общеязыковой среды выполнения (CLR), что диспетчер домена приложения не будет изменять параметры безопасности во время выполнения <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="7992d-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7992d-119">Это позволяет среде CLR для оптимизации загрузки сборок, которые имеют условное <xref:System.Security.AllowPartiallyTrustedCallersAttribute> атрибут (APTCA).</span><span class="sxs-lookup"><span data-stu-id="7992d-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="7992d-120">Это может привести к значительному улучшению время запуска при большом транзитивное замыкание этот набор сборок.</span><span class="sxs-lookup"><span data-stu-id="7992d-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7992d-121">Если узел указывает `eInitializeNewDomainFlags_NoSecurityChanges` для домена приложения, <xref:System.InvalidOperationException> возникает, если все возможные попытки для изменения уровня безопасности домена приложения.</span><span class="sxs-lookup"><span data-stu-id="7992d-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="7992d-122">Вызов [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)метода эквивалентен вызову `ICLRDomainManager::SetAppDomainManagerType` с `eInitializeNewDomainFlags_None`.</span><span class="sxs-lookup"><span data-stu-id="7992d-122">Calling the [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7992d-123">Требования</span><span class="sxs-lookup"><span data-stu-id="7992d-123">Requirements</span></span>  
 <span data-ttu-id="7992d-124">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7992d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7992d-125">**Заголовок.** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7992d-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7992d-126">**Библиотека:** Включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7992d-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7992d-127">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7992d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7992d-128">См. также</span><span class="sxs-lookup"><span data-stu-id="7992d-128">See also</span></span>

- [<span data-ttu-id="7992d-129">Размещение</span><span class="sxs-lookup"><span data-stu-id="7992d-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="7992d-130">Интерфейс ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="7992d-130">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [<span data-ttu-id="7992d-131">Перечисление EInitializeNewDomainFlags</span><span class="sxs-lookup"><span data-stu-id="7992d-131">EInitializeNewDomainFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
