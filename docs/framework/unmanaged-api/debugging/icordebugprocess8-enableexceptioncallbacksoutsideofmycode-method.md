---
title: Метод ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08937e87b8bd2249b8608f8ec1ed1f7734961b3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184838"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="c08fc-102">Метод ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode</span><span class="sxs-lookup"><span data-stu-id="c08fc-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="c08fc-103">[Поддерживается в [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] и более поздних версиях]</span><span class="sxs-lookup"><span data-stu-id="c08fc-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="c08fc-104">Включает или отключает определенные виды [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) обратных вызовов исключения.</span><span class="sxs-lookup"><span data-stu-id="c08fc-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c08fc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c08fc-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c08fc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c08fc-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="c08fc-107">[in]</span><span class="sxs-lookup"><span data-stu-id="c08fc-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c08fc-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="c08fc-108">Remarks</span></span>  
 <span data-ttu-id="c08fc-109">Если `enableExceptionsOutsideOfJMC` имеет значение `false`:</span><span class="sxs-lookup"><span data-stu-id="c08fc-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="c08fc-110">Исключение DEBUG_EXCEPTION_FIRST_CHANCE не приведет к обратный вызов к отладчику.</span><span class="sxs-lookup"><span data-stu-id="c08fc-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="c08fc-111">Исключение DEBUG_EXCEPTION_CATCH_HANDLER_FOUND не произойдет обратный вызов на отладчик Если исключение никогда не попадает в пользовательский код (то есть путь от источника исключения в обработчик исключений имеет нет методов, помеченных как JustMyCode или JMC).</span><span class="sxs-lookup"><span data-stu-id="c08fc-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="c08fc-112">Значением свойства `enableExceptionsOutsideOfJMC` по умолчанию является `true`.</span><span class="sxs-lookup"><span data-stu-id="c08fc-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c08fc-113">Требования</span><span class="sxs-lookup"><span data-stu-id="c08fc-113">Requirements</span></span>  
 <span data-ttu-id="c08fc-114">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c08fc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c08fc-115">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c08fc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c08fc-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c08fc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c08fc-117">**Версии платформы .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c08fc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c08fc-118">См. также</span><span class="sxs-lookup"><span data-stu-id="c08fc-118">See also</span></span>

- [<span data-ttu-id="c08fc-119">Интерфейс ICorDebugProcess8</span><span class="sxs-lookup"><span data-stu-id="c08fc-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="c08fc-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c08fc-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
