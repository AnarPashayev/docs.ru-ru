---
title: Практическое руководство. Условная компиляция с использованием атрибутов Trace и Debug
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df1f1c7e28464781a73a0939c3413f4c9d620d7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942385"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="99e9b-102">Практическое руководство. Условная компиляция с использованием атрибутов Trace и Debug</span><span class="sxs-lookup"><span data-stu-id="99e9b-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="99e9b-103">При отладке приложения во время разработки выходные данные трассировки и отладки отображаются в окне «Вывод» Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99e9b-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="99e9b-104">Однако чтобы включить возможности трассировки в развернутом приложении, необходимо скомпилировать инструментированные приложения с включенной директивой компилятора **TRACE**.</span><span class="sxs-lookup"><span data-stu-id="99e9b-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="99e9b-105">Это позволяет компилировать код трассировки в выпускаемой версии приложения.</span><span class="sxs-lookup"><span data-stu-id="99e9b-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="99e9b-106">Если не включить директиву **TRACE**, весь код трассировки игнорируется во время компиляции и не включается в исполняемый код, который будет развернут.</span><span class="sxs-lookup"><span data-stu-id="99e9b-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="99e9b-107">Методы трассировки и отладки имеют связанные условные атрибуты.</span><span class="sxs-lookup"><span data-stu-id="99e9b-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="99e9b-108">Например, если условный атрибут трассировки имеет значение **true**, все операторы трассировки включаются в сборку (компилированные файлы .exe или .dll); если условный атрибут **Trace** имеет значение **false**, операторы трассировки не включаются.</span><span class="sxs-lookup"><span data-stu-id="99e9b-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="99e9b-109">Для сборки можно включить условный атрибут **Trace** или **Debug**, оба эти атрибута одновременно или ни один из них.</span><span class="sxs-lookup"><span data-stu-id="99e9b-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="99e9b-110">Таким образом, существует четыре типа сборки: **Отладка**, **Трассировка**, оба или ни одного.</span><span class="sxs-lookup"><span data-stu-id="99e9b-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="99e9b-111">Некоторые сборки выпуска для продуктивного развертывания могут не содержать ни одну из них, однако большинство сборок отладки содержат обе.</span><span class="sxs-lookup"><span data-stu-id="99e9b-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="99e9b-112">Можно задать параметры компилятора для вашего приложения несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="99e9b-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="99e9b-113">Страницы свойств</span><span class="sxs-lookup"><span data-stu-id="99e9b-113">The property pages</span></span>  
  
- <span data-ttu-id="99e9b-114">Командная строка</span><span class="sxs-lookup"><span data-stu-id="99e9b-114">The command line</span></span>  
  
