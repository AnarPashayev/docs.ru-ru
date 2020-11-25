---
title: Функция GetCachePath
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
ms.openlocfilehash: c22f0701cfda4523f595366a97435ef8da08b0cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724472"
---
# <a name="getcachepath-function"></a><span data-ttu-id="7bfa3-102">Функция GetCachePath</span><span class="sxs-lookup"><span data-stu-id="7bfa3-102">GetCachePath Function</span></span>

<span data-ttu-id="7bfa3-103">Возвращает путь к кэшированной сборке с использованием указанных флагов.</span><span class="sxs-lookup"><span data-stu-id="7bfa3-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bfa3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7bfa3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bfa3-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="7bfa3-105">Parameters</span></span>  

 `dwCacheFlags`  
 <span data-ttu-id="7bfa3-106">окне Значение [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) , указывающее источник кэшированной сборки.</span><span class="sxs-lookup"><span data-stu-id="7bfa3-106">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="7bfa3-107">заполняет Возвращаемый указатель на путь.</span><span class="sxs-lookup"><span data-stu-id="7bfa3-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="7bfa3-108">[вход, выход] Запрошенная максимальная длина `pwzCachePath` и при возврате фактической длины `pwzCachePath` .</span><span class="sxs-lookup"><span data-stu-id="7bfa3-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bfa3-109">Требования</span><span class="sxs-lookup"><span data-stu-id="7bfa3-109">Requirements</span></span>  

 <span data-ttu-id="7bfa3-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bfa3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bfa3-111">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="7bfa3-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7bfa3-112">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bfa3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfa3-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7bfa3-113">See also</span></span>

- [<span data-ttu-id="7bfa3-114">Перечисление ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="7bfa3-114">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="7bfa3-115">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="7bfa3-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
