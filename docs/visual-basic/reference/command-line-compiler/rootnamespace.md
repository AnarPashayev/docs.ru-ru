---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: d9388ace03f654458eb955e989673b7441e72f23
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085143"
---
# <a name="-rootnamespace"></a><span data-ttu-id="0bb17-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="0bb17-102">-rootnamespace</span></span>

<span data-ttu-id="0bb17-103">Задает пространство имен для всех объявлений типов.</span><span class="sxs-lookup"><span data-stu-id="0bb17-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bb17-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0bb17-104">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="0bb17-105">Аргументы</span><span class="sxs-lookup"><span data-stu-id="0bb17-105">Arguments</span></span>  
  
|<span data-ttu-id="0bb17-106">Термин</span><span class="sxs-lookup"><span data-stu-id="0bb17-106">Term</span></span>|<span data-ttu-id="0bb17-107">Определение</span><span class="sxs-lookup"><span data-stu-id="0bb17-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="0bb17-108">Имя пространства имен, в котором должны быть заключены все объявления типов для текущего проекта.</span><span class="sxs-lookup"><span data-stu-id="0bb17-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bb17-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="0bb17-109">Remarks</span></span>  

 <span data-ttu-id="0bb17-110">Если вы используете исполняемый файл Visual Studio (Devenv.exe) для компиляции проекта, созданного в интегрированной среде разработки Visual Studio, используйте `-rootnamespace`, чтобы указать значение свойства <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="0bb17-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="0bb17-111">Дополнительные сведения см. в разделе [Параметры командной строки для команды Devenv](/visualstudio/ide/reference/devenv-command-line-switches).</span><span class="sxs-lookup"><span data-stu-id="0bb17-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="0bb17-112">Используйте дизассемблер MSIL среды CLR (`Ildasm.exe`) для просмотра имен пространств имен в выходном файле.</span><span class="sxs-lookup"><span data-stu-id="0bb17-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="0bb17-113">Задание параметра -rootnamespace в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0bb17-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0bb17-114">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="0bb17-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0bb17-115">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="0bb17-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="0bb17-116">2.  Перейдите на вкладку **Приложение** .</span><span class="sxs-lookup"><span data-stu-id="0bb17-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="0bb17-117">3.  Измените значение в поле **Корневое пространство имен**.</span><span class="sxs-lookup"><span data-stu-id="0bb17-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0bb17-118">Пример</span><span class="sxs-lookup"><span data-stu-id="0bb17-118">Example</span></span>  

 <span data-ttu-id="0bb17-119">Следующий код компилирует `In.vb` и заключает все объявления типов в пространство имен `mynamespace`.</span><span class="sxs-lookup"><span data-stu-id="0bb17-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bb17-120">См. также</span><span class="sxs-lookup"><span data-stu-id="0bb17-120">See also</span></span>

- [<span data-ttu-id="0bb17-121">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="0bb17-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0bb17-122">Ildasm.exe (дизассемблер IL)</span><span class="sxs-lookup"><span data-stu-id="0bb17-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="0bb17-123">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="0bb17-123">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
