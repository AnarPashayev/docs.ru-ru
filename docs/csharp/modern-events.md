---
title: Обновленный шаблон событий .NET Core
description: Сведения о том, за счет чего шаблон событий .NET Core обеспечивает гибкость и обратную совместимость, а также о способах реализации безопасной обработки событий с использованием асинхронных подписчиков.
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 158295215932f54c75afdf1e96d48453434129fe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751782"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="887cb-103">Обновленный шаблон событий .NET Core</span><span class="sxs-lookup"><span data-stu-id="887cb-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="887cb-104">Назад</span><span class="sxs-lookup"><span data-stu-id="887cb-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="887cb-105">В предыдущей статье рассматривались наиболее распространенные шаблоны событий.</span><span class="sxs-lookup"><span data-stu-id="887cb-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="887cb-106">.NET Core имеет менее жесткий шаблон.</span><span class="sxs-lookup"><span data-stu-id="887cb-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="887cb-107">В этой версии определение `EventHandler<TEventArgs>` больше не имеет ограничения, указывающего на то, что `TEventArgs` должен быть классом, производным от `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="887cb-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="887cb-108">В результате повышается гибкость разработки и обеспечивается обратная совместимость.</span><span class="sxs-lookup"><span data-stu-id="887cb-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="887cb-109">Начнем с гибких возможностей.</span><span class="sxs-lookup"><span data-stu-id="887cb-109">Let's start with the flexibility.</span></span> <span data-ttu-id="887cb-110">Класс System.EventArgs представляет один метод: `MemberwiseClone()`, который создает неполную копию объекта.</span><span class="sxs-lookup"><span data-stu-id="887cb-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="887cb-111">Чтобы реализовать свою функциональность для любого класса, производного от `EventArgs`, этот метод должен использовать отражение.</span><span class="sxs-lookup"><span data-stu-id="887cb-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="887cb-112">Функциональность проще создать в определенном производном классе.</span><span class="sxs-lookup"><span data-stu-id="887cb-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="887cb-113">Это фактически означает, что наследование от System.EventArgs является ограничением, которое регламентирует разработки, но не предоставляет никаких дополнительных преимуществ.</span><span class="sxs-lookup"><span data-stu-id="887cb-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="887cb-114">На самом деле, можно изменить определения `FileFoundArgs` и `SearchDirectoryArgs` так, чтобы они не были производными от `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="887cb-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="887cb-115">Программа будет работать точно так же.</span><span class="sxs-lookup"><span data-stu-id="887cb-115">The program will work exactly the same.</span></span>

<span data-ttu-id="887cb-116">Вместо `SearchDirectoryArgs` можно также использовать структуру, внеся дополнительное изменение.</span><span class="sxs-lookup"><span data-stu-id="887cb-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

<span data-ttu-id="887cb-117">Дополнительное изменение заключается в вызове конструктора без параметров перед входом в конструктор, который инициализирует все поля.</span><span class="sxs-lookup"><span data-stu-id="887cb-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="887cb-118">Без этого согласно правилам языка C# будет выведено сообщение о получении доступа к свойствам до их назначения.</span><span class="sxs-lookup"><span data-stu-id="887cb-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="887cb-119">Не следует изменять `FileFoundArgs` с класса (ссылочный тип) на структуру (тип значения).</span><span class="sxs-lookup"><span data-stu-id="887cb-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="887cb-120">Это связано с тем, что протокол для обработки отмены требует передачи аргументов события по ссылке.</span><span class="sxs-lookup"><span data-stu-id="887cb-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="887cb-121">Если вы выполнили то же изменение, класс поиска файла никогда не сможет отслеживать изменения, внесенные подписчиками событий.</span><span class="sxs-lookup"><span data-stu-id="887cb-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="887cb-122">Для каждого подписчика будет использоваться новая копия, которая будет отличаться от той, которую обнаружил объект поиска файла.</span><span class="sxs-lookup"><span data-stu-id="887cb-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="887cb-123">Теперь давайте рассмотрим обратную совместимость этого изменения.</span><span class="sxs-lookup"><span data-stu-id="887cb-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="887cb-124">Удаление ограничения не влияет на существующий код.</span><span class="sxs-lookup"><span data-stu-id="887cb-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="887cb-125">Все имеющиеся типы аргументов событий по-прежнему являются производными от `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="887cb-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="887cb-126">Обратная совместимость является одной из основных причин, по которой они будут и далее являться производными от `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="887cb-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="887cb-127">Все существующие подписчики на события будут подписчиками на событие, следующее классическому шаблону.</span><span class="sxs-lookup"><span data-stu-id="887cb-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="887cb-128">Согласно аналогичной логике, теперь тип события аргумента не будет иметь подписчиков в существующих базах кода.</span><span class="sxs-lookup"><span data-stu-id="887cb-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="887cb-129">Новые типы событий, которые не являются производными от `System.EventArgs`, не нарушат функциональность этих баз кода.</span><span class="sxs-lookup"><span data-stu-id="887cb-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="887cb-130">События с асинхронными подписчиками</span><span class="sxs-lookup"><span data-stu-id="887cb-130">Events with Async subscribers</span></span>

