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
ms.openlocfilehash: a010b2ee1de17741b2d0bdd6e7c50d5f602256ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754561"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="90e6e-102">Практическое руководство. Условная компиляция с использованием атрибутов Trace и Debug</span><span class="sxs-lookup"><span data-stu-id="90e6e-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="90e6e-103">При отладке приложения во время разработки выходные данные трассировки и отладки отображаются в окне «Вывод» Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e6e-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="90e6e-104">Однако чтобы включить возможности трассировки в развернутом приложении, необходимо скомпилировать инструментированные приложения с включенной директивой компилятора **TRACE**.</span><span class="sxs-lookup"><span data-stu-id="90e6e-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="90e6e-105">Это позволяет компилировать код трассировки в выпускаемой версии приложения.</span><span class="sxs-lookup"><span data-stu-id="90e6e-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="90e6e-106">Если не включить директиву **TRACE**, весь код трассировки игнорируется во время компиляции и не включается в исполняемый код, который будет развернут.</span><span class="sxs-lookup"><span data-stu-id="90e6e-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="90e6e-107">Методы трассировки и отладки имеют связанные условные атрибуты.</span><span class="sxs-lookup"><span data-stu-id="90e6e-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="90e6e-108">Например, если условный атрибут трассировки имеет значение **true**, все операторы трассировки включаются в сборку (компилированные файлы .exe или .dll); если условный атрибут **Trace** имеет значение **false**, операторы трассировки не включаются.</span><span class="sxs-lookup"><span data-stu-id="90e6e-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="90e6e-109">Для сборки можно включить условный атрибут **Trace** или **Debug**, оба эти атрибута одновременно или ни один из них.</span><span class="sxs-lookup"><span data-stu-id="90e6e-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="90e6e-110">Таким образом существует четыре типа сборки: **Отладка**, **трассировки**, оба или ни одной.</span><span class="sxs-lookup"><span data-stu-id="90e6e-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="90e6e-111">Некоторые сборки выпуска для продуктивного развертывания могут не содержать ни одну из них, однако большинство сборок отладки содержат обе.</span><span class="sxs-lookup"><span data-stu-id="90e6e-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="90e6e-112">Можно задать параметры компилятора для вашего приложения несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="90e6e-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="90e6e-113">Страницы свойств</span><span class="sxs-lookup"><span data-stu-id="90e6e-113">The property pages</span></span>  
  
- <span data-ttu-id="90e6e-114">Командная строка</span><span class="sxs-lookup"><span data-stu-id="90e6e-114">The command line</span></span>  
  
