---
title: Команда dotnet msbuild
description: Команда dotnet msbuild обеспечивает доступ к командной строке MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 88e85868e2d7de564b2e4c90ce6e78bde4cb350e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463626"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="5d4dd-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="5d4dd-103">dotnet msbuild</span></span>

<span data-ttu-id="5d4dd-104">**Эта статья относится к следующему:** ✔️ пакет SDK для .NET Core 2.x и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="5d4dd-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5d4dd-105">Имя</span><span class="sxs-lookup"><span data-stu-id="5d4dd-105">Name</span></span>

<span data-ttu-id="5d4dd-106">`dotnet msbuild` — собирает проект и все его зависимости.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5d4dd-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="5d4dd-107">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="5d4dd-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="5d4dd-108">Description</span></span>

<span data-ttu-id="5d4dd-109">Команда `dotnet msbuild` предоставляет доступ к полнофункциональной системе MSBuild.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="5d4dd-110">Команда имеет точно такие же возможности, как и существующий клиент с интерфейсом командной строки MSBuild только для проектов в стиле SDK.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="5d4dd-111">Все параметры одинаковы.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-111">The options are all the same.</span></span> <span data-ttu-id="5d4dd-112">Дополнительные сведения о доступных параметрах см. в [справочнике по командной строке MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="5d4dd-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="5d4dd-113">Команда [dotnet build](dotnet-build.md) эквивалентна `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="5d4dd-114">Обычно для сборки проектов используется команда [dotnet build](dotnet-build.md). Так как команда `dotnet msbuild` всегда запускает целевой объект сборки, вы можете использовать ее, если не хотите выполнять сборку проекта.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="5d4dd-115">Например, если вам нужно запустить конкретный целевой объект, не выполняя сборку проекта, используйте `dotnet msbuild` и укажите целевой объект.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="5d4dd-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="5d4dd-116">Examples</span></span>

- <span data-ttu-id="5d4dd-117">Сборка проекта и его зависимостей:</span><span class="sxs-lookup"><span data-stu-id="5d4dd-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="5d4dd-118">Сборка проекта и его зависимостей с помощью конфигурации Release:</span><span class="sxs-lookup"><span data-stu-id="5d4dd-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="5d4dd-119">Запустите цель публикации и публикацию для RID `osx.10.11-x64`:</span><span class="sxs-lookup"><span data-stu-id="5d4dd-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="5d4dd-120">Весь проект со всеми целевыми объектами, включенными в пакет SDK:</span><span class="sxs-lookup"><span data-stu-id="5d4dd-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