<span data-ttu-id="887cb-131">У вас есть еще один, последний шаблон: как правильно написать подписчики событий, которые вызывают асинхронный код.</span><span class="sxs-lookup"><span data-stu-id="887cb-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="887cb-132">Это описано в статье, посвященной [async и await](async.md).</span><span class="sxs-lookup"><span data-stu-id="887cb-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="887cb-133">Асинхронные методы могут иметь возвращаемый тип void, однако это крайне не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="887cb-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="887cb-134">Когда код подписчика событий вызывает асинхронный метод, вам придется создать метод `async void`.</span><span class="sxs-lookup"><span data-stu-id="887cb-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="887cb-135">Это необходимо для сигнатуры обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="887cb-135">The event handler signature requires it.</span></span>

<span data-ttu-id="887cb-136">Вы должны найти правильное решение.</span><span class="sxs-lookup"><span data-stu-id="887cb-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="887cb-137">Каким-то образом необходимо создать безопасный метод `async void`.</span><span class="sxs-lookup"><span data-stu-id="887cb-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="887cb-138">Ниже приведены основные сведения о шаблоне, которым необходимо следовать.</span><span class="sxs-lookup"><span data-stu-id="887cb-138">The basics of the pattern you need to implement are below:</span></span>

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

<span data-ttu-id="887cb-139">Во-первых, обратите внимание на то, что обработчик помечен как асинхронный обработчик.</span><span class="sxs-lookup"><span data-stu-id="887cb-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="887cb-140">Поскольку он назначается типу делегата обработчика событий, он будет иметь возвращаемый тип void.</span><span class="sxs-lookup"><span data-stu-id="887cb-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="887cb-141">Это означает, что необходимо следовать шаблону, приведенному в обработчике, и не допускать создания исключений вне контекста асинхронного обработчика.</span><span class="sxs-lookup"><span data-stu-id="887cb-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="887cb-142">Поскольку он не возвращает задачу, ничто не сообщает об ошибке при переходе в состояние сбоя.</span><span class="sxs-lookup"><span data-stu-id="887cb-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="887cb-143">Поскольку метод является асинхронным, он просто не может создать исключение.</span><span class="sxs-lookup"><span data-stu-id="887cb-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="887cb-144">(Вызывающий метод продолжал выполнение, так как это `async`.) Фактическое поведение во время выполнения будет определяться по-разному для разных сред.</span><span class="sxs-lookup"><span data-stu-id="887cb-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="887cb-145">Оно может прекратить работу потока, завершить выполнение программы или оставить программу в неопределенном состоянии.</span><span class="sxs-lookup"><span data-stu-id="887cb-145">It may terminate the thread, it may terminate the program, or it may leave the program in an undetermined state.</span></span> <span data-ttu-id="887cb-146">Ничто из этого не является хорошим результатом.</span><span class="sxs-lookup"><span data-stu-id="887cb-146">None of those are good outcomes.</span></span>

<span data-ttu-id="887cb-147">Вот почему необходимо заключить оператор await для асинхронных задач в собственный блок try.</span><span class="sxs-lookup"><span data-stu-id="887cb-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="887cb-148">Если он приводит к сбою задачи, можно записать ошибку в журнал.</span><span class="sxs-lookup"><span data-stu-id="887cb-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="887cb-149">Если это ошибка, из-за которой невозможно восстановить приложение, можно быстро и правильно выйти из программы.</span><span class="sxs-lookup"><span data-stu-id="887cb-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="887cb-150">Это были основные обновления шаблона событий .NET.</span><span class="sxs-lookup"><span data-stu-id="887cb-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="887cb-151">Затем вы увидите множество примеров предыдущих версий в библиотеках, с которыми вы работаете.</span><span class="sxs-lookup"><span data-stu-id="887cb-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="887cb-152">Однако также необходимо иметь представление и о последних шаблонах.</span><span class="sxs-lookup"><span data-stu-id="887cb-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="887cb-153">В следующей статье этой серии материалов вы узнаете об использовании `delegates` и `events` в своих проектах.</span><span class="sxs-lookup"><span data-stu-id="887cb-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="887cb-154">Это относительно схожие понятия, и сведения в этой статье помогут вам принять оптимальное решение.</span><span class="sxs-lookup"><span data-stu-id="887cb-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="887cb-155">Вперед</span><span class="sxs-lookup"><span data-stu-id="887cb-155">Next</span></span>](distinguish-delegates-events.md)
