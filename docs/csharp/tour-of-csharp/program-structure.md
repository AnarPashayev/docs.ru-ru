---
title: Структура программы в C#. Краткий обзор языка C#
description: Узнайте, из каких блоков составляется программа на C#
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: e6b3e0d3b91d3dee8cbc8ac530323e23e0ce8b2a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634565"
---
# <a name="program-structure"></a><span data-ttu-id="45270-103">Структура программы</span><span class="sxs-lookup"><span data-stu-id="45270-103">Program Structure</span></span>

<span data-ttu-id="45270-104">В C# основными понятиями организационной структуры являются ***программы***, ***пространства имен***, ***типы***, ***члены*** и ***сборки***.</span><span class="sxs-lookup"><span data-stu-id="45270-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="45270-105">Программа на языке C# состоит из одного или нескольких файлов.</span><span class="sxs-lookup"><span data-stu-id="45270-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="45270-106">В программе объявляются типы, которые содержат члены. Эти типы можно организовать в пространства имен.</span><span class="sxs-lookup"><span data-stu-id="45270-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="45270-107">Примерами типов являются классы и интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="45270-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="45270-108">К членам относятся поля, методы, свойства и события.</span><span class="sxs-lookup"><span data-stu-id="45270-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="45270-109">При компиляции программы на C# упаковываются в сборки.</span><span class="sxs-lookup"><span data-stu-id="45270-109">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="45270-110">Сборка — это файл, обычно с расширением `.exe` или `.dll`, если она реализует ***приложение*** или ***библиотеку***, соответственно.</span><span class="sxs-lookup"><span data-stu-id="45270-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="45270-111">Этот пример кода объявляет класс с именем `Stack` в пространство имен с именем `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="45270-111">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="45270-112">Полное имя этого класса: `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="45270-112">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="45270-113">Этот класс содержит несколько членов: поле с именем `top`, два метода с именами `Push` и `Pop`, а также вложенный класс с именем `Entry`.</span><span class="sxs-lookup"><span data-stu-id="45270-113">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="45270-114">Класс `Entry`, в свою очередь, содержит три члена: поле с именем `next`, поле с именем `data` и конструктор.</span><span class="sxs-lookup"><span data-stu-id="45270-114">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="45270-115">Если мы сохраним исходный код этого примера в файле `acme.cs`, то для его компиляции нужно выполнить такую командную строку:</span><span class="sxs-lookup"><span data-stu-id="45270-115">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="45270-116">Результатом компиляции будет библиотека (код без точки входа `Main`), сохраненная в сборке с именем `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="45270-116">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45270-117">В приведенных выше примерах используется компилятор командной строки `csc` для C#.</span><span class="sxs-lookup"><span data-stu-id="45270-117">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="45270-118">Он существует в виде исполняемого файла Windows.</span><span class="sxs-lookup"><span data-stu-id="45270-118">This compiler is a Windows executable.</span></span> <span data-ttu-id="45270-119">Чтобы использовать C# на других платформах, вам понадобятся средства для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45270-119">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="45270-120">Экосистема .NET Core использует `dotnet` CLI для управления сборкой из командной строки.</span><span class="sxs-lookup"><span data-stu-id="45270-120">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="45270-121">Она позволяет управлять зависимостями и вызывать компилятор C#.</span><span class="sxs-lookup"><span data-stu-id="45270-121">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="45270-122">[В этом руководстве](../../core/tutorials/using-with-xplat-cli.md) вы найдете полное описание средств для всех платформ, поддерживаемых .NET Core.</span><span class="sxs-lookup"><span data-stu-id="45270-122">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="45270-123">Сборки содержат исполняемый код в виде инструкций промежуточного языка (IL) и символьную информацию в виде метаданных.</span><span class="sxs-lookup"><span data-stu-id="45270-123">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="45270-124">Перед выполнением сборки ее код на языке IL автоматически преобразуется в код для конкретного процессора. Эту задачу выполняет JIT-компилятор среды .NET CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="45270-124">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="45270-125">Cборка полностью описывает сама себя и содержит весь код и метаданные, поэтому в C# не используются директивы `#include` и файлы заголовков.</span><span class="sxs-lookup"><span data-stu-id="45270-125">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="45270-126">Чтобы использовать в программе C# открытые типы и члены, содержащиеся в определенной сборке, вам достаточно указать ссылку на эту сборку при компиляции программы.</span><span class="sxs-lookup"><span data-stu-id="45270-126">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="45270-127">Например, эта программа использует класс `Acme.Collections.Stack` из сборки `acme.dll`:</span><span class="sxs-lookup"><span data-stu-id="45270-127">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="45270-128">Если на момент компиляции `example.cs` программа хранится в файле `example.cs`, то ссылка на сборку acme.dll с использованием параметра компилятора /r будет выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="45270-128">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="45270-129">Эта команда создает исполняемую сборку с именем `example.exe`, которая при запуске возвращает такие данные:</span><span class="sxs-lookup"><span data-stu-id="45270-129">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="45270-130">В C# исходный текст программы можно хранить в нескольких исходных файлах.</span><span class="sxs-lookup"><span data-stu-id="45270-130">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="45270-131">При компиляции многофайловой программы на C# все исходные файлы обрабатываются вместе, и все они могут свободно ссылаться друг на друга. По сути обработка выполняется так, как если бы все исходные файлы были объединены в один большой файл.</span><span class="sxs-lookup"><span data-stu-id="45270-131">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="45270-132">В C# никогда не используются опережающие объявления, поскольку порядок объявления, за редким исключением, не играет никакой роли.</span><span class="sxs-lookup"><span data-stu-id="45270-132">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="45270-133">В C# нет требований объявлять только один открытый тип в одном исходном файле, а также имя исходного файла не обязано совпадать с типом, объявляемом в этом файле.</span><span class="sxs-lookup"><span data-stu-id="45270-133">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="45270-134">[Назад](index.md)
>[Вперед](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="45270-134">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
