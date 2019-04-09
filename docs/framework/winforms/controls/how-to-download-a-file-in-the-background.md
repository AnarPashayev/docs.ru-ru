---
title: Практическое руководство. Фоновая загрузка файла
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
ms.openlocfilehash: af5a607b4800635d096e83b55a5bd5a912c8538d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128782"
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="ef760-102">Практическое руководство. Фоновая загрузка файла</span><span class="sxs-lookup"><span data-stu-id="ef760-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="ef760-103">Загрузка файла — это обычная задача, и было бы разумным запускать эту потенциально длительную операцию в отдельном потоке.</span><span class="sxs-lookup"><span data-stu-id="ef760-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="ef760-104">С помощью компонента <xref:System.ComponentModel.BackgroundWorker> и небольшого фрагмента кода эта задача легко решается.</span><span class="sxs-lookup"><span data-stu-id="ef760-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef760-105">Пример</span><span class="sxs-lookup"><span data-stu-id="ef760-105">Example</span></span>  
 <span data-ttu-id="ef760-106">В примере кода ниже демонстрируется использование компонента <xref:System.ComponentModel.BackgroundWorker> для загрузки XML-файла с URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="ef760-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="ef760-107">Когда пользователь щелкает **загрузить** кнопки <xref:System.Windows.Forms.Control.Click> вызовов обработчика событий <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> метод <xref:System.ComponentModel.BackgroundWorker> компонента для запуска операции загрузки.</span><span class="sxs-lookup"><span data-stu-id="ef760-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="ef760-108">Кнопка отключается во время загрузки, а по его окончании снова становится активной.</span><span class="sxs-lookup"><span data-stu-id="ef760-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="ef760-109">В поле <xref:System.Windows.Forms.MessageBox> выводится содержимое файла.</span><span class="sxs-lookup"><span data-stu-id="ef760-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **<span data-ttu-id="ef760-110">Загрузка файла</span><span class="sxs-lookup"><span data-stu-id="ef760-110">Downloading the file</span></span>**  
  
 <span data-ttu-id="ef760-111">Файл скачивается в рабочем потоке компонента <xref:System.ComponentModel.BackgroundWorker>, который запускает обработчик событий <xref:System.ComponentModel.BackgroundWorker.DoWork>.</span><span class="sxs-lookup"><span data-stu-id="ef760-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="ef760-112">Этот поток запускается, когда код вызывает метод <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef760-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **<span data-ttu-id="ef760-113">Ожидание завершения работы BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="ef760-113">Waiting for a BackgroundWorker to finish</span></span>**  
  
 <span data-ttu-id="ef760-114">Обработчик событий `downloadButton_Click` демонстрирует ожидание завершения выполнения асинхронной задачи компонентом <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="ef760-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="ef760-115">Если нужно, чтобы приложение лишь реагировало на события и не выполняло никакой работы в основном потоке в ожидании, пока не завершится выполнение фонового потока, просто завершите работу обработчика.</span><span class="sxs-lookup"><span data-stu-id="ef760-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="ef760-116">Если нужно продолжить выполнение работы в основном потоке, воспользуйтесь свойством <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A>, чтобы определить, по-прежнему ли выполняется поток <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="ef760-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="ef760-117">В примере индикатор выполнения обновляется в процессе загрузки.</span><span class="sxs-lookup"><span data-stu-id="ef760-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="ef760-118">Для сохранения отклика пользовательского интерфейса обязательно вызовите метод <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef760-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **<span data-ttu-id="ef760-119">Вывод результата</span><span class="sxs-lookup"><span data-stu-id="ef760-119">Displaying the result</span></span>**  
  
 <span data-ttu-id="ef760-120">Метод `backgroundWorker1_RunWorkerCompleted` обрабатывает событие <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> и вызывается по завершении фоновой операции.</span><span class="sxs-lookup"><span data-stu-id="ef760-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="ef760-121">Сначала этот метод проверяет свойство <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef760-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ef760-122">Если свойство <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> имеет значение `null`, то метод выводит содержимое файла.</span><span class="sxs-lookup"><span data-stu-id="ef760-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="ef760-123">Затем он активирует кнопку загрузки, которая была отключена, когда началась загрузка, и сбрасывает индикатор выполнения.</span><span class="sxs-lookup"><span data-stu-id="ef760-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef760-124">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="ef760-124">Compiling the Code</span></span>  
 <span data-ttu-id="ef760-125">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="ef760-125">This example requires:</span></span>  
  
-   <span data-ttu-id="ef760-126">ссылки на сборки System.Drawing, System.Windows.Forms и System.Xml.</span><span class="sxs-lookup"><span data-stu-id="ef760-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="ef760-127">Сведения о выполнении сборки этого примера из командной строки для Visual Basic или Visual C#, см. в разделе [построение из командной строки](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [командной строки создания с помощью csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ef760-127">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ef760-128">Можно также сборке этого примера в Visual Studio путем вставки кода в новый проект.</span><span class="sxs-lookup"><span data-stu-id="ef760-128">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ef760-129">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="ef760-129">Robust Programming</span></span>  
 <span data-ttu-id="ef760-130">Перед попыткой обращения к свойству <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> или любому другому объекту, который может быть изменен обработчиком событий <xref:System.ComponentModel.BackgroundWorker.DoWork>, всегда проверяйте свойство <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> в обработчике событий <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>.</span><span class="sxs-lookup"><span data-stu-id="ef760-130">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef760-131">См. также</span><span class="sxs-lookup"><span data-stu-id="ef760-131">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="ef760-132">Практическое руководство. Фоновое выполнение операции</span><span class="sxs-lookup"><span data-stu-id="ef760-132">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="ef760-133">Практическое руководство. Реализация формы, в которой выполняется фоновая операция</span><span class="sxs-lookup"><span data-stu-id="ef760-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
