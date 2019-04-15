---
title: -target:library (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 2e0935965e9225ab524290429803fe4c9ccc80c6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313649"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="94c4c-102">-target:library (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="94c4c-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="94c4c-103">Параметр **-target:library** заставляет компилятор создавать библиотеку динамической компоновки (DLL), а не исполняемый файл (EXE).</span><span class="sxs-lookup"><span data-stu-id="94c4c-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94c4c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="94c4c-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="94c4c-105">Примечания</span><span class="sxs-lookup"><span data-stu-id="94c4c-105">Remarks</span></span>  
 <span data-ttu-id="94c4c-106">Библиотека DLL создается с расширением DLL.</span><span class="sxs-lookup"><span data-stu-id="94c4c-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="94c4c-107">Выходной файл получает имя первого входного файла, если только с помощью параметра [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) не указано иное.</span><span class="sxs-lookup"><span data-stu-id="94c4c-107">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="94c4c-108">Для создания DLL-файла используются все файлы, указанные в командной строке до следующего параметра **-out** или **-target: module**.</span><span class="sxs-lookup"><span data-stu-id="94c4c-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="94c4c-109">При построении библиотеки DLL метод [Main](../../../csharp/programming-guide/main-and-command-args/index.md) не требуется.</span><span class="sxs-lookup"><span data-stu-id="94c4c-109">When building a .dll file, a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="94c4c-110">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="94c4c-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="94c4c-111">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="94c4c-111">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="94c4c-112">Перейдите на страницу свойств **Приложение**.</span><span class="sxs-lookup"><span data-stu-id="94c4c-112">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="94c4c-113">Измените значение свойства **Тип выходных данных**.</span><span class="sxs-lookup"><span data-stu-id="94c4c-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="94c4c-114">Сведения об установке этого параметра компилятора программными средствами см. в разделе <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="94c4c-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94c4c-115">Пример</span><span class="sxs-lookup"><span data-stu-id="94c4c-115">Example</span></span>  
 <span data-ttu-id="94c4c-116">Компиляция файла`in.cs`, создание модуля `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="94c4c-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="94c4c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="94c4c-117">See also</span></span>

- [<span data-ttu-id="94c4c-118">-target (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="94c4c-118">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="94c4c-119">Параметры компилятора C#</span><span class="sxs-lookup"><span data-stu-id="94c4c-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
