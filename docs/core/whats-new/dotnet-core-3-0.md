---
title: Новые возможности .NET Core 3.0
description: Дополнительные сведения о новых возможностях .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 06/14/2019
ms.openlocfilehash: b1dd243d754bfc3b682c084820547f6b7846f0ea
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484659"
---
# <a name="whats-new-in-net-core-30-preview-6"></a><span data-ttu-id="44a2f-103">Новые возможности .NET Core 3.0 (предварительная версия 6)</span><span class="sxs-lookup"><span data-stu-id="44a2f-103">What's new in .NET Core 3.0 (Preview 6)</span></span>

<span data-ttu-id="44a2f-104">Статья описывает новые возможности .NET Core 3.0 (вплоть до предварительной версии 6).</span><span class="sxs-lookup"><span data-stu-id="44a2f-104">This article describes what is new in .NET Core 3.0 (through preview 6).</span></span> <span data-ttu-id="44a2f-105">Одно из основных усовершенствований — это поддержка классических приложений Windows (только Windows).</span><span class="sxs-lookup"><span data-stu-id="44a2f-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="44a2f-106">С помощью пакета SDK для .NET Core 3.0 под названием Windows Desktop можно переносить приложения Windows Forms и Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="44a2f-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="44a2f-107">Следует уточнить, что компонент Windows Desktop поддерживается и включен только в Windows.</span><span class="sxs-lookup"><span data-stu-id="44a2f-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="44a2f-108">Дополнительные сведения см. далее в этой статье, в разделе [Рабочий стол Windows](#windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="44a2f-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="44a2f-109">В .NET Core 3.0 добавлена поддержка C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="44a2f-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="44a2f-110">Настоятельно рекомендуется использовать [последний выпуск Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview) или Visual Studio Code с расширением OmniSharp.</span><span class="sxs-lookup"><span data-stu-id="44a2f-110">It's highly recommended that you use the [latest release of Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview), or Visual Studio Code with the OmniSharp extension.</span></span>

