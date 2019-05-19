---
title: Команда dotnet migrate
description: Команда dotnet migrate переносит проект и все его зависимости.
ms.date: 05/25/2018
ms.openlocfilehash: 861cd2cb982c6f41baf00a2cbd7e04b26816af76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631951"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="8081c-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="8081c-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8081c-104">name</span><span class="sxs-lookup"><span data-stu-id="8081c-104">Name</span></span>

<span data-ttu-id="8081c-105">`dotnet migrate` — перемещает проект .NET Core предварительной версии 2 в проект пакета SDK для .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="8081c-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8081c-106">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="8081c-106">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="8081c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="8081c-107">Description</span></span>

<span data-ttu-id="8081c-108">Команда `dotnet migrate` переносит действительный проект предварительной версии 2 на основе *project.json* в действительный проект *CSPROJ* пакета SDK для .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="8081c-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span>

<span data-ttu-id="8081c-109">По умолчанию команда переносит корневой проект и все ссылки, которые он содержит.</span><span class="sxs-lookup"><span data-stu-id="8081c-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="8081c-110">Это поведение можно отключить в среде выполнения с помощью параметра `--skip-project-references`.</span><span class="sxs-lookup"><span data-stu-id="8081c-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="8081c-111">Миграция выполняется для следующих ресурсов:</span><span class="sxs-lookup"><span data-stu-id="8081c-111">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="8081c-112">Отдельный проект посредством указания нужного файла *project.json*.</span><span class="sxs-lookup"><span data-stu-id="8081c-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="8081c-113">Все каталоги, указанные в файле *global.json*, посредством передачи пути в файл *global.json*.</span><span class="sxs-lookup"><span data-stu-id="8081c-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="8081c-114">Файл *solution.sln*, куда переносятся проекты, на которые ссылается решение.</span><span class="sxs-lookup"><span data-stu-id="8081c-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="8081c-115">Рекурсивно все подкаталоги в этом каталоге.</span><span class="sxs-lookup"><span data-stu-id="8081c-115">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="8081c-116">Команда `dotnet migrate` сохраняет перенесенный файл *project.json* в каталоге `backup` (создается, если не существует).</span><span class="sxs-lookup"><span data-stu-id="8081c-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="8081c-117">Это поведение можно переопределить с помощью параметра `--skip-backup`.</span><span class="sxs-lookup"><span data-stu-id="8081c-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="8081c-118">По умолчанию операция миграции выводит состояние процесса миграции в стандартный вывод (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="8081c-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="8081c-119">Если вы используете параметр `--report-file <REPORT_FILE>`, выходные данные сохраняются в указанном файле.</span><span class="sxs-lookup"><span data-stu-id="8081c-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="8081c-120">Команда `dotnet migrate` поддерживает только допустимые проекты предварительной версии 2 на основе *project.json*.</span><span class="sxs-lookup"><span data-stu-id="8081c-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="8081c-121">Это означает, что она не позволяет перенести проекты DNX или проекты предварительной версии 1 на базе *project.json* непосредственно в проекты MSBuild/CSPROJ.</span><span class="sxs-lookup"><span data-stu-id="8081c-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="8081c-122">Сначала нужно вручную перенести проект в проект версии 2 на основе *project.json*, а затем воспользоваться командой `dotnet migrate` для переноса проекта.</span><span class="sxs-lookup"><span data-stu-id="8081c-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="8081c-123">Аргументы</span><span class="sxs-lookup"><span data-stu-id="8081c-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="8081c-124">Путь к одному из следующих объектов:</span><span class="sxs-lookup"><span data-stu-id="8081c-124">The path to one of the following:</span></span>

* <span data-ttu-id="8081c-125">переносимый файл *project.json*;</span><span class="sxs-lookup"><span data-stu-id="8081c-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="8081c-126">файл *global.json*: переносятся папки, указанные в *global.json*;</span><span class="sxs-lookup"><span data-stu-id="8081c-126">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="8081c-127">файл *solution.sln*: переносятся проекты, на которые ссылается решение;</span><span class="sxs-lookup"><span data-stu-id="8081c-127">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="8081c-128">каталог для миграции: выполняется рекурсивный поиск переносимых файлов *project.json* в указанном каталоге.</span><span class="sxs-lookup"><span data-stu-id="8081c-128">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="8081c-129">Если значение не задано, по умолчанию используется текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="8081c-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="8081c-130">Параметры</span><span class="sxs-lookup"><span data-stu-id="8081c-130">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="8081c-131">Вывод отчета о миграции в файл JSON вместо отправки сообщений пользователю.</span><span class="sxs-lookup"><span data-stu-id="8081c-131">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="8081c-132">Выводит краткую справку по команде.</span><span class="sxs-lookup"><span data-stu-id="8081c-132">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="8081c-133">Вывод отчета о миграции в файл наряду с выводом в консоль.</span><span class="sxs-lookup"><span data-stu-id="8081c-133">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="8081c-134">Пропуск ссылок проекта для миграции.</span><span class="sxs-lookup"><span data-stu-id="8081c-134">Skip migrating project references.</span></span> <span data-ttu-id="8081c-135">По умолчанию ссылки проекта переносятся рекурсивно.</span><span class="sxs-lookup"><span data-stu-id="8081c-135">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="8081c-136">Пропуск перемещения *project.json*, *global.json* и *\*.xproj* в каталог `backup` после успешной миграции.</span><span class="sxs-lookup"><span data-stu-id="8081c-136">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="8081c-137">Файл CSPROJ шаблона для переноса.</span><span class="sxs-lookup"><span data-stu-id="8081c-137">Template csproj file to use for migration.</span></span> <span data-ttu-id="8081c-138">По умолчанию используется тот же шаблон, что и проигнорированный в `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="8081c-138">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="8081c-139">Версия пакета SDK, на которую ссылается перенесенное приложение.</span><span class="sxs-lookup"><span data-stu-id="8081c-139">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="8081c-140">По умолчанию используется версия пакета SDK в `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="8081c-140">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="8081c-141">Путь к файлу XPROJ, который будет использоваться.</span><span class="sxs-lookup"><span data-stu-id="8081c-141">The path to the xproj file to use.</span></span> <span data-ttu-id="8081c-142">Требуется, если в каталоге проекта несколько файлов XPROJ.</span><span class="sxs-lookup"><span data-stu-id="8081c-142">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="8081c-143">Примеры</span><span class="sxs-lookup"><span data-stu-id="8081c-143">Examples</span></span>

<span data-ttu-id="8081c-144">Перенос проекта в текущем каталоге и всех взаимных зависимостей проектов.</span><span class="sxs-lookup"><span data-stu-id="8081c-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="8081c-145">Перенос всех проектов, включенных в файл *global.json*:</span><span class="sxs-lookup"><span data-stu-id="8081c-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="8081c-146">Перенос только текущего проекта без взаимных зависимостей проектов.</span><span class="sxs-lookup"><span data-stu-id="8081c-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="8081c-147">Кроме того, используется определенная версия пакета SDK:</span><span class="sxs-lookup"><span data-stu-id="8081c-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
