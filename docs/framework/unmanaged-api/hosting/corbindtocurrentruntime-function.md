---
title: Функция CorBindToCurrentRuntime
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 505bba3bb5d08c13e29543c20df2daaebc863d12
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768003"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="9c015-102">Функция CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="9c015-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="9c015-103">Загружает общеязыковой среды выполнения (CLR) в процесс, используя сведения, хранящиеся в XML-файл.</span><span class="sxs-lookup"><span data-stu-id="9c015-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="9c015-104">Формат XML-файла моделируется стандартного файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="9c015-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="9c015-105">Дополнительные сведения о файлах конфигурации см. в разделе [Схема файла конфигурации](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c015-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="9c015-106">Эта функция является устаревшим в .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9c015-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="9c015-107">См. в разделе [загрузка среда CLR в процесс](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9c015-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c015-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9c015-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c015-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="9c015-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="9c015-110">[in] Имя файла конфигурации приложения, который указывает версию среды CLR для загрузки.</span><span class="sxs-lookup"><span data-stu-id="9c015-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="9c015-111">Если имя файла не указано полное имя, предполагается, что он является в том же каталоге, что и исполняемый файл, вызывающий.</span><span class="sxs-lookup"><span data-stu-id="9c015-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="9c015-112">Версия среды выполнения необходимо загрузить описан в атрибуте версии [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) элемент файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9c015-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="9c015-113">Если версия не указана или если `<requiredRuntime>` элемент не найден, загружается последняя версия среды CLR, которая установлена на компьютере.</span><span class="sxs-lookup"><span data-stu-id="9c015-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9c015-114">[in] `CLSID` Компонентного класса, реализующий [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) или [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9c015-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9c015-115">Поддерживаемые значения: CLSID_CorRuntimeHost или CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9c015-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9c015-116">[in] `IID` Интерфейса, для которого запрашивается.</span><span class="sxs-lookup"><span data-stu-id="9c015-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="9c015-117">Поддерживаемые значения: IID_ICorRuntimeHost и IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9c015-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9c015-118">[out] Возвращаемый указатель интерфейса.</span><span class="sxs-lookup"><span data-stu-id="9c015-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c015-119">Требования</span><span class="sxs-lookup"><span data-stu-id="9c015-119">Requirements</span></span>  
 <span data-ttu-id="9c015-120">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c015-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c015-121">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9c015-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c015-122">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c015-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c015-123">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c015-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c015-124">См. также</span><span class="sxs-lookup"><span data-stu-id="9c015-124">See also</span></span>

- [<span data-ttu-id="9c015-125">Функция CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="9c015-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="9c015-126">Функция CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="9c015-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="9c015-127">Функция CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="9c015-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="9c015-128">Функция CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9c015-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="9c015-129">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9c015-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="9c015-130">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="9c015-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