- <span data-ttu-id="90e6e-115">Оператор **#CONST** (для Visual Basic) и **#define** (для C#)</span><span class="sxs-lookup"><span data-stu-id="90e6e-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="90e6e-116">Изменить параметры компиляции можно в диалоговом окне «Страницы свойств».</span><span class="sxs-lookup"><span data-stu-id="90e6e-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="90e6e-117">В **обозревателе решений** щелкните узел проекта правой кнопкой.</span><span class="sxs-lookup"><span data-stu-id="90e6e-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="90e6e-118">Выберите в контекстном меню команду **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="90e6e-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="90e6e-119">В Visual Basic щелкните вкладку **Компиляция** в левой области страницы свойств, затем щелкните **Дополнительные параметры компиляции**, чтобы отобразить диалоговое окно **Дополнительные параметры компилятора**.</span><span class="sxs-lookup"><span data-stu-id="90e6e-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="90e6e-120">Установите флажки для параметров компилятора, которые необходимо включить.</span><span class="sxs-lookup"><span data-stu-id="90e6e-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="90e6e-121">Снимите флажки для параметров, которые необходимо отключить.</span><span class="sxs-lookup"><span data-stu-id="90e6e-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="90e6e-122">В C# выберите **Построить** в левой области страницы свойств, а затем установите флажки для параметров компилятора, которые нужно включить.</span><span class="sxs-lookup"><span data-stu-id="90e6e-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="90e6e-123">Снимите флажки для параметров, которые необходимо отключить.</span><span class="sxs-lookup"><span data-stu-id="90e6e-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="90e6e-124">Компиляция инструментированного кода с помощью командной строки</span><span class="sxs-lookup"><span data-stu-id="90e6e-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="90e6e-125">Задайте условный параметр компилятора в командной строке.</span><span class="sxs-lookup"><span data-stu-id="90e6e-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="90e6e-126">Компилятор включит код трассировки или отладки в исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="90e6e-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="90e6e-127">Например, следующая инструкция компилятора, введенная в командной строке, включит код трассировки в компилируемый исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="90e6e-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="90e6e-128">Для Visual Basic: **vbc-r:System.dll -d: TRACE = TRUE -d: DEBUG = FALSE MyApplication.vb**</span><span class="sxs-lookup"><span data-stu-id="90e6e-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="90e6e-129">Для C#: **csc-r:System.dll -d: TRACE -d: DEBUG = FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="90e6e-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="90e6e-130">Чтобы скомпилировать несколько файлов приложений, оставьте пробел между именами файлов, например **MyApplication1.vb MyApplication2.vb MyApplication3.vb** или **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="90e6e-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="90e6e-131">Директивы условной компиляции, используемые в приведенных выше примерах, имеют следующие значения.</span><span class="sxs-lookup"><span data-stu-id="90e6e-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="90e6e-132">Директива</span><span class="sxs-lookup"><span data-stu-id="90e6e-132">Directive</span></span>|<span data-ttu-id="90e6e-133">Значение</span><span class="sxs-lookup"><span data-stu-id="90e6e-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="90e6e-134">компилятор Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90e6e-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="90e6e-135">Компилятор C#</span><span class="sxs-lookup"><span data-stu-id="90e6e-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="90e6e-136">Ссылка на внешнюю сборку (EXE или DLL)</span><span class="sxs-lookup"><span data-stu-id="90e6e-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="90e6e-137">Определяет символ условной компиляции</span><span class="sxs-lookup"><span data-stu-id="90e6e-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="90e6e-138">Необходимо ввести команды TRACE или DEBUG буквами верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="90e6e-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="90e6e-139">Для получения дополнительных сведений о командах условной компиляции введите `vbc /?` (для Visual Basic) или `csc /?` (для C#) в командной строке.</span><span class="sxs-lookup"><span data-stu-id="90e6e-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="90e6e-140">Дополнительные сведения см. в разделах [Построение из командной строки](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) или [Вызов компилятора командной строки](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="90e6e-140">For more information, see [Building from the Command Line](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="90e6e-141">Выполнение условной компиляции с помощью #CONST или #define</span><span class="sxs-lookup"><span data-stu-id="90e6e-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="90e6e-142">Введите соответствующую инструкцию для используемого языка программирования в верхней части файла исходного кода.</span><span class="sxs-lookup"><span data-stu-id="90e6e-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="90e6e-143">Язык</span><span class="sxs-lookup"><span data-stu-id="90e6e-143">Language</span></span>|<span data-ttu-id="90e6e-144">Оператор</span><span class="sxs-lookup"><span data-stu-id="90e6e-144">Statement</span></span>|<span data-ttu-id="90e6e-145">Результат</span><span class="sxs-lookup"><span data-stu-id="90e6e-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="90e6e-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="90e6e-146">**Visual Basic**</span></span>|<span data-ttu-id="90e6e-147">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="90e6e-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="90e6e-148">Включает трассировку</span><span class="sxs-lookup"><span data-stu-id="90e6e-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="90e6e-149">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="90e6e-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="90e6e-150">Отключает трассировку</span><span class="sxs-lookup"><span data-stu-id="90e6e-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="90e6e-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="90e6e-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="90e6e-152">Включает отладку</span><span class="sxs-lookup"><span data-stu-id="90e6e-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="90e6e-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="90e6e-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="90e6e-154">Отключает отладку</span><span class="sxs-lookup"><span data-stu-id="90e6e-154">Disables debugging</span></span>|  
    |<span data-ttu-id="90e6e-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="90e6e-155">**C#**</span></span>|<span data-ttu-id="90e6e-156">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="90e6e-156">**#define TRACE**</span></span>|<span data-ttu-id="90e6e-157">Включает трассировку</span><span class="sxs-lookup"><span data-stu-id="90e6e-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="90e6e-158">**#undef TRACE**</span><span class="sxs-lookup"><span data-stu-id="90e6e-158">**#undef TRACE**</span></span>|<span data-ttu-id="90e6e-159">Отключает трассировку</span><span class="sxs-lookup"><span data-stu-id="90e6e-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="90e6e-160">**#define DEBUG**</span><span class="sxs-lookup"><span data-stu-id="90e6e-160">**#define DEBUG**</span></span>|<span data-ttu-id="90e6e-161">Включает отладку</span><span class="sxs-lookup"><span data-stu-id="90e6e-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="90e6e-162">**#undef DEBUG**</span><span class="sxs-lookup"><span data-stu-id="90e6e-162">**#undef DEBUG**</span></span>|<span data-ttu-id="90e6e-163">Отключает отладку</span><span class="sxs-lookup"><span data-stu-id="90e6e-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="90e6e-164">Отключение трассировки или отладки</span><span class="sxs-lookup"><span data-stu-id="90e6e-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="90e6e-165">Удалите директиву компилятора из исходного кода.</span><span class="sxs-lookup"><span data-stu-id="90e6e-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="90e6e-166">\- или -</span><span class="sxs-lookup"><span data-stu-id="90e6e-166">\- or -</span></span>  
  
<span data-ttu-id="90e6e-167">Удалите комментарий к директиве компилятора.</span><span class="sxs-lookup"><span data-stu-id="90e6e-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90e6e-168">Когда все готово для компиляции, можно выбрать команду **Построить** из меню **Сборка** или использовать метод командной строки (но без ввода **d:**), чтобы определить символы условной компиляции.</span><span class="sxs-lookup"><span data-stu-id="90e6e-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e6e-169">См. также</span><span class="sxs-lookup"><span data-stu-id="90e6e-169">See also</span></span>

- [<span data-ttu-id="90e6e-170">Трассировка и инструментирование приложений</span><span class="sxs-lookup"><span data-stu-id="90e6e-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="90e6e-171">Практическое руководство. Создание, инициализация и настройка переключателей трассировки</span><span class="sxs-lookup"><span data-stu-id="90e6e-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="90e6e-172">Переключатели трассировки</span><span class="sxs-lookup"><span data-stu-id="90e6e-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="90e6e-173">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="90e6e-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="90e6e-174">Практическое руководство. Добавление операторов трассировки в код приложения</span><span class="sxs-lookup"><span data-stu-id="90e6e-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="90e6e-175">Практическое руководство. Настройка переменных среды для командной строки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="90e6e-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="90e6e-176">Практическое руководство. Вызов компилятора командной строки</span><span class="sxs-lookup"><span data-stu-id="90e6e-176">How to: Invoke the Command-Line Compiler</span></span>](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
