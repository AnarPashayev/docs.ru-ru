---
title: Метод ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db0e794953578fccd08428b730b3d7951e13bee3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074083"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="d0b07-102">Метод ICorDebugExceptionObjectValue::EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="d0b07-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="d0b07-103">Получает перечислитель для стека вызовов, внедренных в объект исключения.</span><span class="sxs-lookup"><span data-stu-id="d0b07-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0b07-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d0b07-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0b07-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="d0b07-105">Parameters</span></span>  
 <span data-ttu-id="d0b07-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="d0b07-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="d0b07-107">[out] Указатель на адрес [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) интерфейс объект, являющийся перечислитель трассировки стека для управляемого объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="d0b07-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0b07-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="d0b07-108">Remarks</span></span>  
 <span data-ttu-id="d0b07-109">Если доступен без сведений стека вызовов, метод возвращает `S_OK`, и [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) является допустимым перечислителем с длиной 0.</span><span class="sxs-lookup"><span data-stu-id="d0b07-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="d0b07-110">Если метод является не удалось получить сведения о трассировке стека, возвращаемое значение равно `E_FAIL` и возвращается перечислитель.</span><span class="sxs-lookup"><span data-stu-id="d0b07-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="d0b07-111">[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) объект отвечает за декодирование данные трассировки стека из `_stackTrace` поле объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="d0b07-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0b07-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d0b07-112">Requirements</span></span>  
 <span data-ttu-id="d0b07-113">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0b07-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0b07-114">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0b07-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0b07-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0b07-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d0b07-116">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d0b07-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d0b07-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d0b07-117">See also</span></span>

- [<span data-ttu-id="d0b07-118">Интерфейс ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="d0b07-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="d0b07-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d0b07-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
