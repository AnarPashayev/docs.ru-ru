---
title: Практическое руководство. Использование именованных и необязательных аргументов в программировании приложений Office (руководство по программированию на C#)
description: Узнайте, как использовать именованные и необязательные аргументы для упрощения доступа к COM-интерфейсам, таким как API-интерфейсы автоматизации Microsoft Office.
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 7e24331d37e8fdbe2bc66a2d9f73a5f6a7242af9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864349"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="5f7f4-103">Практическое руководство. Использование именованных и необязательных аргументов в программировании приложений Office (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="5f7f4-103">How to use named and optional arguments in Office programming (C# Programming Guide)</span></span>

<span data-ttu-id="5f7f4-104">Появившиеся в C# 4 именованные и необязательные аргументы повышают удобство, гибкость и удобочитаемость программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-104">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="5f7f4-105">Кроме того, эти функции значительно упрощают доступ к COM-интерфейсам, таким как интерфейсы API автоматизации Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-105">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="5f7f4-106">В следующем примере у метода [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) имеется шестнадцать параметров, представляющих характеристики таблицы, например число столбцов и строк, форматирование, границы и цвета.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-106">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="5f7f4-107">Все шестнадцать параметров являются необязательными, поскольку в большинстве случаев не требуется задавать конкретные значения для всех этих параметров.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-107">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="5f7f4-108">Однако без именованных и необязательных аргументов приходилось указывать значение или значение-заполнитель для каждого из параметров.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-108">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="5f7f4-109">Именованные и необязательные параметры позволяют задавать значения только для тех параметров, которые требуются в конкретном проекте.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-109">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="5f7f4-110">Для выполнения этих процедур на компьютере должно быть установлено приложение Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-110">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="5f7f4-111">Создание нового проекта консольного приложения</span><span class="sxs-lookup"><span data-stu-id="5f7f4-111">To create a new console application</span></span>

1. <span data-ttu-id="5f7f4-112">Запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-112">Start Visual Studio.</span></span>

2. <span data-ttu-id="5f7f4-113">В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-113">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="5f7f4-114">В области **Категории шаблонов** разверните узел **Visual C#** и выберите **Windows**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-114">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="5f7f4-115">В верхней части области **Шаблоны** в поле **Требуемая версия .NET Framework** должно отображаться значение **.NET Framework 4**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-115">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="5f7f4-116">В области **Шаблоны** щелкните **Консольное приложение**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-116">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="5f7f4-117">Введите имя проекта в поле **Имя**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-117">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="5f7f4-118">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-118">Click **OK**.</span></span>

     <span data-ttu-id="5f7f4-119">В **обозревателе решений** появится новый проект.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-119">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="5f7f4-120">Добавление ссылки</span><span class="sxs-lookup"><span data-stu-id="5f7f4-120">To add a reference</span></span>

1. <span data-ttu-id="5f7f4-121">В **обозревателе решений** щелкните имя проекта правой кнопкой мыши и выберите пункт **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-121">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="5f7f4-122">Откроется диалоговое окно **Добавление ссылки**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-122">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="5f7f4-123">На странице **.NET** выберите **Microsoft.Office.Interop.Word** в списке **Имя компонента**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-123">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="5f7f4-124">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-124">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="5f7f4-125">Добавление необходимых директив using</span><span class="sxs-lookup"><span data-stu-id="5f7f4-125">To add necessary using directives</span></span>

1. <span data-ttu-id="5f7f4-126">В **обозревателе решений** щелкните правой кнопкой мыши файл *Program.cs* и выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-126">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="5f7f4-127">В начало файла кода добавьте следующие директивы `using`:</span><span class="sxs-lookup"><span data-stu-id="5f7f4-127">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="5f7f4-128">Отображение текста в документ Word</span><span class="sxs-lookup"><span data-stu-id="5f7f4-128">To display text in a Word document</span></span>

1. <span data-ttu-id="5f7f4-129">В класс `Program` в файле *Program.cs* добавьте следующий метод для создания приложения Word и документа Word.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-129">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="5f7f4-130">Метод [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) имеет четыре необязательных параметра.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-130">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="5f7f4-131">В этом примере используются значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-131">This example uses their default values.</span></span> <span data-ttu-id="5f7f4-132">Поэтому в операторе вызова указывать аргументы не требуется.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-132">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="5f7f4-133">Добавьте в конец метода следующий код, чтобы определить место отображения текста в документе и текст для отображения:</span><span class="sxs-lookup"><span data-stu-id="5f7f4-133">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="5f7f4-134">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="5f7f4-134">To run the application</span></span>

1. <span data-ttu-id="5f7f4-135">Добавьте в метод Main следующую инструкцию:</span><span class="sxs-lookup"><span data-stu-id="5f7f4-135">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="5f7f4-136">Нажмите клавиши <kbd>CTRL</kbd>+<kbd>F5</kbd>, чтобы запустить проект.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-136">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="5f7f4-137">Появится документ Word, содержащий указанный текст.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-137">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="5f7f4-138">Замена текста на таблицу</span><span class="sxs-lookup"><span data-stu-id="5f7f4-138">To change the text to a table</span></span>
  
1. <span data-ttu-id="5f7f4-139">Метод `ConvertToTable` служит для преобразования текста в таблицу.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-139">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="5f7f4-140">У метода имеется шестнадцать необязательных параметров.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-140">The method has sixteen optional parameters.</span></span> <span data-ttu-id="5f7f4-141">IntelliSense заключает необязательные параметры в квадратные скобки, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-141">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![Список параметров для метода ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="5f7f4-143">Именованные и необязательные аргументы позволяют задавать значения только для тех параметров, которые требуется изменить.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="5f7f4-144">Добавьте в конец метода `DisplayInWord` следующий код, чтобы создать простую таблицу.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="5f7f4-145">Аргумент указывает, что запятые в текстовой строке в `range` разделяют ячейки таблицы.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="5f7f4-146">В более ранних версиях C# для вызова `ConvertToTable` каждому параметру требовался ссылочный аргумент, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="5f7f4-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="5f7f4-147">Нажмите клавиши <kbd>CTRL</kbd>+<kbd>F5</kbd>, чтобы запустить проект.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-147">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="5f7f4-148">Экспериментирование с другими параметрами</span><span class="sxs-lookup"><span data-stu-id="5f7f4-148">To experiment with other parameters</span></span>

1. <span data-ttu-id="5f7f4-149">Для изменения таблицы, чтобы она содержала один столбец и три строки, замените последнюю строку метода `DisplayInWord` следующей инструкцией и нажмите сочетание клавиш <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="5f7f4-150">Чтобы использовать заранее определенный формат таблицы, замените последнюю строку метода `DisplayInWord` следующей инструкцией и нажмите сочетание клавиш <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5f7f4-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="5f7f4-151">В качестве формата можно использовать любую из констант [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>).</span><span class="sxs-lookup"><span data-stu-id="5f7f4-151">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="5f7f4-152">Пример</span><span class="sxs-lookup"><span data-stu-id="5f7f4-152">Example</span></span>

<span data-ttu-id="5f7f4-153">Следующий код включает полный пример:</span><span class="sxs-lookup"><span data-stu-id="5f7f4-153">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="5f7f4-154">См. также</span><span class="sxs-lookup"><span data-stu-id="5f7f4-154">See also</span></span>

- [<span data-ttu-id="5f7f4-155">Именованные и необязательные аргументы</span><span class="sxs-lookup"><span data-stu-id="5f7f4-155">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
