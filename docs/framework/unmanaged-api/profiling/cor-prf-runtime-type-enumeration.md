---
title: Перечисление COR_PRF_RUNTIME_TYPE
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
ms.openlocfilehash: b599a97f414491ff80000f99551a727b86ae13de
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696756"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="76d41-102">Перечисление COR_PRF_RUNTIME_TYPE</span><span class="sxs-lookup"><span data-stu-id="76d41-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>

<span data-ttu-id="76d41-103">Содержит значения, указывающие версию среды CLR: Desktop или CoreCLR, которая используется в Silverlight.</span><span class="sxs-lookup"><span data-stu-id="76d41-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d41-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="76d41-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="76d41-105">Члены</span><span class="sxs-lookup"><span data-stu-id="76d41-105">Members</span></span>  
  
|<span data-ttu-id="76d41-106">Член</span><span class="sxs-lookup"><span data-stu-id="76d41-106">Member</span></span>|<span data-ttu-id="76d41-107">Описание</span><span class="sxs-lookup"><span data-stu-id="76d41-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="76d41-108">Версия среды CLR для настольных систем.</span><span class="sxs-lookup"><span data-stu-id="76d41-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="76d41-109">Основная версия среды CLR, используемая в Silverlight.</span><span class="sxs-lookup"><span data-stu-id="76d41-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76d41-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="76d41-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76d41-111">Требования</span><span class="sxs-lookup"><span data-stu-id="76d41-111">Requirements</span></span>  

 <span data-ttu-id="76d41-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76d41-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76d41-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="76d41-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76d41-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76d41-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76d41-115">**.NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76d41-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d41-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="76d41-116">See also</span></span>

- [<span data-ttu-id="76d41-117">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="76d41-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
