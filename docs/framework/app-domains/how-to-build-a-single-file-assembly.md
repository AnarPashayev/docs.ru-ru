---
title: Как выполнить Построение однофайловой сборки
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a73b2d8948c9a046fd77c02f1bcc87f5738105d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304003"
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="a88a1-102">Как выполнить Построение однофайловой сборки</span><span class="sxs-lookup"><span data-stu-id="a88a1-102">How to: Build a Single-File Assembly</span></span>

<span data-ttu-id="a88a1-103">Однофайловая сборка, являясь простейшим типом сборки, содержит данные о типе и реализации, а также [манифест сборки](../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="a88a1-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="a88a1-104">Для создания однофайловой сборки можно использовать компиляторы командной строки или Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a88a1-104">You can use command-line compilers or Visual Studio to create a single-file assembly.</span></span> <span data-ttu-id="a88a1-105">По умолчанию компилятор создает файл сборки с расширением .exe.</span><span class="sxs-lookup"><span data-stu-id="a88a1-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>

> [!NOTE]
> <span data-ttu-id="a88a1-106">Visual Studio для C# и Visual Basic можно использовать только для создания однофайловых сборок.</span><span class="sxs-lookup"><span data-stu-id="a88a1-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="a88a1-107">Чтобы создать многофайловую сборку, необходимо использовать компиляторы командной строки или Visual C++.</span><span class="sxs-lookup"><span data-stu-id="a88a1-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="a88a1-108">В следующих процедурах показано создани6 однофайловых сборок с помощью компиляторов, работающих в режиме командной строки.</span><span class="sxs-lookup"><span data-stu-id="a88a1-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="a88a1-109">Создание сборки с расширением .exe</span><span class="sxs-lookup"><span data-stu-id="a88a1-109">To create an assembly with an .exe extension</span></span>

1. <span data-ttu-id="a88a1-110">В командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="a88a1-110">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="a88a1-111">\<*команда компилятора*> \<*имя модуля*></span><span class="sxs-lookup"><span data-stu-id="a88a1-111">\<*compiler command*> \<*module name*></span></span>

     <span data-ttu-id="a88a1-112">В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, а *имя модуля* — имя компилируемого в сборку модуля кода.</span><span class="sxs-lookup"><span data-stu-id="a88a1-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="a88a1-113">В следующем примере создается сборка с именем `myCode.exe` из модуля кода с именем `myCode`.</span><span class="sxs-lookup"><span data-stu-id="a88a1-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="a88a1-114">Создание сборки с расширением .exe и указание имени выходного файла</span><span class="sxs-lookup"><span data-stu-id="a88a1-114">To create an assembly with an .exe extension and specify the output file name</span></span>

1. <span data-ttu-id="a88a1-115">В командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="a88a1-115">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="a88a1-116">\<*команда компилятора*> **/out:**\<*имя файла*> \<*имя модуля*></span><span class="sxs-lookup"><span data-stu-id="a88a1-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

     <span data-ttu-id="a88a1-117">В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, *имя файла* — имя выходного файла, а *имя модуля* — имя компилируемого в сборку модуля кода.</span><span class="sxs-lookup"><span data-stu-id="a88a1-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="a88a1-118">В следующем примере создается сборка с именем `myAssembly.exe` из модуля кода с именем `myCode`.</span><span class="sxs-lookup"><span data-stu-id="a88a1-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a><span data-ttu-id="a88a1-119">Создание библиотечных сборок</span><span class="sxs-lookup"><span data-stu-id="a88a1-119">Creating Library Assemblies</span></span>
 <span data-ttu-id="a88a1-120">Библиотечная сборка аналогична библиотеке классов.</span><span class="sxs-lookup"><span data-stu-id="a88a1-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="a88a1-121">Библиотечная сборка аналогична библиотеке классов. Она содержит типы, на которые имеются ссылки в других сборках, но не имеет точки входа, с которой начинается выполнение.</span><span class="sxs-lookup"><span data-stu-id="a88a1-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

### <a name="to-create-a-library-assembly"></a><span data-ttu-id="a88a1-122">Создание библиотечной сборки</span><span class="sxs-lookup"><span data-stu-id="a88a1-122">To create a library assembly</span></span>

1. <span data-ttu-id="a88a1-123">В командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="a88a1-123">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="a88a1-124">\<*команда компилятора*> **/t:library** \<*имя модуля*></span><span class="sxs-lookup"><span data-stu-id="a88a1-124">\<*compiler command*> **-t:library** \<*module name*></span></span>

     <span data-ttu-id="a88a1-125">В этой команде *команда компилятора* — команда компилятора для языка, используемого в модуле кода, а *имя модуля* — имя компилируемого в сборку модуля кода.</span><span class="sxs-lookup"><span data-stu-id="a88a1-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="a88a1-126">Можно также использовать другие параметры компилятора, такие как **-out:**.</span><span class="sxs-lookup"><span data-stu-id="a88a1-126">You can also use other compiler options, such as the **-out:** option.</span></span>

 <span data-ttu-id="a88a1-127">В следующем примере создается библиотечная сборка с именем `myCodeAssembly.dll` из модуля кода с именем `myCode`.</span><span class="sxs-lookup"><span data-stu-id="a88a1-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="a88a1-128">См. также</span><span class="sxs-lookup"><span data-stu-id="a88a1-128">See also</span></span>

- [<span data-ttu-id="a88a1-129">Создание сборок</span><span class="sxs-lookup"><span data-stu-id="a88a1-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="a88a1-130">Многофайловые сборки</span><span class="sxs-lookup"><span data-stu-id="a88a1-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="a88a1-131">Практическое руководство. Создание многофайловой сборки</span><span class="sxs-lookup"><span data-stu-id="a88a1-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="a88a1-132">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="a88a1-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)