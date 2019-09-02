---
title: Отмена асинхронных задач после определенного периода времени (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 110c4700d0d2afc87f9144bf258cdd4991f107f4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204338"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="da6b8-102">Отмена асинхронных задач после определенного периода времени (C#)</span><span class="sxs-lookup"><span data-stu-id="da6b8-102">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="da6b8-103">Если не нужно дожидаться, пока завершится выполнение асинхронной операции, ее можно отменить по истечении определенного периода времени с помощью метода <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da6b8-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="da6b8-104">Этот метод планирует отмену всех связанных задач, не завершенных в течение времени, установленного выражением `CancelAfter`.</span><span class="sxs-lookup"><span data-stu-id="da6b8-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="da6b8-105">В этом примере добавляется код, составленный в разделе [Отмена асинхронной задачи или списка задач (C#)](./cancel-an-async-task-or-a-list-of-tasks.md), для загрузки списка веб-сайтов и отображения длины содержимого каждого из них.</span><span class="sxs-lookup"><span data-stu-id="da6b8-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="da6b8-106">Для выполнения примеров необходимо, чтобы на компьютере были установлены Visual Studio 2012 или более поздняя версия и .NET Framework 4.5 или более поздняя версия.</span><span class="sxs-lookup"><span data-stu-id="da6b8-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="da6b8-107">Скачивание примера</span><span class="sxs-lookup"><span data-stu-id="da6b8-107">Download the example</span></span>

<span data-ttu-id="da6b8-108">Скачать полный проект Windows Presentation Foundation (WPF) можно со страницы [Пример асинхронности. Тонкая настройка приложения](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea). Затем выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="da6b8-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="da6b8-109">Распакуйте загруженный файл, а затем запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da6b8-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="da6b8-110">В строке меню выберите **Файл** > **Открыть** > **Решение или проект**.</span><span class="sxs-lookup"><span data-stu-id="da6b8-110">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="da6b8-111">В диалоговом окне **Открытие проекта** откройте папку с примером кода, который вы распаковали, а затем откройте файл решения (SLN) для AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="da6b8-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="da6b8-112">В **обозревателе решений** откройте контекстное меню проекта **CancelAfterTime** и выберите команду **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="da6b8-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="da6b8-113">Нажмите клавишу **F5**, чтобы запустить проект.</span><span class="sxs-lookup"><span data-stu-id="da6b8-113">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="da6b8-114">(Или нажмите **CTRL**+**F5**, чтобы запустить проект без отладки).</span><span class="sxs-lookup"><span data-stu-id="da6b8-114">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="da6b8-115">Выполните программу несколько раз, чтобы убедиться, что ее выходные данные могут содержать выходные данные по всем веб-сайтам, по некоторым из них или не содержать никакие данные по веб-сайтам.</span><span class="sxs-lookup"><span data-stu-id="da6b8-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="da6b8-116">Если вы не хотите скачивать проект, можете просмотреть файл MainWindow.xaml.cs в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="da6b8-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="da6b8-117">Сборка примера</span><span class="sxs-lookup"><span data-stu-id="da6b8-117">Build the example</span></span>

<span data-ttu-id="da6b8-118">Пример в этом разделе добавляется в проект для отмены списка задач, разработка которого описывается в разделе [Отмена асинхронной задачи или списка задач (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="da6b8-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="da6b8-119">В примере используется тот же пользовательский интерфейс, хотя кнопка **Отмена** не используется явно.</span><span class="sxs-lookup"><span data-stu-id="da6b8-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="da6b8-120">Для самостоятельной сборки примера шаг за шагом следуйте инструкциям в разделе "Загрузка примера", но выберите в качестве **запускаемого проекта** проект **CancelAfterOneTask**.</span><span class="sxs-lookup"><span data-stu-id="da6b8-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="da6b8-121">Добавьте изменения, приведенные в данном разделе, в этот проект.</span><span class="sxs-lookup"><span data-stu-id="da6b8-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="da6b8-122">Чтобы задать максимальный период времени, по истечении которого задачи будут отмечены как отмененные, добавьте вызов `CancelAfter` в `startButton_Click`, как показано в приведенном ниже примере.</span><span class="sxs-lookup"><span data-stu-id="da6b8-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="da6b8-123">Добавления помечены звездочками.</span><span class="sxs-lookup"><span data-stu-id="da6b8-123">The addition is marked with asterisks.</span></span>

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
    }
    catch (OperationCanceledException)
    {
        resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        resultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }

    cts = null;
}
```

 <span data-ttu-id="da6b8-124">Выполните программу несколько раз, чтобы убедиться, что ее выходные данные могут содержать выходные данные по всем веб-сайтам, по некоторым из них или не содержать никакие данные по веб-сайтам.</span><span class="sxs-lookup"><span data-stu-id="da6b8-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="da6b8-125">Следующие результаты приводятся для примера.</span><span class="sxs-lookup"><span data-stu-id="da6b8-125">The following output is a sample.</span></span>

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="da6b8-126">Полный пример</span><span class="sxs-lookup"><span data-stu-id="da6b8-126">Complete example</span></span>

<span data-ttu-id="da6b8-127">Приведенный ниже код — полный текст файла MainWindow.xaml.cs для примера.</span><span class="sxs-lookup"><span data-stu-id="da6b8-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="da6b8-128">Звездочками помечаются элементы, добавленные для этого примера.</span><span class="sxs-lookup"><span data-stu-id="da6b8-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="da6b8-129">Обратите внимание на то, что необходимо добавить ссылку для <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="da6b8-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="da6b8-130">Вы можете скачать проект из статьи [Пример асинхронности. Тонкая настройка приложения](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="da6b8-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive.
using System.Threading;

namespace CancelAfterTime
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";
            }

            cts = null;
        }

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="da6b8-131">См. также</span><span class="sxs-lookup"><span data-stu-id="da6b8-131">See also</span></span>

- [<span data-ttu-id="da6b8-132">Асинхронное программирование с использованием ключевых слов async и await (C#)</span><span class="sxs-lookup"><span data-stu-id="da6b8-132">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="da6b8-133">Пошаговое руководство: Доступ к Интернету с помощью модификатора Async и оператора Await в C#</span><span class="sxs-lookup"><span data-stu-id="da6b8-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="da6b8-134">Отмена асинхронной задачи или списка задач в C#</span><span class="sxs-lookup"><span data-stu-id="da6b8-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- <span data-ttu-id="da6b8-135">[Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) (Тонкая настройка асинхронного приложения в C#)</span><span class="sxs-lookup"><span data-stu-id="da6b8-135">[Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md)</span></span>
- [<span data-ttu-id="da6b8-136">Пример использования Async. Настройка приложения</span><span class="sxs-lookup"><span data-stu-id="da6b8-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
