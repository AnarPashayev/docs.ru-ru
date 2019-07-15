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
ms.openlocfilehash: 5f3e39d94996f14f1ae6593b9adaa5db3ef674c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769664"
---
# <a name="eclrfailure-enumeration"></a>Перечисление EClrFailure
Описывает набор сбоев, для которых узел может задать действия политики.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|Произошла ошибка во время попытки выделения ресурсов (например, поток, блок памяти или блокировки) в некритические область кода.|  
|`FAIL_CriticalResource`|Произошла ошибка при попытке выделить ресурс (например, поток, блок памяти или блокировки) в критической области кода.|  
|`FAIL_FatalRuntime`|Среда CLR (CLR) больше не может выполнять управляемый код в процессе. Исходя из этого вызовов любого размещения функций возвращают значение HRESULT значение HOST_E_CLRNOTAVAILABLE.|  
|`FAIL_OrphanedLock`|Поток не удалось снять блокировку возврата <xref:System.AppDomain> объекта. Узел не удается задать удалось вызвать прерывание потока.|  
|`FAIL_StackOverflow`|Произошло переполнение стека.|  
|`FAIL_AccessViolation`|Была предпринята попытка чтения или записи в защищенную память. Не поддерживается в .NET Framework 4.|  
|`FAIL_CodeContract`|Сбой кода контракта. См. в разделе [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Примечания  
 См. в разделе [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) метод список [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) значения узла можно использовать для указания действия политики условий ошибки. Дополнительные сведения о критических и некритических областях кода, см. в разделе [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Требования  
 **Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок.** MSCorEE.h  
  
 **Библиотека:** MSCorEE.dll  
  
 **Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также

- [Интерфейс ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [Метод SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [Интерфейс IHostPolicyManager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Размещение перечислений](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
