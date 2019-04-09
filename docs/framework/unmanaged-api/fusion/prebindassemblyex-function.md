---
title: Функция PreBindAssemblyEx
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8251d21fe535f85cc6abd0a7bc6c96ab320007f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090242"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="fce4b-102">Функция PreBindAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="fce4b-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="fce4b-103">Возвращает после применения политики отображаемое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="fce4b-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="fce4b-104">Эта функция поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="fce4b-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fce4b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fce4b-105">Syntax</span></span>  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="fce4b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fce4b-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="fce4b-107">[in] Определяет контекст приложения.</span><span class="sxs-lookup"><span data-stu-id="fce4b-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="fce4b-108">[in] Обозначает имя сборки.</span><span class="sxs-lookup"><span data-stu-id="fce4b-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="fce4b-109">[in] Идентифицирует родительской сборки.</span><span class="sxs-lookup"><span data-stu-id="fce4b-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="fce4b-110">Этот параметр не учитывается.</span><span class="sxs-lookup"><span data-stu-id="fce4b-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="fce4b-111">[in] Определяет версию среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="fce4b-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="fce4b-112">[out] Содержит имя отображаемое после применения политики.</span><span class="sxs-lookup"><span data-stu-id="fce4b-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="fce4b-113">[in] Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="fce4b-113">[in] Reserved for future extensibility.</span></span> `pvReserved` <span data-ttu-id="fce4b-114">должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="fce4b-114">must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fce4b-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="fce4b-115">Remarks</span></span>  
 <span data-ttu-id="fce4b-116">`ppNamePostPolicy` Выходной параметр имеет значение только в том случае, если функция возвращает значение HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="fce4b-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="fce4b-117">В противном случае — значение null.</span><span class="sxs-lookup"><span data-stu-id="fce4b-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fce4b-118">Требования</span><span class="sxs-lookup"><span data-stu-id="fce4b-118">Requirements</span></span>  
 <span data-ttu-id="fce4b-119">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fce4b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fce4b-120">**Заголовок.** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="fce4b-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fce4b-121">**Библиотека:** Включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fce4b-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="fce4b-122">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fce4b-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fce4b-123">См. также</span><span class="sxs-lookup"><span data-stu-id="fce4b-123">See also</span></span>

- [<span data-ttu-id="fce4b-124">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="fce4b-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
