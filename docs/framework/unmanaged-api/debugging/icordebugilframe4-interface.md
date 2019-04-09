---
title: Интерфейс ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b17c7630160af78fe3163e6962b8fe085af1edc1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206620"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="75f65-102">Интерфейс ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="75f65-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="75f65-103">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="75f65-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="75f65-104">Предоставляет методы, обеспечивающие доступ к локальным переменным и коду в кадре стека кода промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="75f65-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="75f65-105">Параметр показывает, имеет ли отладчик доступ к переменным и коду, добавленным в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="75f65-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75f65-106">Методы</span><span class="sxs-lookup"><span data-stu-id="75f65-106">Methods</span></span>  
  
|<span data-ttu-id="75f65-107">Метод</span><span class="sxs-lookup"><span data-stu-id="75f65-107">Method</span></span>|<span data-ttu-id="75f65-108">Описание</span><span class="sxs-lookup"><span data-stu-id="75f65-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75f65-109">Метод EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="75f65-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="75f65-110">Возвращает список локальных переменных, доступных в текущем кадре.</span><span class="sxs-lookup"><span data-stu-id="75f65-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="75f65-111">Метод GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="75f65-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="75f65-112">Возвращает код, который выполняется этим кадром стека.</span><span class="sxs-lookup"><span data-stu-id="75f65-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="75f65-113">Метод GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="75f65-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="75f65-114">Возвращает значение локальной переменной в кадре промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="75f65-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75f65-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="75f65-115">Remarks</span></span>  
 <span data-ttu-id="75f65-116">Эти методы обеспечивают функциональные возможности, предоставляемые [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), и [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) методы.</span><span class="sxs-lookup"><span data-stu-id="75f65-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="75f65-117">Каждый метод включает параметр `flags`, определяющий видимость дополнительных локальных переменных или кода, определенных ReJIT-запросом профилировщика.</span><span class="sxs-lookup"><span data-stu-id="75f65-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75f65-118">Требования</span><span class="sxs-lookup"><span data-stu-id="75f65-118">Requirements</span></span>  
 <span data-ttu-id="75f65-119">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75f65-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75f65-120">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75f65-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75f65-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75f65-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="75f65-122">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="75f65-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="75f65-123">См. также</span><span class="sxs-lookup"><span data-stu-id="75f65-123">See also</span></span>

- [<span data-ttu-id="75f65-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="75f65-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="75f65-125">Отладка</span><span class="sxs-lookup"><span data-stu-id="75f65-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