- <span data-ttu-id="99e9b-115">Оператор **#CONST** (для Visual Basic) и **#define** (для C#)</span><span class="sxs-lookup"><span data-stu-id="99e9b-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="99e9b-116">Изменить параметры компиляции можно в диалоговом окне «Страницы свойств».</span><span class="sxs-lookup"><span data-stu-id="99e9b-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="99e9b-117">В **обозревателе решений** щелкните узел проекта правой кнопкой.</span><span class="sxs-lookup"><span data-stu-id="99e9b-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="99e9b-118">Выберите в контекстном меню команду **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="99e9b-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="99e9b-119">В Visual Basic щелкните вкладку **Компиляция** в левой области страницы свойств, затем щелкните **Дополнительные параметры компиляции**, чтобы отобразить диалоговое окно **Дополнительные параметры компилятора**.</span><span class="sxs-lookup"><span data-stu-id="99e9b-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="99e9b-120">Установите флажки для параметров компилятора, которые необходимо включить.</span><span class="sxs-lookup"><span data-stu-id="99e9b-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="99e9b-121">Снимите флажки для параметров, которые необходимо отключить.</span><span class="sxs-lookup"><span data-stu-id="99e9b-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="99e9b-122">В C# выберите **Построить** в левой области страницы свойств, а затем установите флажки для параметров компилятора, которые нужно включить.</span><span class="sxs-lookup"><span data-stu-id="99e9b-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="99e9b-123">Снимите флажки для параметров, которые необходимо отключить.</span><span class="sxs-lookup"><span data-stu-id="99e9b-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="99e9b-124">Компиляция инструментированного кода с помощью командной строки</span><span class="sxs-lookup"><span data-stu-id="99e9b-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="99e9b-125">Задайте условный параметр компилятора в командной строке.</span><span class="sxs-lookup"><span data-stu-id="99e9b-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="99e9b-126">Компилятор включит код трассировки или отладки в исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="99e9b-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="99e9b-127">Например, следующая инструкция компилятора, введенная в командной строке, включит код трассировки в компилируемый исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="99e9b-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="99e9b-128">Для Visual Basic: **vbc-р:систем.длл-д:траце = true-д:дебуг = false MyApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="99e9b-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="99e9b-129">Для C#: **Csc-р:систем.длл-д:траце-д:дебуг = false MyApplication.CS**</span><span class="sxs-lookup"><span data-stu-id="99e9b-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="99e9b-130">Чтобы скомпилировать несколько файлов приложений, оставьте пробел между именами файлов, например **MyApplication1.vb MyApplication2.vb MyApplication3.vb** или **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="99e9b-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="99e9b-131">Директивы условной компиляции, используемые в приведенных выше примерах, имеют следующие значения.</span><span class="sxs-lookup"><span data-stu-id="99e9b-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="99e9b-132">Директива</span><span class="sxs-lookup"><span data-stu-id="99e9b-132">Directive</span></span>|<span data-ttu-id="99e9b-133">Значение</span><span class="sxs-lookup"><span data-stu-id="99e9b-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="99e9b-134">компилятор Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99e9b-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="99e9b-135">Компилятор C#</span><span class="sxs-lookup"><span data-stu-id="99e9b-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="99e9b-136">Ссылка на внешнюю сборку (EXE или DLL)</span><span class="sxs-lookup"><span data-stu-id="99e9b-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="99e9b-137">Определяет символ условной компиляции</span><span class="sxs-lookup"><span data-stu-id="99e9b-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="99e9b-138">Необходимо ввести команды TRACE или DEBUG буквами верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="99e9b-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="99e9b-139">Для получения дополнительных сведений о командах условной компиляции введите `vbc /?` (для Visual Basic) или `csc /?` (для C#) в командной строке.</span><span class="sxs-lookup"><span data-stu-id="99e9b-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="99e9b-140">Дополнительные сведения см. в разделах [Построение из командной строки](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) или [Вызов компилятора командной строки](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="99e9b-140">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="99e9b-141">Выполнение условной компиляции с помощью #CONST или #define</span><span class="sxs-lookup"><span data-stu-id="99e9b-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="99e9b-142">Введите соответствующую инструкцию для используемого языка программирования в верхней части файла исходного кода.</span><span class="sxs-lookup"><span data-stu-id="99e9b-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="99e9b-143">Язык</span><span class="sxs-lookup"><span data-stu-id="99e9b-143">Language</span></span>|<span data-ttu-id="99e9b-144">Оператор</span><span class="sxs-lookup"><span data-stu-id="99e9b-144">Statement</span></span>|<span data-ttu-id="99e9b-145">Результат</span><span class="sxs-lookup"><span data-stu-id="99e9b-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="99e9b-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="99e9b-146">**Visual Basic**</span></span>|<span data-ttu-id="99e9b-147">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="99e9b-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="99e9b-148">Включает трассировку</span><span class="sxs-lookup"><span data-stu-id="99e9b-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="99e9b-149">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="99e9b-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="99e9b-150">Отключает трассировку</span><span class="sxs-lookup"><span data-stu-id="99e9b-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="99e9b-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="99e9b-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="99e9b-152">Включает отладку</span><span class="sxs-lookup"><span data-stu-id="99e9b-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="99e9b-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="99e9b-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="99e9b-154">Отключает отладку</span><span class="sxs-lookup"><span data-stu-id="99e9b-154">Disables debugging</span></span>|  
    |<span data-ttu-id="99e9b-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="99e9b-155">**C#**</span></span>|<span data-ttu-id="99e9b-156">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="99e9b-156">**#define TRACE**</span></span>|<span data-ttu-id="99e9b-157">Включает трассировку</span><span class="sxs-lookup"><span data-stu-id="99e9b-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="99e9b-158">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="99e9b-158">**#undef TRACE**</span></span>|<span data-ttu-id="99e9b-159">Отключает трассировку</span><span class="sxs-lookup"><span data-stu-id="99e9b-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="99e9b-160">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="99e9b-160">**#define DEBUG**</span></span>|<span data-ttu-id="99e9b-161">Включает отладку</span><span class="sxs-lookup"><span data-stu-id="99e9b-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="99e9b-162">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="99e9b-162">**#undef DEBUG**</span></span>|<span data-ttu-id="99e9b-163">Отключает отладку</span><span class="sxs-lookup"><span data-stu-id="99e9b-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="99e9b-164">Отключение трассировки или отладки</span><span class="sxs-lookup"><span data-stu-id="99e9b-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="99e9b-165">Удалите директиву компилятора из исходного кода.</span><span class="sxs-lookup"><span data-stu-id="99e9b-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="99e9b-166">\- или -</span><span class="sxs-lookup"><span data-stu-id="99e9b-166">\- or -</span></span>  
  
<span data-ttu-id="99e9b-167">Удалите комментарий к директиве компилятора.</span><span class="sxs-lookup"><span data-stu-id="99e9b-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99e9b-168">Когда все готово для компиляции, можно выбрать команду **Построить** из меню **Сборка** или использовать метод командной строки (но без ввода **d:** ), чтобы определить символы условной компиляции.</span><span class="sxs-lookup"><span data-stu-id="99e9b-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99e9b-169">См. также</span><span class="sxs-lookup"><span data-stu-id="99e9b-169">See also</span></span>

- [<span data-ttu-id="99e9b-170">Трассировка и инструментирование приложений</span><span class="sxs-lookup"><span data-stu-id="99e9b-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="99e9b-171">Практическое руководство. Создание, инициализация и настройка переключателей трассировки</span><span class="sxs-lookup"><span data-stu-id="99e9b-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="99e9b-172">Переключатели трассировки</span><span class="sxs-lookup"><span data-stu-id="99e9b-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="99e9b-173">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="99e9b-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="99e9b-174">Практическое руководство. Добавление операторов трассировки в код приложения</span><span class="sxs-lookup"><span data-stu-id="99e9b-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="99e9b-175">Практическое руководство. Настройка переменных среды для командной строки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="99e9b-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="99e9b-176">Практическое руководство. Вызов компилятора командной строки</span><span class="sxs-lookup"><span data-stu-id="99e9b-176">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
