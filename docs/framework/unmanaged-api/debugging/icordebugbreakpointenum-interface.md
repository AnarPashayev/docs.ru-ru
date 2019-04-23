---
title: Интерфейс ICorDebugBreakpointEnum
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fd42f13f699b0b79fd69311186f2b2ca0c9998a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149075"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="17da1-102">Интерфейс ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="17da1-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="17da1-103">Реализует методы ICorDebugEnum и выполняет перечисление массивов ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="17da1-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17da1-104">Методы</span><span class="sxs-lookup"><span data-stu-id="17da1-104">Methods</span></span>  
  
|<span data-ttu-id="17da1-105">Метод</span><span class="sxs-lookup"><span data-stu-id="17da1-105">Method</span></span>|<span data-ttu-id="17da1-106">Описание</span><span class="sxs-lookup"><span data-stu-id="17da1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17da1-107">Метод Next</span><span class="sxs-lookup"><span data-stu-id="17da1-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="17da1-108">Возвращает заданное число `ICorDebugBreakpoint` экземпляров из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="17da1-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17da1-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="17da1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17da1-110">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="17da1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17da1-111">Требования</span><span class="sxs-lookup"><span data-stu-id="17da1-111">Requirements</span></span>  
 <span data-ttu-id="17da1-112">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17da1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17da1-113">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17da1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17da1-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17da1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17da1-115">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17da1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17da1-116">См. также</span><span class="sxs-lookup"><span data-stu-id="17da1-116">See also</span></span>

- [<span data-ttu-id="17da1-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="17da1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
