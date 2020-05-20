---
title: Метод ICLRDomainManager::SetPropertiesForDefaultAppDomain
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
ms.openlocfilehash: 5e1c1b1984c63bedb3c073f45a7b9a3574afdcec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615687"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="ada64-102">Метод ICLRDomainManager::SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="ada64-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="ada64-103">Задает свойства, которые будут использоваться для инициализации домена приложения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ada64-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada64-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ada64-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ada64-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="ada64-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="ada64-106">окне Число записей в `pwszPropertyNames` и `pwszPropertyValues` .</span><span class="sxs-lookup"><span data-stu-id="ada64-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="ada64-107">окне Массив имен свойств или значение null, если свойства отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="ada64-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="ada64-108">В настоящее время единственным именем свойства, распознаваемым этим методом, является "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span><span class="sxs-lookup"><span data-stu-id="ada64-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="ada64-109">окне Массив значений свойств или значение null, если свойства отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="ada64-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ada64-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ada64-110">Return Value</span></span>  
 <span data-ttu-id="ada64-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="ada64-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ada64-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ada64-112">HRESULT</span></span>|<span data-ttu-id="ada64-113">Описание</span><span class="sxs-lookup"><span data-stu-id="ada64-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ada64-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ada64-114">S_OK</span></span>|<span data-ttu-id="ada64-115">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="ada64-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="ada64-116">HRESULT_FROM_WIN32 (ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="ada64-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="ada64-117">`pwszPropertyNames`содержит имя свойства, которое не распознается этим методом.</span><span class="sxs-lookup"><span data-stu-id="ada64-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ada64-118">Комментарии</span><span class="sxs-lookup"><span data-stu-id="ada64-118">Remarks</span></span>  
 <span data-ttu-id="ada64-119">Значение свойства для "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" — это список сборок, имеющих условный <xref:System.Security.AllowPartiallyTrustedCallersAttribute> атрибут (APTCA) с <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> флагом, который должен быть видимым для частично доверенных вызывающих объектов в домене приложения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ada64-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ada64-120">Требования</span><span class="sxs-lookup"><span data-stu-id="ada64-120">Requirements</span></span>  
 <span data-ttu-id="ada64-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ada64-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada64-122">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="ada64-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ada64-123">**Библиотека:** Включается в качестве ресурса в библиотеку MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ada64-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ada64-124">**.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada64-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada64-125">См. также статью</span><span class="sxs-lookup"><span data-stu-id="ada64-125">See also</span></span>

- [<span data-ttu-id="ada64-126">Размещение</span><span class="sxs-lookup"><span data-stu-id="ada64-126">Hosting</span></span>](index.md)
- [<span data-ttu-id="ada64-127">Интерфейс ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="ada64-127">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
