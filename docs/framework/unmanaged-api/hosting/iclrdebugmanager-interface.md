---
title: Интерфейс ICLRDebugManager
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a408995793caf879f8d5624ab727102c4859195
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959614"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="43d6a-102">Интерфейс ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="43d6a-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="43d6a-103">Предоставляет методы, позволяющие узлу связать набор задач с идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="43d6a-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43d6a-104">Методы</span><span class="sxs-lookup"><span data-stu-id="43d6a-104">Methods</span></span>  
  
|<span data-ttu-id="43d6a-105">Метод</span><span class="sxs-lookup"><span data-stu-id="43d6a-105">Method</span></span>|<span data-ttu-id="43d6a-106">Описание</span><span class="sxs-lookup"><span data-stu-id="43d6a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43d6a-107">Метод BeginConnection</span><span class="sxs-lookup"><span data-stu-id="43d6a-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="43d6a-108">Устанавливает новое соединение между узлом и отладчиком для связывания задач с идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="43d6a-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="43d6a-109">Метод EndConnection</span><span class="sxs-lookup"><span data-stu-id="43d6a-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="43d6a-110">Удаляет связь между списком задач и идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="43d6a-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="43d6a-111">Метод GetDacl</span><span class="sxs-lookup"><span data-stu-id="43d6a-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="43d6a-112">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="43d6a-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="43d6a-113">Метод IsDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="43d6a-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="43d6a-114">Получает значение, показывающее, присоединен ли отладчик к процессу.</span><span class="sxs-lookup"><span data-stu-id="43d6a-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="43d6a-115">Метод SetConnectionTasks</span><span class="sxs-lookup"><span data-stu-id="43d6a-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="43d6a-116">Связывает список экземпляров [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) с идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="43d6a-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="43d6a-117">Метод SetDacl</span><span class="sxs-lookup"><span data-stu-id="43d6a-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="43d6a-118">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="43d6a-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="43d6a-119">Метод SetSymbolReadingPolicy</span><span class="sxs-lookup"><span data-stu-id="43d6a-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="43d6a-120">Задает политику чтения файлов базы данных программы (PDB).</span><span class="sxs-lookup"><span data-stu-id="43d6a-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="43d6a-121">Политика определяет, включаются ли в стеки вызовов сведения о номерах строк и файлах.</span><span class="sxs-lookup"><span data-stu-id="43d6a-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43d6a-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="43d6a-122">Remarks</span></span>  
 <span data-ttu-id="43d6a-123">В сценариях отладки узлу может потребоваться сгруппировать задачи в соответствии с собственной логикой программирования.</span><span class="sxs-lookup"><span data-stu-id="43d6a-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="43d6a-124">Например, группирование позволит разработчику видеть только задачи, необходимые API разработчика, а не выполнять все задачи, выполняемые в процессе.</span><span class="sxs-lookup"><span data-stu-id="43d6a-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="43d6a-125">`ICLRDebugManager`позволяет ведущему приложению реализовать такой тип группирования.</span><span class="sxs-lookup"><span data-stu-id="43d6a-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="43d6a-126">Три `ICLRDebugManager` метода `BeginConnection` ,и`EndConnection`,зависят друг от друга. `SetConnectionTasks`</span><span class="sxs-lookup"><span data-stu-id="43d6a-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="43d6a-127">Их необходимо вызывать в заданном порядке, чтобы работать должным образом.</span><span class="sxs-lookup"><span data-stu-id="43d6a-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="43d6a-128">Группирование и идентификаторы и понятные имена, которые узел назначает группе, не имеют смысла для среды CLR.</span><span class="sxs-lookup"><span data-stu-id="43d6a-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="43d6a-129">CLR просто передает информацию в отладчик.</span><span class="sxs-lookup"><span data-stu-id="43d6a-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43d6a-130">Требования</span><span class="sxs-lookup"><span data-stu-id="43d6a-130">Requirements</span></span>  
 <span data-ttu-id="43d6a-131">**Платформ** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43d6a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43d6a-132">**Заголовок.** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="43d6a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43d6a-133">**Библиотечная** Включается в качестве ресурса в библиотеку MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="43d6a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43d6a-134">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43d6a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43d6a-135">См. также</span><span class="sxs-lookup"><span data-stu-id="43d6a-135">See also</span></span>

- [<span data-ttu-id="43d6a-136">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="43d6a-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
