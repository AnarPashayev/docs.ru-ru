---
title: Построение из командной строки (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 798baa90308c83e42b335635fb23a9983f5180fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61839388"
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="09b95-102">Построение из командной строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09b95-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="09b95-103">Проект Visual Basic состоит из одного или нескольких файлов отдельный источник.</span><span class="sxs-lookup"><span data-stu-id="09b95-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="09b95-104">В процессе компиляции эти файлы соединяются в один пакет — исполняемый файл, который запускается как приложение.</span><span class="sxs-lookup"><span data-stu-id="09b95-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 <span data-ttu-id="09b95-105">Visual Basic предоставляет компилятора командной строки в качестве альтернативы компиляции программ из Интегрированной среды разработки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="09b95-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="09b95-106">Компилятор командной строки предназначен для ситуаций, в которых вам не требуется полный набор функций в интегрированной среде разработки, например, при использовании или запись для компьютеров с помощью ограниченных системных памяти или дисковое пространство.</span><span class="sxs-lookup"><span data-stu-id="09b95-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
  <span data-ttu-id="09b95-107">Для компиляции исходных файлов из интегрированной среды разработки Visual Studio, выберите **построения** команду **построения** меню.</span><span class="sxs-lookup"><span data-stu-id="09b95-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="09b95-108">При построении проекта файлы с помощью Visual Studio IDE можно отобразить сведения о связанном **vbc** команду и ее параметры в окне вывода.</span><span class="sxs-lookup"><span data-stu-id="09b95-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="09b95-109">Чтобы отобразить эту информацию, откройте [диалоговое окно "Параметры", проекты и решения, построения и выполнения](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)и задайте **степень подробности сообщений при сборке проекта MSBuild** для **обычный** или более высокий уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="09b95-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="09b95-110">Дополнительные сведения см. в разделе [Как Просмотр, сохранение и настройка файлов журнала сборки](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span><span class="sxs-lookup"><span data-stu-id="09b95-110">For more information, see [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span></span>  
  
 <span data-ttu-id="09b95-111">Файлы проекта (VBPROJ) в командной строке можно скомпилировать с помощью MSBuild.</span><span class="sxs-lookup"><span data-stu-id="09b95-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="09b95-112">Дополнительные сведения см. в разделе [справочнике по командной строке](/visualstudio/msbuild/msbuild-command-line-reference) и [Пошаговое руководство: в Visual Studio](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="09b95-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09b95-113">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="09b95-113">In This Section</span></span>  
 [<span data-ttu-id="09b95-114">Практическое руководство. Вызов компилятора командной строки</span><span class="sxs-lookup"><span data-stu-id="09b95-114">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="09b95-115">В этой статье описывается вызов компилятора командной строки в командную строку или из определенной папки.</span><span class="sxs-lookup"><span data-stu-id="09b95-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="09b95-116">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="09b95-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="09b95-117">Предоставляет список примеры командных строк, которые можно изменить для собственного использования.</span><span class="sxs-lookup"><span data-stu-id="09b95-117">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="09b95-118">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="09b95-118">Related Sections</span></span>  
 [<span data-ttu-id="09b95-119">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="09b95-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="09b95-120">Предоставляет список параметров компилятора, упорядоченные по алфавиту или по назначению.</span><span class="sxs-lookup"><span data-stu-id="09b95-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="09b95-121">Условная компиляция</span><span class="sxs-lookup"><span data-stu-id="09b95-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="09b95-122">Описывает процедуру компиляции определенных частей кода.</span><span class="sxs-lookup"><span data-stu-id="09b95-122">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="09b95-123">Построение и очистка проектов и решений в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="09b95-123">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="09b95-124">Описывает способ организации будут включены в каждой из них, выберите свойства проекта и убедитесь, что сборка проектов в правильном порядке.</span><span class="sxs-lookup"><span data-stu-id="09b95-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
