---
title: Перечисления отладки
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: bdd4b60d068677ae2a0874b589294ba220f0d854
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723003"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="4b555-102">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="4b555-102">Debugging Enumerations</span></span>

<span data-ttu-id="4b555-103">В этом разделе описываются неуправляемые перечисления, которые использует API отладки.</span><span class="sxs-lookup"><span data-stu-id="4b555-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b555-104">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="4b555-104">In This Section</span></span>  

 [<span data-ttu-id="4b555-105">Перечисление CLR_DEBUGGING_PROCESS_FLAGS</span><span class="sxs-lookup"><span data-stu-id="4b555-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="4b555-106">Предоставляет значения, используемые методом [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4b555-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="4b555-107">Перечисление CLRDataEnumMemoryFlags</span><span class="sxs-lookup"><span data-stu-id="4b555-107">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="4b555-108">Указывает, к каким областям памяти должен быть вызван вызов метода [иклрдатаенуммеморирегионс:: енуммеморирегионс](iclrdataenummemoryregions-enummemoryregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4b555-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="4b555-109">Перечисление COR_PUB_ENUMPROCESS</span><span class="sxs-lookup"><span data-stu-id="4b555-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="4b555-110">Идентифицирует тип процесса для перечисления.</span><span class="sxs-lookup"><span data-stu-id="4b555-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="4b555-111">Перечисление CorDebugBlockingReason</span><span class="sxs-lookup"><span data-stu-id="4b555-111">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="4b555-112">Указывает возможные причины блокировки потока на данном объекте.</span><span class="sxs-lookup"><span data-stu-id="4b555-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="4b555-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="4b555-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="4b555-114">Указывает причину или причины запуска цепочки вызовов.</span><span class="sxs-lookup"><span data-stu-id="4b555-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="4b555-115">Перечисление CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="4b555-115">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="4b555-116">Описывает, каким образом экспортируемая функция вызывает управляемый код.</span><span class="sxs-lookup"><span data-stu-id="4b555-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="4b555-117">Перечисление CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="4b555-117">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="4b555-118">Описывает, почему экспортируемая функция вызывает управляемый код.</span><span class="sxs-lookup"><span data-stu-id="4b555-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="4b555-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="4b555-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="4b555-120">Предоставляет дополнительные параметры отладки, которые можно использовать при вызове метода [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4b555-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="4b555-121">Перечисление CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="4b555-121">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="4b555-122">Указывает тип события, сведения о котором декодированы методом [DecodeEvent](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4b555-122">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="4b555-123">Перечисление CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="4b555-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="4b555-124">Предоставляет дополнительную информацию о событиях отладки на платформе Windows.</span><span class="sxs-lookup"><span data-stu-id="4b555-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="4b555-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="4b555-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="4b555-126">Указывает тип обратного вызова, сделанный из события [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4b555-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="4b555-127">Перечисление CorDebugExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="4b555-127">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="4b555-128">Предоставляет дополнительные сведения об исключении.</span><span class="sxs-lookup"><span data-stu-id="4b555-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="4b555-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="4b555-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="4b555-130">Указывает событие, о котором сообщает обратный вызов во время фазы перемотки.</span><span class="sxs-lookup"><span data-stu-id="4b555-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="4b555-131">Перечисление CorDebugGCType</span><span class="sxs-lookup"><span data-stu-id="4b555-131">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="4b555-132">Указывает, где выполняется сборщик мусора: на рабочей станции или на сервере.</span><span class="sxs-lookup"><span data-stu-id="4b555-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="4b555-133">Перечисление CorDebugGenerationTypes</span><span class="sxs-lookup"><span data-stu-id="4b555-133">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="4b555-134">Указывает на создание области памяти в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="4b555-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="4b555-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="4b555-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="4b555-136">Указывает тип обработки.</span><span class="sxs-lookup"><span data-stu-id="4b555-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="4b555-137">Перечисление CorDebugIlToNativeMappingTypes</span><span class="sxs-lookup"><span data-stu-id="4b555-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="4b555-138">Указывает, соответствует ли определенный диапазон машинных инструкций специальной области кода.</span><span class="sxs-lookup"><span data-stu-id="4b555-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="4b555-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="4b555-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="4b555-140">Указывает типы кода, который может быть пошагово выполнен.</span><span class="sxs-lookup"><span data-stu-id="4b555-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="4b555-141">Перечисление CorDebugInterfaceVersion</span><span class="sxs-lookup"><span data-stu-id="4b555-141">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="4b555-142">Указывает либо версию платформы .NET Framework, либо версию платформы .NET Framework, в которой был представлен интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4b555-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="4b555-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="4b555-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="4b555-144">Указывает тип кадра стека.</span><span class="sxs-lookup"><span data-stu-id="4b555-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="4b555-145">Перечисление CorDebugJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="4b555-145">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="4b555-146">Содержит значения, которые влияют на поведение управляемого JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="4b555-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="4b555-147">Перечисление CorDebugJITCompilerFlagsDeprecated</span><span class="sxs-lookup"><span data-stu-id="4b555-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="4b555-148">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="4b555-148">Obsolete.</span></span> <span data-ttu-id="4b555-149">`CORDEBUG_JIT_DEFAULT`Вместо этого используйте член перечисления [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4b555-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="4b555-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="4b555-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="4b555-151">Предоставляет сведения о том, как было получено значение указателя инструкций.</span><span class="sxs-lookup"><span data-stu-id="4b555-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="4b555-152">Перечисление CorDebugMDAFlags</span><span class="sxs-lookup"><span data-stu-id="4b555-152">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="4b555-153">Указывает состояние потока, по которому был вызван помощник по отладке управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="4b555-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="4b555-154">Перечисление CorDebugNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="4b555-154">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="4b555-155">Предоставляет значение, который определяет, загружает ли отладчик образы в машинном коде (NGen) из кэша образов в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="4b555-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="4b555-156">Перечисление CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="4b555-156">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="4b555-157">Предоставляет значения целевой платформы, используемые методом [ICorDebugDataTarget::](icordebugdatatarget-getplatform-method.md) WebMethod.</span><span class="sxs-lookup"><span data-stu-id="4b555-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="4b555-158">Перечисление CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="4b555-158">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="4b555-159">Описывает формат данных в массиве байтов, который содержит информацию о событии отладки собственного исключения.</span><span class="sxs-lookup"><span data-stu-id="4b555-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="4b555-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="4b555-160">CorDebugRegister</span></span>  
 <span data-ttu-id="4b555-161">Указывает регистры, связанные с данной архитектурой процессора.</span><span class="sxs-lookup"><span data-stu-id="4b555-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="4b555-162">Перечисление CorDebugSetContextFlag</span><span class="sxs-lookup"><span data-stu-id="4b555-162">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="4b555-163">Указывает происхождение контекста: взят из активного (или листового) кадра в стеке или был вычислен в результате освобождения другого кадра.</span><span class="sxs-lookup"><span data-stu-id="4b555-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="4b555-164">Перечисление CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="4b555-164">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="4b555-165">Описывает объем кэшированных данных, которые должны быть отброшены на основе изменений, внесенных в процесс.</span><span class="sxs-lookup"><span data-stu-id="4b555-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="4b555-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="4b555-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="4b555-167">Указывает результат отдельного шага.</span><span class="sxs-lookup"><span data-stu-id="4b555-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="4b555-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="4b555-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="4b555-169">Указывает состояние потока для отладки.</span><span class="sxs-lookup"><span data-stu-id="4b555-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="4b555-170">\>кордебугунмаппедстоп</span><span class="sxs-lookup"><span data-stu-id="4b555-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="4b555-171">Указывает тип несопоставимого кода, который может привести к прерыванию выполнения кода пошаговым средством.</span><span class="sxs-lookup"><span data-stu-id="4b555-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="4b555-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="4b555-172">CorDebugUserState</span></span>  
 <span data-ttu-id="4b555-173">Указывает состояние пользователя потока.</span><span class="sxs-lookup"><span data-stu-id="4b555-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="4b555-174">Перечисление CorGCReferenceType</span><span class="sxs-lookup"><span data-stu-id="4b555-174">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="4b555-175">Идентифицирует источник объекта, в котором должна быть выполнена сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="4b555-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="4b555-176">Перечисление ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="4b555-176">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="4b555-177">Предоставляет значения, которые указывают, может ли отладчик получить доступ к локальным переменным или коду, добавленным в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="4b555-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="4b555-178">Перечисление LoggingLevelEnum</span><span class="sxs-lookup"><span data-stu-id="4b555-178">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="4b555-179">Указывает уровень важности описательного сообщения, записанного в журнале событий при регистрации события управляемым потоком.</span><span class="sxs-lookup"><span data-stu-id="4b555-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="4b555-180">Перечисление LogSwitchCallReason</span><span class="sxs-lookup"><span data-stu-id="4b555-180">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="4b555-181">Указывает операцию, выполненную на переключателе отладки и трассировки.</span><span class="sxs-lookup"><span data-stu-id="4b555-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="4b555-182">Перечисление VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="4b555-182">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="4b555-183">Указывает тип собственного расположения переменной.</span><span class="sxs-lookup"><span data-stu-id="4b555-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="4b555-184">Перечисление WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="4b555-184">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="4b555-185">Предоставляет значения, указывающие, будут ли видны в отладчике обновления копии метаданных в памяти.</span><span class="sxs-lookup"><span data-stu-id="4b555-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>

 <span data-ttu-id="4b555-186">[Перечисление клрдатасаурцетипе](clrdatasourcetype-enumeration.md) Предоставляет значения, используемые структурой CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="4b555-186">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4b555-187">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="4b555-187">Related Sections</span></span>  

 [<span data-ttu-id="4b555-188">Компонентные классы отладки</span><span class="sxs-lookup"><span data-stu-id="4b555-188">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="4b555-189">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="4b555-189">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="4b555-190">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="4b555-190">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="4b555-191">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="4b555-191">Debugging Structures</span></span>](debugging-structures.md)
