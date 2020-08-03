---
title: Использование метода Async для доступа к файлам (C#)
description: Узнайте, как использовать функцию Async для доступа к файлам в C#. Можно вызывать асинхронные методы, не прибегая к использованию обратных вызовов или разделению кода между методами.
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: eb67bd408fe37b99e6c5ffdc2550e8f95110d7eb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925128"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="39a12-104">Использование метода Async для доступа к файлам (C#)</span><span class="sxs-lookup"><span data-stu-id="39a12-104">Using Async for File Access (C#)</span></span>
<span data-ttu-id="39a12-105">Для доступа к файлам можно использовать функцию Async.</span><span class="sxs-lookup"><span data-stu-id="39a12-105">You can use the async feature to access files.</span></span> <span data-ttu-id="39a12-106">При использовании функции Async вы можете вызывать асинхронные методы без использования обратных вызовов или разделения вашего кода на множество методов или лямбда-выражений.</span><span class="sxs-lookup"><span data-stu-id="39a12-106">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="39a12-107">Для выполнения последовательного кода асинхронно просто вызовите асинхронный метод вместо синхронного метода и добавьте несколько ключевых слов в код.</span><span class="sxs-lookup"><span data-stu-id="39a12-107">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="39a12-108">Можно рассмотреть следующие причины для добавления асинхронности для вызовов для доступа к файлам.</span><span class="sxs-lookup"><span data-stu-id="39a12-108">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="39a12-109">Асинхронность делает приложения пользовательского интерфейса более отзывчивыми, потому что поток пользовательского интерфейса, который запускает операцию, может продолжать выполнять и другую работу.</span><span class="sxs-lookup"><span data-stu-id="39a12-109">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="39a12-110">Если поток пользовательского интерфейса должен выполнять код, который занимает много времени (например, более 50 миллисекунд), пользовательский интерфейс можно приостановить до тех пор, пока не будет завершен ввод-вывод, и затем пользовательский интерфейс сможет снова обрабатывать ввод с клавиатуры, мыши и другие события.</span><span class="sxs-lookup"><span data-stu-id="39a12-110">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="39a12-111">Асинхронность улучшает масштабируемость ASP.NET и других серверных приложений за счет уменьшения необходимости использования потоков.</span><span class="sxs-lookup"><span data-stu-id="39a12-111">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="39a12-112">Если приложение использует выделенный поток на ответ и тысяча запросов приходит одновременно, тысяча потоков не потребуется.</span><span class="sxs-lookup"><span data-stu-id="39a12-112">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="39a12-113">Асинхронные операции часто не нуждаются в пользовании потоком во время ожидания.</span><span class="sxs-lookup"><span data-stu-id="39a12-113">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="39a12-114">Они пользуются существующим потоком завершения ввода-вывода короткое время в конце.</span><span class="sxs-lookup"><span data-stu-id="39a12-114">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="39a12-115">Задержка операции доступа к файлу может быть очень низкой при текущих условиях, но может значительно увеличиться в будущем.</span><span class="sxs-lookup"><span data-stu-id="39a12-115">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="39a12-116">Например, файл может быть перемещен на сервер через Интернет.</span><span class="sxs-lookup"><span data-stu-id="39a12-116">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="39a12-117">Добавленные издержки при использовании функции Async являются малыми.</span><span class="sxs-lookup"><span data-stu-id="39a12-117">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="39a12-118">Асинхронные задачи могут легко выполняться параллельно.</span><span class="sxs-lookup"><span data-stu-id="39a12-118">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="39a12-119">Выполнение примеров</span><span class="sxs-lookup"><span data-stu-id="39a12-119">Running the Examples</span></span>  
 <span data-ttu-id="39a12-120">Чтобы выполнить примеры в этом разделе, вы можете создать **приложение WPF** или **приложение Windows Forms**, а затем добавить **кнопку**.</span><span class="sxs-lookup"><span data-stu-id="39a12-120">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="39a12-121">В событии `Click` кнопки добавьте вызов к первому методу в каждом примере.</span><span class="sxs-lookup"><span data-stu-id="39a12-121">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="39a12-122">В следующие примеры добавьте указанные ниже директивы `using`.</span><span class="sxs-lookup"><span data-stu-id="39a12-122">In the following examples, include the following `using` directives.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="39a12-123">Использование класса FileStream</span><span class="sxs-lookup"><span data-stu-id="39a12-123">Use of the FileStream Class</span></span>  
 <span data-ttu-id="39a12-124">В приведенных в этой статье примерах используется класс <xref:System.IO.FileStream>, содержащий параметр, который вызывает асинхронный ввод-вывод на уровне операционной системы.</span><span class="sxs-lookup"><span data-stu-id="39a12-124">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="39a12-125">С помощью этого параметра можно избежать блокирования пула потоков во многих случаях.</span><span class="sxs-lookup"><span data-stu-id="39a12-125">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="39a12-126">Чтобы включить этот параметр, необходимо добавить в вызов конструктора аргумент `useAsync=true` или `options=FileOptions.Asynchronous`.</span><span class="sxs-lookup"><span data-stu-id="39a12-126">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="39a12-127">Этот параметр нельзя использовать с классами <xref:System.IO.StreamReader> и <xref:System.IO.StreamWriter>, если вы открываете их напрямую (указав путь к файлу).</span><span class="sxs-lookup"><span data-stu-id="39a12-127">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="39a12-128">При этом параметр можно использовать, если им предоставлен <xref:System.IO.Stream>, открытый классом <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="39a12-128">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="39a12-129">Обратите внимание, что асинхронные вызовы выполняются быстрее в приложениях пользовательского интерфейса, даже если поток в пуле потоков блокирован, поскольку поток пользовательского интерфейса не блокирован во время ожидания.</span><span class="sxs-lookup"><span data-stu-id="39a12-129">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="39a12-130">Запись текста</span><span class="sxs-lookup"><span data-stu-id="39a12-130">Writing Text</span></span>  
 <span data-ttu-id="39a12-131">Следующие примеры записывают текст в файл.</span><span class="sxs-lookup"><span data-stu-id="39a12-131">The following example writes text to a file.</span></span> <span data-ttu-id="39a12-132">На каждой точке await происходит немедленный выход из метода.</span><span class="sxs-lookup"><span data-stu-id="39a12-132">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="39a12-133">После завершения файлового ввода-вывода метод возобновляет работу с пункта, следующего за await.</span><span class="sxs-lookup"><span data-stu-id="39a12-133">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="39a12-134">Обратите внимание, что модификатор async в определении методов требует наличия await в теле метода.</span><span class="sxs-lookup"><span data-stu-id="39a12-134">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async Task ProcessWriteAsync()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 <span data-ttu-id="39a12-135">Первоначальная строка с оператором `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);` является сокращенной формой записи двух следующих операторов:</span><span class="sxs-lookup"><span data-stu-id="39a12-135">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="39a12-136">Первый оператор возвращает задачу и вызывает запуск обработки файла.</span><span class="sxs-lookup"><span data-stu-id="39a12-136">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="39a12-137">Вторая строка с await немедленно оставляет метод и возвращается в другую задачу.</span><span class="sxs-lookup"><span data-stu-id="39a12-137">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="39a12-138">При окончании обработки файла выполнение возвращается в точку выполнения, которая следует за await.</span><span class="sxs-lookup"><span data-stu-id="39a12-138">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="39a12-139">Дополнительные сведения см. в разделе [Поток управления в асинхронных программах (C#)](./control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="39a12-139">For more information, see  [Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="39a12-140">Чтение текста</span><span class="sxs-lookup"><span data-stu-id="39a12-140">Reading Text</span></span>  
 <span data-ttu-id="39a12-141">Следующий пример считывает текст из файла.</span><span class="sxs-lookup"><span data-stu-id="39a12-141">The following example reads text from a file.</span></span> <span data-ttu-id="39a12-142">Текст добавляется в буфер обмена, а затем, в данном случае, помещается в <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="39a12-142">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="39a12-143">В отличие от предыдущего примера await выдаёт в результате значение.</span><span class="sxs-lookup"><span data-stu-id="39a12-143">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="39a12-144">Метод <xref:System.IO.Stream.ReadAsync%2A> возвращает <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>, поэтому по завершении операции оценка await выдает значение `Int32` (`numRead`).</span><span class="sxs-lookup"><span data-stu-id="39a12-144">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="39a12-145">Дополнительные сведения см. в разделе [Асинхронные типы возвращаемых значений (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="39a12-145">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>  
  
```csharp  
public async Task ProcessReadAsync()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="39a12-146">Параллельный асинхронный ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="39a12-146">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="39a12-147">В следующем примере показана параллельная обработка при записи 10 текстовых файлов.</span><span class="sxs-lookup"><span data-stu-id="39a12-147">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="39a12-148">Для каждого файла метод <xref:System.IO.Stream.WriteAsync%2A> возвращает задачу, которая затем добавляется в список задач.</span><span class="sxs-lookup"><span data-stu-id="39a12-148">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="39a12-149">Оператор `await Task.WhenAll(tasks);` существует и возобновляется в методе, как только завершается обработка файла для всех задач.</span><span class="sxs-lookup"><span data-stu-id="39a12-149">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="39a12-150">Пример закрывает все экземпляры <xref:System.IO.FileStream> в блоке `finally` после завершения всех задач.</span><span class="sxs-lookup"><span data-stu-id="39a12-150">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="39a12-151">Если бы вместо этого каждый `FileStream` был бы создан в операторе `using`, то `FileStream` можно было бы удалить до завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="39a12-151">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="39a12-152">Обратите внимание, что любое увеличение производительности зависит почти полностью от параллельной, а не асинхронной обработки.</span><span class="sxs-lookup"><span data-stu-id="39a12-152">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="39a12-153">Преимущества асинхронности в том, что она не привязана к количеству потоков и не связана с потоком пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="39a12-153">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async Task ProcessWriteMultAsync()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="39a12-154">При использовании методов <xref:System.IO.Stream.WriteAsync%2A> и <xref:System.IO.Stream.ReadAsync%2A> можно указать <xref:System.Threading.CancellationToken>, который позволяет отменить операцию в середине потока.</span><span class="sxs-lookup"><span data-stu-id="39a12-154">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="39a12-155">Дополнительные сведения см. в разделах [Настройка асинхронного приложения (C#)](./fine-tuning-your-async-application.md) и [Отмена в управляемых потоках](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="39a12-155">For more information, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a12-156">См. также</span><span class="sxs-lookup"><span data-stu-id="39a12-156">See also</span></span>

- [<span data-ttu-id="39a12-157">Асинхронное программирование с использованием ключевых слов async и await (C#)</span><span class="sxs-lookup"><span data-stu-id="39a12-157">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- <span data-ttu-id="39a12-158">[Async Return Types (C#)](./async-return-types.md) (Типы возвращаемых значений асинхронных операций в C#)</span><span class="sxs-lookup"><span data-stu-id="39a12-158">[Async Return Types (C#)](./async-return-types.md)</span></span>
- <span data-ttu-id="39a12-159">[Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md) (Поток управления в асинхронных программах C#)</span><span class="sxs-lookup"><span data-stu-id="39a12-159">[Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md)</span></span>
