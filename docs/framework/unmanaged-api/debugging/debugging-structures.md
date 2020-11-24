---
title: Структуры отладки
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: bf84f8ddb1e86da3b9d0e4326584e61304640558
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676274"
---
# <a name="debugging-structures"></a><span data-ttu-id="045be-102">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="045be-102">Debugging Structures</span></span>

<span data-ttu-id="045be-103">В этом разделе описаны неуправляемые структуры, которые использует API отладки.</span><span class="sxs-lookup"><span data-stu-id="045be-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="045be-104">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="045be-104">In This Section</span></span>

 <span data-ttu-id="045be-105">[Структура CLRDATA_ADDRESS_RANGE](clrdata-address-range-structure.md) Определяет диапазон адресов.</span><span class="sxs-lookup"><span data-stu-id="045be-105">[CLRDATA_ADDRESS_RANGE Structure](clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="045be-106">[Структура CLRDATA_IL_ADDRESS_MAP](clrdata-il-address-map-structure.md) Определяет IL для сопоставления адресов</span><span class="sxs-lookup"><span data-stu-id="045be-106">[CLRDATA_IL_ADDRESS_MAP Structure](clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="045be-107">[Структура CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) Определяет версию продукта среды CLR для целей отладки.</span><span class="sxs-lookup"><span data-stu-id="045be-107">[CLR_DEBUGGING_VERSION Structure](clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="045be-108">[Структура кодечункинфо](codechunkinfo-structure.md) Представляет отдельный фрагмент кода в памяти.</span><span class="sxs-lookup"><span data-stu-id="045be-108">[CodeChunkInfo Structure](codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="045be-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Содержит сведения о функциях, которые в данный момент активны в кадрах потока.</span><span class="sxs-lookup"><span data-stu-id="045be-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="045be-110">[Структура COR_ARRAY_LAYOUT](cor-array-layout-structure.md) Предоставляет сведения о макете объекта массива в памяти.</span><span class="sxs-lookup"><span data-stu-id="045be-110">[COR_ARRAY_LAYOUT Structure](cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="045be-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Содержит смещения, используемые для преобразования кода MSIL в машинный код.</span><span class="sxs-lookup"><span data-stu-id="045be-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="045be-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Содержит сведения о смещении для диапазона кода.</span><span class="sxs-lookup"><span data-stu-id="045be-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="045be-113">[Структура COR_FIELD](cor-field-structure.md) Предоставляет сведения о поле в объекте.</span><span class="sxs-lookup"><span data-stu-id="045be-113">[COR_FIELD Structure](cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="045be-114">[Структура COR_GC_REFERENCE](cor-gc-reference-structure.md) Содержит сведения об объекте, который должен быть собран в мусор.</span><span class="sxs-lookup"><span data-stu-id="045be-114">[COR_GC_REFERENCE Structure](cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="045be-115">[Структура COR_HEAPINFO](cor-heapinfo-structure.md) Содержит общие сведения о куче сборки мусора, в том числе о том, является ли она перечислимой.</span><span class="sxs-lookup"><span data-stu-id="045be-115">[COR_HEAPINFO Structure](cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="045be-116">[Структура COR_HEAPOBJECT](cor-heapobject-structure.md) Предоставляет сведения об объекте в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="045be-116">[COR_HEAPOBJECT Structure](cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="045be-117">[COR_IL_MAP](cor-il-map-structure.md) Задает изменения в относительном смещении функции.</span><span class="sxs-lookup"><span data-stu-id="045be-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="045be-118">[Структура COR_SEGMENT](cor-segment-structure.md) Содержит сведения о области памяти в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="045be-118">[COR_SEGMENT Structure](cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="045be-119">[Структура COR_TYPEID](cor-typeid-structure.md) Содержит идентификатор типа.</span><span class="sxs-lookup"><span data-stu-id="045be-119">[COR_TYPEID Structure](cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="045be-120">[Структура COR_TYPE_LAYOUT](cor-type-layout-structure.md) Предоставляет сведения о макете объекта в памяти.</span><span class="sxs-lookup"><span data-stu-id="045be-120">[COR_TYPE_LAYOUT Structure](cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="045be-121">[COR_VERSION](cor-version-structure.md) Хранит Стандартный номер версии, сообщая из четырех частей, для общеязыковой среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="045be-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="045be-122">[Структура CorDebugBlockingObject](cordebugblockingobject-structure.md) Определяет объект, который блокирует поток и причину блокировки потока.</span><span class="sxs-lookup"><span data-stu-id="045be-122">[CorDebugBlockingObject Structure](cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="045be-123">[Структура кордебужехклаусе](cordebugehclause-structure.md) Представляет предложение обработки исключений (EH) для заданного фрагмента промежуточного языка (IL).</span><span class="sxs-lookup"><span data-stu-id="045be-123">[CorDebugEHClause Structure](cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="045be-124">[Структура кордебужексцептионобжектстаккфраме](cordebugexceptionobjectstackframe-structure.md) Представляет сведения о кадре стека из объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="045be-124">[CorDebugExceptionObjectStackFrame Structure](cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="045be-125">[Структура кордебуггуидтотипемаппинг](cordebugguidtotypemapping-structure.md) Сопоставляет идентификатор GUID среда выполнения Windows с соответствующим объектом [ICorDebugType](icordebugtype-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="045be-125">[CorDebugGuidToTypeMapping Structure](cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="045be-126">[Структура дакпжетмодулеаддресс](dacpgetmoduleaddress-structure.md) Определяет контейнер для запроса адреса модуля.</span><span class="sxs-lookup"><span data-stu-id="045be-126">[DacpGetModuleAddress Structure](dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="045be-127">[Структура дакпмесоддескдата](dacpmethoddescdata-structure.md) Определяет транспортный буфер для сведений о среде выполнения метода.</span><span class="sxs-lookup"><span data-stu-id="045be-127">[DacpMethodDescData Structure](dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="045be-128">[Структура дакпмодуледата](dacpmoduledata-structure.md) Определяет транспортный буфер для сведений о среде выполнения модуля.</span><span class="sxs-lookup"><span data-stu-id="045be-128">[DacpModuleData Structure](dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="045be-129">[Структура дакпрежитдата](dacprejitdata-structure.md) Определяет основные сведения о конкретном инструментированном методе профилирования.</span><span class="sxs-lookup"><span data-stu-id="045be-129">[DacpReJitData Structure](dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="045be-130">[Структура StackTrace_SimpleContext](stacktrace-simplecontext-structure.md) Предоставляет простой контекст, который можно использовать вместо полной `CONTEXT` структуры.</span><span class="sxs-lookup"><span data-stu-id="045be-130">[StackTrace_SimpleContext Structure](stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="045be-131">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="045be-131">Related Sections</span></span>

 [<span data-ttu-id="045be-132">Компонентные классы отладки</span><span class="sxs-lookup"><span data-stu-id="045be-132">Debugging Coclasses</span></span>](debugging-coclasses.md)

 [<span data-ttu-id="045be-133">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="045be-133">Debugging Interfaces</span></span>](debugging-interfaces.md)

 [<span data-ttu-id="045be-134">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="045be-134">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

 [<span data-ttu-id="045be-135">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="045be-135">Debugging Enumerations</span></span>](debugging-enumerations.md)

 [<span data-ttu-id="045be-136">Отладка</span><span class="sxs-lookup"><span data-stu-id="045be-136">Debugging</span></span>](index.md)