<span data-ttu-id="44a2f-111">[Скачайте .NET Core 3.0 (предварительная версия 6) и начните работу с ](https://aka.ms/netcore3download) прямо сейчас в Windows, Mac и Linux.</span><span class="sxs-lookup"><span data-stu-id="44a2f-111">[Download and get started with .NET Core 3.0 Preview 6](https://aka.ms/netcore3download) right now on Windows, Mac, and Linux.</span></span>

<span data-ttu-id="44a2f-112">Для получения дополнительных сведений о каждой предварительной версии см. следующие объявления:</span><span class="sxs-lookup"><span data-stu-id="44a2f-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="44a2f-113">Объявление о .NET Core 3.0 (предварительная версия 6)</span><span class="sxs-lookup"><span data-stu-id="44a2f-113">.NET Core 3.0 Preview 6 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [<span data-ttu-id="44a2f-114">Объявление о .NET Core 3.0 (предварительная версия 5)</span><span class="sxs-lookup"><span data-stu-id="44a2f-114">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="44a2f-115">Объявление о .NET Core 3.0 (предварительная версия 4)</span><span class="sxs-lookup"><span data-stu-id="44a2f-115">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="44a2f-116">Объявление о .NET Core 3.0 (предварительная версия 3)</span><span class="sxs-lookup"><span data-stu-id="44a2f-116">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="44a2f-117">Объявление о .NET Core 3.0, предварительная версия 2</span><span class="sxs-lookup"><span data-stu-id="44a2f-117">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="44a2f-118">Объявление о .NET Core 3.0, предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="44a2f-118">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="44a2f-119">Установщик пакета SDK Windows для .NET Core</span><span class="sxs-lookup"><span data-stu-id="44a2f-119">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="44a2f-120">Начиная с .NET Core 3.0, установщик MSI для Windows был изменен.</span><span class="sxs-lookup"><span data-stu-id="44a2f-120">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="44a2f-121">Установщики пакетов SDK теперь обновляют дополнительные пакеты функций SDK на месте.</span><span class="sxs-lookup"><span data-stu-id="44a2f-121">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="44a2f-122">Пакеты функций определяют *сотни* в обозначении *исправления* в номере версии.</span><span class="sxs-lookup"><span data-stu-id="44a2f-122">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="44a2f-123">Например, в версиях **3.0._101_** и **3.0._201_** пакеты функций различаются, а в версиях **3.0._101_** и **3.0._199_**  — одинаковы.</span><span class="sxs-lookup"><span data-stu-id="44a2f-123">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="44a2f-124">При установке пакета SDK для .NET Core **3.0._101_** пакет SDK для .NET Core **3.0._100_** , если он есть на компьютере, удаляется.</span><span class="sxs-lookup"><span data-stu-id="44a2f-124">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="44a2f-125">Когда на тот же компьютер устанавливается пакет SDK для .NET Core **3.0._200_** , пакет SDK для .NET Core **3.0._101_** удаляться не будет.</span><span class="sxs-lookup"><span data-stu-id="44a2f-125">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="44a2f-126">Дополнительные сведения об управлении версиями см. в разделе [Общие сведения об управлении версиями в .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="44a2f-126">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="44a2f-127">Предварительная версия C# 8.0</span><span class="sxs-lookup"><span data-stu-id="44a2f-127">C# 8.0 preview</span></span>

<span data-ttu-id="44a2f-128">.NET Core 3.0 поддерживает предварительную версию C# 8.</span><span class="sxs-lookup"><span data-stu-id="44a2f-128">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="44a2f-129">Дополнительные сведения о функциях C# 8.0 см. в разделе [Новые возможности C# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="44a2f-129">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="44a2f-130">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="44a2f-130">.NET Standard 2.1</span></span>

<span data-ttu-id="44a2f-131">Несмотря на то что .NET Core 3.0 поддерживает **.NET Standard 2.1**, шаблон `dotnet new classlib` по умолчанию создает проект, предназначенный для **.NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="44a2f-131">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="44a2f-132">Чтобы создать проект для **.NET Standard 2.1**, откройте файл проекта и измените значение свойства `TargetFramework` на `netstandard2.1`:</span><span class="sxs-lookup"><span data-stu-id="44a2f-132">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

<span data-ttu-id="44a2f-133">Если вы используете Visual Studio, у вас должна быть версия [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), так как Visual Studio 2017 не поддерживает **.NET Standard 2.1** или **.NET Core 3.0**.</span><span class="sxs-lookup"><span data-stu-id="44a2f-133">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="44a2f-134">Улучшенные API версий .NET Core</span><span class="sxs-lookup"><span data-stu-id="44a2f-134">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="44a2f-135">Начиная с .NET Core 3.0, API версий, предоставляемые с .NET Core, возвращают те данные, которые должны.</span><span class="sxs-lookup"><span data-stu-id="44a2f-135">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="44a2f-136">Например:</span><span class="sxs-lookup"><span data-stu-id="44a2f-136">For example:</span></span>

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="44a2f-137">Критическое изменение.</span><span class="sxs-lookup"><span data-stu-id="44a2f-137">Breaking change.</span></span> <span data-ttu-id="44a2f-138">С технической точки зрения это изменение является критическим, поскольку изменилась схема управления версиями.</span><span class="sxs-lookup"><span data-stu-id="44a2f-138">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="44a2f-139">Встроенные объекты, зависимые от платформы .NET</span><span class="sxs-lookup"><span data-stu-id="44a2f-139">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="44a2f-140">Были добавлены API-интерфейсы, которые разрешают доступ к определенным инструкциям ЦП, ориентированным на производительность, например **SIMD** или наборы **инструкций побитовой обработки**.</span><span class="sxs-lookup"><span data-stu-id="44a2f-140">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="44a2f-141">Эти инструкции помогут значительно улучшить производительность в некоторых сценариях, таких как эффективная параллельная обработка данных.</span><span class="sxs-lookup"><span data-stu-id="44a2f-141">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> 

<span data-ttu-id="44a2f-142">Там, где это возможно, библиотеки .NET начали использовать эти инструкции для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="44a2f-142">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="44a2f-143">Дополнительные сведения см. в разделе [Встроенные объекты, зависимые от платформы .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="44a2f-143">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="44a2f-144">Исполняемые файлы по умолчанию</span><span class="sxs-lookup"><span data-stu-id="44a2f-144">Default executables</span></span>

<span data-ttu-id="44a2f-145">.NET Core теперь по умолчанию собирает [исполняемые файлы, зависимые от платформы](../deploying/index.md#framework-dependent-executables-fde).</span><span class="sxs-lookup"><span data-stu-id="44a2f-145">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="44a2f-146">Такое поведение ново для приложений, которые используют глобально установленную версию .NET Core.</span><span class="sxs-lookup"><span data-stu-id="44a2f-146">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="44a2f-147">Раньше исполняемые файлы создавались только в [автономных развертываниях](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="44a2f-147">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="44a2f-148">Во время выполнения команды `dotnet build` или `dotnet publish` создается исполняемый файл, который соответствует среде и платформе используемого пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="44a2f-148">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="44a2f-149">Предполагается, что с этими исполняемыми файлами можно выполнять те же действия, что и с другими исполняемыми файлами в машинном коде, например:</span><span class="sxs-lookup"><span data-stu-id="44a2f-149">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="44a2f-150">исполняемый файл можно дважды щелкнуть;</span><span class="sxs-lookup"><span data-stu-id="44a2f-150">You can double-click on the executable.</span></span>
* <span data-ttu-id="44a2f-151">приложение можно запустить из командной строки напрямую, например `myapp.exe` в Windows и `./myapp` в Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="44a2f-151">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="44a2f-152">Однофайловые исполняемые файлы</span><span class="sxs-lookup"><span data-stu-id="44a2f-152">Single-file executables</span></span>

<span data-ttu-id="44a2f-153">Команда `dotnet publish` поддерживает упаковку приложения в однофайловый исполняемый файл для конкретной платформы.</span><span class="sxs-lookup"><span data-stu-id="44a2f-153">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="44a2f-154">Исполняемый файл является самоизвлекаемым и содержит все зависимости (включая машинные), необходимые для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="44a2f-154">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="44a2f-155">При первом запуске приложение извлекается в каталог, который зависит от имени и идентификатора сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="44a2f-155">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="44a2f-156">Впоследствии запуск происходит быстрее.</span><span class="sxs-lookup"><span data-stu-id="44a2f-156">Startup is faster when the application is run again.</span></span> <span data-ttu-id="44a2f-157">Если версия не изменилась, приложению не нужно извлекать себя заново.</span><span class="sxs-lookup"><span data-stu-id="44a2f-157">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="44a2f-158">Чтобы опубликовать однофайловый исполняемый файл, задайте `PublishSingleFile` в своем проекте или в командной строке с помощью команды `dotnet publish`:</span><span class="sxs-lookup"><span data-stu-id="44a2f-158">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="44a2f-159">-или-</span><span class="sxs-lookup"><span data-stu-id="44a2f-159">-or-</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="44a2f-160">Дополнительные сведения о публикации однофайловых исполняемых файлов см. в [документе о разработке однофайловых пакетных установщиков](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="44a2f-160">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="assembly-linking"></a><span data-ttu-id="44a2f-161">Связывание сборок</span><span class="sxs-lookup"><span data-stu-id="44a2f-161">Assembly linking</span></span>

<span data-ttu-id="44a2f-162">Пакет SDK для .NET Core 3.0 содержит инструмент, который позволяет уменьшить размер приложения, анализируя промежуточный язык и устраняя неиспользуемые сборки.</span><span class="sxs-lookup"><span data-stu-id="44a2f-162">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="44a2f-163">Автономные приложения включают все необходимое для выполнения кода. Это позволяет не устанавливать .NET на соответствующем компьютере.</span><span class="sxs-lookup"><span data-stu-id="44a2f-163">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="44a2f-164">Но во многих случаях для работы приложения достаточно небольшого набора функций платформы, а все неиспользуемые библиотеки можно удалить.</span><span class="sxs-lookup"><span data-stu-id="44a2f-164">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="44a2f-165">Теперь .NET Core предоставляет параметр, который позволяет использовать [компоновщик IL](https://github.com/mono/linker) для сканирования кода приложения на промежуточном языке.</span><span class="sxs-lookup"><span data-stu-id="44a2f-165">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="44a2f-166">Это средство отслеживает необходимый код, а затем удаляет все неиспользуемые библиотеки.</span><span class="sxs-lookup"><span data-stu-id="44a2f-166">this tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="44a2f-167">Это позволяет значительно снизить размер развертывания для некоторых приложений.</span><span class="sxs-lookup"><span data-stu-id="44a2f-167">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="44a2f-168">Чтобы включить этот инструмент, укажите в проекте параметр `<PublishTrimmed>` и опубликуйте автономное приложение:</span><span class="sxs-lookup"><span data-stu-id="44a2f-168">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="44a2f-169">Например, простейший шаблон консольного приложения hello world, который входит в стандартную поставку, при публикации достигает размера около 70 МБ.</span><span class="sxs-lookup"><span data-stu-id="44a2f-169">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="44a2f-170">С помощью `<PublishTrimmed>` этот размер можно снизить до 30 МБ.</span><span class="sxs-lookup"><span data-stu-id="44a2f-170">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="44a2f-171">Важно учитывать, что приложения и платформы (в том числе ASP.NET Core и WPF), которые используют отражение или связанные динамические функции, могут стать неработоспособными после обрезки.</span><span class="sxs-lookup"><span data-stu-id="44a2f-171">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="44a2f-172">Такие нарушения возникают потому, что компоновщик ничего не знает о динамическом поведении и не может определить, какие типы платформы потребуются для отражения.</span><span class="sxs-lookup"><span data-stu-id="44a2f-172">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="44a2f-173">Но вы можете настроить компоновщик IL так, чтобы он учитывал этот сценарий.</span><span class="sxs-lookup"><span data-stu-id="44a2f-173">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="44a2f-174">В любом случае обязательно протестируйте приложение после обрезки.</span><span class="sxs-lookup"><span data-stu-id="44a2f-174">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="44a2f-175">Дополнительные сведения о компоновщике IL вы найдете в [этой документации](https://aka.ms/dotnet-illink) или на страницах репозитория [mono/linker]( https://github.com/mono/linker).</span><span class="sxs-lookup"><span data-stu-id="44a2f-175">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="44a2f-176">Многоуровневая компиляция</span><span class="sxs-lookup"><span data-stu-id="44a2f-176">Tiered compilation</span></span>

<span data-ttu-id="44a2f-177">[Многоуровневая компиляция](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (МК) по умолчанию входит только в .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="44a2f-177">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="44a2f-178">Эта функция позволяет среде выполнения более адаптивно использовать компилятор JIT для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="44a2f-178">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="44a2f-179">Основное преимущество МК состоит в том, что с ее помощью можно использовать методы JIT и выбирать более простой и при этом более медленный код или более сложный код, который лучше работает.</span><span class="sxs-lookup"><span data-stu-id="44a2f-179">The main benefit of TC is to enable (re-)jitting methods with slower-but-faster to produce code or higher-quality-but-slower to produce code.</span></span> <span data-ttu-id="44a2f-180">Это позволяет повысить производительность приложения на разных этапах его выполнения, с первого запуска и до достижения стабильной работы.</span><span class="sxs-lookup"><span data-stu-id="44a2f-180">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="44a2f-181">Если же МК не используется, каждый метод компилируется одним и тем же способом (как уровень высокого качества), который опирается на стабильную работу после запуска.</span><span class="sxs-lookup"><span data-stu-id="44a2f-181">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="44a2f-182">Чтобы включить быстрый JIT (код JIT уровня 0), добавьте в файл проекта следующий параметр:</span><span class="sxs-lookup"><span data-stu-id="44a2f-182">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="44a2f-183">Чтобы полностью отключить МК, добавьте в файл проекта следующий параметр:</span><span class="sxs-lookup"><span data-stu-id="44a2f-183">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a><span data-ttu-id="44a2f-184">Образы ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="44a2f-184">ReadyToRun images</span></span>

<span data-ttu-id="44a2f-185">Вы можете снизить время запуска приложения .NET Core, скомпилировав все сборки приложения в формат ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="44a2f-185">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="44a2f-186">R2R является разновидностью компиляции AOT.</span><span class="sxs-lookup"><span data-stu-id="44a2f-186">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="44a2f-187">Бинарные файлы R2R повышают производительность при запуске, снижая объем работы, выполняемой на этом этапе компилятором JIT.</span><span class="sxs-lookup"><span data-stu-id="44a2f-187">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="44a2f-188">Бинарные файлы содержат такой же машинный код, который создается компилятором JIT.</span><span class="sxs-lookup"><span data-stu-id="44a2f-188">The binaries contain similar native code compared to what the JIT would produce.</span></span>

<span data-ttu-id="44a2f-189">Бинарные файлы R2R имеют больший размер, так как содержат не только код на промежуточном языке (IL), который по-прежнему необходим для некоторых сценариев, но и версию того же кода на машинном языке.</span><span class="sxs-lookup"><span data-stu-id="44a2f-189">R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="44a2f-190">Функция R2R доступна только при публикации автономного приложения, предназначенного для конкретной среды выполнения (RID), например для Windows x64 или Linux x64.</span><span class="sxs-lookup"><span data-stu-id="44a2f-190">R2R is only available when you publish a self-contained app that targets a specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="44a2f-191">Чтобы скомпилировать приложение в формате R2R, добавьте параметр `<PublishReadyToRun>`:</span><span class="sxs-lookup"><span data-stu-id="44a2f-191">To compile your app as R2R, add the `<PublishReadyToRun>` setting:</span></span>

```xml
<PropertyGroup>
  <PublishReadyToRun>true</PublishReadyToRun>
</PropertyGroup>
```

<span data-ttu-id="44a2f-192">Опубликуйте автономное приложение.</span><span class="sxs-lookup"><span data-stu-id="44a2f-192">Publish a self-contained app.</span></span> <span data-ttu-id="44a2f-193">Например, такая команда создает автономное приложение для 64-разрядной версии Windows:</span><span class="sxs-lookup"><span data-stu-id="44a2f-193">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

```console
dotnet publish -c Release -r win-x64 --self-contained true
```

### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="44a2f-194">Ограничения при работе с несколькими платформами и архитектурами</span><span class="sxs-lookup"><span data-stu-id="44a2f-194">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="44a2f-195">Компилятор ReadyToRun пока не поддерживает перекрестное нацеливание.</span><span class="sxs-lookup"><span data-stu-id="44a2f-195">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="44a2f-196">Компиляцию необходимо выполнять в конкретной целевой среде.</span><span class="sxs-lookup"><span data-stu-id="44a2f-196">You must compile on a given target.</span></span> <span data-ttu-id="44a2f-197">Например, если вам нужен образ R2R для 64-разрядной ОС Windows, команду публикации следует выполнять именно в этой среде.</span><span class="sxs-lookup"><span data-stu-id="44a2f-197">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="44a2f-198">Исключения для кроссплатформенного таргетирования:</span><span class="sxs-lookup"><span data-stu-id="44a2f-198">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="44a2f-199">можно использовать Windows x64 для компиляции образов Windows ARM32, ARM64 и x86;</span><span class="sxs-lookup"><span data-stu-id="44a2f-199">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="44a2f-200">можно использовать Windows x86 для компиляции образов Windows ARM32;</span><span class="sxs-lookup"><span data-stu-id="44a2f-200">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="44a2f-201">можно использовать Linux x64 для компиляции образов Linux ARM32 и ARM64.</span><span class="sxs-lookup"><span data-stu-id="44a2f-201">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="44a2f-202">Сборка копирует зависимости</span><span class="sxs-lookup"><span data-stu-id="44a2f-202">Build copies dependencies</span></span>

<span data-ttu-id="44a2f-203">Команда `dotnet build` копирует зависимости NuGet для вашего приложения из кэша NuGet в выходную папку сборки.</span><span class="sxs-lookup"><span data-stu-id="44a2f-203">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="44a2f-204">Ранее зависимости копировались только в рамках выполнения команды `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-204">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="44a2f-205">Для некоторых операций, таких как связывание и публикация страницы Razor, по-прежнему будет требоваться публикация.</span><span class="sxs-lookup"><span data-stu-id="44a2f-205">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="44a2f-206">Локальные средства</span><span class="sxs-lookup"><span data-stu-id="44a2f-206">Local tools</span></span>

<span data-ttu-id="44a2f-207">В .NET Core 3.0 появились локальные средства.</span><span class="sxs-lookup"><span data-stu-id="44a2f-207">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="44a2f-208">Локальные средства похожи на [глобальные средства](../tools/global-tools.md), но связаны с определенным расположением на диске.</span><span class="sxs-lookup"><span data-stu-id="44a2f-208">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="44a2f-209">Локальные средства недоступны глобально и распространяются в виде пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="44a2f-209">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="44a2f-210">Если вы пробовали использовать локальные средства в предварительной версии 1 .NET Core 3.0, например запуск `dotnet tool restore` или `dotnet tool install`, удалите папку кэша локальных средств.</span><span class="sxs-lookup"><span data-stu-id="44a2f-210">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="44a2f-211">В противном случае локальные средства не будут работать ни в одной более новой версии.</span><span class="sxs-lookup"><span data-stu-id="44a2f-211">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="44a2f-212">Эта папка находится по адресу:</span><span class="sxs-lookup"><span data-stu-id="44a2f-212">This folder is located at:</span></span>
>
> <span data-ttu-id="44a2f-213">В macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="44a2f-213">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="44a2f-214">В Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="44a2f-214">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="44a2f-215">Локальные средства используют имя файла манифеста `dotnet-tools.json` в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="44a2f-215">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="44a2f-216">Этот файл манифеста определяет, какие средства доступны в этой папке и далее.</span><span class="sxs-lookup"><span data-stu-id="44a2f-216">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="44a2f-217">Файл манифеста можно распространять вместе с кодом, чтобы те же средства мог восстановить и использовать любой, кто работает с вашим кодом.</span><span class="sxs-lookup"><span data-stu-id="44a2f-217">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="44a2f-218">Для глобальных и локальных средств требуется совместимая версия среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="44a2f-218">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="44a2f-219">Сейчас на сайте NuGet.org многие средства предназначены для среды выполнения .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="44a2f-219">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="44a2f-220">Чтобы установить эти средства глобально или локально, нужно, как и раньше, установить [среду выполнения NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="44a2f-220">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="44a2f-221">Накат основной версии</span><span class="sxs-lookup"><span data-stu-id="44a2f-221">Major-version Roll Forward</span></span>

<span data-ttu-id="44a2f-222">В .NET Core 3.0 появилась функция согласия, которая позволяет приложению выполнять накат до последней основной версии .NET Core.</span><span class="sxs-lookup"><span data-stu-id="44a2f-222">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="44a2f-223">Кроме того, добавлен новый параметр для управления тем, как накат применяется к приложению.</span><span class="sxs-lookup"><span data-stu-id="44a2f-223">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="44a2f-224">Его можно настроить одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="44a2f-224">This can be configured in the following ways:</span></span>

- <span data-ttu-id="44a2f-225">Свойство файла проекта: `RollForward`</span><span class="sxs-lookup"><span data-stu-id="44a2f-225">Project file property: `RollForward`</span></span>
- <span data-ttu-id="44a2f-226">Свойство файла конфигурации среды выполнения: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="44a2f-226">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="44a2f-227">Переменная среды: `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="44a2f-227">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="44a2f-228">Аргумент командной строки: `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="44a2f-228">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="44a2f-229">Необходимо указать одно из следующих значений.</span><span class="sxs-lookup"><span data-stu-id="44a2f-229">One of the following values must be specified.</span></span> <span data-ttu-id="44a2f-230">Если параметр не указан, ему по умолчанию присваивается значение **Minor**.</span><span class="sxs-lookup"><span data-stu-id="44a2f-230">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="44a2f-231">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="44a2f-231">**LatestPatch**</span></span>\
<span data-ttu-id="44a2f-232">Накат до версии с наибольшим номером исправления.</span><span class="sxs-lookup"><span data-stu-id="44a2f-232">Roll forward to the highest patch version.</span></span> <span data-ttu-id="44a2f-233">Отключает накат дополнительных версий.</span><span class="sxs-lookup"><span data-stu-id="44a2f-233">This disables minor version roll forward.</span></span>
- <span data-ttu-id="44a2f-234">**Minor**</span><span class="sxs-lookup"><span data-stu-id="44a2f-234">**Minor**</span></span>\
<span data-ttu-id="44a2f-235">Накат до дополнительной версии со следующим по порядку возрастания номером, если запрошенная дополнительная версия отсутствует.</span><span class="sxs-lookup"><span data-stu-id="44a2f-235">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="44a2f-236">Если запрошенная дополнительная версия присутствует, используется политика **LatestPatch**.</span><span class="sxs-lookup"><span data-stu-id="44a2f-236">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="44a2f-237">**Major**</span><span class="sxs-lookup"><span data-stu-id="44a2f-237">**Major**</span></span>\
<span data-ttu-id="44a2f-238">Накат до основной версии со следующим по порядку возрастания или дополнительной версии с наименьшим номером, если запрошенная дополнительная версия отсутствует.</span><span class="sxs-lookup"><span data-stu-id="44a2f-238">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="44a2f-239">Если запрошенная основная версия присутствует, используется политика **Minor**.</span><span class="sxs-lookup"><span data-stu-id="44a2f-239">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="44a2f-240">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="44a2f-240">**LatestMinor**</span></span>\
<span data-ttu-id="44a2f-241">Накат до дополнительной версии с наибольшим номером, даже если запрошенная дополнительная версия присутствует.</span><span class="sxs-lookup"><span data-stu-id="44a2f-241">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="44a2f-242">Предназначен для сценариев размещения компонентов.</span><span class="sxs-lookup"><span data-stu-id="44a2f-242">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="44a2f-243">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="44a2f-243">**LatestMajor**</span></span>\
<span data-ttu-id="44a2f-244">Накат до основной версии с наибольшим номером и дополнительной версии с наибольшим номером, даже если запрошенная основная версия присутствует.</span><span class="sxs-lookup"><span data-stu-id="44a2f-244">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="44a2f-245">Предназначен для сценариев размещения компонентов.</span><span class="sxs-lookup"><span data-stu-id="44a2f-245">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="44a2f-246">**Disable**</span><span class="sxs-lookup"><span data-stu-id="44a2f-246">**Disable**</span></span>\
<span data-ttu-id="44a2f-247">Накат не выполняется.</span><span class="sxs-lookup"><span data-stu-id="44a2f-247">Don't roll forward.</span></span> <span data-ttu-id="44a2f-248">Привязка только к указанной версии.</span><span class="sxs-lookup"><span data-stu-id="44a2f-248">Only bind to specified version.</span></span> <span data-ttu-id="44a2f-249">Эта политика не рекомендуется для общего использования, поскольку отключает возможность наката до последних исправлений.</span><span class="sxs-lookup"><span data-stu-id="44a2f-249">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="44a2f-250">Это значение рекомендуется использовать только для тестирования.</span><span class="sxs-lookup"><span data-stu-id="44a2f-250">This value is only recommended for testing.</span></span>

<span data-ttu-id="44a2f-251">Все параметры, кроме параметра **Disable**, будут использовать версию с последним доступным исправлением.</span><span class="sxs-lookup"><span data-stu-id="44a2f-251">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="44a2f-252">Классические приложения Windows</span><span class="sxs-lookup"><span data-stu-id="44a2f-252">Windows desktop</span></span>

<span data-ttu-id="44a2f-253">.NET Core 3.0 поддерживает классические приложения Windows с помощью Windows Presentation Foundation (WPF) и Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="44a2f-253">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="44a2f-254">Эти платформы также поддерживают использование современных элементов управления и стилей Fluent из библиотеки XAML пользовательского интерфейса Windows (WinUI) через [острова XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="44a2f-254">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="44a2f-255">Компонент Windows Desktop является частью пакета SDK .NET Core 3.0 для Windows.</span><span class="sxs-lookup"><span data-stu-id="44a2f-255">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="44a2f-256">Вы можете создать приложение WPF или Windows Forms с помощью следующих команд `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="44a2f-256">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="44a2f-257">Visual Studio 2019 добавляет шаблоны **Новый проект** для .NET Core 3.0 Windows Forms и WPF.</span><span class="sxs-lookup"><span data-stu-id="44a2f-257">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="44a2f-258">Дополнительные сведения о переносе существующего приложения .NET Framework см. в разделах [Перенос проектов WPF](../porting/wpf.md) и [Перенос проектов Windows Forms](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="44a2f-258">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="44a2f-259">Компоненты, вызываемые COM — Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="44a2f-259">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="44a2f-260">Теперь в Windows можно создавать управляемые компоненты, вызываемые COM.</span><span class="sxs-lookup"><span data-stu-id="44a2f-260">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="44a2f-261">Эта возможность необходима для использования .NET Core с моделями надстроек COM и обеспечивает соответствие с платформой .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44a2f-261">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="44a2f-262">В отличие от .NET Framework, где в качестве сервера использовалась библиотека *mscoree.dll*, .NET Core при сборке вашего COM-компонента добавляет в каталог *bin* dll собственного средства запуска.</span><span class="sxs-lookup"><span data-stu-id="44a2f-262">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="44a2f-263">Пример того, как создать и использовать компонент COM, см. в разделе [Демонстрация COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="44a2f-263">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="44a2f-264">Развертывание MSIX — Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="44a2f-264">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="44a2f-265">[MSIX](https://docs.microsoft.com/windows/msix/) — это новый формат пакета приложения Windows.</span><span class="sxs-lookup"><span data-stu-id="44a2f-265">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="44a2f-266">Его можно использовать для развертывания классических приложений .NET Core 3.0 для Windows 10.</span><span class="sxs-lookup"><span data-stu-id="44a2f-266">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="44a2f-267">[Проект упаковки приложений Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), доступный в Visual Studio 2019, позволяет создавать пакеты MSIX с [автономными](../deploying/index.md#self-contained-deployments-scd) приложениями .NET Core.</span><span class="sxs-lookup"><span data-stu-id="44a2f-267">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="44a2f-268">Файл проекта .NET Core должен указывать поддерживаемые среды выполнения в свойстве `<RuntimeIdentifiers>`:</span><span class="sxs-lookup"><span data-stu-id="44a2f-268">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a><span data-ttu-id="44a2f-269">WinForms HighDPI</span><span class="sxs-lookup"><span data-stu-id="44a2f-269">WinForms HighDPI</span></span>

<span data-ttu-id="44a2f-270">Приложения .NET Core Windows Forms могут устанавливать режим высокого разрешения экрана с помощью <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44a2f-270">.NET Core Windows Forms applications can set High DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44a2f-271">Метод `SetHighDpiMode` задает соответствующий режим высокого разрешения экрана, если соответствующий параметр не был задан другими способами, такими как `App.Manifest` или P/Invoke, до `Application.Run`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-271">The `SetHighDpiMode` method sets the corresponding High DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="44a2f-272">Возможны следующие значения `highDpiMode`, выраженные перечислением <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="44a2f-272">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

<span data-ttu-id="44a2f-273">Дополнительные сведения о режимах высокого разрешения экрана см. в разделе [Разработка классических приложений с поддержкой высокого разрешения экрана в Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="44a2f-273">For more information about High DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="44a2f-274">Диапазоны и индексы</span><span class="sxs-lookup"><span data-stu-id="44a2f-274">Ranges and indices</span></span>

<span data-ttu-id="44a2f-275">Новый тип <xref:System.Index?displayProperty=nameWithType> можно использовать для индексирования.</span><span class="sxs-lookup"><span data-stu-id="44a2f-275">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="44a2f-276">Вы можете создать с помощью `int` индекс, который отсчитывается с начала, а с помощью оператора `^` префикса (C#) индекс, который отсчитывается с конца:</span><span class="sxs-lookup"><span data-stu-id="44a2f-276">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="44a2f-277">Кроме того, есть тип <xref:System.Range?displayProperty=nameWithType>, который состоит из двух значений `Index` (одно для начала и одно для конца) и который можно написать с помощью выражения диапазона `x..y` (C#).</span><span class="sxs-lookup"><span data-stu-id="44a2f-277">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="44a2f-278">После этого можно выполнить индексацию с помощью команды `Range`, которая создает срез:</span><span class="sxs-lookup"><span data-stu-id="44a2f-278">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="44a2f-279">Дополнительные сведения см. в [руководстве по диапазонам и индексам](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="44a2f-279">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="44a2f-280">Асинхронные потоки</span><span class="sxs-lookup"><span data-stu-id="44a2f-280">Async streams</span></span>

<span data-ttu-id="44a2f-281">Тип <xref:System.Collections.Generic.IAsyncEnumerable%601> — это новая асинхронная версия <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="44a2f-281">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="44a2f-282">Язык позволяет выполнить действие `await foreach` с этими объектами `IAsyncEnumerable<T>`, чтобы использовать их элементы, и действие `yield return` по отношению к ним, чтобы создать элементы.</span><span class="sxs-lookup"><span data-stu-id="44a2f-282">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="44a2f-283">В приведенном ниже примере демонстрируется создание и применение асинхронных потоков.</span><span class="sxs-lookup"><span data-stu-id="44a2f-283">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="44a2f-284">Инструкция `foreach` является асинхронной и использует `yield return`, чтобы создать асинхронные потоки для вызывающих объектов.</span><span class="sxs-lookup"><span data-stu-id="44a2f-284">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="44a2f-285">Этот шаблон (с использованием `yield return`) является рекомендуемой моделью для создания асинхронных потоков.</span><span class="sxs-lookup"><span data-stu-id="44a2f-285">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="44a2f-286">Помимо возможности `await foreach` вы также можете создать асинхронные итераторы, например, итератор, который возвращает `IAsyncEnumerable/IAsyncEnumerator`, для которого можно применить `await` и `yield`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-286">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="44a2f-287">Для объектов, которые необходимо удалить, можно использовать `IAsyncDisposable`, который реализовывают различные типы BCL, такие как `Stream` и `Timer`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-287">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="44a2f-288">Дополнительные сведения см. в [руководстве по асинхронным потокам](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="44a2f-288">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="44a2f-289">Усовершенствования чисел с плавающей запятой по IEEE</span><span class="sxs-lookup"><span data-stu-id="44a2f-289">IEEE Floating-point improvements</span></span>

<span data-ttu-id="44a2f-290">API плавающей запятой сейчас обновляются, чтобы соответствовать [редакции IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="44a2f-290">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="44a2f-291">Цель этих изменений — предоставлять все **обязательные** операции и гарантировать, что их поведение будет соответствовать спецификации IEEE. Дополнительные сведения об улучшениях, связанных с плавающей запятой, см. в записи блога [Улучшения в синтаксическом анализе и форматировании плавающей запятой в .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="44a2f-291">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="44a2f-292">Исправления синтаксического анализа и форматирования включают:</span><span class="sxs-lookup"><span data-stu-id="44a2f-292">Parsing and formatting fixes include:</span></span>

* <span data-ttu-id="44a2f-293">Правильный анализ и округление входных данных любой длины.</span><span class="sxs-lookup"><span data-stu-id="44a2f-293">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="44a2f-294">Правильный анализ и форматирование отрицательного нуля.</span><span class="sxs-lookup"><span data-stu-id="44a2f-294">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="44a2f-295">Правильный анализ `Infinity` и `NaN` с помощью проверки без учета регистра и допущения необязательного `+` в начале, где это применимо.</span><span class="sxs-lookup"><span data-stu-id="44a2f-295">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="44a2f-296">Новый API <xref:System.Math?displayProperty=nameWithType> включают:</span><span class="sxs-lookup"><span data-stu-id="44a2f-296">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

* <span data-ttu-id="44a2f-297"><xref:System.Math.BitIncrement(System.Double)> и <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="44a2f-297"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="44a2f-298">Соответствует операциям IEEE `nextUp` и `nextDown`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-298">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="44a2f-299">Они возвращают наименьшее число с плавающей запятой, которое может быть больше или меньше входных данных (соответственно).</span><span class="sxs-lookup"><span data-stu-id="44a2f-299">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="44a2f-300">Например, `Math.BitIncrement(0.0)` вернет `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-300">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* <span data-ttu-id="44a2f-301"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> и <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="44a2f-301"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="44a2f-302">Соответствуют операциям IEEE `maxNumMag` и `minNumMag`. Они возвращают значение, которое будет больше или меньше из двух величин (соответственно).</span><span class="sxs-lookup"><span data-stu-id="44a2f-302">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="44a2f-303">Например, `Math.MaxMagnitude(2.0, -3.0)` вернет `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-303">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="44a2f-304">Соответствует операции IEEE `logB`, которая возвращает целочисленное значение. Она возвращает целочисленный логарифм по основанию 2 входного параметра.</span><span class="sxs-lookup"><span data-stu-id="44a2f-304">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="44a2f-305">Этот метод действует практически так же, как `floor(log2(x))`, но с минимальными погрешностями округления.</span><span class="sxs-lookup"><span data-stu-id="44a2f-305">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="44a2f-306">Соответствует операции IEEE `scaleB`, которая принимает целочисленное значение. Возвращает `x * pow(2, n)`, но выполняется с минимальными погрешностями округления.</span><span class="sxs-lookup"><span data-stu-id="44a2f-306">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="44a2f-307">Соответствует операции IEEE `log2`. Возвращает логарифм по основанию 2.</span><span class="sxs-lookup"><span data-stu-id="44a2f-307">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="44a2f-308">Сводит к минимуму погрешность округления.</span><span class="sxs-lookup"><span data-stu-id="44a2f-308">It minimizes rounding error.</span></span>

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="44a2f-309">Соответствует операции IEEE `fma`. Выполняет умножение и сложение.</span><span class="sxs-lookup"><span data-stu-id="44a2f-309">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="44a2f-310">То есть он выполняет `(x * y) + z` как одну операцию, тем самым сводя к минимуму погрешность округления.</span><span class="sxs-lookup"><span data-stu-id="44a2f-310">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="44a2f-311">Пример — `FusedMultiplyAdd(1e308, 2.0, -1e308)`, возвращающий `1e308`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-311">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="44a2f-312">Стандартный `(1e308 * 2.0) - 1e308` возвращает `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-312">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="44a2f-313">Соответствует операции IEEE `copySign`. Возвращает значение `x`, но со знаком `y`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-313">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="44a2f-314">Быстрая встроенная поддержка JSON</span><span class="sxs-lookup"><span data-stu-id="44a2f-314">Fast built-in JSON support</span></span>

<span data-ttu-id="44a2f-315">Пользователи .NET в основном полагались на [**Json.NET**](https://www.newtonsoft.com/json) и другие популярные библиотеки JSON, которые по-прежнему остаются хорошими вариантами.</span><span class="sxs-lookup"><span data-stu-id="44a2f-315">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="44a2f-316">**Json.NET** использует в качестве базового типа данных строки .NET, которые обладают внутренней структурой UTF-16.</span><span class="sxs-lookup"><span data-stu-id="44a2f-316">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="44a2f-317">Новая встроенная поддержка JSON отличается высокой производительностью и малым распределением и основана на `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-317">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="44a2f-318">Были добавлены три новых основных типа, связанных с JSON, в пространство имен <xref:System.Text.Json?displayProperty=nameWithType> в .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="44a2f-318">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="44a2f-319">Эти типы *пока* не поддерживают сериализацию и десериализацию POCO CLR.</span><span class="sxs-lookup"><span data-stu-id="44a2f-319">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="44a2f-320">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="44a2f-320">Utf8JsonReader</span></span>

<span data-ttu-id="44a2f-321"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> — это однопроходный модуль чтения текста JSON в кодировке UTF-8 из `ReadOnlySpan<byte>` с высокой производительностью и низким уровнем распределения.</span><span class="sxs-lookup"><span data-stu-id="44a2f-321"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="44a2f-322">`Utf8JsonReader` — это основной тип низкого уровня, с помощью которого можно создавать пользовательские средства синтаксического анализа и десериализаторы.</span><span class="sxs-lookup"><span data-stu-id="44a2f-322">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="44a2f-323">Чтение полезных данных JSON с помощью нового `Utf8JsonReader` осуществляется в два раза быстрее, чем при использовании модуля чтения от **JSON.NET**.</span><span class="sxs-lookup"><span data-stu-id="44a2f-323">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="44a2f-324">Распределение не осуществляется, пока не понадобится актуализировать токены JSON в виде строк (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="44a2f-324">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="44a2f-325">Ниже приведен пример чтения с помощью файла [ **launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json), созданного Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="44a2f-325">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="44a2f-326">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="44a2f-326">Utf8JsonWriter</span></span>

<span data-ttu-id="44a2f-327"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> предоставляет высокопроизводительный, не использующий кэширование и однонаправленный способ записи текста JSON в кодировке UTF-8 из распространенных типов .NET, например `String`, `Int32` и `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-327"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="44a2f-328">Как и средство чтения, средство записи — это основной тип низкого уровня, с помощью которого можно создавать пользовательские сериализаторы.</span><span class="sxs-lookup"><span data-stu-id="44a2f-328">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="44a2f-329">Запись полезных данных JSON с помощью нового `Utf8JsonWriter` выполняется на 30–80 % быстрее, чем с помощью средства записи из **Json.NET**, и не требует выделения.</span><span class="sxs-lookup"><span data-stu-id="44a2f-329">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="44a2f-330">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="44a2f-330">JsonDocument</span></span>

<span data-ttu-id="44a2f-331"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> создается на основе `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-331"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="44a2f-332">`JsonDocument` предоставляет возможность анализировать данные JSON и создавать модель DOM только для чтения, которая может запрашиваться для поддержки случайного доступа и перечисления.</span><span class="sxs-lookup"><span data-stu-id="44a2f-332">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="44a2f-333">Доступ к элементам JSON, составляющим данные, может осуществляться через тип <xref:System.Text.Json.JsonElement>, который `JsonDocument` предоставляет как свойство с именем `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-333">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="44a2f-334">`JsonElement` содержит перечислители массива и объекта JSON вместе с API-интерфейсами для преобразования текста JSON в стандартные типы .NET.</span><span class="sxs-lookup"><span data-stu-id="44a2f-334">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="44a2f-335">Синтаксический анализ типичных полезных данных JSON и доступ ко всем членам с помощью `JsonDocument` выполняется в 2–3 раза быстрее, чем **Json.NET**, с небольшим количеством распределений данных приемлемого размера (т. е. < 1 МБ).</span><span class="sxs-lookup"><span data-stu-id="44a2f-335">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="44a2f-336">Ниже приведен пример использования `JsonDocument` и `JsonElement`, который может использоваться в качестве отправной точки:</span><span class="sxs-lookup"><span data-stu-id="44a2f-336">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

<span data-ttu-id="44a2f-337">Ниже приведен пример чтения в C# 8.0 с помощью файла [ **launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json), созданного Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="44a2f-337">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="44a2f-338">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="44a2f-338">JsonSerializer</span></span>

<span data-ttu-id="44a2f-339"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> создается на основе <xref:System.Text.Json.Utf8JsonReader> и <xref:System.Text.Json.Utf8JsonWriter> и позволяет при работе с JSON-документами и фрагментами выполнять быструю сериализацию с минимальной нагрузкой на ресурсы памяти.</span><span class="sxs-lookup"><span data-stu-id="44a2f-339"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="44a2f-340">ИЗУЧИТЕ: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md — пример для переноса в эту статью</span><span class="sxs-lookup"><span data-stu-id="44a2f-340">EXAMINE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md for an example to port to this article</span></span>

<span data-ttu-id="44a2f-341">Пример сериализации объекта в JSON:</span><span class="sxs-lookup"><span data-stu-id="44a2f-341">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="44a2f-342">Ниже приведен пример десериализации строки JSON в объект.</span><span class="sxs-lookup"><span data-stu-id="44a2f-342">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="44a2f-343">Можно использовать строку JSON, созданную в предыдущем примере:</span><span class="sxs-lookup"><span data-stu-id="44a2f-343">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="44a2f-344">Улучшения в совместимости</span><span class="sxs-lookup"><span data-stu-id="44a2f-344">Interop improvements</span></span>

<span data-ttu-id="44a2f-345">В .NET Core 3.0 улучшена совместимость собственного API.</span><span class="sxs-lookup"><span data-stu-id="44a2f-345">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="44a2f-346">Тип: NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="44a2f-346">Type: NativeLibrary</span></span>

<span data-ttu-id="44a2f-347"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> обеспечивает инкапсуляцию для загрузки собственной библиотеки (используя ту же логику загрузки, что и .NET Core P/Invoke) и предоставления соответствующих вспомогательных функций, таких как `getSymbol`.</span><span class="sxs-lookup"><span data-stu-id="44a2f-347"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="44a2f-348">Пример кода см. в разделе [Демонстрация DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="44a2f-348">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="44a2f-349">Собственное взаимодействие Windows</span><span class="sxs-lookup"><span data-stu-id="44a2f-349">Windows Native Interop</span></span>

<span data-ttu-id="44a2f-350">Windows предоставляет собственный API с широкими возможностями в виде API C, COM и WinRT.</span><span class="sxs-lookup"><span data-stu-id="44a2f-350">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="44a2f-351">При том что .NET Core поддерживает **P/Invoke**, в .NET Core 3.0 добавлена возможность **воссоздавать API COM** и **активировать API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="44a2f-351">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="44a2f-352">Пример кода см. в разделе [Демонстрация Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="44a2f-352">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="44a2f-353">Поддержка HTTP/2</span><span class="sxs-lookup"><span data-stu-id="44a2f-353">HTTP/2 support</span></span>

<span data-ttu-id="44a2f-354">Тип <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> поддерживает протокол HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="44a2f-354">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="44a2f-355">Если протокол HTTP/2 включен, версия протокола HTTP согласуется через TLS/ALPN, а HTTP/2 используется, только если его выбрал сервер.</span><span class="sxs-lookup"><span data-stu-id="44a2f-355">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="44a2f-356">Протоколом по умолчанию остается HTTP/1.1, но у вас есть два способа включить HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="44a2f-356">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="44a2f-357">Во-первых, можно указать использование HTTP/2 в заголовке запроса:</span><span class="sxs-lookup"><span data-stu-id="44a2f-357">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="44a2f-358">Во-вторых, можно изменить <xref:System.Net.Http.HttpClient> для использования HTTP/2 по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="44a2f-358">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="44a2f-359">При разработке приложений часто требуется подключение без шифрования.</span><span class="sxs-lookup"><span data-stu-id="44a2f-359">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="44a2f-360">Если вы знаете, что целевая конечная точка использует протокол HTTP/2, вы можете включить незашифрованные подключения для HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="44a2f-360">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="44a2f-361">Для этого задайте переменной среды `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` значение `1` или включите этот параметр в контексте приложения:</span><span class="sxs-lookup"><span data-stu-id="44a2f-361">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="44a2f-362">TLS 1.3 и OpenSSL 1.1.1 в Linux</span><span class="sxs-lookup"><span data-stu-id="44a2f-362">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="44a2f-363">Теперь .NET Core использует преимущества [поддержки TLS 1.3 в OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), когда она доступна в данной среде.</span><span class="sxs-lookup"><span data-stu-id="44a2f-363">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="44a2f-364">В TLS 1.3:</span><span class="sxs-lookup"><span data-stu-id="44a2f-364">With TLS 1.3:</span></span>

* <span data-ttu-id="44a2f-365">За счет уменьшения количества круговых путей между клиентом и сервером уменьшено время соединения.</span><span class="sxs-lookup"><span data-stu-id="44a2f-365">Connection times are improved with reduced round trips required between the client and server.</span></span>
* <span data-ttu-id="44a2f-366">За счет удаления различных устаревших и небезопасных алгоритмов шифрования повышена безопасность.</span><span class="sxs-lookup"><span data-stu-id="44a2f-366">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="44a2f-367">В системе Linux .NET Core 3.0 по возможности использует **OpenSSL 1.1.1**, **OpenSSL 1.1.0** или **OpenSSL 1.0.2**.</span><span class="sxs-lookup"><span data-stu-id="44a2f-367">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="44a2f-368">Если есть доступ к **OpenSSL 1.1.1**, оба типа, <xref:System.Net.Security.SslStream?displayProperty=nameWithType> и <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>, используют **TLS 1.3** (при условии что клиент и сервер поддерживают **TLS 1.3**).</span><span class="sxs-lookup"><span data-stu-id="44a2f-368">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="44a2f-369">Windows и macOS еще не поддерживают **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="44a2f-369">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="44a2f-370">.NET Core 3.0 будет поддерживать **TLS 1.3** в этих операционных системах, когда поддержка станет доступной.</span><span class="sxs-lookup"><span data-stu-id="44a2f-370">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="44a2f-371">В следующем примере C# 8.0 показано, как .NET Core 3.0 в Ubuntu 18.10 подключается к <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="44a2f-371">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="44a2f-372">Шифры криптографии</span><span class="sxs-lookup"><span data-stu-id="44a2f-372">Cryptography ciphers</span></span>

<span data-ttu-id="44a2f-373">В .NET 3.0 добавлена поддержка шифров **AES-GCM** и **AES-CCM**, реализованных с помощью <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> и <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> соответственно.</span><span class="sxs-lookup"><span data-stu-id="44a2f-373">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="44a2f-374">Оба этих алгоритма представляют собой [алгоритмы AEAD (аутентифицированного шифрования с присоединенными данными)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="44a2f-374">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="44a2f-375">В следующем коде показано использование шифра `AesGcm` для шифрования и расшифровки случайных данных.</span><span class="sxs-lookup"><span data-stu-id="44a2f-375">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="44a2f-376">Импорт и экспорт криптографических ключей</span><span class="sxs-lookup"><span data-stu-id="44a2f-376">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="44a2f-377">.NET Core 3.0 поддерживает импорт и экспорт асимметричных открытых и закрытых ключей из стандартных форматов.</span><span class="sxs-lookup"><span data-stu-id="44a2f-377">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="44a2f-378">Сертификат X.509 использовать не нужно.</span><span class="sxs-lookup"><span data-stu-id="44a2f-378">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="44a2f-379">Все типы ключей, включая *RSA*, *DSA*, *ECDsa* и *ECDiffieHellman*, поддерживают следующие форматы:</span><span class="sxs-lookup"><span data-stu-id="44a2f-379">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

* <span data-ttu-id="44a2f-380">**Открытый ключ**</span><span class="sxs-lookup"><span data-stu-id="44a2f-380">**Public Key**</span></span>
  * <span data-ttu-id="44a2f-381">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="44a2f-381">X.509 SubjectPublicKeyInfo</span></span>

* <span data-ttu-id="44a2f-382">**Закрытый ключ**</span><span class="sxs-lookup"><span data-stu-id="44a2f-382">**Private key**</span></span>
  * <span data-ttu-id="44a2f-383">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="44a2f-383">PKCS#8 PrivateKeyInfo</span></span>
  * <span data-ttu-id="44a2f-384">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="44a2f-384">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="44a2f-385">Ключи RSA также поддерживают:</span><span class="sxs-lookup"><span data-stu-id="44a2f-385">RSA keys also support:</span></span>

* <span data-ttu-id="44a2f-386">**Открытый ключ**</span><span class="sxs-lookup"><span data-stu-id="44a2f-386">**Public Key**</span></span>
  * <span data-ttu-id="44a2f-387">PKCS#1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="44a2f-387">PKCS#1 RSAPublicKey</span></span>

* <span data-ttu-id="44a2f-388">**Закрытый ключ**</span><span class="sxs-lookup"><span data-stu-id="44a2f-388">**Private key**</span></span>
  * <span data-ttu-id="44a2f-389">PKCS#1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="44a2f-389">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="44a2f-390">Методы экспорта создают двоичные данные в кодировке DER, а методы импорта выполняют то же самое.</span><span class="sxs-lookup"><span data-stu-id="44a2f-390">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="44a2f-391">Если ключ хранится в формате PEM в виде текста, вызывающему объекту потребуется выполнить декодирование содержимого в формате base64, прежде чем вызывать метод импорта.</span><span class="sxs-lookup"><span data-stu-id="44a2f-391">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="44a2f-392">Файлы **PKCS 8** можно проверять с помощью <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType>, а файлы **PFX/PKCS #12** — с помощью <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44a2f-392">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44a2f-393">Для манипуляций с файлами **PFX/PKCS #12** можно использовать <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44a2f-393">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="44a2f-394">SerialPort для Linux</span><span class="sxs-lookup"><span data-stu-id="44a2f-394">SerialPort for Linux</span></span>

<span data-ttu-id="44a2f-395">.NET Core 3.0 поддерживает <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> в Linux.</span><span class="sxs-lookup"><span data-stu-id="44a2f-395">.NET Core 3.0 supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="44a2f-396">Раньше среда .NET Core поддерживала `SerialPort` только в Windows.</span><span class="sxs-lookup"><span data-stu-id="44a2f-396">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="44a2f-397">Ограничения памяти в Docker и cgroup</span><span class="sxs-lookup"><span data-stu-id="44a2f-397">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="44a2f-398">Начиная с предварительной версии 3, запуск .NET Core 3.0 на платформе Linux с помощью Docker лучше работает с ограничениями памяти в cgroup.</span><span class="sxs-lookup"><span data-stu-id="44a2f-398">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="44a2f-399">Запуск контейнера Docker с ограничениями памяти, например с `docker run -m`, изменяет поведение .NET Core.</span><span class="sxs-lookup"><span data-stu-id="44a2f-399">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

* <span data-ttu-id="44a2f-400">Размер кучи сборщика мусора (GC) по умолчанию составляет не более 20 МБ или 75 % от ограничения памяти для контейнера.</span><span class="sxs-lookup"><span data-stu-id="44a2f-400">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
* <span data-ttu-id="44a2f-401">Конкретный размер можно указать абсолютным числом или в виде процента от ограничения cgroup.</span><span class="sxs-lookup"><span data-stu-id="44a2f-401">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
* <span data-ttu-id="44a2f-402">Минимальный зарезервированный размер сегмента в куче GC составляет 16 МБ.</span><span class="sxs-lookup"><span data-stu-id="44a2f-402">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="44a2f-403">При использовании такого размера количество создаваемых на компьютерах куч будет меньше.</span><span class="sxs-lookup"><span data-stu-id="44a2f-403">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="44a2f-404">Уменьшенные размеры куч сборки мусора</span><span class="sxs-lookup"><span data-stu-id="44a2f-404">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="44a2f-405">Размер кучи сборщика мусора по умолчанию был уменьшен, так что теперь .NET Core использует меньше памяти.</span><span class="sxs-lookup"><span data-stu-id="44a2f-405">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="44a2f-406">Это изменение лучше соответствует выделению бюджета нулевого поколения и размерам кэша современных процессоров.</span><span class="sxs-lookup"><span data-stu-id="44a2f-406">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="44a2f-407">Поддержка больших страниц сборки мусора</span><span class="sxs-lookup"><span data-stu-id="44a2f-407">Garbage Collection Large Page support</span></span>

<span data-ttu-id="44a2f-408">Большие страницы (также известные как огромные страницы в Linux) — это функция, благодаря которой операционная система может задавать области памяти больше, чем размер нативной страницы (часто 4K), чтобы повысить производительность приложения, запрашивающего такие страницы.</span><span class="sxs-lookup"><span data-stu-id="44a2f-408">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="44a2f-409">Сборщик мусора теперь можно настраивать с помощью параметра **GCLargePages** как дополнительной функции, позволяющей выделять большие страницы в Windows.</span><span class="sxs-lookup"><span data-stu-id="44a2f-409">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="44a2f-410">Поддержка GPIO для Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="44a2f-410">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="44a2f-411">В NuGet выпущено два новых пакета, которые можно использовать для программирования GPIO:</span><span class="sxs-lookup"><span data-stu-id="44a2f-411">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

* [<span data-ttu-id="44a2f-412">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="44a2f-412">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
* [<span data-ttu-id="44a2f-413">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="44a2f-413">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="44a2f-414">Пакеты GPIO содержат API для устройств *GPIO*, *SPI*, *I2C* и *PWM*.</span><span class="sxs-lookup"><span data-stu-id="44a2f-414">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="44a2f-415">Пакет привязок Интернета вещей содержит привязки устройств.</span><span class="sxs-lookup"><span data-stu-id="44a2f-415">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="44a2f-416">Дополнительные сведения см. в [репозитории GitHub устройств](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="44a2f-416">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="44a2f-417">Поддержка ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="44a2f-417">ARM64 Linux support</span></span>

<span data-ttu-id="44a2f-418">В .NET Core 3.0 добавлена поддержка ARM64 для Linux.</span><span class="sxs-lookup"><span data-stu-id="44a2f-418">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="44a2f-419">Основной вариант использования для ARM64 в данный момент — это сценарии Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="44a2f-419">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="44a2f-420">Дополнительные сведения см. в статье [Состояние .NET Core в ARM64](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="44a2f-420">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="44a2f-421">[Образы Docker для .NET Core в ARM64](https://hub.docker.com/r/microsoft/dotnet/) доступны для Alpine, Debian и Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="44a2f-421">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="44a2f-422">Поддержка **ARM64** в Windows еще недоступна.</span><span class="sxs-lookup"><span data-stu-id="44a2f-422">**ARM64** Windows support isn't yet available.</span></span>
