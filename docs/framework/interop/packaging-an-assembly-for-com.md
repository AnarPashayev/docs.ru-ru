---
title: Упаковка сборки .NET Framework для COM
description: Упаковка сборки .NET для COM. Соберите список типов, которые могут использоваться приложениями COM, инструкции по управлению версиями и развертыванию, а также библиотеку типов.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
ms.openlocfilehash: 5fde7f7f00aadf4d941d4ffe522453970b67e9e2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554134"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="e5a49-104">Упаковка сборки .NET Framework для COM</span><span class="sxs-lookup"><span data-stu-id="e5a49-104">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="e5a49-105">Разработчики приложений на основе модели COM могут использовать следующую информацию об управляемых типах, которые они планируют включать в свои приложения:</span><span class="sxs-lookup"><span data-stu-id="e5a49-105">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="e5a49-106">Список типов, которые можно использовать в приложениях на основе модели COM</span><span class="sxs-lookup"><span data-stu-id="e5a49-106">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="e5a49-107">Некоторые управляемые типы невидимы в модели COM, другие видны, но недоступны для создания, однако третьи можно как видеть, так и создавать.</span><span class="sxs-lookup"><span data-stu-id="e5a49-107">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="e5a49-108">В сборку можно включать типы любого вида в любом сочетании.</span><span class="sxs-lookup"><span data-stu-id="e5a49-108">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="e5a49-109">Для полноты информации определите типы в сборке, которые будут предоставлены модели COM. Особое внимание уделите типам, входящим в подмножество типов, предоставляемых платформе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5a49-109">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="e5a49-110">Дополнительные сведения см. в разделе [Уточнение типов .NET для взаимодействия](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="e5a49-110">For additional information, see [Qualifying .NET Types for Interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="e5a49-111">Инструкции по управлению версиями</span><span class="sxs-lookup"><span data-stu-id="e5a49-111">Versioning instructions</span></span>

  <span data-ttu-id="e5a49-112">В отношении управления версиями управляемых классов, которые реализуют интерфейс класса (создаваемые в результате COM-взаимодействия класс), действуют определенные ограничения.</span><span class="sxs-lookup"><span data-stu-id="e5a49-112">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="e5a49-113">Рекомендации по использованию интерфейса класса см. в разделе [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface) (Введение в интерфейс класса).</span><span class="sxs-lookup"><span data-stu-id="e5a49-113">For guidelines on using the class interface, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="e5a49-114">Инструкции по развертыванию</span><span class="sxs-lookup"><span data-stu-id="e5a49-114">Deployment instructions</span></span>

  <span data-ttu-id="e5a49-115">Сборки со строгими именами, подписанные издателем, могут устанавливаться в глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="e5a49-115">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="e5a49-116">Неподписанные сборки необходимо устанавливать на компьютер пользователя в виде частных сборок.</span><span class="sxs-lookup"><span data-stu-id="e5a49-116">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="e5a49-117">Дополнительные сведения см. в разделе [Вопросы безопасности сборок](../../standard/assembly/security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="e5a49-117">For additional information, see [Assembly Security Considerations](../../standard/assembly/security-considerations.md).</span></span>

- <span data-ttu-id="e5a49-118">Включение библиотеки типов</span><span class="sxs-lookup"><span data-stu-id="e5a49-118">Type library inclusion</span></span>

  <span data-ttu-id="e5a49-119">Для использования большинства типов в COM-приложении требуется библиотека типов.</span><span class="sxs-lookup"><span data-stu-id="e5a49-119">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="e5a49-120">Вы можете создать библиотеку типов самостоятельно или поручить эту задачу разработчикам COM-приложений.</span><span class="sxs-lookup"><span data-stu-id="e5a49-120">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="e5a49-121">Windows SDK предоставляет следующие возможности для создания библиотеки типов:</span><span class="sxs-lookup"><span data-stu-id="e5a49-121">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="e5a49-122">Программа экспорта библиотек типов</span><span class="sxs-lookup"><span data-stu-id="e5a49-122">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="e5a49-123">Класс TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="e5a49-123">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="e5a49-124">Средство регистрации сборок</span><span class="sxs-lookup"><span data-stu-id="e5a49-124">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="e5a49-125">Средство установки служб .NET</span><span class="sxs-lookup"><span data-stu-id="e5a49-125">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="e5a49-126">Независимо от выбранного механизма, в созданную библиотеку типов включаются только открытые типы, определенные в предоставленной сборке.</span><span class="sxs-lookup"><span data-stu-id="e5a49-126">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="e5a49-127">Инструкции см. в разделе [Практическое руководство. Встраивание библиотек типов как ресурсов Win32 в приложения на основе платформы .NET](/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e5a49-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="e5a49-128">программа экспорта библиотек типов</span><span class="sxs-lookup"><span data-stu-id="e5a49-128">Type Library Exporter</span></span>

<span data-ttu-id="e5a49-129">[Программа экспорта библиотек типов (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) — это средство командной строки, которое преобразует классы и интерфейсы, содержащиеся в сборке, в библиотеку типов COM.</span><span class="sxs-lookup"><span data-stu-id="e5a49-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="e5a49-130">После получения информации о типе класса COM-клиенты могут создать экземпляр класса .NET и вызывать его методы так, как если бы он был COM-объектом.</span><span class="sxs-lookup"><span data-stu-id="e5a49-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="e5a49-131">Программа Tlbexp.exe преобразует всю сборку за одну операцию.</span><span class="sxs-lookup"><span data-stu-id="e5a49-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="e5a49-132">Программу Tlbexp.exe нельзя использовать с целью генерации сведений о типах для подмножества типов, определенных в сборке.</span><span class="sxs-lookup"><span data-stu-id="e5a49-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="e5a49-133">Класс TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="e5a49-133">TypeLibConverter Class</span></span>

<span data-ttu-id="e5a49-134">Класс <xref:System.Runtime.InteropServices.TypeLibConverter> располагается в пространстве имен **System.Runtime.Interop** и преобразует классы и интерфейсы, содержащиеся в сборке, в библиотеку типов COM.</span><span class="sxs-lookup"><span data-stu-id="e5a49-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="e5a49-135">Этот API предоставляет те же сведения, что и программа экспорта библиотек типов, которая описывается в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="e5a49-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="e5a49-136">Класс **TypeLibConverter** реализует <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="e5a49-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="e5a49-137">Средство регистрации сборок</span><span class="sxs-lookup"><span data-stu-id="e5a49-137">Assembly Registration Tool</span></span>

<span data-ttu-id="e5a49-138">[Средство регистрации сборок (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) позволяет создавать и регистрировать библиотеку типов с использованием параметров **/tlb:** .</span><span class="sxs-lookup"><span data-stu-id="e5a49-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="e5a49-139">COM-клиентам требуется установка библиотек типов в реестр Windows.</span><span class="sxs-lookup"><span data-stu-id="e5a49-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="e5a49-140">Без этого параметра программа Regasm.exe регистрирует только типы в сборке, а не библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="e5a49-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="e5a49-141">Регистрация типов сборки и регистрация библиотеки типов — это разные операции.</span><span class="sxs-lookup"><span data-stu-id="e5a49-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="e5a49-142">Средство установки служб .NET</span><span class="sxs-lookup"><span data-stu-id="e5a49-142">.NET Services Installation Tool</span></span>

<span data-ttu-id="e5a49-143">[Средство установки служб .NET (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) добавляет управляемые классы в службы компонентов Windows 2000 и реализует одновременно несколько задач.</span><span class="sxs-lookup"><span data-stu-id="e5a49-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="e5a49-144">Помимо загрузки и регистрации сборки программа Regsvcs.exe может создавать, регистрировать и устанавливать библиотеку типов в существующее приложение COM+ 1.0.</span><span class="sxs-lookup"><span data-stu-id="e5a49-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5a49-145">См. также</span><span class="sxs-lookup"><span data-stu-id="e5a49-145">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="e5a49-146">Предоставление компонентов .NET Framework клиентам COM</span><span class="sxs-lookup"><span data-stu-id="e5a49-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="e5a49-147">Oпределение типов .NET для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="e5a49-147">Qualifying .NET Types for Interoperation</span></span>](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- <span data-ttu-id="e5a49-148">[Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface) (Введение в интерфейс класса)</span><span class="sxs-lookup"><span data-stu-id="e5a49-148">[Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)</span></span>
- [<span data-ttu-id="e5a49-149">Вопросы безопасности сборок</span><span class="sxs-lookup"><span data-stu-id="e5a49-149">Assembly Security Considerations</span></span>](../../standard/assembly/security-considerations.md)
- [<span data-ttu-id="e5a49-150">Tlbexp.exe (программа экспорта библиотек типов)</span><span class="sxs-lookup"><span data-stu-id="e5a49-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="e5a49-151">Регистрация сборок в COM</span><span class="sxs-lookup"><span data-stu-id="e5a49-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="e5a49-152">[Практическое руководство. Встраивание библиотек типов как ресурсов Win32 в приложения](/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e5a49-152">[How to: Embed Type Libraries as Win32 Resources in Applications](/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>
