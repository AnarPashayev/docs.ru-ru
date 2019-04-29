---
title: Оператор Await (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: d9d50433e3bc24df7cda137a145ab3f0f0302a1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608676"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="f06b8-102">Оператор Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f06b8-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="f06b8-103">Можно применить `Await` оператор для операнда в асинхронный метод или лямбда-выражения для приостановки выполнения метода до завершения выполнения ожидающей задачи.</span><span class="sxs-lookup"><span data-stu-id="f06b8-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="f06b8-104">Задача представляет выполняющуюся работу.</span><span class="sxs-lookup"><span data-stu-id="f06b8-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="f06b8-105">Метод, в котором `Await` используется должен иметь [Async](../../../visual-basic/language-reference/modifiers/async.md) модификатор.</span><span class="sxs-lookup"><span data-stu-id="f06b8-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="f06b8-106">Такой метод, определенный с помощью модификатора `Async` и обычно содержащий одно или несколько выражений `Await`, называется *асинхронным методом*.</span><span class="sxs-lookup"><span data-stu-id="f06b8-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f06b8-107">Ключевые слова `Async` и `Await` появились в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f06b8-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="f06b8-108">Введение в асинхронное программирование, см. в разделе [асинхронное программирование с использованием Async и Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="f06b8-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="f06b8-109">Как правило, задача, к которому применяется `Await` оператор является возвращаемым значением из вызова метода, реализующего [асинхронную модель на основе задач](https://go.microsoft.com/fwlink/?LinkId=204847), то есть <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f06b8-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="f06b8-110">В следующем коде <xref:System.Net.Http.HttpClient> метод <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> возвращает `getContentsTask`, `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="f06b8-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="f06b8-111">Задача является обещанием создать фактический массив байтов, при завершении операции.</span><span class="sxs-lookup"><span data-stu-id="f06b8-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="f06b8-112">Оператор `Await` применяется к `getContentsTask` для приостановки выполнения в `SumPageSizesAsync` до завершения `getContentsTask`.</span><span class="sxs-lookup"><span data-stu-id="f06b8-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="f06b8-113">В то же время управление возвращается вызывающему объекту `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="f06b8-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="f06b8-114">Когда `getContentsTask` завершается, результатом выражения `Await` является массив байтов.</span><span class="sxs-lookup"><span data-stu-id="f06b8-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
```vb  
Private Async Function SumPageSizesAsync() As Task  
  
    ' To use the HttpClient type in desktop apps, you must include a using directive and add a   
    ' reference for the System.Net.Http namespace.  
    Dim client As HttpClient = New HttpClient()   
    ' . . .   
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
    Dim urlContents As Byte() = Await getContentsTask  
  
    ' Equivalently, now that you see how it works, you can write the same thing in a single line.  
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ' . . .  
End Function  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="f06b8-115">Полный пример см. в [руководстве по получению доступа к Интернету с помощью модификатора Async и оператора Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="f06b8-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="f06b8-116">Вы можете скачать этот пример в разделе [Примеры кода для разработчиков](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) на веб-сайте Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="f06b8-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="f06b8-117">Этот пример представлен в проекте AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="f06b8-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="f06b8-118">Если `Await` применяется к результату вызова метода, который возвращает `Task(Of TResult)`, тип `Await` выражение является TResult.</span><span class="sxs-lookup"><span data-stu-id="f06b8-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="f06b8-119">Если `Await` применяется к результату вызова метода, который возвращает `Task`, `Await` выражение не возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="f06b8-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="f06b8-120">В следующем примере демонстрируется это различие.</span><span class="sxs-lookup"><span data-stu-id="f06b8-120">The following example illustrates the difference.</span></span>  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 <span data-ttu-id="f06b8-121">`Await` Выражение или оператор не блокирует поток, на котором он выполняется.</span><span class="sxs-lookup"><span data-stu-id="f06b8-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="f06b8-122">Вместо этого он предписывает компилятору входа остальную часть асинхронного метода, после `Await` выражения, как продолжение ожидаемой задачи.</span><span class="sxs-lookup"><span data-stu-id="f06b8-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="f06b8-123">Затем управление возвращается в объект, вызывающий асинхронный метод.</span><span class="sxs-lookup"><span data-stu-id="f06b8-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="f06b8-124">Когда задача завершается, она вызывает свое продолжение и выполнение асинхронного метода возобновляется с того момента, где оно было остановлено.</span><span class="sxs-lookup"><span data-stu-id="f06b8-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="f06b8-125">`Await` Выражение может находиться только в теле немедленно включающего метода или лямбда-выражения, помеченный атрибутом `Async` модификатор.</span><span class="sxs-lookup"><span data-stu-id="f06b8-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="f06b8-126">Термин *Await* служит как ключевое слово только в этом контексте.</span><span class="sxs-lookup"><span data-stu-id="f06b8-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="f06b8-127">В другом месте он интерпретируется как идентификатор.</span><span class="sxs-lookup"><span data-stu-id="f06b8-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="f06b8-128">Внутри асинхронного метода или лямбда-выражение `Await` выражение не может использоваться в выражении запроса в `catch` или `finally` блока [попробуйте... CATCH... Наконец](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) инструкции в среде управления переменной выражение цикла `For` или `For Each` цикла, или в теле [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) инструкции.</span><span class="sxs-lookup"><span data-stu-id="f06b8-128">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="f06b8-129">Исключения</span><span class="sxs-lookup"><span data-stu-id="f06b8-129">Exceptions</span></span>  
 <span data-ttu-id="f06b8-130">Большинство асинхронных методов возвращает <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f06b8-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f06b8-131">Свойства возвращаемой задачи содержат сведения о ее состоянии и журнале, например завершена ли задача, вызвал ли асинхронный метод исключение или был отменен и каков окончательный результат.</span><span class="sxs-lookup"><span data-stu-id="f06b8-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="f06b8-132">Оператор `Await` обращается к этим свойствам.</span><span class="sxs-lookup"><span data-stu-id="f06b8-132">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="f06b8-133">Если вы ожидаете возвращающий задачу асинхронный метод, который вызывает исключение, то оператор `Await` повторно создает это исключение.</span><span class="sxs-lookup"><span data-stu-id="f06b8-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="f06b8-134">Если вы ожидаете возвращающий задачу асинхронный метод, отменяется, `Await` повторно вызывает оператор <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="f06b8-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="f06b8-135">Одна задача, которая находится в состоянии сбоя, может отражать несколько исключений.</span><span class="sxs-lookup"><span data-stu-id="f06b8-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="f06b8-136">Например, задача может быть результатом вызова метода <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f06b8-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f06b8-137">Если вы ожидаете такую задачу, операция await повторно вызывает только одно из исключений.</span><span class="sxs-lookup"><span data-stu-id="f06b8-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="f06b8-138">Однако невозможно предсказать, какие исключения создаются повторно.</span><span class="sxs-lookup"><span data-stu-id="f06b8-138">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="f06b8-139">Примеры обработки ошибок в асинхронных методах см. в разделе [попробуйте... CATCH... Оператор Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f06b8-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f06b8-140">Пример</span><span class="sxs-lookup"><span data-stu-id="f06b8-140">Example</span></span>  
 <span data-ttu-id="f06b8-141">В следующем примере Windows Forms демонстрируется использование `Await` в асинхронном методе `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="f06b8-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="f06b8-142">Сравните поведение этого метода с поведением `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="f06b8-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="f06b8-143">Без `Await` оператор, `WaitSynchronously` выполняется синхронно, несмотря на использование `Async` модификатор в его определении и вызов <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> в его тексте.</span><span class="sxs-lookup"><span data-stu-id="f06b8-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="f06b8-144">См. также</span><span class="sxs-lookup"><span data-stu-id="f06b8-144">See also</span></span>

- [<span data-ttu-id="f06b8-145">Асинхронное программирование с использованием ключевых слов Async и Await</span><span class="sxs-lookup"><span data-stu-id="f06b8-145">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="f06b8-146">Пошаговое руководство: Получение доступа к Интернету с помощью модификатора Async и оператора Await (C#)</span><span class="sxs-lookup"><span data-stu-id="f06b8-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="f06b8-147">Async</span><span class="sxs-lookup"><span data-stu-id="f06b8-147">Async</span></span>](../../../visual-basic/language-reference/modifiers/async.md)
