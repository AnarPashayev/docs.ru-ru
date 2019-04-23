---
title: Интерфейс ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b0d67d390931cc92c0b6a1320f66545517cde3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223047"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="1f1b7-102">Интерфейс ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="1f1b7-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="1f1b7-103">Логически расширяет [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) интерфейс для предоставления сведений о загруженных модулях.</span><span class="sxs-lookup"><span data-stu-id="1f1b7-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="1f1b7-104">Метод</span><span class="sxs-lookup"><span data-stu-id="1f1b7-104">Method</span></span>  
  
|<span data-ttu-id="1f1b7-105">Метод</span><span class="sxs-lookup"><span data-stu-id="1f1b7-105">Method</span></span>|<span data-ttu-id="1f1b7-106">Описание</span><span class="sxs-lookup"><span data-stu-id="1f1b7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1f1b7-107">Метод GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="1f1b7-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="1f1b7-108">Возвращает список модулей, загруженных на данный момент.</span><span class="sxs-lookup"><span data-stu-id="1f1b7-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f1b7-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="1f1b7-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f1b7-110">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1f1b7-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1f1b7-111">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="1f1b7-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f1b7-112">Требования</span><span class="sxs-lookup"><span data-stu-id="1f1b7-112">Requirements</span></span>  
 <span data-ttu-id="1f1b7-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f1b7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f1b7-114">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f1b7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f1b7-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f1b7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f1b7-116">**Версии платформы .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f1b7-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f1b7-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1f1b7-117">See also</span></span>

- [<span data-ttu-id="1f1b7-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1f1b7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1f1b7-119">Отладка</span><span class="sxs-lookup"><span data-stu-id="1f1b7-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
