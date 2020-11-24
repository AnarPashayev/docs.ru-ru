---
title: Интерфейсы отладки
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: a3dd81ceaab2ba467d4c8ca091c1c2219040a273
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676300"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="9b35c-102">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="9b35c-102">Debugging Interfaces</span></span>

<span data-ttu-id="9b35c-103">В этом разделе описываются неуправляемые интерфейсы отладки, управляющие отладкой программы, выполняемой в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="9b35c-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b35c-104">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="9b35c-104">In This Section</span></span>  

 <span data-ttu-id="9b35c-105">[Интерфейс Иклрдатаенуммеморирегионс](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="9b35c-106">Предоставляет метод, выполняющий перечисление областей памяти, заданной вызовами.</span><span class="sxs-lookup"><span data-stu-id="9b35c-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="9b35c-107">[Интерфейс Иклрдатаенуммеморирегионскаллбакк](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="9b35c-108">Предоставляет метод обратного вызова для метода `EnumMemoryRegions`, сообщающий отладчику результат попытки перечисления заданной области памяти.</span><span class="sxs-lookup"><span data-stu-id="9b35c-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="9b35c-109">[Интерфейс ICLRDataTarget](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="9b35c-110">Предоставляет методы для взаимодействия с целевым процессом среды CLR.</span><span class="sxs-lookup"><span data-stu-id="9b35c-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="9b35c-111">[Интерфейс ICLRDataTarget2](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-112">Подкласс `ICLRDataTarget`, используемый уровнем служб доступа к данным с целью управления областями виртуальной памяти в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="9b35c-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="9b35c-113">[Интерфейс метод iclrdatatarget3](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-114">Подкласс [ICLRDataTarget2](iclrdatatarget2-interface.md) , предоставляющий доступ к сведениям об исключениях.</span><span class="sxs-lookup"><span data-stu-id="9b35c-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="9b35c-115">[Интерфейс ICLRDebugging](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-115">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="9b35c-116">Предоставляет методы, обрабатывающие загрузку и выгрузку модулей для отладки.</span><span class="sxs-lookup"><span data-stu-id="9b35c-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="9b35c-117">[Интерфейс Иклрдебуггинглибрарипровидер](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="9b35c-118">Включает метод [метода ProvideLibrary](iclrdebugginglibraryprovider-providelibrary-method.md) , который получает интерфейс обратного вызова поставщика библиотеки, который позволяет находить и загружать библиотеки отладки, относящиеся к конкретной версии среды CLR, по запросу.</span><span class="sxs-lookup"><span data-stu-id="9b35c-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="9b35c-119">[Интерфейс Иклрметадаталокатор](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="9b35c-120">Интерфейс, используемый уровнем служб доступа к данным для определения местонахождения метаданных сборок в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="9b35c-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="9b35c-121">[Интерфейс ICorDebug](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-121">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="9b35c-122">Предоставляет методы, позволяющие разработчикам отлаживать приложения в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="9b35c-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="9b35c-123">[Интерфейс ICorDebugAppDomain](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="9b35c-124">Предоставляет методы для отладки доменов приложения.</span><span class="sxs-lookup"><span data-stu-id="9b35c-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="9b35c-125">[Интерфейс ICorDebugAppDomain2](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-126">Предоставляет методы для работы с массивами, указателями, указателями функций и типами ByRef.</span><span class="sxs-lookup"><span data-stu-id="9b35c-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="9b35c-127">Этот интерфейс является расширением интерфейса `ICorDebugAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="9b35c-128">[Интерфейс ICorDebugAppDomain3](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-129">Предоставляет методы для работы с типами среда выполнения Windows в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="9b35c-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="9b35c-130">Этот интерфейс является расширением интерфейса `ICorDebugAppDomain` и `ICorDebugAppDomain2`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="9b35c-131">[Интерфейс ICorDebugAppDomain4](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="9b35c-132">Логически расширяет интерфейс [ICorDebugAppDomain](icordebugappdomain-interface.md) для получения управляемого объекта из вызываемой оболочки COM.</span><span class="sxs-lookup"><span data-stu-id="9b35c-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="9b35c-133">[Интерфейс Икордебугаппдомаиненум](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-134">Предоставляет метод, возвращающий заданное число значений `ICorDebugAppDomain`, начиная со следующего расположения в перечислении.</span><span class="sxs-lookup"><span data-stu-id="9b35c-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="9b35c-135">[Интерфейс ICorDebugArrayValue](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-136">Подкласс интерфейса `ICorDebugHeapValue`, представляющий одномерный или многомерный массив.</span><span class="sxs-lookup"><span data-stu-id="9b35c-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="9b35c-137">[Интерфейс ICorDebugAssembly](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="9b35c-138">Представляет сборку.</span><span class="sxs-lookup"><span data-stu-id="9b35c-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="9b35c-139">[Интерфейс ICorDebugAssembly2](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-140">Представляет сборку.</span><span class="sxs-lookup"><span data-stu-id="9b35c-140">Represents an assembly.</span></span> <span data-ttu-id="9b35c-141">Этот интерфейс является расширением интерфейса `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="9b35c-142">[Интерфейс ICorDebugAssembly3](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-143">Логически расширяет интерфейс [ICorDebugAssembly](icordebugassembly-interface.md) , чтобы обеспечить поддержку для сборок контейнеров и содержащихся в них сборок.</span><span class="sxs-lookup"><span data-stu-id="9b35c-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="9b35c-144">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-145">[Интерфейс ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-146">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-147">[Интерфейс Икордебугблоккингобжектенум](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-148">Предоставляет перечислитель для списка структур [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="9b35c-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="9b35c-149">[Интерфейс Икордебугбоксвалуе](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-150">Подкласс интерфейса `ICorDebugHeapValue`, представляющий упакованное значение объектов класса.</span><span class="sxs-lookup"><span data-stu-id="9b35c-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="9b35c-151">[Интерфейс Икордебугбреакпоинт](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="9b35c-152">Представляет точку останова в функции или контрольную точку для значения.</span><span class="sxs-lookup"><span data-stu-id="9b35c-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="9b35c-153">[Интерфейс ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-154">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-155">[Интерфейс ICorDebugChain](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="9b35c-156">Представляет сегмент физического или логического стека вызовов.</span><span class="sxs-lookup"><span data-stu-id="9b35c-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="9b35c-157">[Интерфейс Икордебугчаиненум](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-158">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugChain`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-159">[Интерфейс ICorDebugClass](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="9b35c-160">Представляет тип, который может быть базовым или сложным (иными словами, пользовательским).</span><span class="sxs-lookup"><span data-stu-id="9b35c-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="9b35c-161">Если тип универсальный, `ICorDebugClass` представляет универсальный тип, у которого отсутствуют экземпляры.</span><span class="sxs-lookup"><span data-stu-id="9b35c-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="9b35c-162">[Интерфейс ICorDebugClass2](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-163">Представляет универсальный класс или класс параметром метода типа <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="9b35c-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="9b35c-164">Этот интерфейс расширяет интерфейс `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="9b35c-165">[Интерфейс ICorDebugCode](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="9b35c-166">Представляет сегмент кода на языке MSIL или сегмент машинного кода.</span><span class="sxs-lookup"><span data-stu-id="9b35c-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="9b35c-167">[Интерфейс ICorDebugCode2](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-168">Предоставляет методы, расширяющие возможности интерфейса `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="9b35c-169">[Интерфейс ICorDebugCode3](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-170">Предоставляет метод, расширяющий интерфейс [ICorDebugCode](icordebugcode-interface1.md) и [ICorDebugCode2](icordebugcode2-interface.md) для предоставления сведений об управляемом возвращаемом значении.</span><span class="sxs-lookup"><span data-stu-id="9b35c-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="9b35c-171">[Интерфейс ICorDebugCode4](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="9b35c-172">Предоставляет метод, позволяющий отладчику перечислить локальные переменные и аргументы в функции.</span><span class="sxs-lookup"><span data-stu-id="9b35c-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="9b35c-173">[Интерфейс Икордебугкодинум](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-174">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-175">[Интерфейс Икордебугкомобжектвалуе](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-176">Предоставляет методы для получения кэшированных объектов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="9b35c-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="9b35c-177">[Интерфейс Икордебугконтекст](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-177">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="9b35c-178">Представляет объект контекста.</span><span class="sxs-lookup"><span data-stu-id="9b35c-178">Represents a context object.</span></span> <span data-ttu-id="9b35c-179">Этот интерфейс еще не реализован.</span><span class="sxs-lookup"><span data-stu-id="9b35c-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="9b35c-180">[Интерфейс ICorDebugController](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-180">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="9b35c-181">Представляет область (<xref:System.Diagnostics.Process> или <xref:System.AppDomain>), в которой можно осуществлять управление контекстом выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="9b35c-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="9b35c-182">[Интерфейс ICorDebugDataTarget](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="9b35c-183">Предоставляет интерфейс обратного вызова, обеспечивающий доступ к конкретному целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="9b35c-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="9b35c-184">[Интерфейс метод icordebugdatatarget2](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-185">Логически расширяет интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9b35c-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="9b35c-186">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-187">[Интерфейс ICorDebugDataTarget3](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-188">Логически расширяет интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md) , чтобы предоставить сведения о загруженных модулях.</span><span class="sxs-lookup"><span data-stu-id="9b35c-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="9b35c-189">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-190">[Интерфейс ICorDebugDebugEvent](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="9b35c-191">Определяет базовый интерфейс, из которого возникают все события отладки `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="9b35c-192">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-193">[Интерфейс Икордебужедитандконтинуирроринфо](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="9b35c-194">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="9b35c-194">Obsolete.</span></span> <span data-ttu-id="9b35c-195">Не следует использовать данный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9b35c-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="9b35c-196">[Интерфейс метод icordebugeditandcontinuesnapshot](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="9b35c-197">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="9b35c-197">Obsolete.</span></span> <span data-ttu-id="9b35c-198">Не следует использовать данный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9b35c-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="9b35c-199">[Интерфейс ICorDebugEnum](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="9b35c-200">Служит абстрактным базовым интерфейсом для перечислителей отладки.</span><span class="sxs-lookup"><span data-stu-id="9b35c-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="9b35c-201">[Интерфейс ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-202">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="9b35c-202">Obsolete.</span></span> <span data-ttu-id="9b35c-203">Не следует использовать данный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9b35c-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="9b35c-204">[Интерфейс ICorDebugEval](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="9b35c-205">Предоставляет методы, позволяющие отладчику выполнять код в контексте отлаживаемого кода.</span><span class="sxs-lookup"><span data-stu-id="9b35c-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="9b35c-206">[Интерфейс ICorDebugEval2](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-207">Расширяет интерфейс `ICorDebugEval` для предоставления поддержки универсальных типов.</span><span class="sxs-lookup"><span data-stu-id="9b35c-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="9b35c-208">[Интерфейс Икордебужексцептиондебужевент](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="9b35c-209">Расширяет интерфейс [ICorDebugDebugEvent](icordebugdebugevent-interface.md) для поддержки событий исключения.</span><span class="sxs-lookup"><span data-stu-id="9b35c-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="9b35c-210">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-211">[Интерфейс ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-212">Предоставляет перечислитель для сведений стека вызовов, встроенных в объект исключения.</span><span class="sxs-lookup"><span data-stu-id="9b35c-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="9b35c-213">[Интерфейс ICorDebugExceptionObjectValue](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-214">Расширяет интерфейс [ICorDebugObjectValue](icordebugobjectvalue-interface.md) для предоставления сведений о трассировке стека из управляемого объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="9b35c-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="9b35c-215">[Интерфейс ICorDebugFrame](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="9b35c-216">Представляет кадр текущего стека.</span><span class="sxs-lookup"><span data-stu-id="9b35c-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="9b35c-217">[Интерфейс ICorDebugFrameEnum](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-218">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-219">[Интерфейс ICorDebugFunction](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="9b35c-220">Представляет управляемую функцию или метод.</span><span class="sxs-lookup"><span data-stu-id="9b35c-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="9b35c-221">[Интерфейс ICorDebugFunction2](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-222">Локально расширяет интерфейс `ICorDebugFunction` для предоставления поддержки отладки в пошаговом режиме "Только мой код".</span><span class="sxs-lookup"><span data-stu-id="9b35c-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="9b35c-223">[Интерфейс ICorDebugFunction3](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-224">Логически расширяет интерфейс [ICorDebugFunction](icordebugfunction-interface1.md) , чтобы предоставить доступ к коду из запроса ReJIT.</span><span class="sxs-lookup"><span data-stu-id="9b35c-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="9b35c-225">[Интерфейс ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="9b35c-226">Расширяет интерфейс `ICorDebugBreakpoint` для поддержки точек останова в функциях.</span><span class="sxs-lookup"><span data-stu-id="9b35c-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="9b35c-227">[Интерфейс ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-228">Предоставляет перечислитель для объектов, для которых будет выполнена сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="9b35c-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="9b35c-229">[Интерфейс ICorDebugGenericValue](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-230">Подкласс интерфейса `ICorDebugValue`, применяемый ко всем значениям.</span><span class="sxs-lookup"><span data-stu-id="9b35c-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="9b35c-231">Этот интерфейс предоставляет для значения методы Get и Set.</span><span class="sxs-lookup"><span data-stu-id="9b35c-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="9b35c-232">[Интерфейс ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-233">Предоставляет перечислитель для объекта, сопоставляющего идентификаторы GUID и соответствующие объекты `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="9b35c-234">[Интерфейс ICorDebugHandleValue](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-235">Подкласс интерфейса `ICorDebugReferenceValue`, представляющий значение ссылки, для которого отладчик создал дескриптор сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="9b35c-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="9b35c-236">[Интерфейс Икордебугхеапенум](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-237">Предоставляет перечислитель для объектов в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="9b35c-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="9b35c-238">[Интерфейс Икордебугхеапсегментенум](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-239">Предоставляет перечислитель для областей памяти управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="9b35c-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="9b35c-240">[Интерфейс ICorDebugHeapValue](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-241">Подкласс интерфейса `ICorDebugValue`, представляющий объект, подобранный сборщиком мусора среды CLR.</span><span class="sxs-lookup"><span data-stu-id="9b35c-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="9b35c-242">[Интерфейс ICorDebugHeapValue2](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="9b35c-243">Расширение интерфейса `ICorDebugHeapValue`, предоставляющее поддержку дескрипторов среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="9b35c-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="9b35c-244">[Интерфейс ICorDebugHeapValue3](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-245">Предоставляет свойства блокировки монитора объектов.</span><span class="sxs-lookup"><span data-stu-id="9b35c-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="9b35c-246">[Интерфейс Икордебугилкоде](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="9b35c-247">Представляет сегмент кода промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="9b35c-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="9b35c-248">[Интерфейс ICorDebugILCode2](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-249">Логически расширяет интерфейс [икордебугилкоде](icordebugilcode-interface.md) , чтобы предоставить методы, которые возвращают маркер для сигнатуры локальной переменной функции и сопоставляют смещенные промежуточные языки (IL) профилировщика с исходными смещениями Il метода.</span><span class="sxs-lookup"><span data-stu-id="9b35c-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="9b35c-250">[Интерфейс ICorDebugILFrame](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="9b35c-251">Предоставляет кадр стека кода MSIL.</span><span class="sxs-lookup"><span data-stu-id="9b35c-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="9b35c-252">[Интерфейс ICorDebugILFrame2](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-253">Логическое расширение интерфейса `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="9b35c-254">[Интерфейс ICorDebugILFrame3](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-255">Предоставляет метод, инкапсулирующий возвращаемое значение функции.</span><span class="sxs-lookup"><span data-stu-id="9b35c-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="9b35c-256">[Интерфейс ICorDebugILFrame4](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="9b35c-257">Предоставляет методы, обеспечивающие доступ к локальным переменным и коду в кадре стека кода промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="9b35c-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="9b35c-258">Параметр показывает, имеет ли отладчик доступ к переменным и коду, добавленным в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="9b35c-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="9b35c-259">[Интерфейс ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="9b35c-260">Представляет сведения отладочного символа для поля экземпляра.</span><span class="sxs-lookup"><span data-stu-id="9b35c-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="9b35c-261">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-262">[Интерфейс ICorDebugInternalFrame](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="9b35c-263">Задает типы кадров для отладчика.</span><span class="sxs-lookup"><span data-stu-id="9b35c-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="9b35c-264">[Интерфейс ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-265">Предоставляет сведения о внутренних кадрах, включая адрес стека и расположение по отношению к объектам [ICorDebugFrame](icordebugframe-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9b35c-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="9b35c-266">[Интерфейс Икордебуглоадедмодуле](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="9b35c-267">Предоставляет сведения о загруженном модуле.</span><span class="sxs-lookup"><span data-stu-id="9b35c-267">Provides information about a loaded module.</span></span> <span data-ttu-id="9b35c-268">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-269">[Интерфейс ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="9b35c-270">Предоставляет методы для обработки обратных вызовов отладчика.</span><span class="sxs-lookup"><span data-stu-id="9b35c-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="9b35c-271">[Интерфейс ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-272">Предоставляет методы для поддержки обработки исключений отладчика и управляемых помощников по отладке (MDA).</span><span class="sxs-lookup"><span data-stu-id="9b35c-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="9b35c-273">Интерфейс `ICorDebugManagedCallback2` является логическим расширением интерфейса `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="9b35c-274">[Интерфейс ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-275">Предоставляет метод обратного вызова, указывающий, что создано включенное пользовательское уведомление отладчика.</span><span class="sxs-lookup"><span data-stu-id="9b35c-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="9b35c-276">[Интерфейс ICorDebugMDA](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="9b35c-277">Представляет сообщение управляемого помощника по отладке (MDA).</span><span class="sxs-lookup"><span data-stu-id="9b35c-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="9b35c-278">[Интерфейс Икордебугмеморибуффер](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="9b35c-279">Представляет буфер в памяти.</span><span class="sxs-lookup"><span data-stu-id="9b35c-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="9b35c-280">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-281">[Интерфейс Икордебугмержедассемблирекорд](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="9b35c-282">Предоставляет сведения о сборке после слияния.</span><span class="sxs-lookup"><span data-stu-id="9b35c-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="9b35c-283">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-284">[Интерфейс Икордебугметадаталокатор](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="9b35c-285">Предоставляет сведения о метаданных для отладчика.</span><span class="sxs-lookup"><span data-stu-id="9b35c-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="9b35c-286">[Интерфейс ICorDebugModule](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="9b35c-287">Представляет модуль среды CLR, который является либо исполняемым файлом, либо библиотекой динамической компоновки (DLL).</span><span class="sxs-lookup"><span data-stu-id="9b35c-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="9b35c-288">[Интерфейс ICorDebugModule2](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-289">Служит логическим расширением интерфейса `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="9b35c-290">[Интерфейс метод icordebugmodule3](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-291">Создает средство чтения символов для динамического модуля.</span><span class="sxs-lookup"><span data-stu-id="9b35c-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="9b35c-292">[Интерфейс Икордебугмодулебреакпоинт](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="9b35c-293">Расширяет интерфейс `ICorDebugBreakpoint` для предоставления доступа к указанным модулям.</span><span class="sxs-lookup"><span data-stu-id="9b35c-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="9b35c-294">[Интерфейс Икордебугмодуледебужевент](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="9b35c-295">Расширяет интерфейс [ICorDebugDebugEvent](icordebugdebugevent-interface.md) для поддержки событий уровня модуля.</span><span class="sxs-lookup"><span data-stu-id="9b35c-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="9b35c-296">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-297">[Интерфейс Икордебугмодулинум](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-298">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-299">[Интерфейс Икордебугмутабледататаржет](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="9b35c-300">Расширяет интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md) для поддержки целевых объектов данных.</span><span class="sxs-lookup"><span data-stu-id="9b35c-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="9b35c-301">[Интерфейс ICorDebugNativeFrame](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="9b35c-302">Специализированная реализация интерфейса `ICorDebugFrame`, используемая для кадров машинного кода.</span><span class="sxs-lookup"><span data-stu-id="9b35c-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="9b35c-303">[Интерфейс ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-304">Предоставляет методы, проверяющие для кадров наличие взаимоотношений типа "дочерний-родительский".</span><span class="sxs-lookup"><span data-stu-id="9b35c-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="9b35c-305">[Интерфейс Икордебугобжектенум](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-306">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов объектов по их относительным виртуальным адресам (RVA).</span><span class="sxs-lookup"><span data-stu-id="9b35c-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="9b35c-307">[Интерфейс ICorDebugObjectValue](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-308">Подкласс `ICorDebugValue`, представляющий значение, содержащее объект.</span><span class="sxs-lookup"><span data-stu-id="9b35c-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="9b35c-309">[Интерфейс ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-310">Расширяет интерфейс `ICorDebugObjectValue` для поддержки наследования и переопределений.</span><span class="sxs-lookup"><span data-stu-id="9b35c-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="9b35c-311">[Интерфейс ICorDebugProcess](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="9b35c-312">Представляет процесс, выполняющий управляемый код.</span><span class="sxs-lookup"><span data-stu-id="9b35c-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="9b35c-313">[Интерфейс ICorDebugProcess2](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="9b35c-314">Логическое расширение интерфейса `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="9b35c-315">[Интерфейс ICorDebugProcess3](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-316">Управляет пользовательскими уведомлениями отладчика.</span><span class="sxs-lookup"><span data-stu-id="9b35c-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="9b35c-317">[Интерфейс ICorDebugProcess4](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="9b35c-318">Обеспечивает поддержку управления выполнением в процессе.</span><span class="sxs-lookup"><span data-stu-id="9b35c-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="9b35c-319">[Интерфейс метод ICorDebugProcess5](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="9b35c-320">Расширяет интерфейс [ICorDebugProcess](icordebugprocess-interface.md) для поддержки доступа к управляемой куче, предоставляет сведения о сборке мусора управляемых объектов и определяет, загружает ли отладчик изображения из локального кэша образов в машинном код.</span><span class="sxs-lookup"><span data-stu-id="9b35c-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="9b35c-321">[Интерфейс ICorDebugProcess6](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="9b35c-322">Логически расширяет интерфейс [ICorDebugProcess](icordebugprocess-interface.md) , позволяя выполнять такие функции, как декодирование управляемых событий отладки, которые кодируются в событиях отладки машинного кода и разбиении виртуального модуля.</span><span class="sxs-lookup"><span data-stu-id="9b35c-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="9b35c-323">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-324">[Интерфейс ICorDebugProcess7](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="9b35c-325">Предоставляет метод, который настраивает отладчик для обработки обновлений находящихся в памяти метаданных в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="9b35c-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="9b35c-326">[Интерфейс ICorDebugProcess8](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="9b35c-327">Логически расширяет интерфейс [ICorDebugProcess](icordebugprocess-interface.md) , чтобы включать или отключать определенные типы обратных вызовов исключений [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9b35c-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="9b35c-328">[Интерфейс Икордебугпроцессенум](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-329">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-330">[Интерфейс ICorDebugReferenceValue](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-331">Подкласс интерфейса `ICorDebugValue`, поддерживающего ссылочные типы.</span><span class="sxs-lookup"><span data-stu-id="9b35c-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="9b35c-332">[Интерфейс ICorDebugRegisterSet](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="9b35c-333">Представляет набор регистров, доступных для компьютера, на котором в данный момент выполняется код.</span><span class="sxs-lookup"><span data-stu-id="9b35c-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="9b35c-334">[Интерфейс ICorDebugRegisterSet2](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-335">Расширяет возможности интерфейса `ICorDebugRegisterSet` для аппаратных платформ, количество регистров которых превышает 64.</span><span class="sxs-lookup"><span data-stu-id="9b35c-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="9b35c-336">[Интерфейс метод icordebugremote](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-336">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="9b35c-337">Позволяет запускать или подключать управляемый отладчик к удаленному целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="9b35c-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="9b35c-338">[Интерфейс ICorDebugRemoteTarget](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="9b35c-339">Предоставляет методы, позволяющие отлаживать приложения на основе Silverlight в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="9b35c-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="9b35c-340">[Интерфейс Икордебугрунтимеунвиндаблефраме](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="9b35c-341">Предоставляет поддержку для неуправляемых методов, которым требуется среда CLR для раскручивания кадра.</span><span class="sxs-lookup"><span data-stu-id="9b35c-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="9b35c-342">[Интерфейс Икордебугстакквалк](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="9b35c-343">Обеспечивает методы для получения управляемых методов или кадров в стеке потока.</span><span class="sxs-lookup"><span data-stu-id="9b35c-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="9b35c-344">[Интерфейс Икордебугстатикфиелдсимбол](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="9b35c-345">Представляет сведения символа отладки для статического поля.</span><span class="sxs-lookup"><span data-stu-id="9b35c-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="9b35c-346">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-347">[Интерфейс ICorDebugStepper](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="9b35c-348">Представляет предпринимаемый отладчиком шаг при выполнении кода, служащий идентификатором на промежутке между подачей команды и ее завершением, а также предоставляет возможность отмены шага.</span><span class="sxs-lookup"><span data-stu-id="9b35c-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="9b35c-349">[Интерфейс ICorDebugStepper2](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="9b35c-350">Предоставляет поддержку отладки "Только мой код".</span><span class="sxs-lookup"><span data-stu-id="9b35c-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="9b35c-351">[Интерфейс Икордебугстепперенум](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-352">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugStepper`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-353">[Интерфейс ICorDebugStringValue](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-354">Подкласс `ICorDebugHeapValue`, применяемый к строковым значениям.</span><span class="sxs-lookup"><span data-stu-id="9b35c-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="9b35c-355">[Интерфейс метод icordebugsymbolprovider](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="9b35c-356">Предоставляет методы, которые могут использоваться для получения сведений об отладочных символах.</span><span class="sxs-lookup"><span data-stu-id="9b35c-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="9b35c-357">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-358">[Интерфейс ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-359">Логически расширяет интерфейс [метод icordebugsymbolprovider](icordebugsymbolprovider-interface.md) для получения дополнительных сведений об отладочных символах.</span><span class="sxs-lookup"><span data-stu-id="9b35c-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="9b35c-360">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-361">[Интерфейс ICorDebugThread](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="9b35c-362">Представляет поток в процессе.</span><span class="sxs-lookup"><span data-stu-id="9b35c-362">Represents a thread in a process.</span></span> <span data-ttu-id="9b35c-363">Время существования экземпляра `ICorDebugThread` равно времени существования потока, который он представляет.</span><span class="sxs-lookup"><span data-stu-id="9b35c-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="9b35c-364">[Интерфейс ICorDebugThread2](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-365">Служит логическим расширением интерфейса `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="9b35c-366">[Интерфейс ICorDebugThread3](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-367">Предоставляет точку входа для [икордебугстакквалк](icordebugstackwalk-interface.md) и соответствующих интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="9b35c-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="9b35c-368">[Интерфейс ICorDebugThread4](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="9b35c-369">Предоставляет сведения о блокировке потока.</span><span class="sxs-lookup"><span data-stu-id="9b35c-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="9b35c-370">[Интерфейс Икордебугсреаденум](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="9b35c-371">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-372">[Интерфейс ICorDebugType](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-372">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="9b35c-373">Представляет тип, который может быть базовым или сложным (иными словами, пользовательским).</span><span class="sxs-lookup"><span data-stu-id="9b35c-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="9b35c-374">Если тип универсален, интерфейс `ICorDebugType` представляет универсальный тип с экземплярами.</span><span class="sxs-lookup"><span data-stu-id="9b35c-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="9b35c-375">[Интерфейс ICorDebugType2](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-376">Расширяет интерфейс [ICorDebugType](icordebugtype-interface.md) для получения идентификатора типа базового типа или сложного (определяемого пользователем) типа.</span><span class="sxs-lookup"><span data-stu-id="9b35c-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="9b35c-377">[Интерфейс ICorDebugTypeEnum](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-378">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-379">[Интерфейс Икордебугунманажедкаллбакк](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="9b35c-380">Предоставляет уведомление о событиях машинного кода, которые не связаны непосредственно со средой CLR.</span><span class="sxs-lookup"><span data-stu-id="9b35c-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="9b35c-381">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="9b35c-382">Представляет значение для записи или чтения в отлаживаемом процессе.</span><span class="sxs-lookup"><span data-stu-id="9b35c-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="9b35c-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="9b35c-384">Расширяет интерфейс `ICorDebugValue` для предоставления поддержки интерфейса `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="9b35c-385">[Интерфейс ICorDebugValue3](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="9b35c-386">Расширяет интерфейсы "ICorDebugValue" и "ICorDebugValue2", чтобы обеспечить поддержку массивов, размер которых превышает 2 ГБ.</span><span class="sxs-lookup"><span data-stu-id="9b35c-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="9b35c-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="9b35c-388">Расширяет интерфейс `ICorDebugBreakpoint` для обеспечения доступа к указанным значениям.</span><span class="sxs-lookup"><span data-stu-id="9b35c-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="9b35c-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-390">Реализует методы `ICorDebugEnum` и выполняет перечисление массивов `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="9b35c-391">[Интерфейс ICorDebugVariableHome](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="9b35c-392">Представляет локальную переменную или аргумент функции.</span><span class="sxs-lookup"><span data-stu-id="9b35c-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="9b35c-393">[Интерфейс ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-394">Предоставляет перечислитель для локальных переменных и аргументов в функции.</span><span class="sxs-lookup"><span data-stu-id="9b35c-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="9b35c-395">[Интерфейс ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="9b35c-396">Извлекает сведения символа отладки для статического поля.</span><span class="sxs-lookup"><span data-stu-id="9b35c-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="9b35c-397">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-398">[Интерфейс ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="9b35c-399">Предоставляет методы, помогающие очистить стек.</span><span class="sxs-lookup"><span data-stu-id="9b35c-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="9b35c-400">**Доступен только в .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="9b35c-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="9b35c-401">[Интерфейс ICorPublish](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-401">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="9b35c-402">Служит универсальным интерфейсом для процессов публикации.</span><span class="sxs-lookup"><span data-stu-id="9b35c-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="9b35c-403">[Интерфейс ICorPublishAppDomain](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="9b35c-404">Представляет и предоставляет информацию о домене приложения.</span><span class="sxs-lookup"><span data-stu-id="9b35c-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="9b35c-405">[Интерфейс ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-406">Предоставляет методы, выполняющие перебор коллекции объектов `ICorPublishAppDomain`, существующих в процессе в данный момент.</span><span class="sxs-lookup"><span data-stu-id="9b35c-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="9b35c-407">[Интерфейс ICorPublishEnum](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-408">Служит абстрактной базой для перечислителей публикации.</span><span class="sxs-lookup"><span data-stu-id="9b35c-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="9b35c-409">[Интерфейс ICorPublishProcess](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="9b35c-410">Предоставляет методы, позволяющие получить доступ к сведениям о процессе.</span><span class="sxs-lookup"><span data-stu-id="9b35c-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="9b35c-411">[Интерфейс ICorPublishProcessEnum](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="9b35c-412">Предоставляет методы, выполняющие перебор коллекции объектов `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="9b35c-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="9b35c-413">[Интерфейс ИсосдаЦинтерфаце](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="9b35c-414">Предоставляет вспомогательные методы для доступа к данным из `SOS` .</span><span class="sxs-lookup"><span data-stu-id="9b35c-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="9b35c-415">[Интерфейс Иксклрдатамесоддефинитион](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="9b35c-416">Предоставляет методы для запроса сведений об определении метода.</span><span class="sxs-lookup"><span data-stu-id="9b35c-416">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="9b35c-417">[Интерфейс Иксклрдатамесодинстанце](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="9b35c-418">Предоставляет методы для запроса сведений об экземпляре метода.</span><span class="sxs-lookup"><span data-stu-id="9b35c-418">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="9b35c-419">[Интерфейс Иксклрдатамодуле](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="9b35c-420">Предоставляет методы для запроса сведений о загруженном модуле.</span><span class="sxs-lookup"><span data-stu-id="9b35c-420">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="9b35c-421">[Интерфейс Иксклрдатапроцесс](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="9b35c-422">Предоставляет методы для запроса сведений о процессе.</span><span class="sxs-lookup"><span data-stu-id="9b35c-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="9b35c-423">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="9b35c-423">Related Sections</span></span>  

 <span data-ttu-id="9b35c-424">[Коклассы отладки](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="9b35c-425">[Отладка глобальных статических функций](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="9b35c-426">[Перечисления отладки](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-426">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="9b35c-427">[Структуры отладки](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="9b35c-427">[Debugging Structures](debugging-structures.md)</span></span>\
