---
title: Использование библиотеки .NET Standard в Visual Studio 2017
description: Создайте приложение .NET Core, которое вызывает члены из другой библиотеки классов, в Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 31a9183f541afa5365862b1e89704354cf7bd527
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969295"
---
# <a name="consume-a-net-standard-library-in-visual-studio-2017"></a><span data-ttu-id="a860a-103">Использование библиотеки .NET Standard в Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a860a-103">Consume a .NET Standard library in Visual Studio 2017</span></span>

<span data-ttu-id="a860a-104">Итак, вы создали библиотеку классов .NET Standard, проделав шаги, описанные в статье [Создание библиотеки классов с помощью C# и .NET Core в Visual Studio 2017](./library-with-visual-studio.md) или [Создание библиотеки классов с помощью Visual Basic и .NET Core в Visual Studio 2017](vb-library-with-visual-studio.md), протестировали ее по инструкциям из статьи [Тестирование библиотеки классов с помощью .NET Core в Visual Studio 2017](testing-library-with-visual-studio.md), а затем создали версию выпуска этой библиотеки. Теперь пора предоставить ее для использования вызывающим объектам.</span><span class="sxs-lookup"><span data-stu-id="a860a-104">Once you've created a .NET Standard class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="a860a-105">Для этого существуют два способа:</span><span class="sxs-lookup"><span data-stu-id="a860a-105">You can do this in two ways:</span></span>

* <span data-ttu-id="a860a-106">Если вся библиотека будет использоваться в одном решении (например, она является компонентом крупного приложения), достаточно включить библиотеку в проект этого решения.</span><span class="sxs-lookup"><span data-stu-id="a860a-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="a860a-107">Если же библиотеку нужно сделать общедоступной, ее следует предоставлять как пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="a860a-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="a860a-108">Включение библиотеки в решение в качестве проекта</span><span class="sxs-lookup"><span data-stu-id="a860a-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="a860a-109">Ранее вы включали модульные тесты в решение библиотеки классов. Теперь можно точно так же включить в это решение новое приложение.</span><span class="sxs-lookup"><span data-stu-id="a860a-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="a860a-110">Например, библиотеку классов можно использовать в консольном приложении, которое будет предлагать пользователю ввести строку и определять, является ли первый символ этой строки символом верхнего регистра:</span><span class="sxs-lookup"><span data-stu-id="a860a-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="a860a-111">C#</span><span class="sxs-lookup"><span data-stu-id="a860a-111">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="a860a-112">Откройте решение `ClassLibraryProjects`, созданное в рамках статьи [Создание библиотеки классов с помощью C# и .NET Core в Visual Studio 2017](./library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="a860a-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="a860a-113">В **обозревателе решений** щелкните правой кнопкой мыши решение **ClassLibraryProjects** и в контекстном меню выберите **Добавить** > **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="a860a-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="a860a-114">В диалоговом окне **Добавление нового проекта** разверните узел **Visual C#** , выберите узел **.NET Core**, а затем — шаблон проекта **Консольное приложение (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="a860a-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="a860a-115">В текстовом поле **Имя** введите "ShowCase", а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="a860a-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Диалоговое окно "Добавление нового проекта" в Visual Studio (C#)](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. <span data-ttu-id="a860a-117">В окне **Обозреватель решений** щелкните правой кнопкой мыши проект **ShowCase** и выберите команду **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="a860a-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Контекстное меню проекта с пунктом "Назначить запускаемым проектом" в Visual Studio (C#)](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="a860a-119">Изначально у этого проекта нет доступа к библиотеке классов.</span><span class="sxs-lookup"><span data-stu-id="a860a-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="a860a-120">Чтобы позволить приложению вызывать методы из библиотеки классов, создайте ссылку на библиотеку классов.</span><span class="sxs-lookup"><span data-stu-id="a860a-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="a860a-121">В окне **Обозреватель решений** щелкните правой кнопкой мыши узел **Зависимости** проекта `ShowCase` и выберите команду **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="a860a-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Контекстное меню проекта с пунктом "Добавить ссылку" в Visual Studio (C#)](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="a860a-123">В диалоговом окне **Диспетчер ссылок** выберите проект библиотеки классов **StringLibrary**, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="a860a-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Диалоговое окно "Диспетчер ссылок" в Visual Studio (C#)](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="a860a-125">В окне кода замените весь код файла *Program.cs* следующим текстом:</span><span class="sxs-lookup"><span data-stu-id="a860a-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="a860a-126">В этом коде используется переменная `row` для сохранения количества строк данных, записываемых в окно консоли.</span><span class="sxs-lookup"><span data-stu-id="a860a-126">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="a860a-127">Всякий раз, когда оно достигает значения 25 или превышает его, код очищает окно консоли и отображается сообщение для пользователя.</span><span class="sxs-lookup"><span data-stu-id="a860a-127">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="a860a-128">Сама программа предлагает пользователю ввести строку.</span><span class="sxs-lookup"><span data-stu-id="a860a-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="a860a-129">Она сообщает, начинается ли строка с символа верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="a860a-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="a860a-130">Если пользователь нажимает клавишу ВВОД, не введя никакой строки, приложение завершает свою работу и окно консоли закрывается.</span><span class="sxs-lookup"><span data-stu-id="a860a-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="a860a-131">При необходимости можно изменить режим на панели инструментов, чтобы скомпилировать **отладочную** версию проекта `ShowCase`.</span><span class="sxs-lookup"><span data-stu-id="a860a-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="a860a-132">Скомпилируйте и запустите программу, нажав зеленую стрелку на кнопке **ShowCase**.</span><span class="sxs-lookup"><span data-stu-id="a860a-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Панель инструментов проекта в Visual Studio с кнопкой отладки (C#)](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

# <a name="visual-basictabvb"></a>[<span data-ttu-id="a860a-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a860a-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="a860a-135">Откройте решение `ClassLibraryProjects`, созданное в рамках статьи [Создание библиотеки классов на Visual Basic с помощью .NET Core в Visual Studio 2017](vb-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="a860a-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="a860a-136">В **обозревателе решений** щелкните правой кнопкой мыши решение **ClassLibraryProjects** и в контекстном меню выберите **Добавить** > **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="a860a-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="a860a-137">В диалоговом окне **Добавление нового проекта** разверните узел **Visual Basic**, выберите узел **.NET Core**, а затем — шаблон проекта **Консольное приложение (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="a860a-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="a860a-138">В текстовом поле **Имя** введите "ShowCase", а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="a860a-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Диалоговое окно "Добавление нового проекта" в Visual Studio (Visual Basic)](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. <span data-ttu-id="a860a-140">В окне **Обозреватель решений** щелкните правой кнопкой мыши проект **ShowCase** и выберите команду **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="a860a-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Контекстное меню проекта с пунктом "Назначить запускаемым проектом" в Visual Studio (Visual Basic)](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="a860a-142">Изначально у этого проекта нет доступа к библиотеке классов.</span><span class="sxs-lookup"><span data-stu-id="a860a-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="a860a-143">Чтобы позволить приложению вызывать методы из библиотеки классов, создайте ссылку на библиотеку классов.</span><span class="sxs-lookup"><span data-stu-id="a860a-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="a860a-144">В окне **Обозреватель решений** щелкните правой кнопкой мыши узел **Зависимости** проекта `ShowCase` и выберите команду **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="a860a-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Контекстное меню проекта с пунктом "Добавить ссылку" в Visual Studio (Visual Basic)](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="a860a-146">В диалоговом окне **Диспетчер ссылок** выберите проект библиотеки классов **StringLibrary**, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="a860a-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Диалоговое окно "Диспетчер ссылок" в Visual Studio (Visual Basic)](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="a860a-148">В окне кода замените весь код файла *Program.vb* следующим текстом:</span><span class="sxs-lookup"><span data-stu-id="a860a-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="a860a-149">В этом коде используется переменная `row` для сохранения количества строк данных, записываемых в окно консоли.</span><span class="sxs-lookup"><span data-stu-id="a860a-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="a860a-150">Всякий раз, когда оно достигает значения 25 или превышает его, код очищает окно консоли и отображается сообщение для пользователя.</span><span class="sxs-lookup"><span data-stu-id="a860a-150">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="a860a-151">Сама программа предлагает пользователю ввести строку.</span><span class="sxs-lookup"><span data-stu-id="a860a-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="a860a-152">Она сообщает, начинается ли строка с символа верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="a860a-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="a860a-153">Если пользователь нажимает клавишу ВВОД, не введя никакой строки, приложение завершает свою работу и окно консоли закрывается.</span><span class="sxs-lookup"><span data-stu-id="a860a-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="a860a-154">При необходимости можно изменить режим на панели инструментов, чтобы скомпилировать **отладочную** версию проекта `ShowCase`.</span><span class="sxs-lookup"><span data-stu-id="a860a-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="a860a-155">Скомпилируйте и запустите программу, нажав зеленую стрелку на кнопке **ShowCase**.</span><span class="sxs-lookup"><span data-stu-id="a860a-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Режим отладки на панели инструментов (Visual Basic)](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

---

<span data-ttu-id="a860a-157">Чтобы отладить и опубликовать приложение, которое использует эту библиотеку, выполните действия из статей [Отладка приложения Hello World в Visual Studio 2017](debugging-with-visual-studio.md) и [Публикация приложения Hello World в Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="a860a-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="a860a-158">Распространение библиотеки в виде пакета NuGet</span><span class="sxs-lookup"><span data-stu-id="a860a-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="a860a-159">Библиотеку классов можно распространить и для других разработчиков, опубликовав ее в виде пакета NuGet.</span><span class="sxs-lookup"><span data-stu-id="a860a-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="a860a-160">Visual Studio не поддерживает создание пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="a860a-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="a860a-161">Для создания пакета используйте [служебную программу командной строки](../tools/dotnet.md) `dotnet` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a860a-161">To create one, you use the [`dotnet` command line utility](../tools/dotnet.md):</span></span>

1. <span data-ttu-id="a860a-162">Откройте окно консоли.</span><span class="sxs-lookup"><span data-stu-id="a860a-162">Open a console window.</span></span> <span data-ttu-id="a860a-163">Например, в текстовом поле **Задайте любой вопрос** на панели задач Windows введите `Command Prompt` (или `cmd` для краткости), а затем откройте окно консоли с помощью приложения **командной строки** или клавиши ВВОД, если оно выделено в результатах поиска.</span><span class="sxs-lookup"><span data-stu-id="a860a-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="a860a-164">Перейдите в каталог с проектом библиотеки.</span><span class="sxs-lookup"><span data-stu-id="a860a-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="a860a-165">Если вы не меняли расположение файлов, проект размещается в каталоге *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary*.</span><span class="sxs-lookup"><span data-stu-id="a860a-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="a860a-166">Этот каталог содержит исходный код и файл проекта (*StringLibrary.csproj*).</span><span class="sxs-lookup"><span data-stu-id="a860a-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="a860a-167">Выполните команду `dotnet pack --no-build`.</span><span class="sxs-lookup"><span data-stu-id="a860a-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="a860a-168">Служебная программа `dotnet` создаст пакет с расширением *.nupkg*.</span><span class="sxs-lookup"><span data-stu-id="a860a-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="a860a-169">Если каталог, содержащий *dotnet.exe*, не находится в системном пути, найдите расположение этого файла, введя `where dotnet.exe` в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="a860a-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="a860a-170">Дополнительные сведения о создании пакетов NuGet см. в статье [How to Create a NuGet Package with Cross Platform Tools](../deploying/creating-nuget-packages.md) (Создание пакета NuGet с помощью кроссплатформенных средств).</span><span class="sxs-lookup"><span data-stu-id="a860a-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../deploying/creating-nuget-packages.md).</span></span>
