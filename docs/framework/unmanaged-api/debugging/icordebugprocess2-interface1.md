---
title: Интерфейс ICorDebugProcess2
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b3bb51f307093ea1cc8cc45064d5c405974822
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178026"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="7b1ef-102">Интерфейс ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="7b1ef-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="7b1ef-103">Логическим расширением интерфейса ICorDebugProcess, который представляет процесс выполнение управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="7b1ef-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b1ef-104">Методы</span><span class="sxs-lookup"><span data-stu-id="7b1ef-104">Methods</span></span>  
  
|<span data-ttu-id="7b1ef-105">Метод</span><span class="sxs-lookup"><span data-stu-id="7b1ef-105">Method</span></span>|<span data-ttu-id="7b1ef-106">Описание</span><span class="sxs-lookup"><span data-stu-id="7b1ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b1ef-107">Метод ClearUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7b1ef-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="7b1ef-108">Удаляет точку останова с указанным смещением, установленное с предыдущими вызовами `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="7b1ef-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="7b1ef-109">Метод GetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="7b1ef-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="7b1ef-110">Получает флаги, которые должны быть заданы для общеязыковой среды выполнения (CLR) для загрузки изображения в процесс, который ссылается этот `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="7b1ef-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="7b1ef-111">Метод GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="7b1ef-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="7b1ef-112">Получает указатель ссылки на указанный управляемый объект, с дескриптором сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="7b1ef-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="7b1ef-113">Метод GetThreadForTaskID</span><span class="sxs-lookup"><span data-stu-id="7b1ef-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="7b1ef-114">Получает поток, на котором выполняется задача с указанным идентификатором.</span><span class="sxs-lookup"><span data-stu-id="7b1ef-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="7b1ef-115">Метод GetVersion</span><span class="sxs-lookup"><span data-stu-id="7b1ef-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="7b1ef-116">Получает версию среды CLR, на котором выполняется отлаживаемый процесс.</span><span class="sxs-lookup"><span data-stu-id="7b1ef-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="7b1ef-117">Метод SetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="7b1ef-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="7b1ef-118">Задает флаги, которые требуются для компилятор just-in-time (JIT) для загрузки изображения в отлаживаемом процессе.</span><span class="sxs-lookup"><span data-stu-id="7b1ef-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="7b1ef-119">Метод SetUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7b1ef-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="7b1ef-120">Задает неуправляемую точку останова с указанным образов в машинном коде смещения.</span><span class="sxs-lookup"><span data-stu-id="7b1ef-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b1ef-121">Примечания</span><span class="sxs-lookup"><span data-stu-id="7b1ef-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b1ef-122">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="7b1ef-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b1ef-123">Требования</span><span class="sxs-lookup"><span data-stu-id="7b1ef-123">Requirements</span></span>  
 <span data-ttu-id="7b1ef-124">**Платформы:** См. раздел [Требования к системе](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b1ef-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b1ef-125">**Заголовок.** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b1ef-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b1ef-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b1ef-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7b1ef-127">Версии платформы .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7b1ef-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7b1ef-128">См. также</span><span class="sxs-lookup"><span data-stu-id="7b1ef-128">See also</span></span>

- [<span data-ttu-id="7b1ef-129">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7b1ef-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
