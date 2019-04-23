---
title: -win32icon (параметры компилятора C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 7bc7da8121ec1190908d9b94fc7c987f9888c020
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317458"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="7f18b-102">-win32icon (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="7f18b-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="7f18b-103">Параметр **-win32icon** вставляет в выходной файл ICO-файл, который придает выходному файлу необходимый вид в проводнике.</span><span class="sxs-lookup"><span data-stu-id="7f18b-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f18b-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7f18b-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="7f18b-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="7f18b-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="7f18b-106">ICO-файл, который требуется добавить в выходной файл.</span><span class="sxs-lookup"><span data-stu-id="7f18b-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f18b-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="7f18b-107">Remarks</span></span>  
 <span data-ttu-id="7f18b-108">ICO-файл можно создать с помощью [компилятора ресурсов](/windows/desktop/menurc/resource-compiler).</span><span class="sxs-lookup"><span data-stu-id="7f18b-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="7f18b-109">Компилятор ресурсов вызывается при компиляции программы Visual C++; ICO-файл создается из RC-файла.</span><span class="sxs-lookup"><span data-stu-id="7f18b-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="7f18b-110">Дополнительные сведения о ссылках на файлы ресурсов .NET Framework и их присоединении см. в разделах [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) и [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) соответственно.</span><span class="sxs-lookup"><span data-stu-id="7f18b-110">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="7f18b-111">Дополнительные сведения об импорте RES-файла см. в разделе [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7f18b-111">See [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7f18b-112">Установка данного параметра компилятора в среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7f18b-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="7f18b-113">Откройте страницу **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="7f18b-113">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="7f18b-114">Перейдите на страницу свойств **Приложение**.</span><span class="sxs-lookup"><span data-stu-id="7f18b-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="7f18b-115">Измените свойство **Значок приложения**.</span><span class="sxs-lookup"><span data-stu-id="7f18b-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="7f18b-116">Сведения об установке этого параметра компилятора программными средствами см. в разделе <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="7f18b-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f18b-117">Пример</span><span class="sxs-lookup"><span data-stu-id="7f18b-117">Example</span></span>  
 <span data-ttu-id="7f18b-118">Скомпилируйте `in.cs` и присоедините ICO-файл `rf.ico`, чтобы получить файл `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="7f18b-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f18b-119">См. также</span><span class="sxs-lookup"><span data-stu-id="7f18b-119">See also</span></span>

- [<span data-ttu-id="7f18b-120">Параметры компилятора C# </span><span class="sxs-lookup"><span data-stu-id="7f18b-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="7f18b-121">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="7f18b-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
