---
description: -target:winexe (параметры компилятора C#)
title: -target:winexe (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 5f8717115464ec3d9798228d7d50a8f08b2db300
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466096"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="01048-103">-target:winexe (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="01048-103">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="01048-104">Параметр **-target:winexe** предписывает компилятору создать исполняемый файл (EXE), программу Windows.</span><span class="sxs-lookup"><span data-stu-id="01048-104">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01048-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="01048-105">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="01048-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="01048-106">Remarks</span></span>  
 <span data-ttu-id="01048-107">Исполняемый файл создается с расширением ЕХЕ.</span><span class="sxs-lookup"><span data-stu-id="01048-107">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="01048-108">Программа Windows предоставляет пользовательский интерфейс либо из библиотеки .NET, либо с помощью API-интерфейсов Windows.</span><span class="sxs-lookup"><span data-stu-id="01048-108">A Windows program is one that provides a user interface from either the .NET library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="01048-109">Воспользуйтесь параметром [-target:exe](./target-exe-compiler-option.md), чтобы создать консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="01048-109">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="01048-110">Если не указано иное с помощью параметра [-out](./out-compiler-option.md), имя выходного файла совпадает с именем входного файла, который содержит метод [Main](../../programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="01048-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="01048-111">Для создания DLL-файла используются все файлы, указанные в командной строке вплоть до следующего параметра **-out** или [-target](./target-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="01048-111">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="01048-112">В файлах исходного кода, который компилируется в EXE-файл, должен содержаться один и только один метод **Main**.</span><span class="sxs-lookup"><span data-stu-id="01048-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="01048-113">Параметр [-main](./main-compiler-option.md) позволяет указывать класс, содержащий метод **Main**, в случаях, когда код содержит несколько классов с методом **Main**.</span><span class="sxs-lookup"><span data-stu-id="01048-113">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="01048-114">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01048-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="01048-115">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="01048-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="01048-116">Перейдите на страницу свойств **Приложение**.</span><span class="sxs-lookup"><span data-stu-id="01048-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="01048-117">Измените значение свойства **Тип выходных данных**.</span><span class="sxs-lookup"><span data-stu-id="01048-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="01048-118">Сведения об установке этого параметра компилятора программными средствами см. в статье <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="01048-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01048-119">Пример</span><span class="sxs-lookup"><span data-stu-id="01048-119">Example</span></span>  
 <span data-ttu-id="01048-120">Компиляция `in.cs` в программу Windows:</span><span class="sxs-lookup"><span data-stu-id="01048-120">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="01048-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="01048-121">See also</span></span>

- [<span data-ttu-id="01048-122">-target (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="01048-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="01048-123">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="01048-123">C# Compiler Options</span></span>](./index.md)
