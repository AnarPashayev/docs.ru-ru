---
title: Перечисление EMemoryAvailable
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76fc5f578e6da731ffd6406344d00cda8b57f493
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772405"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="e90ec-102">Перечисление EMemoryAvailable</span><span class="sxs-lookup"><span data-stu-id="e90ec-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="e90ec-103">Содержит значения, указывающие объем свободной физической памяти на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e90ec-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="e90ec-104">Эти значения логически сопоставления с событиями для высокой и низкой память, возвращаемая вызовом `CreateMemoryResourceNotification` функции в Windows API.</span><span class="sxs-lookup"><span data-stu-id="e90ec-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e90ec-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e90ec-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="e90ec-106">Участники</span><span class="sxs-lookup"><span data-stu-id="e90ec-106">Members</span></span>  
  
|<span data-ttu-id="e90ec-107">Член</span><span class="sxs-lookup"><span data-stu-id="e90ec-107">Member</span></span>|<span data-ttu-id="e90ec-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e90ec-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="e90ec-109">Доступно множество физической памяти.</span><span class="sxs-lookup"><span data-stu-id="e90ec-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="e90ec-110">Доступна очень мало физической памяти.</span><span class="sxs-lookup"><span data-stu-id="e90ec-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="e90ec-111">Доступная физическая память является нейтральным.</span><span class="sxs-lookup"><span data-stu-id="e90ec-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e90ec-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="e90ec-112">Remarks</span></span>  
 <span data-ttu-id="e90ec-113">Это значение передается по основному приложению выполнения (CLR), используя вызов [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="e90ec-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e90ec-114">Требования</span><span class="sxs-lookup"><span data-stu-id="e90ec-114">Requirements</span></span>  
 <span data-ttu-id="e90ec-115">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e90ec-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e90ec-116">**Заголовок.** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e90ec-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e90ec-117">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e90ec-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e90ec-118">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e90ec-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e90ec-119">См. также</span><span class="sxs-lookup"><span data-stu-id="e90ec-119">See also</span></span>

- [<span data-ttu-id="e90ec-120">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="e90ec-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
