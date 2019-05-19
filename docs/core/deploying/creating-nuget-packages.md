---
title: Создание пакета NuGet с помощью средств интерфейса командной строки (CLI) .NET Core
description: Узнайте, как создать пакет NuGet с помощью команды dotnet pack.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: b86b2706968bf302a8421bcc8e12c32a97102e9e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632108"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="1d6b2-103">Как создать пакет NuGet с помощью средств интерфейса командной строки (CLI) .NET Core</span><span class="sxs-lookup"><span data-stu-id="1d6b2-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="1d6b2-104">Ниже приведены примеры команд командной строки для Unix.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="1d6b2-105">Показанная здесь команда `dotnet pack` точно так же работает в Windows.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="1d6b2-106">Библиотеки .NET Standard и .NET Core должны распространяться в виде пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="1d6b2-107">Именно так распространяются и используются все библиотеки .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="1d6b2-108">Проще всего это делать с помощью команды `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="1d6b2-109">Представим, что вы только что создали полезную библиотеку, которую хотите распространить через NuGet.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="1d6b2-110">Для этого можно создать пакет NuGet с помощью кроссплатформенных средств.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span> <span data-ttu-id="1d6b2-111">В приведенном ниже примере используется библиотека **SuperAwesomeLibrary**, предназначенная для `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="1d6b2-112">Если у вас есть транзитивные зависимости, то есть проекты, которые зависят от других пакетов, необходимо обязательно восстановить пакеты для всего решения с помощью команды `dotnet restore`, прежде чем создавать пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-112">If you have transitive dependencies; that is, a project which depends on another package, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span> <span data-ttu-id="1d6b2-113">Если не сделать этого, команда `dotnet pack` будет работать неправильно.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="1d6b2-114">Восстановив пакеты, можно перейти в каталог, где находится библиотека:</span><span class="sxs-lookup"><span data-stu-id="1d6b2-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="1d6b2-115">Затем нужно выполнить всего лишь одну команду в командной строке:</span><span class="sxs-lookup"><span data-stu-id="1d6b2-115">Then it's just a single command from the command line:</span></span>

```console
dotnet pack
```

<span data-ttu-id="1d6b2-116">Папка `/bin/Debug` теперь будет выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="1d6b2-116">Your `/bin/Debug` folder will now look like this:</span></span>

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="1d6b2-117">Обратите внимание на то, что при этом создается пакет, который можно отлаживать.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-117">Note that this will produce a package which is capable of being debugged.</span></span> <span data-ttu-id="1d6b2-118">Если вы хотите создать пакет NuGet с двоичными файлами выпуска, вам нужно просто добавить параметр `--configuration` (или `-c`) и использовать `release` в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```console
dotnet pack --configuration release
```

<span data-ttu-id="1d6b2-119">В папке `/bin` теперь будет папка `release`, содержащая пакет NuGet с двоичными файлами выпуска:</span><span class="sxs-lookup"><span data-stu-id="1d6b2-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="1d6b2-120">теперь у вас есть все необходимые файлы для публикации пакета NuGet.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="1d6b2-121">Не путайте команду `dotnet pack` с командой `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="1d6b2-122">Важно заметить, что команда `dotnet publish` в этом процессе не применяется.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="1d6b2-123">Команда `dotnet publish` предназначена для развертывания приложений со всеми зависимостями в одном пакете, а не для создания пакета NuGet, который будет распространяться и использоваться посредством NuGet.</span><span class="sxs-lookup"><span data-stu-id="1d6b2-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d6b2-124">См. также</span><span class="sxs-lookup"><span data-stu-id="1d6b2-124">See also</span></span>

- [<span data-ttu-id="1d6b2-125">Краткое руководство. Создание и публикация пакета (dotnet CLI)</span><span class="sxs-lookup"><span data-stu-id="1d6b2-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
