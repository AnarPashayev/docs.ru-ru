---
title: Функция CorBindToRuntimeByCfg
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbba208296dd2099c9da58c81ff66fddc78fdc86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093823"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="434d3-102">Функция CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="434d3-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="434d3-103">Загружает общеязыковой среды выполнения (CLR) в процесс, используя сведения о версии, которая фактически считывается из файла XML.</span><span class="sxs-lookup"><span data-stu-id="434d3-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="434d3-104">Эта функция устарели в [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="434d3-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="434d3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="434d3-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="434d3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="434d3-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="434d3-107">[in] Указатель на `IStream` объект, который считывает XML-файле.</span><span class="sxs-lookup"><span data-stu-id="434d3-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="434d3-108">[in] Зарезервировано для будущего использования.</span><span class="sxs-lookup"><span data-stu-id="434d3-108">[in] Reserved for future use.</span></span> <span data-ttu-id="434d3-109">Использовать в качестве значения 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="434d3-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="434d3-110">[in] Значение [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) перечисление, указывающее поведение при запуске среды CLR.</span><span class="sxs-lookup"><span data-stu-id="434d3-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="434d3-111">[in] `CLSID` Компонентного класса, реализующий [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) или [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) интерфейс.</span><span class="sxs-lookup"><span data-stu-id="434d3-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="434d3-112">Поддерживаемые значения: CLSID_CorRuntimeHost или CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="434d3-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="434d3-113">[in] `IID` Либо `ICorRuntimeHost` или `ICLRRuntimeHost` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="434d3-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="434d3-114">Поддерживаемые значения: IID_ICorRuntimeHost и IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="434d3-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="434d3-115">[out] Указатель на адрес возвращенный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="434d3-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="434d3-116">Примечания</span><span class="sxs-lookup"><span data-stu-id="434d3-116">Remarks</span></span>  
 <span data-ttu-id="434d3-117">Формат XML-файла моделируется стандартного файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="434d3-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="434d3-118">Дополнительные сведения о XML-файлов, см. в разделе [схема файла конфигурации](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="434d3-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="434d3-119">Требования</span><span class="sxs-lookup"><span data-stu-id="434d3-119">Requirements</span></span>  
 <span data-ttu-id="434d3-120">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="434d3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="434d3-121">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="434d3-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="434d3-122">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="434d3-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="434d3-123">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="434d3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434d3-124">См. также</span><span class="sxs-lookup"><span data-stu-id="434d3-124">See also</span></span>

- [<span data-ttu-id="434d3-125">Функция CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="434d3-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="434d3-126">Функция CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="434d3-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="434d3-127">Функция CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="434d3-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="434d3-128">Функция CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="434d3-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="434d3-129">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="434d3-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="434d3-130">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="434d3-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
