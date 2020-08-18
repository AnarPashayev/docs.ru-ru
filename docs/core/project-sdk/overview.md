---
title: Обзор пакета SDK для проекта .NET Core
titleSuffix: ''
description: Сведения о пакетах SDK для проектов .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 873c06007307c5892c4828f987486b4dd98dc9ae
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187918"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="8c7be-103">Пакеты SDK для проектов .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c7be-103">.NET Core project SDKs</span></span>

<span data-ttu-id="8c7be-104">Проекты .NET Core связаны с пакетом средств разработки программного обеспечения (SDK).</span><span class="sxs-lookup"><span data-stu-id="8c7be-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="8c7be-105">Каждый *пакет SDK для проекта* является набором [целевых объектов](/visualstudio/msbuild/msbuild-targets) MSBuild и связанных [задач](/visualstudio/msbuild/msbuild-tasks), которые отвечают за компиляцию, упаковку и публикацию кода.</span><span class="sxs-lookup"><span data-stu-id="8c7be-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="8c7be-106">Проект, который ссылается на пакет SDK для проекта, иногда называется *проектом в стиле пакета SDK*.</span><span class="sxs-lookup"><span data-stu-id="8c7be-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="8c7be-107">Доступные пакеты SDK</span><span class="sxs-lookup"><span data-stu-id="8c7be-107">Available SDKs</span></span>

<span data-ttu-id="8c7be-108">Для .NET Core доступны следующие пакеты SDK:</span><span class="sxs-lookup"><span data-stu-id="8c7be-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="8c7be-109">ID</span><span class="sxs-lookup"><span data-stu-id="8c7be-109">ID</span></span> | <span data-ttu-id="8c7be-110">Описание</span><span class="sxs-lookup"><span data-stu-id="8c7be-110">Description</span></span> | <span data-ttu-id="8c7be-111">Репозиторий</span><span class="sxs-lookup"><span data-stu-id="8c7be-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="8c7be-112">Пакет SDK для .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c7be-112">The .NET Core SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="8c7be-113">[Веб-пакет SDK](/aspnet/core/razor-pages/web-sdk) для .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c7be-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="8c7be-114">[Пакет SDK для Razor](/aspnet/core/razor-pages/sdk) в .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c7be-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="8c7be-115">Пакет SDK для службы рабочей роли в .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c7be-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="8c7be-116">Пакет SDK для WinForms и WPF в .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c7be-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="8c7be-117">Пакет SDK для .NET Core является базовым пакетом SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c7be-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="8c7be-118">Другие пакеты SDK ссылаются на пакет SDK для .NET Core, а проекты, связанные с другими пакетами SDK, имеют все доступные им свойства пакета SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c7be-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="8c7be-119">Например, веб-пакет SDK зависит от пакета SDK для .NET Core и пакета SDK для Razor.</span><span class="sxs-lookup"><span data-stu-id="8c7be-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="8c7be-120">Можно также создать собственный пакет SDK и распространять его с помощью NuGet.</span><span class="sxs-lookup"><span data-stu-id="8c7be-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="8c7be-121">Файлы проекта</span><span class="sxs-lookup"><span data-stu-id="8c7be-121">Project files</span></span>

