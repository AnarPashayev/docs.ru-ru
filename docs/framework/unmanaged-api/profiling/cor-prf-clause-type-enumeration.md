---
title: Перечисление COR_PRF_CLAUSE_TYPE
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 861f4c18f4c5151dc7215d300775928b88f018aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090632"
---
# <a name="corprfclausetype-enumeration"></a><span data-ttu-id="a70f7-102">Перечисление COR_PRF_CLAUSE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a70f7-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="a70f7-103">Указывает тип предложения исключения, код которого был только что введен или удален.</span><span class="sxs-lookup"><span data-stu-id="a70f7-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a70f7-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a70f7-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="a70f7-105">Участники</span><span class="sxs-lookup"><span data-stu-id="a70f7-105">Members</span></span>  
  
|<span data-ttu-id="a70f7-106">Член</span><span class="sxs-lookup"><span data-stu-id="a70f7-106">Member</span></span>|<span data-ttu-id="a70f7-107">Описание</span><span class="sxs-lookup"><span data-stu-id="a70f7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="a70f7-108">Предложение исключения является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="a70f7-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="a70f7-109">Предложение исключения является выражением фильтра.</span><span class="sxs-lookup"><span data-stu-id="a70f7-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="a70f7-110">Предложение исключения является `catch` инструкции.</span><span class="sxs-lookup"><span data-stu-id="a70f7-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="a70f7-111">Предложение исключения является `finally` инструкции.</span><span class="sxs-lookup"><span data-stu-id="a70f7-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a70f7-112">Требования</span><span class="sxs-lookup"><span data-stu-id="a70f7-112">Requirements</span></span>  
 <span data-ttu-id="a70f7-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a70f7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a70f7-114">**Заголовок.** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a70f7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a70f7-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a70f7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a70f7-116">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a70f7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a70f7-117">См. также</span><span class="sxs-lookup"><span data-stu-id="a70f7-117">See also</span></span>

- [<span data-ttu-id="a70f7-118">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="a70f7-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
