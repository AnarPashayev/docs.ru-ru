---
title: Практическое руководство. Создание однофайловой сборки .NET Framework
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: b7cb06da74a21dab6f60f0d4c3ac1748fcbe4526
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644305"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="dc27e-102">Практическое руководство. Создание однофайловой сборки .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dc27e-102">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="dc27e-103">Однофайловая сборка, являясь простейшим типом сборки, содержит данные о типе и реализации, а также [манифест сборки](../../standard/assembly/manifest.md).</span><span class="sxs-lookup"><span data-stu-id="dc27e-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="dc27e-104">Для создания однофайловой сборки, ориентированной на .NET Framework, можно использовать компиляторы командной строки или Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc27e-104">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="dc27e-105">По умолчанию компилятор создает файл сборки с расширением *EXE*.</span><span class="sxs-lookup"><span data-stu-id="dc27e-105">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="dc27e-106">Visual Studio для C# и Visual Basic можно использовать только для создания однофайловых сборок.</span><span class="sxs-lookup"><span data-stu-id="dc27e-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="dc27e-107">Чтобы создать многофайловую сборку, необходимо использовать компиляторы командной строки или Visual C++.</span><span class="sxs-lookup"><span data-stu-id="dc27e-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="dc27e-108">В следующих процедурах показано создани6 однофайловых сборок с помощью компиляторов, работающих в режиме командной строки.</span><span class="sxs-lookup"><span data-stu-id="dc27e-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="dc27e-109">Создание сборки с расширением EXE</span><span class="sxs-lookup"><span data-stu-id="dc27e-109">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="dc27e-110">В командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="dc27e-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="dc27e-111">\<*команда компилятора*> \<*имя модуля*></span><span class="sxs-lookup"><span data-stu-id="dc27e-111">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="dc27e-112">В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, а *имя модуля* — имя компилируемого в сборку модуля кода.</span><span class="sxs-lookup"><span data-stu-id="dc27e-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="dc27e-113">В следующем примере создается сборка с именем *myCode.exe* из модуля кода с именем `myCode`.</span><span class="sxs-lookup"><span data-stu-id="dc27e-113">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="dc27e-114">Создание сборки с расширением EXE и указание имени выходного файла</span><span class="sxs-lookup"><span data-stu-id="dc27e-114">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="dc27e-115">В командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="dc27e-115">At the command prompt, type the following command:</span></span>

<span data-ttu-id="dc27e-116">\<*команда компилятора*>  **/out:** \<*имя файла*> \<*имя модуля*></span><span class="sxs-lookup"><span data-stu-id="dc27e-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="dc27e-117">В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, *имя файла* — имя выходного файла, а *имя модуля* — имя компилируемого в сборку модуля кода.</span><span class="sxs-lookup"><span data-stu-id="dc27e-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="dc27e-118">В следующем примере создается сборка с именем *myAssembly.exe* из модуля кода с именем `myCode`.</span><span class="sxs-lookup"><span data-stu-id="dc27e-118">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="dc27e-119">Создание библиотечных сборок</span><span class="sxs-lookup"><span data-stu-id="dc27e-119">Create library assemblies</span></span>
 <span data-ttu-id="dc27e-120">Библиотечная сборка аналогична библиотеке классов.</span><span class="sxs-lookup"><span data-stu-id="dc27e-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="dc27e-121">Библиотечная сборка аналогична библиотеке классов. Она содержит типы, на которые имеются ссылки в других сборках, но не имеет точки входа, с которой начинается выполнение.</span><span class="sxs-lookup"><span data-stu-id="dc27e-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="dc27e-122">Чтобы создать библиотечную сборку, в командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="dc27e-122">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="dc27e-123">\<*команда компилятора*>  **-t:library** \<*имя модуля*></span><span class="sxs-lookup"><span data-stu-id="dc27e-123">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="dc27e-124">В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, а *имя модуля* — имя компилируемого в сборку модуля кода.</span><span class="sxs-lookup"><span data-stu-id="dc27e-124">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="dc27e-125">Можно также использовать другие параметры компилятора, такие как **-out:** .</span><span class="sxs-lookup"><span data-stu-id="dc27e-125">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="dc27e-126">В следующем примере создается библиотечная сборка с именем *myCodeAssembly.dll* из модуля кода с именем `myCode`.</span><span class="sxs-lookup"><span data-stu-id="dc27e-126">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="dc27e-127">См. также</span><span class="sxs-lookup"><span data-stu-id="dc27e-127">See also</span></span>

- [<span data-ttu-id="dc27e-128">Создание сборок</span><span class="sxs-lookup"><span data-stu-id="dc27e-128">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="dc27e-129">Многофайловые сборки</span><span class="sxs-lookup"><span data-stu-id="dc27e-129">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="dc27e-130">Практическое руководство. Создание многофайловой сборки</span><span class="sxs-lookup"><span data-stu-id="dc27e-130">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="dc27e-131">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="dc27e-131">Program with assemblies</span></span>](../../standard/assembly/index.md)
