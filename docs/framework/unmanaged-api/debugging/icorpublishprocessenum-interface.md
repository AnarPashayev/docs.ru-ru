---
title: Интерфейс ICorPublishProcessEnum
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5186df61eb82b29fcfa9776408498b748068e122
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173658"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="b3c29-102">Интерфейс ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="b3c29-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="b3c29-103">Подкласс [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) интерфейс, который предоставляет методы для обхода коллекции [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) объектов.</span><span class="sxs-lookup"><span data-stu-id="b3c29-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3c29-104">Методы</span><span class="sxs-lookup"><span data-stu-id="b3c29-104">Methods</span></span>  
  
|<span data-ttu-id="b3c29-105">Метод</span><span class="sxs-lookup"><span data-stu-id="b3c29-105">Method</span></span>|<span data-ttu-id="b3c29-106">Описание</span><span class="sxs-lookup"><span data-stu-id="b3c29-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3c29-107">Метод Next</span><span class="sxs-lookup"><span data-stu-id="b3c29-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="b3c29-108">Возвращает заданное число `ICorPublishProcess` экземпляров из коллекции, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="b3c29-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3c29-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="b3c29-109">Remarks</span></span>  
 <span data-ttu-id="b3c29-110">`ICorPublishProcessEnum` Интерфейс реализует методы интерфейса абстрактный, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b3c29-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="b3c29-111">`ICorPublishProcessEnum` Создал экземпляр [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="b3c29-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="b3c29-112">Обход коллекцию `ICorPublishProcess` объектов зависит от условия фильтра, предоставленных во время `ICorPublishProcessEnum` был создан экземпляр.</span><span class="sxs-lookup"><span data-stu-id="b3c29-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3c29-113">Требования</span><span class="sxs-lookup"><span data-stu-id="b3c29-113">Requirements</span></span>  
 <span data-ttu-id="b3c29-114">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3c29-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3c29-115">**Заголовок.** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b3c29-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b3c29-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3c29-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3c29-117">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3c29-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c29-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b3c29-118">See also</span></span>

- [<span data-ttu-id="b3c29-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b3c29-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b3c29-120">Кокласс CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="b3c29-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
