---
title: Начало работы с .NET Core
description: Ресурсы, посвященные созданию приложений .NET Core в Windows, Linux и Mac OS.
author: thraka
ms.author: adegeo
ms.date: 06/27/2018
ms.openlocfilehash: b111d464b83f3bc6a4a0da86678c5364bf4a9537
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802300"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="e0b9a-103">Начало работы с .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0b9a-103">Get started with .NET Core</span></span>

<span data-ttu-id="e0b9a-104">В этой статье представлены сведения по началу работы с .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="e0b9a-105">.NET Core можно установить в Windows, Linux и macOS.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="e0b9a-106">Вы можете писать код в любом текстовом редакторе, а также создавать кроссплатформенные библиотеки и приложения.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="e0b9a-107">Если вы не знаете, что такое .NET Core и как это связано с другими технологиями .NET, начните с обзора [Что такое .NET](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e0b9a-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="e0b9a-108">Простыми словами, .NET Core — это кроссплатформенная реализация .NET с открытым исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="e0b9a-109">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="e0b9a-109">Create an application</span></span>

<span data-ttu-id="e0b9a-110">Сначала скачайте и установите [пакет SDK для .NET Core](https://www.microsoft.com/net/download/) на компьютер.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-110">First, download and install the [.NET Core SDK](https://www.microsoft.com/net/download/) on your computer.</span></span>

<span data-ttu-id="e0b9a-111">Затем откройте окно терминала, например **PowerShell**, **командную строку** или **bash**.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="e0b9a-112">Для создания и запуска приложения C# введите следующие команды `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-112">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="e0b9a-113">Должны выводиться следующие данные:</span><span class="sxs-lookup"><span data-stu-id="e0b9a-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="e0b9a-114">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="e0b9a-114">Congratulations!</span></span> <span data-ttu-id="e0b9a-115">Вы создали простое приложение .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="e0b9a-116">Вы также можете использовать [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (только для Windows) или [Visual Studio для Mac](tutorials/using-on-mac-vs.md) (только для macOS), чтобы создать приложение .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="e0b9a-117">Учебники</span><span class="sxs-lookup"><span data-stu-id="e0b9a-117">Tutorials</span></span>

<span data-ttu-id="e0b9a-118">Чтобы приступить к разработке приложений .NET Core, воспользуйтесь следующими пошаговыми руководствами.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="e0b9a-119">Windows</span><span class="sxs-lookup"><span data-stu-id="e0b9a-119">Windows</span></span>](#tab/windows)

* [<span data-ttu-id="e0b9a-120">Создание приложения Hello World на C# с помощью .NET Core в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)

* [<span data-ttu-id="e0b9a-121">Создание библиотеки классов C# с помощью .NET Core в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)

* [<span data-ttu-id="e0b9a-122">Создание приложения Hello World на Visual Basic с помощью .NET Core в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)

* [<span data-ttu-id="e0b9a-123">Создание библиотеки классов с помощью Visual Basic и .NET Core в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  

* <span data-ttu-id="e0b9a-124">Посмотрите видео о том, [как установить и использовать Visual Studio Code и .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span><span class="sxs-lookup"><span data-stu-id="e0b9a-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>

* <span data-ttu-id="e0b9a-125">Посмотрите видео о том, [как установить и использовать Visual Studio 2017 и .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span><span class="sxs-lookup"><span data-stu-id="e0b9a-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>

* [<span data-ttu-id="e0b9a-126">Начало работы с .NET Core с помощью командной строки.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

<span data-ttu-id="e0b9a-127">Список поддерживаемых версий Windows см. в статье [Предварительные требования для разработки в Windows](windows-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="e0b9a-127">See the [Prerequisites for Windows development](windows-prerequisites.md) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="e0b9a-128">Linux</span><span class="sxs-lookup"><span data-stu-id="e0b9a-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="e0b9a-129">Чтобы приступить к разработке приложения .NET Core, воспользуйтесь следующими пошаговыми руководствами.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-129">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* [<span data-ttu-id="e0b9a-130">Начало работы с .NET Core с помощью командной строки.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* <span data-ttu-id="e0b9a-131">Посмотрите видео о [начале работы с Visual Studio Code с использованием C# и .NET Core в Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="e0b9a-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="e0b9a-132">Список поддерживаемых версий и дистрибутивов Linux см. в статье [Необходимые компоненты для .NET Core в Linux](linux-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="e0b9a-132">See the [Prerequisites for Linux development](linux-prerequisites.md) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="e0b9a-133">macOS</span><span class="sxs-lookup"><span data-stu-id="e0b9a-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="e0b9a-134">Чтобы приступить к разработке приложения .NET Core, воспользуйтесь следующими пошаговыми руководствами.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-134">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* <span data-ttu-id="e0b9a-135">Посмотрите видео о [начале работы с Visual Studio Code с использованием C# и .NET Core в macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="e0b9a-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>

* [<span data-ttu-id="e0b9a-136">Начало работы с .NET Core в macOS с помощью Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)

* [<span data-ttu-id="e0b9a-137">Начало работы с .NET Core с помощью командной строки.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* [<span data-ttu-id="e0b9a-138">Начало работы с .NET Core в macOS с помощью Visual Studio для Mac.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)

* [<span data-ttu-id="e0b9a-139">Создание полноценного решения .NET Core на базе macOS с помощью Visual Studio для Mac.</span><span class="sxs-lookup"><span data-stu-id="e0b9a-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="e0b9a-140">Список поддерживаемых версий OS X и macOS см. в статье [Предварительные требования для разработки в macOS](macos-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="e0b9a-140">See the [Prerequisites for macOS development](macos-prerequisites.md) article for a list of the supported OS X / macOS versions.</span></span>

---
