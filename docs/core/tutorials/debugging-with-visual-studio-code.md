---
title: Отладка консольного приложения .NET Core в Visual Studio Code
description: Узнайте, как выполнить отладку консольного приложения .NET Core в Visual Studio Code.
ms.date: 05/26/2020
ms.openlocfilehash: 82b2798397d702aa2a50c04bf6e4d569b97e3666
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241517"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="dd441-103">Учебник. Отладка консольного приложения .NET Core с помощью Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dd441-103">Tutorial: Debug a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="dd441-104">В этом учебнике представлены средства отладки, доступные в Visual Studio Code для работы с приложениями .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dd441-104">This tutorial introduces the debugging tools available in Visual Studio Code for working with .NET Core apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dd441-105">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="dd441-105">Prerequisites</span></span>

- <span data-ttu-id="dd441-106">В этом руководстве используется консольное приложение, созданное в руководстве [Создание консольного приложения .NET Core в Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="dd441-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="dd441-107">Использование конфигурации отладочной сборки</span><span class="sxs-lookup"><span data-stu-id="dd441-107">Use Debug build configuration</span></span>

<span data-ttu-id="dd441-108">В .NET Core используются две конфигурации сборки — *Отладка* и *Выпуск*.</span><span class="sxs-lookup"><span data-stu-id="dd441-108">*Debug* and *Release* are two of .NET Core's build configurations.</span></span> <span data-ttu-id="dd441-109">Вы воспользуетесь отладочной конфигурацией сборки для отладки и конфигурацией для выпуска для окончательного выпуска программы.</span><span class="sxs-lookup"><span data-stu-id="dd441-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="dd441-110">В отладочной конфигурации программы компилируется с полной символической отладочной информацией и без оптимизации.</span><span class="sxs-lookup"><span data-stu-id="dd441-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="dd441-111">Оптимизация усложняет отладку, поскольку усложняется связь между исходным кодом и сгенерированными инструкциями.</span><span class="sxs-lookup"><span data-stu-id="dd441-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="dd441-112">Конфигурация для выпуска полностью оптимизирована и не содержит символической отладочной информации.</span><span class="sxs-lookup"><span data-stu-id="dd441-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="dd441-113">По умолчанию Visual Studio Code использует отладочную конфигурацию сборки, поэтому ее не нужно изменять перед отладкой.</span><span class="sxs-lookup"><span data-stu-id="dd441-113">By default, Visual Studio Code uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="dd441-114">Установка точки останова</span><span class="sxs-lookup"><span data-stu-id="dd441-114">Set a breakpoint</span></span>

<span data-ttu-id="dd441-115">Точка останова приостанавливает выполнение приложения на инструкции, *предшествующей* той строке, в которой установлена точка останова.</span><span class="sxs-lookup"><span data-stu-id="dd441-115">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="dd441-116">Откройте Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dd441-116">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="dd441-117">Откройте папку проекта *HelloWorld*, созданного в руководстве [Создание консольного приложения .NET Core в Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="dd441-117">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="dd441-118">Откройте файл *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="dd441-118">Open the *Program.cs* file.</span></span>

1. <span data-ttu-id="dd441-119">Установите *точку останова* в строке, где отображается имя, дата и время, щелкнув в левом поле окна кода.</span><span class="sxs-lookup"><span data-stu-id="dd441-119">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window.</span></span> <span data-ttu-id="dd441-120">Левое поле находится слева от номеров строк.</span><span class="sxs-lookup"><span data-stu-id="dd441-120">The left margin is to the left of the line numbers.</span></span> <span data-ttu-id="dd441-121">Кроме того, установить точку останова можно, поместив курсор в строку кода и нажав клавишу <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-121">Another way to set a breakpoint is by placing the cursor in the line of code and then pressing <kbd>F9</kbd>.</span></span>

   <span data-ttu-id="dd441-122">Как видно на следующем рисунке, строку с точкой останова Visual Studio Code обозначает красной точкой в левом поле.</span><span class="sxs-lookup"><span data-stu-id="dd441-122">As the following image shows, Visual Studio Code indicates the line on which the breakpoint is set by displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Заданная точка останова":::

## <a name="set-up-for-terminal-input"></a><span data-ttu-id="dd441-124">Настройка входных данных терминала</span><span class="sxs-lookup"><span data-stu-id="dd441-124">Set up for terminal input</span></span>

<span data-ttu-id="dd441-125">Точка останова находится после вызова метода `Console.ReadLine`.</span><span class="sxs-lookup"><span data-stu-id="dd441-125">The breakpoint is located after a `Console.ReadLine` method call.</span></span> <span data-ttu-id="dd441-126">**Консоль отладки** не принимает входные данные терминала для выполняющейся программы.</span><span class="sxs-lookup"><span data-stu-id="dd441-126">The **Debug Console** doesn't accept terminal input for a running program.</span></span> <span data-ttu-id="dd441-127">Чтобы использовать выходные данные терминала во время отладки, можно использовать встроенный терминал (одно из окон Visual Studio Code) или внешний терминал.</span><span class="sxs-lookup"><span data-stu-id="dd441-127">To handle terminal input while debugging, you can use the integrated terminal (one of the Visual Studio Code windows) or an external terminal.</span></span> <span data-ttu-id="dd441-128">В этом учебнике используется встроенный терминал.</span><span class="sxs-lookup"><span data-stu-id="dd441-128">For this tutorial, you use the integrated terminal.</span></span>

1. <span data-ttu-id="dd441-129">Откройте файл *.vscode/launch.json*.</span><span class="sxs-lookup"><span data-stu-id="dd441-129">Open *.vscode/launch.json*.</span></span>

1. <span data-ttu-id="dd441-130">Измените параметр `console` на `integratedTerminal`.</span><span class="sxs-lookup"><span data-stu-id="dd441-130">Change the `console` setting to `integratedTerminal`.</span></span>

   <span data-ttu-id="dd441-131">От:</span><span class="sxs-lookup"><span data-stu-id="dd441-131">From:</span></span>

   ```
   "console": "internalConsole",
   ```

   <span data-ttu-id="dd441-132">В:</span><span class="sxs-lookup"><span data-stu-id="dd441-132">To:</span></span>

   ```
   "console": "integratedTerminal",
   ```

1. <span data-ttu-id="dd441-133">Сохраните изменения.</span><span class="sxs-lookup"><span data-stu-id="dd441-133">Save your changes.</span></span>

## <a name="start-debugging"></a><span data-ttu-id="dd441-134">Начать отладку</span><span class="sxs-lookup"><span data-stu-id="dd441-134">Start debugging</span></span>

1. <span data-ttu-id="dd441-135">Откройте окно отладки, щелкнув значок "Отладка" в меню слева.</span><span class="sxs-lookup"><span data-stu-id="dd441-135">Open the Debug view by selecting the Debugging icon on the left side menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Открытие вкладки "Отладка" в Visual Studio Code":::

1. <span data-ttu-id="dd441-137">Начните отладку, нажав зеленую стрелку в верхней части области, рядом с элементом **запуска .NET Core (консоль)** .</span><span class="sxs-lookup"><span data-stu-id="dd441-137">Start debugging by selecting the green arrow at the top of the pane, next to **.NET Core Launch (console)**.</span></span>  <span data-ttu-id="dd441-138">Также отладку можно запустить с помощью клавиши <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-138">Another way to start debugging is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Запуск отладки":::

1. <span data-ttu-id="dd441-140">Выберите вкладку **Терминал**, чтобы отобразить запрос "What is your name?" (Как вас зовут?),</span><span class="sxs-lookup"><span data-stu-id="dd441-140">Select the **Terminal** tab to see the "What is your name?"</span></span> <span data-ttu-id="dd441-141">который появляется перед ожиданием ответа.</span><span class="sxs-lookup"><span data-stu-id="dd441-141">prompt that the program displays before waiting for a response.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Выбор вкладки "Терминал"":::

1. <span data-ttu-id="dd441-143">Введите строку в окне **Терминал** в ответ на запрос имени, а затем нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-143">Enter a string in the **Terminal** window in response to the prompt for a name, and then press <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="dd441-144">Выполнение программы остановится, когда будет достигнута точка останова, то есть перед выполнением метода `Console.WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="dd441-144">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="dd441-145">В окне **Локальные** окна **Переменные** отображаются значения переменных, которые определены в текущем выполняемом методе.</span><span class="sxs-lookup"><span data-stu-id="dd441-145">The **Locals** section of the **Variables** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Достижение точки останова, отображение окна "Локальные"":::

## <a name="change-variable-values"></a><span data-ttu-id="dd441-147">Изменение значений переменных</span><span class="sxs-lookup"><span data-stu-id="dd441-147">Change variable values</span></span>

<span data-ttu-id="dd441-148">Окно **Консоль отладки** служит для взаимодействия с приложением, которое вы отлаживаете.</span><span class="sxs-lookup"><span data-stu-id="dd441-148">The **Debug Console** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="dd441-149">Вы можете изменить значения переменных и посмотреть, как это повлияет на работу программы.</span><span class="sxs-lookup"><span data-stu-id="dd441-149">You can change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="dd441-150">Выберите вкладку **Консоль отладки**.</span><span class="sxs-lookup"><span data-stu-id="dd441-150">Select the **Debug Console** tab.</span></span>

1. <span data-ttu-id="dd441-151">Введите `name = "Gracie"` в запросе в нижней части окна **Консоль отладки** и нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-151">Enter `name = "Gracie"` at the prompt at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Изменение значений переменных":::

1. <span data-ttu-id="dd441-153">Введите `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` в нижней части окна **Консоль отладки** и нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-153">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="dd441-154">В окне **Переменные** отображаются новые значения переменных `name` и `date`.</span><span class="sxs-lookup"><span data-stu-id="dd441-154">The **Variables** window displays the new values of the `name` and `date` variables.</span></span>

1. <span data-ttu-id="dd441-155">Продолжите выполнение программы, нажав кнопку **Продолжить** на панели инструментов.</span><span class="sxs-lookup"><span data-stu-id="dd441-155">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="dd441-156">Еще один способ продолжить — нажать клавишу <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-156">Another way to continue is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Продолжение отладки":::

1. <span data-ttu-id="dd441-158">Снова выберите вкладку **Терминал**.</span><span class="sxs-lookup"><span data-stu-id="dd441-158">Select the **Terminal** tab again.</span></span>

   <span data-ttu-id="dd441-159">Значения, отображаемые в окне консоли, соответствуют изменениям, произведенным в окне **Консоль отладки**.</span><span class="sxs-lookup"><span data-stu-id="dd441-159">The values displayed in the console window correspond to the changes you made in the **Debug Console**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Окно терминала с указанными значениями":::

1. <span data-ttu-id="dd441-161">Нажмите любую клавишу, чтобы выйти из приложения и остановить отладку.</span><span class="sxs-lookup"><span data-stu-id="dd441-161">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="dd441-162">Установка условной точки останова</span><span class="sxs-lookup"><span data-stu-id="dd441-162">Set a conditional breakpoint</span></span>

<span data-ttu-id="dd441-163">Программа отображает строку, которую вводит пользователь.</span><span class="sxs-lookup"><span data-stu-id="dd441-163">The program displays the string that the user enters.</span></span> <span data-ttu-id="dd441-164">Что произойдет, если пользователь ничего не введет?</span><span class="sxs-lookup"><span data-stu-id="dd441-164">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="dd441-165">Это можно проверить с помощью полезной функции отладки, которая называется *условной точкой останова*.</span><span class="sxs-lookup"><span data-stu-id="dd441-165">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="dd441-166">Щелкните правой кнопкой мыши красную точку, обозначающую точку останова (или щелкните ее, удерживая нажатой клавишу <kbd>CTRL</kbd> в macOS).</span><span class="sxs-lookup"><span data-stu-id="dd441-166">Right-click (<kbd>Ctrl</kbd>+click on macOS) on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="dd441-167">В контекстном меню выберите **Изменить точку останова**, чтобы открыть диалоговое окно, в котором можно ввести условное выражение.</span><span class="sxs-lookup"><span data-stu-id="dd441-167">In the context menu, select **Edit Breakpoint** to open a dialog that lets you enter a conditional expression.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Контекстное меню точки останова":::

1. <span data-ttu-id="dd441-169">Выберите `Expression` в раскрывающемся списке, введите следующее условное выражение и нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-169">Select `Expression` in the drop-down, enter the following conditional expression, and press <kbd>Enter</kbd>.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Ввод условного выражения":::

   <span data-ttu-id="dd441-171">При каждом достижении точки останова отладчик вызывает метод `String.IsNullOrEmpty(name)` и останавливается на этой строке только в том случае, если вызов метода возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="dd441-171">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="dd441-172">Вместо условного выражения можно указать *количество обращений* (в этом случае выполнение программы будет прерываться до тех пор, пока не будет достигнуто заданное количество обращений) или *условие фильтра* (в этом случае выполнение программы будет прерываться на основе таких атрибутов, как идентификатор потока, имя процесса и имя потока).</span><span class="sxs-lookup"><span data-stu-id="dd441-172">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="dd441-173">Запустите отладку программы, нажав клавишу <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-173">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="dd441-174">Когда на вкладке **Терминал** появится предложение ввести имя, нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-174">In the **Terminal** tab, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

   <span data-ttu-id="dd441-175">Поскольку указанное вами условие соблюдается (`name` имеет значение `null` или <xref:System.String.Empty?displayProperty=nameWithType>), выполнение программы будет остановлено при достижении точки останова, то есть перед выполнением метода `Console.WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="dd441-175">Because the condition you specified (`name` is `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

   <span data-ttu-id="dd441-176">В окне **Переменные** указывается, что значение переменной `name` `""`или <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd441-176">The **Variables** window shows that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="dd441-177">Убедитесь в том, что переменная содержит пустую строку, введя следующий оператор в окне **Консоль отладки** и нажав клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-177">Confirm the value is an empty string by entering the following statement at the **Debug Console** prompt and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="dd441-178">Результат равен `true`.</span><span class="sxs-lookup"><span data-stu-id="dd441-178">The result is `true`.</span></span>

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="Значение true в окне "Консоль отладки" после выполнения оператора":::

1. <span data-ttu-id="dd441-180">Нажмите кнопку **Продолжить** на панели инструментов, чтобы возобновить выполнение программы.</span><span class="sxs-lookup"><span data-stu-id="dd441-180">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="dd441-181">Перейдите на вкладку **Терминалов** и нажмите любую клавишу, чтобы выйти из программы и прекратить отладку.</span><span class="sxs-lookup"><span data-stu-id="dd441-181">Select the **Terminal** tab, and press any key to exit the program and stop debugging.</span></span>

1. <span data-ttu-id="dd441-182">Очистите точку останова. Для этого щелкните красную точку в левом поле окна с кодом.</span><span class="sxs-lookup"><span data-stu-id="dd441-182">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="dd441-183">Или нажмите клавишу <kbd>F9</kbd> при выбранной строке кода.</span><span class="sxs-lookup"><span data-stu-id="dd441-183">Another way to clear a breakpoint is by pressing <kbd>F9</kbd> while the line of code is selected.</span></span>

1. <span data-ttu-id="dd441-184">При появлении предупреждения о том, что условие точки останова будет потеряно, выберите **Удалить точку останова**.</span><span class="sxs-lookup"><span data-stu-id="dd441-184">If you get a warning that the breakpoint condition will be lost, select **Remove Breakpoint**.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="dd441-185">Пошаговое выполнение программы</span><span class="sxs-lookup"><span data-stu-id="dd441-185">Step through a program</span></span>

<span data-ttu-id="dd441-186">Visual Studio Code позволяет выполнять программу пошагово, отслеживая результат ее выполнения.</span><span class="sxs-lookup"><span data-stu-id="dd441-186">Visual Studio Code also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="dd441-187">Для этого обычно задают точку останова и запускают программу в небольшой части ее кода.</span><span class="sxs-lookup"><span data-stu-id="dd441-187">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="dd441-188">Поскольку наша программа невелика, давайте выполним ее пошагово.</span><span class="sxs-lookup"><span data-stu-id="dd441-188">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="dd441-189">Установите точку останова на открывающей фигурной скобке метода `Main`.</span><span class="sxs-lookup"><span data-stu-id="dd441-189">Set a breakpoint on the opening curly brace of the `Main` method.</span></span>

1. <span data-ttu-id="dd441-190">Нажмите клавишу <kbd>F5</kbd> , чтобы начать отладку.</span><span class="sxs-lookup"><span data-stu-id="dd441-190">Press <kbd>F5</kbd> to start debugging.</span></span>

   <span data-ttu-id="dd441-191">Visual Studio Code выделит строку точки останова.</span><span class="sxs-lookup"><span data-stu-id="dd441-191">Visual Studio Code highlights the breakpoint line.</span></span>

   <span data-ttu-id="dd441-192">На этом этапе в окне **Переменные** показано, что массив `args` пуст, а `name` и `date` имеют значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="dd441-192">At this point, the **Variables** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span>

1. <span data-ttu-id="dd441-193">Выберите **Шаг с заходом** или нажмите клавишу <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-193">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Кнопка "Шаг с заходом"":::

   <span data-ttu-id="dd441-195">Будет выделена следующая строка.</span><span class="sxs-lookup"><span data-stu-id="dd441-195">Visual Studio Code highlights the next line.</span></span>

1. <span data-ttu-id="dd441-196">Выберите **Шаг с заходом** или нажмите клавишу <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-196">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="dd441-197">Visual Studio Code выполняет `Console.WriteLine` для запроса имени и выделяет следующую строку выполнения.</span><span class="sxs-lookup"><span data-stu-id="dd441-197">Visual Studio Code executes the `Console.WriteLine` for the name prompt and highlights the next line of execution.</span></span> <span data-ttu-id="dd441-198">Следующая строка — это `Console.ReadLine` для `name`.</span><span class="sxs-lookup"><span data-stu-id="dd441-198">The next line is the `Console.ReadLine` for the `name`.</span></span> <span data-ttu-id="dd441-199">Содержимое окна **Переменные** останется без изменений, а на вкладке **Терминал** появится сообщение "What is your name?"</span><span class="sxs-lookup"><span data-stu-id="dd441-199">The **Variables** window is unchanged, and the **Terminal** tab shows the "What is your name?"</span></span> <span data-ttu-id="dd441-200">(Как вас зовут?).</span><span class="sxs-lookup"><span data-stu-id="dd441-200">prompt.</span></span>

1. <span data-ttu-id="dd441-201">Выберите **Шаг с заходом** или нажмите клавишу <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-201">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="dd441-202">Visual Studio выделит назначение переменной `name`.</span><span class="sxs-lookup"><span data-stu-id="dd441-202">Visual Studio highlights the `name` variable assignment.</span></span> <span data-ttu-id="dd441-203">В окне **Переменные** видно, что `name` по-прежнему `null`.</span><span class="sxs-lookup"><span data-stu-id="dd441-203">The **Variables** window shows that `name` is still `null`.</span></span>

1. <span data-ttu-id="dd441-204">Ответьте на этот запрос, введя строку на вкладке "Терминал" и нажав клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-204">Respond to the prompt by entering a string in the Terminal tab and pressing <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="dd441-205">На вкладке **Терминал** может не отображаться введенная строка, однако метод <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> будет записывать входные данные.</span><span class="sxs-lookup"><span data-stu-id="dd441-205">The **Terminal** tab might not display the string you enter while you're entering it, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will capture your input.</span></span>

1. <span data-ttu-id="dd441-206">Выберите **Шаг с заходом** или нажмите клавишу <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-206">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="dd441-207">Visual Studio Code выделит назначение переменной `date`.</span><span class="sxs-lookup"><span data-stu-id="dd441-207">Visual Studio Code highlights the `date` variable assignment.</span></span> <span data-ttu-id="dd441-208">В окне **Переменные** отображается значение, полученное в результате вызова метода <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd441-208">The **Variables** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dd441-209">На вкладке **Терминал** также отображается строка, указанная в командной строке.</span><span class="sxs-lookup"><span data-stu-id="dd441-209">The **Terminal** tab displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="dd441-210">Выберите **Шаг с заходом** или нажмите клавишу <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-210">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="dd441-211">В окне **Переменные** отображается значение переменной `date`, которому было присвоено свойство <xref:System.DateTime.Now?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd441-211">The **Variables** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span>

1. <span data-ttu-id="dd441-212">Выберите **Шаг с заходом** или нажмите клавишу <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-212">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="dd441-213">Visual Studio Code вызывает метод <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd441-213">Visual Studio Code calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dd441-214">В окне консоли отображается форматированная строка.</span><span class="sxs-lookup"><span data-stu-id="dd441-214">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="dd441-215">Выберите **Шаг с выходом** или нажмите клавиши <kbd>SHIFT</kbd>+<kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dd441-215">Select **Step Out** or press <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Кнопка "Шаг с выходом"":::

1. <span data-ttu-id="dd441-217">Выберите вкладку **Терминал**.</span><span class="sxs-lookup"><span data-stu-id="dd441-217">Select the **Terminal** tab.</span></span>

   <span data-ttu-id="dd441-218">В окне терминала отобразится сообщение "Нажмите любую клавишу, чтобы выйти..."</span><span class="sxs-lookup"><span data-stu-id="dd441-218">The terminal displays "Press any key to exit..."</span></span>

1. <span data-ttu-id="dd441-219">Нажмите любую клавишу для выхода из программы.</span><span class="sxs-lookup"><span data-stu-id="dd441-219">Press any key to exit the program.</span></span>

## <a name="select-release-build-configuration"></a><span data-ttu-id="dd441-220">Выбор конфигурации сборки для выпуска</span><span class="sxs-lookup"><span data-stu-id="dd441-220">Select Release build configuration</span></span>

<span data-ttu-id="dd441-221">После тестирования отладочной версии приложения следует скомпилировать и протестировать версию в режиме выпуска.</span><span class="sxs-lookup"><span data-stu-id="dd441-221">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="dd441-222">Версию для выпуска компилятор собирает с использованием методов оптимизации, которые могут влиять на поведение приложения.</span><span class="sxs-lookup"><span data-stu-id="dd441-222">The Release version incorporates compiler optimizations that can affect the behavior of an application.</span></span> <span data-ttu-id="dd441-223">Например, оптимизации компилятора для повышения производительности могут привести к состоянию конкуренции в многопоточных приложениях.</span><span class="sxs-lookup"><span data-stu-id="dd441-223">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="dd441-224">Чтобы создать и протестировать версию консольного приложения для выпуска, откройте **терминал** и выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="dd441-224">To build and test the Release version of your console application, open the **Terminal** and run the following command:</span></span>

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a><span data-ttu-id="dd441-225">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="dd441-225">Additional resources</span></span>

* <span data-ttu-id="dd441-226">[Debugging in Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging) (Отладка в Visual Studio Code)</span><span class="sxs-lookup"><span data-stu-id="dd441-226">[Debugging in Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)</span></span>

## <a name="next-steps"></a><span data-ttu-id="dd441-227">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="dd441-227">Next steps</span></span>

<span data-ttu-id="dd441-228">В этом учебнике вы использовали средства отладки Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dd441-228">In this tutorial, you used Visual Studio Code debugging tools.</span></span> <span data-ttu-id="dd441-229">В следующем руководстве вы опубликуете развертываемую версию приложения.</span><span class="sxs-lookup"><span data-stu-id="dd441-229">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dd441-230">Публикация консольного приложения .NET Core в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dd441-230">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
