---
description: -target (параметры компилятора C#)
title: -target (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 5bfd988e8e399273dbd3292543a3730234c022d6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128560"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="25896-103">-target (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="25896-103">-target (C# Compiler Options)</span></span>
<span data-ttu-id="25896-104">Параметр компилятора **-target** можно задать в одной из следующих форм:</span><span class="sxs-lookup"><span data-stu-id="25896-104">The **-target** compiler option can be specified in one of the following forms:</span></span>  
  
 [<span data-ttu-id="25896-105">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="25896-105">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="25896-106">Создание EXE-файла для приложений Магазина Windows 8.x.</span><span class="sxs-lookup"><span data-stu-id="25896-106">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="25896-107">/target:exe</span><span class="sxs-lookup"><span data-stu-id="25896-107">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="25896-108">Создание EXE-файла.</span><span class="sxs-lookup"><span data-stu-id="25896-108">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="25896-109">/target:library</span><span class="sxs-lookup"><span data-stu-id="25896-109">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="25896-110">Создание библиотеки кодов.</span><span class="sxs-lookup"><span data-stu-id="25896-110">To create a code library.</span></span>  
  
 [<span data-ttu-id="25896-111">/target:module</span><span class="sxs-lookup"><span data-stu-id="25896-111">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="25896-112">Создание модуля.</span><span class="sxs-lookup"><span data-stu-id="25896-112">To create a module.</span></span>  
  
 [<span data-ttu-id="25896-113">/target:winexe</span><span class="sxs-lookup"><span data-stu-id="25896-113">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="25896-114">Создание программы Windows.</span><span class="sxs-lookup"><span data-stu-id="25896-114">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="25896-115">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="25896-115">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="25896-116">Создание промежуточного WINMDOBJ-файла.</span><span class="sxs-lookup"><span data-stu-id="25896-116">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="25896-117">Если **-target:module** не указан, **-target** предписывает разместить манифест сборки .NET Framework в выходном файле.</span><span class="sxs-lookup"><span data-stu-id="25896-117">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="25896-118">Дополнительные сведения см. в разделах [Сборки в .NET](../../../standard/assembly/index.md) и [Общие атрибуты](../attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="25896-118">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../attributes/global.md).</span></span>  
  
 <span data-ttu-id="25896-119">Манифест сборки помещается в первый выходной файл EXE в компиляции или в первый файл DLL, если выходной файл EXE не существует.</span><span class="sxs-lookup"><span data-stu-id="25896-119">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="25896-120">Например, в следующей командной строке манифест будут помещен в `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="25896-120">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="25896-121">При каждой компиляции компилятор создает только один манифест сборки.</span><span class="sxs-lookup"><span data-stu-id="25896-121">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="25896-122">В манифест сборки добавляются сведения обо всех файлах в компиляции.</span><span class="sxs-lookup"><span data-stu-id="25896-122">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="25896-123">Все выходные файлы, кроме созданных с **-target:module**, могут содержать манифест сборки.</span><span class="sxs-lookup"><span data-stu-id="25896-123">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="25896-124">При создании нескольких выходных файлов в командной строке может быть создан только один манифест сборки, который добавляется в первый выходной файл, указанный в командной строке.</span><span class="sxs-lookup"><span data-stu-id="25896-124">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="25896-125">Каким бы ни был выходной файл ( **-target:exe**, **-target:winexe**, **-target:library** или **-target:module**), все остальные выходные файлы в той же компиляции должны быть модулями ( **-target:module**).</span><span class="sxs-lookup"><span data-stu-id="25896-125">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="25896-126">При создании сборки можно указать, что код полностью или частично CLS-совместим с атрибутом <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="25896-126">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="25896-127">Дополнительные сведения об установке этого параметра компилятора программным путем см. в разделе <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="25896-127">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25896-128">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="25896-128">See also</span></span>

- [<span data-ttu-id="25896-129">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="25896-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="25896-130">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="25896-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="25896-131">-subsystemversion (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="25896-131">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
