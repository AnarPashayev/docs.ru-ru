---
title: Интерфейс IXCLRDataProcess
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ff74a7acb5cc84c177f083c19402cd78977aeab5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775249"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="60294-102">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="60294-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="60294-103">Предоставляет методы для запроса на получение сведений о процессе.</span><span class="sxs-lookup"><span data-stu-id="60294-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="60294-104">Методы</span><span class="sxs-lookup"><span data-stu-id="60294-104">Methods</span></span>

| <span data-ttu-id="60294-105">Метод</span><span class="sxs-lookup"><span data-stu-id="60294-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="60294-106">Описание</span><span class="sxs-lookup"><span data-stu-id="60294-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="60294-107">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="60294-107">GetAppDomainByUniqueId</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="60294-108">Получает `AppDomain` в процессе по ее уникальному идентификатору.</span><span class="sxs-lookup"><span data-stu-id="60294-108">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="60294-109">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="60294-109">StartEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="60294-110">Предоставляет маркер, чтобы перечислить модули, процесса.</span><span class="sxs-lookup"><span data-stu-id="60294-110">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="60294-111">EnumModule</span><span class="sxs-lookup"><span data-stu-id="60294-111">EnumModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="60294-112">Перечисляет модули этого процесса.</span><span class="sxs-lookup"><span data-stu-id="60294-112">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="60294-113">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="60294-113">EndEnumModules</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="60294-114">Освобождает ресурсы, используемые внутренней итераторы, используемые при перечислении модуля.</span><span class="sxs-lookup"><span data-stu-id="60294-114">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="60294-115">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="60294-115">StartEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="60294-116">Предоставляет дескриптор для перечисления экземпляров метод `AppDomain` начиная с данного адреса.</span><span class="sxs-lookup"><span data-stu-id="60294-116">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="60294-117">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="60294-117">EnumMethodInstanceByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="60294-118">Перечисление экземпляров метод класса этот процесс, начиная с смещение адреса.</span><span class="sxs-lookup"><span data-stu-id="60294-118">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="60294-119">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="60294-119">EndEnumMethodInstancesByAddress</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="60294-120">Освобождает ресурсы, используемые внутренней итераторы, используется в процессе экземпляра перечисления.</span><span class="sxs-lookup"><span data-stu-id="60294-120">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="60294-121">Примечания</span><span class="sxs-lookup"><span data-stu-id="60294-121">Remarks</span></span>

<span data-ttu-id="60294-122">Этот интерфейс находится внутри среды выполнения и не предоставляется через любой заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="60294-122">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="60294-123">Однако это COM-интерфейс, наследуемый от `IUnknown` с идентификатором GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` , можно получить с помощью обычных механизмов COM.</span><span class="sxs-lookup"><span data-stu-id="60294-123">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="60294-124">Требования</span><span class="sxs-lookup"><span data-stu-id="60294-124">Requirements</span></span>

<span data-ttu-id="60294-125">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60294-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="60294-126">**Заголовок.** Нет</span><span class="sxs-lookup"><span data-stu-id="60294-126">**Header:** None</span></span>  
<span data-ttu-id="60294-127">**Библиотека:** Нет</span><span class="sxs-lookup"><span data-stu-id="60294-127">**Library:** None</span></span>  
<span data-ttu-id="60294-128">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="60294-128">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="60294-129">См. также</span><span class="sxs-lookup"><span data-stu-id="60294-129">See also</span></span>

- [<span data-ttu-id="60294-130">Отладка</span><span class="sxs-lookup"><span data-stu-id="60294-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="60294-131">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="60294-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
