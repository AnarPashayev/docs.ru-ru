---
title: Перечисление EClrFailure
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19dacae05766566521f563d0d24980c01dfb7a0b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144291"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="2124d-102">Перечисление EClrFailure</span><span class="sxs-lookup"><span data-stu-id="2124d-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="2124d-103">Описывает набор сбоев, для которых узел может задать действия политики.</span><span class="sxs-lookup"><span data-stu-id="2124d-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2124d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2124d-104">Syntax</span></span>  
  
```  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="2124d-105">Участники</span><span class="sxs-lookup"><span data-stu-id="2124d-105">Members</span></span>  
  
|<span data-ttu-id="2124d-106">Член</span><span class="sxs-lookup"><span data-stu-id="2124d-106">Member</span></span>|<span data-ttu-id="2124d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="2124d-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="2124d-108">Произошла ошибка во время попытки выделения ресурсов (например, поток, блок памяти или блокировки) в некритические область кода.</span><span class="sxs-lookup"><span data-stu-id="2124d-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="2124d-109">Произошла ошибка при попытке выделить ресурс (например, поток, блок памяти или блокировки) в критической области кода.</span><span class="sxs-lookup"><span data-stu-id="2124d-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="2124d-110">Среда CLR (CLR) больше не может выполнять управляемый код в процессе.</span><span class="sxs-lookup"><span data-stu-id="2124d-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="2124d-111">Исходя из этого вызовов любого размещения функций возвращают значение HRESULT значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2124d-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="2124d-112">Поток не удалось снять блокировку возврата <xref:System.AppDomain> объекта.</span><span class="sxs-lookup"><span data-stu-id="2124d-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="2124d-113">Узел не удается задать удалось вызвать прерывание потока.</span><span class="sxs-lookup"><span data-stu-id="2124d-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="2124d-114">Произошло переполнение стека.</span><span class="sxs-lookup"><span data-stu-id="2124d-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="2124d-115">Была предпринята попытка чтения или записи в защищенную память.</span><span class="sxs-lookup"><span data-stu-id="2124d-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="2124d-116">Не поддерживается в [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2124d-116">Not supported in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="2124d-117">Сбой кода контракта.</span><span class="sxs-lookup"><span data-stu-id="2124d-117">A code contract failure occurred.</span></span> <span data-ttu-id="2124d-118">См. в разделе [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="2124d-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2124d-119">Примечания</span><span class="sxs-lookup"><span data-stu-id="2124d-119">Remarks</span></span>  
 <span data-ttu-id="2124d-120">См. в разделе [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) метод список [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) значения узла можно использовать для указания действия политики условий ошибки.</span><span class="sxs-lookup"><span data-stu-id="2124d-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="2124d-121">Дополнительные сведения о критических и некритических областях кода, см. в разделе [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2124d-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2124d-122">Требования</span><span class="sxs-lookup"><span data-stu-id="2124d-122">Requirements</span></span>  
 <span data-ttu-id="2124d-123">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2124d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2124d-124">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2124d-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2124d-125">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2124d-125">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2124d-126">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="2124d-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2124d-127">См. также</span><span class="sxs-lookup"><span data-stu-id="2124d-127">See also</span></span>

- [<span data-ttu-id="2124d-128">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="2124d-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="2124d-129">Метод SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="2124d-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="2124d-130">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="2124d-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="2124d-131">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="2124d-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
