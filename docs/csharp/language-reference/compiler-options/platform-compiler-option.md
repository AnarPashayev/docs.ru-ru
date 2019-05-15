---
title: -platform (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 5a00820b01ee0ac78715efa0140e2a5aef28bef8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592800"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="54131-102">-platform (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="54131-102">-platform (C# Compiler Options)</span></span>
<span data-ttu-id="54131-103">Указывает, в какой версии среды CLR может запускаться сборка.</span><span class="sxs-lookup"><span data-stu-id="54131-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54131-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="54131-104">Syntax</span></span>  
  
```console  
-platform:string  
```  
  
## <a name="parameters"></a><span data-ttu-id="54131-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="54131-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="54131-106">anycpu (по умолчанию), anycpu32bitpreferred, ARM, x64, x86 или Itanium.</span><span class="sxs-lookup"><span data-stu-id="54131-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54131-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="54131-107">Remarks</span></span>  
  
- <span data-ttu-id="54131-108">**anycpu** (по умолчанию) позволяет компилировать сборку для запуска на любой платформе.</span><span class="sxs-lookup"><span data-stu-id="54131-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="54131-109">Если возможно, приложение выполняется как 64-разрядный процесс, а если доступен только 32-разрядный режим, переключается на него.</span><span class="sxs-lookup"><span data-stu-id="54131-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
- <span data-ttu-id="54131-110">**anycpu32bitpreferred** (по умолчанию) позволяет компилировать сборку для запуска на любой платформе.</span><span class="sxs-lookup"><span data-stu-id="54131-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="54131-111">Приложение выполняется в 32-разрядном режиме в системах, поддерживающих и 64-разрядные, и 32-разрядные приложения.</span><span class="sxs-lookup"><span data-stu-id="54131-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="54131-112">Можно задать этот параметр только для проектов, предназначенных для среды .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="54131-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
- <span data-ttu-id="54131-113">**ARM** компилирует сборку для выполнения на компьютере с процессором Advanced RISC Machine (ARM).</span><span class="sxs-lookup"><span data-stu-id="54131-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
- <span data-ttu-id="54131-114">**ARM64** компилирует сборку для выполнения 64-разрядной средой CLR на компьютере с процессором Advanced RISC Machine (ARM) с поддержкой набора инструкций А64.</span><span class="sxs-lookup"><span data-stu-id="54131-114">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>  

- <span data-ttu-id="54131-115">**x64** компилирует сборку для запуска в 64-разрядной среде CLR на компьютере, поддерживающем набор инструкций AMD64 или EM64T.</span><span class="sxs-lookup"><span data-stu-id="54131-115">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
- <span data-ttu-id="54131-116">**x86** компилирует сборку для запуска в 32-разрядной среде CLR с архитектурой x86.</span><span class="sxs-lookup"><span data-stu-id="54131-116">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>  
  
- <span data-ttu-id="54131-117">**Itanium** компилирует сборку для запуска в 64-разрядной среде CLR на компьютере с процессором Itanium.</span><span class="sxs-lookup"><span data-stu-id="54131-117">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="54131-118">В 64-разрядной ОС Windows:</span><span class="sxs-lookup"><span data-stu-id="54131-118">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="54131-119">Сборки, скомпилированные с параметром **-platform:x86**, будут выполняться в 32-разрядной среде CLR с WOW64.</span><span class="sxs-lookup"><span data-stu-id="54131-119">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="54131-120">Библиотека DLL, скомпилированная с использованием параметра **-platform:anycpu**, выполняется в той же среде CLR, в которую загружается процесс.</span><span class="sxs-lookup"><span data-stu-id="54131-120">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
- <span data-ttu-id="54131-121">Исполняемые файлы, скомпилированные с использованием параметра **-platform:anycpu**, выполняются в 64-разрядной среде CLR.</span><span class="sxs-lookup"><span data-stu-id="54131-121">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="54131-122">Исполняемые файлы, скомпилированные с использованием параметра **-platform:anycpu32bitpreferred**, выполняются в 32-разрядной среде CLR.</span><span class="sxs-lookup"><span data-stu-id="54131-122">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="54131-123">Параметр **anycpu32bitpreferred** допустим только для исполняемых файлов (EXE-файлов), и для него необходима среда .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="54131-123">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="54131-124">Дополнительные сведения о разработке приложений для запуска в 64-разрядной операционной системе Windows см. в разделе [64-разрядные приложения](../../../framework/64-bit-apps.md).</span><span class="sxs-lookup"><span data-stu-id="54131-124">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="54131-125">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="54131-125">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="54131-126">Откройте страницу **свойств** для проекта.</span><span class="sxs-lookup"><span data-stu-id="54131-126">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="54131-127">Щелкните страницу свойств **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="54131-127">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="54131-128">Измените значение свойства **Целевая платформа**, а для проектов, предназначенных для среды .NET Framework 4.5, установите или снимите флажок **Предпочитать 32-разрядную**.</span><span class="sxs-lookup"><span data-stu-id="54131-128">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="54131-129">Обратите внимание, что параметр **-platform** недоступен в среде разработки в Visual C# Express.</span><span class="sxs-lookup"><span data-stu-id="54131-129">**Note -platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="54131-130">Сведения об установке этого параметра компилятора программными средствами см. в разделе <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span><span class="sxs-lookup"><span data-stu-id="54131-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54131-131">Пример</span><span class="sxs-lookup"><span data-stu-id="54131-131">Example</span></span>  
 <span data-ttu-id="54131-132">В следующем примере показано использование параметра **-platform**, чтобы указать, что приложение должно выполняться в 64-разрядной среде CLR в 64-разрядной операционной системой Windows.</span><span class="sxs-lookup"><span data-stu-id="54131-132">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="54131-133">См. также</span><span class="sxs-lookup"><span data-stu-id="54131-133">See also</span></span>

- [<span data-ttu-id="54131-134">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="54131-134">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="54131-135">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="54131-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