<span data-ttu-id="8c7be-122">В основе проектов .NET Core лежит формат [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="8c7be-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="8c7be-123">Файлы проекта с такими расширениями, как *CPROJ* для проектов C# и *FPROJ* для проектов F#, имеют формат XML.</span><span class="sxs-lookup"><span data-stu-id="8c7be-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="8c7be-124">Корневым элементом файла проекта MSBuild является элемент [Project](/visualstudio/msbuild/project-element-msbuild).</span><span class="sxs-lookup"><span data-stu-id="8c7be-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="8c7be-125">Элемент `Project` имеет необязательный атрибут `Sdk`, указывающий, какой пакет SDK (и версию) следует использовать.</span><span class="sxs-lookup"><span data-stu-id="8c7be-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="8c7be-126">Чтобы использовать средства .NET Core и выполнить сборку кода, задайте в качестве значения атрибута `Sdk` один из идентификаторов, указанных в таблице[Доступные пакеты SDK](#available-sdks).</span><span class="sxs-lookup"><span data-stu-id="8c7be-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="8c7be-127">Чтобы указать пакет SDK, который содержится в NuGet, добавьте версию в конец имени или укажите имя и версию в файле *global.json*.</span><span class="sxs-lookup"><span data-stu-id="8c7be-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="8c7be-128">Другим способом указания пакета SDK является элемент [Sdk](/visualstudio/msbuild/sdk-element-msbuild) верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="8c7be-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="8c7be-129">Указание пакета SDK одним из этих способов значительно упрощает файлы проекта для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c7be-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="8c7be-130">На этапе оценки проекта MSBuild добавляет неявные директивы импорта для `Sdk.props` в начале и для `Sdk.targets` в конце файла проекта.</span><span class="sxs-lookup"><span data-stu-id="8c7be-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="8c7be-131">На компьютере Windows файлы *Sdk.props* и *Sdk.targets* можно найти в папке *%ProgramFiles%\dotnet\sdk\\[версия]\Sdks\Microsoft.NET.Sdk\Sdk*.</span><span class="sxs-lookup"><span data-stu-id="8c7be-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="8c7be-132">Предварительная обработка файла проекта</span><span class="sxs-lookup"><span data-stu-id="8c7be-132">Preprocess the project file</span></span>

<span data-ttu-id="8c7be-133">Увидеть полностью развернутый проект так, как он отображается в MSBuild, можно после включения пакета SDK и его целевых объектов с помощью команды `dotnet msbuild -preprocess`.</span><span class="sxs-lookup"><span data-stu-id="8c7be-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="8c7be-134">Включите параметр [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) в команду [`dotnet msbuild`](../tools/dotnet-msbuild.md), чтобы просмотреть сведения об импортированных файлах, их источниках, вкладе в сборку без фактического создания проекта.</span><span class="sxs-lookup"><span data-stu-id="8c7be-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="8c7be-135">Если проект имеет несколько требуемых версий .NET Framework, результаты выполнения команды должны касаться только одной из них. Эту версию следует указать в качестве свойства MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8c7be-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="8c7be-136">Пример:</span><span class="sxs-lookup"><span data-stu-id="8c7be-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="8c7be-137">Включения для элементов компиляции по умолчанию</span><span class="sxs-lookup"><span data-stu-id="8c7be-137">Default compilation includes</span></span>

<span data-ttu-id="8c7be-138">В пакете SDK определены стандартные включения и исключения для элементов компиляции, внедренных ресурсов и элементов `None`.</span><span class="sxs-lookup"><span data-stu-id="8c7be-138">The default includes and excludes for compile items, embedded resources, and `None` items are defined in the SDK.</span></span> <span data-ttu-id="8c7be-139">В отличие от проектов .NET Framework без пакетов SDK в файле проекта не нужно указывать эти элементы, так как для наиболее распространенных вариантов использования действуют значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8c7be-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="8c7be-140">Это позволяет уменьшить файлы проекта и без труда понимать их, а при необходимости даже вносить правки вручную.</span><span class="sxs-lookup"><span data-stu-id="8c7be-140">This makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="8c7be-141">В следующей таблице показано, какие элементы и [стандартные маски](https://en.wikipedia.org/wiki/Glob_(programming)) включены и исключены в пакете SDK для .NET Core:</span><span class="sxs-lookup"><span data-stu-id="8c7be-141">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="8c7be-142">Элемент</span><span class="sxs-lookup"><span data-stu-id="8c7be-142">Element</span></span>           | <span data-ttu-id="8c7be-143">Стандартная маска включения</span><span class="sxs-lookup"><span data-stu-id="8c7be-143">Include glob</span></span>                              | <span data-ttu-id="8c7be-144">Стандартная маска исключения</span><span class="sxs-lookup"><span data-stu-id="8c7be-144">Exclude glob</span></span>                                                  | <span data-ttu-id="8c7be-145">Стандартная маска удаления</span><span class="sxs-lookup"><span data-stu-id="8c7be-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="8c7be-146">Компилятор</span><span class="sxs-lookup"><span data-stu-id="8c7be-146">Compile</span></span>           | <span data-ttu-id="8c7be-147">\*\*/\*.cs (или другие расширения языка)</span><span class="sxs-lookup"><span data-stu-id="8c7be-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="8c7be-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="8c7be-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="8c7be-149">Н/Д</span><span class="sxs-lookup"><span data-stu-id="8c7be-149">N/A</span></span>                      |
| <span data-ttu-id="8c7be-150">ВнедренныйРесурс</span><span class="sxs-lookup"><span data-stu-id="8c7be-150">EmbeddedResource</span></span>  | <span data-ttu-id="8c7be-151">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="8c7be-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="8c7be-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="8c7be-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="8c7be-153">Н/Д</span><span class="sxs-lookup"><span data-stu-id="8c7be-153">N/A</span></span>                      |
| <span data-ttu-id="8c7be-154">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="8c7be-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="8c7be-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="8c7be-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="8c7be-156">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="8c7be-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="8c7be-157">Папки `./bin` и `./obj`, которые представлены свойствами MSBuild `$(BaseOutputPath)` и `$(BaseIntermediateOutputPath)`, исключаются из стандартных масок исключения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8c7be-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="8c7be-158">Исключения представляется свойством `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="8c7be-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

#### <a name="build-errors"></a><span data-ttu-id="8c7be-159">Ошибки сборки</span><span class="sxs-lookup"><span data-stu-id="8c7be-159">Build errors</span></span>

<span data-ttu-id="8c7be-160">Если вы явным образом определите любой из этих элементов в файле проекта, скорее всего, произойдет ошибка сборки NETSDK1022 с примерно таким сообщением:</span><span class="sxs-lookup"><span data-stu-id="8c7be-160">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="8c7be-161">"Duplicate 'Compile' items were included.</span><span class="sxs-lookup"><span data-stu-id="8c7be-161">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="8c7be-162">The .NET SDK includes Compile items from your project directory by default.</span><span class="sxs-lookup"><span data-stu-id="8c7be-162">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="8c7be-163">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file. (Включены повторяющиеся элементы Compile. По умолчанию пакет SDK для .NET включает элементы Compile из каталога проекта. Можно удалить эти элементы из файла проекта или задать для свойства "EnableDefaultCompileItems" значение "false", чтобы явно включить их в файл проекта.)</span><span class="sxs-lookup"><span data-stu-id="8c7be-163">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="8c7be-164">"Duplicate 'EmbeddedResource' items were included.</span><span class="sxs-lookup"><span data-stu-id="8c7be-164">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="8c7be-165">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span><span class="sxs-lookup"><span data-stu-id="8c7be-165">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="8c7be-166">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file" (Включены повторяющиеся элементы EmbeddedResource. По умолчанию пакет SDK для .NET включает элементы EmbeddedResource из каталога проекта. Можно удалить эти элементы из файла проекта или задать для свойства EnableDefaultEmbeddedResourceItems значение false, чтобы явно включить их в файл проекта).</span><span class="sxs-lookup"><span data-stu-id="8c7be-166">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="8c7be-167">Чтобы устранить такую проблему, выполните любое из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="8c7be-167">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="8c7be-168">Удалите явно заданные элементы `Compile`, `EmbeddedResource` или `None`, которые совпадают с неявно заданными параметрами из предыдущей таблицы.</span><span class="sxs-lookup"><span data-stu-id="8c7be-168">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="8c7be-169">Задайте свойству `EnableDefaultItems` значение `false`, чтобы отключить все неявные включения файлов.</span><span class="sxs-lookup"><span data-stu-id="8c7be-169">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="8c7be-170">Если вы хотите указать файлы, которые нужно публиковать вместе с приложением, для этого можно по-прежнему использовать привычные механизмы MSBuild (например, элемент `Content`).</span><span class="sxs-lookup"><span data-stu-id="8c7be-170">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="8c7be-171">Выборочно отключите только стандартные маски `Compile`, `EmbeddedResource` или `None`, задав для свойства `EnableDefaultCompileItems`, `EnableDefaultEmbeddedResourceItems` или `EnableDefaultNoneItems` значение `false`.</span><span class="sxs-lookup"><span data-stu-id="8c7be-171">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the `EnableDefaultCompileItems`, `EnableDefaultEmbeddedResourceItems`, or `EnableDefaultNoneItems` property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="8c7be-172">Если вы отключите только стандартные маски `Compile`, обозреватель решений в Visual Studio будет по-прежнему отображать элементы \*.cs в составе проекта, включая их в виде элементов `None`.</span><span class="sxs-lookup"><span data-stu-id="8c7be-172">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="8c7be-173">Чтобы отключить неявную стандартную маску `None`, задайте свойству `EnableDefaultNoneItems` значение `false`.</span><span class="sxs-lookup"><span data-stu-id="8c7be-173">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="customize-the-build"></a><span data-ttu-id="8c7be-174">Настройка сборки</span><span class="sxs-lookup"><span data-stu-id="8c7be-174">Customize the build</span></span>

<span data-ttu-id="8c7be-175">Существует несколько способов [настройки сборки](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="8c7be-175">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="8c7be-176">Может потребоваться переопределить свойство, передав его в качестве аргумента в команду [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) или [dotnet](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="8c7be-176">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="8c7be-177">Можно также добавить свойство в файл проекта или в файл *Directory.Build.props*.</span><span class="sxs-lookup"><span data-stu-id="8c7be-177">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="8c7be-178">Список полезных свойств для проектов .NET Core см. в статье [Свойства MSBuild для проектов пакета SDK для .NET Core](msbuild-props.md).</span><span class="sxs-lookup"><span data-stu-id="8c7be-178">For a list of useful properties for .NET Core projects, see [MSBuild reference for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="8c7be-179">Пользовательские целевые объекты</span><span class="sxs-lookup"><span data-stu-id="8c7be-179">Custom targets</span></span>

<span data-ttu-id="8c7be-180">В проектах .NET Core доступна возможность упаковки пользовательских целевых объектов и свойства MSBuild для использования в проектах, применяющих этот пакет.</span><span class="sxs-lookup"><span data-stu-id="8c7be-180">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="8c7be-181">Используйте этот тип расширяемости, если нужно выполнить следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="8c7be-181">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="8c7be-182">расширить процесс сборки;</span><span class="sxs-lookup"><span data-stu-id="8c7be-182">Extend the build process.</span></span>
- <span data-ttu-id="8c7be-183">получить доступ к артефактам процесса сборки, таким как созданные файлы;</span><span class="sxs-lookup"><span data-stu-id="8c7be-183">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="8c7be-184">проверить конфигурацию, с которой была запущена сборка.</span><span class="sxs-lookup"><span data-stu-id="8c7be-184">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="8c7be-185">Чтобы добавить пользовательские целевые объекты или свойства сборки, нужно поместить файлы в форме `<package_id>.targets` или `<package_id>.props` (например, `Contoso.Utility.UsefulStuff.targets`) в папку *build* проекта.</span><span class="sxs-lookup"><span data-stu-id="8c7be-185">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="8c7be-186">Следующий XML-код является фрагментом из файла *CPROJ*, который указывает команде [`dotnet pack`](../tools/dotnet-pack.md), что именно нужно упаковать.</span><span class="sxs-lookup"><span data-stu-id="8c7be-186">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="8c7be-187">Элемент `<ItemGroup Label="dotnet pack instructions">` помещает файлы целевых объектов в папку *build* в пакете.</span><span class="sxs-lookup"><span data-stu-id="8c7be-187">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="8c7be-188">Элемент `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` помещает сборки и файлы *JSON* в папку *build*.</span><span class="sxs-lookup"><span data-stu-id="8c7be-188">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

<span data-ttu-id="8c7be-189">Чтобы использовать пользовательский целевой объект в проекте, добавьте элемент `PackageReference`, указывающий на пакет и его версию.</span><span class="sxs-lookup"><span data-stu-id="8c7be-189">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="8c7be-190">В отличие от средств пакет пользовательских целевых объектов входит в замыкание зависимостей исходного проекта.</span><span class="sxs-lookup"><span data-stu-id="8c7be-190">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="8c7be-191">Вы можете настроить способ использования пользовательского целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="8c7be-191">You can configure how to use the custom target.</span></span> <span data-ttu-id="8c7be-192">Так как это целевой объект MSBuild, он может зависеть от заданного целевого объекта, запускаться после другого целевого объекта или быть вызван вручную с помощью команды `dotnet msbuild -t:<target-name>`.</span><span class="sxs-lookup"><span data-stu-id="8c7be-192">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="8c7be-193">Однако для удобства пользователей можно объединить средства для отдельных проектов и пользовательские целевые объекты.</span><span class="sxs-lookup"><span data-stu-id="8c7be-193">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="8c7be-194">В этом сценарии средство для отдельного проекта принимает необходимые параметры и преобразует их в требуемый вызов [`dotnet msbuild`](../tools/dotnet-msbuild.md), который выполняет целевой объект.</span><span class="sxs-lookup"><span data-stu-id="8c7be-194">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="8c7be-195">Пример подобного типа синергии можно увидеть в репозитории [примеров хакатона MVP Summit 2016](https://github.com/dotnet/MVPSummitHackathon2016) в проекте [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).</span><span class="sxs-lookup"><span data-stu-id="8c7be-195">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c7be-196">См. также</span><span class="sxs-lookup"><span data-stu-id="8c7be-196">See also</span></span>

- <span data-ttu-id="8c7be-197">[установите .NET Core](../install/index.yml).</span><span class="sxs-lookup"><span data-stu-id="8c7be-197">[Install .NET Core](../install/index.yml)</span></span>
- [<span data-ttu-id="8c7be-198">Использование пакетов SDK проекта MSBuild</span><span class="sxs-lookup"><span data-stu-id="8c7be-198">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="8c7be-199">Упаковка пользовательских целевых объектов и свойств MSBuild с помощью NuGet</span><span class="sxs-lookup"><span data-stu-id="8c7be-199">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
