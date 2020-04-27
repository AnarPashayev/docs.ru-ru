---
title: Команда dotnet run
description: Команда dotnet run — это удобное средство для запуска приложения из исходного кода.
ms.date: 02/19/2020
ms.openlocfilehash: 77282fd8615ef01b7867c1bf0f741c834b6ddb30
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102776"
---
# <a name="dotnet-run"></a><span data-ttu-id="c8c7f-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="c8c7f-103">dotnet run</span></span>

<span data-ttu-id="c8c7f-104">**Эта статья относится к следующему:** ✔️ пакет SDK для .NET Core 2.x и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="c8c7f-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c8c7f-105">name</span><span class="sxs-lookup"><span data-stu-id="c8c7f-105">Name</span></span>

<span data-ttu-id="c8c7f-106">`dotnet run` — выполняет исходный код без дополнительных явных команд компиляции или запуска.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c8c7f-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="c8c7f-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a><span data-ttu-id="c8c7f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c8c7f-108">Description</span></span>

<span data-ttu-id="c8c7f-109">`dotnet run` — это удобное средство для запуска приложения из исходного кода одной командой.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="c8c7f-110">Это полезно для быстрой последовательной разработки из командной строки.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="c8c7f-111">В отношении сборки кода эта команда зависима от команды [`dotnet build`](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="c8c7f-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="c8c7f-112">Любые требования к сборке, например, то, что проект сначала нужно восстановить, применяются и к `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="c8c7f-113">Выходные файлы записываются в расположение по умолчанию, которым является `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="c8c7f-114">Например, если у вас есть приложение `netcoreapp2.1` и вы запускаете `dotnet run`, выходные данные помещаются в `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="c8c7f-115">При необходимости файлы перезаписываются.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-115">Files are overwritten as needed.</span></span> <span data-ttu-id="c8c7f-116">Временные файлы помещаются в каталог `obj`.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="c8c7f-117">Когда в проекте задано несколько платформ, выполнение `dotnet run` приводит к ошибке, если только для указания платформы не используется параметр `-f|--framework <FRAMEWORK>`.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="c8c7f-118">Команда `dotnet run` используется в контексте проектов, а не созданных сборок.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="c8c7f-119">Если вместо этого вы пытаетесь запустить библиотеку DLL платформозависимого приложения, следует использовать [dotnet](dotnet.md) без команды.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="c8c7f-120">Например, для выполнения `myapp.dll` используйте:</span><span class="sxs-lookup"><span data-stu-id="c8c7f-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="c8c7f-121">Дополнительные сведения о драйвере `dotnet` см. в разделе [Средства интерфейса командной строки (CLI) .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="c8c7f-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="c8c7f-122">Для запуска приложения команда `dotnet run` разрешает зависимости приложения, выходящие за пределы общей среды выполнения, из кэша NuGet.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="c8c7f-123">Из-за использования кэшированных зависимостей не рекомендуется применять команду `dotnet run` для запуска приложений в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="c8c7f-124">Вместо этого [создайте развертывание](../deploying/index.md) с помощью команды [`dotnet publish`](dotnet-publish.md) и разверните опубликованные выходные данные.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="c8c7f-125">Неявное восстановление</span><span class="sxs-lookup"><span data-stu-id="c8c7f-125">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="c8c7f-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="c8c7f-126">Options</span></span>

- **`--`**

  <span data-ttu-id="c8c7f-127">Отделяет аргументы, предназначенные для `dotnet run`, от аргументов для выполняемого приложения.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-127">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="c8c7f-128">Все аргументы после разделителя передаются выполняемому приложению.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-128">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="c8c7f-129">Определяет конфигурацию сборки.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-129">Defines the build configuration.</span></span> <span data-ttu-id="c8c7f-130">По умолчанию для большинства проектов используется `Debug`, но можно переопределить параметры конфигурации сборки в проекте.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-130">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c8c7f-131">Выполняет сборку и запуск приложения с использованием указанной [платформы](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c8c7f-131">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="c8c7f-132">Эта платформа должна быть указана в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-132">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="c8c7f-133">Принудительное разрешение всех зависимостей, даже если последнее восстановление прошло успешно.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-133">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="c8c7f-134">Указание этого флага дает тот же результат, что удаление файла *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-134">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c8c7f-135">Выводит краткую справку по команде.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-135">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="c8c7f-136">Позволяет остановить команду и дождаться, пока пользователь введет данные или выполнит действие (например, завершит проверку подлинности).</span><span class="sxs-lookup"><span data-stu-id="c8c7f-136">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="c8c7f-137">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-137">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="c8c7f-138">Имя профиля запуска (при его наличии), который следует использовать при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="c8c7f-139">Профили запуска обычно определяются в файле *launchSettings.json* и, как правило, называются `Development`, `Staging` и `Production`.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="c8c7f-140">Дополнительные сведения см. в разделе [Работа с несколькими средами](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="c8c7f-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="c8c7f-141">Не выполняет сборку проекта перед запуском.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-141">Doesn't build the project before running.</span></span> <span data-ttu-id="c8c7f-142">Он также неявно задает флаг `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-142">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="c8c7f-143">При восстановлении проекта с перекрестными ссылками между проектами восстанавливает только корневой проект, но не ссылки.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="c8c7f-144">Не пытается использовать файл *launchSettings.json* для настройки приложения.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c8c7f-145">Не выполняет неявное восстановление при выполнении команды.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-145">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="c8c7f-146">Задает путь к запускаемому файлу проекта (имя папки или полный путь).</span><span class="sxs-lookup"><span data-stu-id="c8c7f-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="c8c7f-147">Если значение не задано, по умолчанию используется текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-147">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="c8c7f-148">Задает целевую среду выполнения для восстановления пакетов.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="c8c7f-149">Список идентификаторов сред выполнения (RID) см. в [каталоге RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="c8c7f-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="c8c7f-150">Короткий параметр `-r` доступен, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-150">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c8c7f-151">Задает уровень детализации команды.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c8c7f-152">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="c8c7f-153">Значение по умолчанию — `m`.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-153">The default value is `m`.</span></span> <span data-ttu-id="c8c7f-154">Доступно начиная с пакета SDK для .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="c8c7f-154">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="c8c7f-155">Примеры</span><span class="sxs-lookup"><span data-stu-id="c8c7f-155">Examples</span></span>

- <span data-ttu-id="c8c7f-156">Выполнение проекта в текущем каталоге:</span><span class="sxs-lookup"><span data-stu-id="c8c7f-156">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="c8c7f-157">Выполнение указанного проекта:</span><span class="sxs-lookup"><span data-stu-id="c8c7f-157">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="c8c7f-158">Выполнение проекта в текущем каталоге (аргумент `--help` в этом примере передается приложению, так как используется пустой параметр `--`):</span><span class="sxs-lookup"><span data-stu-id="c8c7f-158">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="c8c7f-159">Восстановление зависимостей и средств для проекта в текущем каталоге с выводом минимального объема выходных данных и последующим запуском проекта (пакет SDK для .NET Core 2.0 и более поздних версий).</span><span class="sxs-lookup"><span data-stu-id="c8c7f-159">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
