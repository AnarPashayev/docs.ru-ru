---
title: Создание исключений
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 6f22878a9ddfb394f6705a335930ef2cc270895f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821272"
---
# <a name="exception-throwing"></a><span data-ttu-id="0259c-102">Создание исключений</span><span class="sxs-lookup"><span data-stu-id="0259c-102">Exception Throwing</span></span>
<span data-ttu-id="0259c-103">Рекомендации по генерации исключений, описанные в этом разделе, занимают хорошее определение значения сбоя при выполнении.</span><span class="sxs-lookup"><span data-stu-id="0259c-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="0259c-104">Сбой выполнения происходит каждый раз, когда член не может сделать то, что он был разработан (что подразумевает имя члена).</span><span class="sxs-lookup"><span data-stu-id="0259c-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="0259c-105">Например, если `OpenFile` метод не может вернуть открытый обработчик файла вызывающему объекту, это будет считаться ошибкой при выполнении.</span><span class="sxs-lookup"><span data-stu-id="0259c-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="0259c-106">Большинство разработчиков хорошо знакомы с использованием исключений для ошибок использования, таких как деление на ноль или ссылки со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="0259c-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="0259c-107">В платформе исключения используются для всех условий ошибок, включая ошибки выполнения.</span><span class="sxs-lookup"><span data-stu-id="0259c-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="0259c-108">❌ НЕ возвращайте коды ошибок.</span><span class="sxs-lookup"><span data-stu-id="0259c-108">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="0259c-109">Исключения являются основным средством формирования отчетов об ошибках в платформах.</span><span class="sxs-lookup"><span data-stu-id="0259c-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="0259c-110">✔️ сообщать об ошибках выполнения, вызывая исключения.</span><span class="sxs-lookup"><span data-stu-id="0259c-110">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="0259c-111">✔️ Рассмотрите возможность завершения процесса, вызвав `System.Environment.FailFast` (.NET Framework 2,0), а не вызывая исключение, если в коде возникает ситуация, когда она является ненадежной для дальнейшего выполнения.</span><span class="sxs-lookup"><span data-stu-id="0259c-111">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="0259c-112">❌ НЕ используйте исключения для обычного потока управления, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="0259c-112">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="0259c-113">За исключением системных сбоев и операций с потенциальными состояниями гонки, конструкторы платформы должны проектировать интерфейсы API, чтобы пользователи могли писать код, который не создает исключения.</span><span class="sxs-lookup"><span data-stu-id="0259c-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="0259c-114">Например, можно предоставить способ проверки предварительных условий перед вызовом члена, чтобы пользователи могли написать код, который не создает исключения.</span><span class="sxs-lookup"><span data-stu-id="0259c-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="0259c-115">Элемент, используемый для проверки предусловий другого элемента, часто называется тест-инженером, а член, фактически выполняющий работу, называется злодея.</span><span class="sxs-lookup"><span data-stu-id="0259c-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="0259c-116">Бывают случаи, когда шаблон Tester-Doer может иметь неприемлемые затраты на производительность.</span><span class="sxs-lookup"><span data-stu-id="0259c-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="0259c-117">В таких случаях следует учитывать так называемый шаблон Try-Parse (Дополнительные сведения см. в разделе [исключения и производительность](exceptions-and-performance.md) ).</span><span class="sxs-lookup"><span data-stu-id="0259c-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="0259c-118">✔️ Рассмотрите последствия возникновения исключений в производительности.</span><span class="sxs-lookup"><span data-stu-id="0259c-118">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="0259c-119">Скорости создания свыше 100 в секунду, скорее всего, заметно повлияют на производительность большинства приложений.</span><span class="sxs-lookup"><span data-stu-id="0259c-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="0259c-120">✔️ Задокументируйте все исключения, вызванные публичными вызываемыми членами, из-за нарушения контракта члена (а не системного сбоя) и их интерпретации в рамках контракта.</span><span class="sxs-lookup"><span data-stu-id="0259c-120">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="0259c-121">Исключения, которые являются частью контракта, не должны изменяться от одной версии к следующей (т. е. тип исключения не должен изменяться, а новые исключения не должны добавляться).</span><span class="sxs-lookup"><span data-stu-id="0259c-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="0259c-122">❌ НЕ следует иметь открытые члены, которые могут создавать или не использовать ни один из параметров.</span><span class="sxs-lookup"><span data-stu-id="0259c-122">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="0259c-123">❌ НЕ имеют открытых членов, возвращающих исключения в качестве возвращаемого значения или `out` параметра.</span><span class="sxs-lookup"><span data-stu-id="0259c-123">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="0259c-124">Возвращение исключений из общедоступных API, а не их создание, не нарушает многие преимущества отчетов об ошибках на основе исключений.</span><span class="sxs-lookup"><span data-stu-id="0259c-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="0259c-125">✔️ Рассмотрите возможность использования методов построителя исключений.</span><span class="sxs-lookup"><span data-stu-id="0259c-125">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="0259c-126">Часто возникает исключение из разных мест.</span><span class="sxs-lookup"><span data-stu-id="0259c-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="0259c-127">Чтобы избежать чрезмерного использования кода, используйте вспомогательные методы, которые создают исключения и инициализируют их свойства.</span><span class="sxs-lookup"><span data-stu-id="0259c-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="0259c-128">Кроме того, члены, которые создают исключения, не получают встроенные.</span><span class="sxs-lookup"><span data-stu-id="0259c-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="0259c-129">Перемещение инструкции Throw в построителе может привести к встраиванию элемента.</span><span class="sxs-lookup"><span data-stu-id="0259c-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="0259c-130">❌ НЕ создавайте исключения из блоков фильтра исключений.</span><span class="sxs-lookup"><span data-stu-id="0259c-130">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="0259c-131">Если фильтр исключений вызывает исключение, исключение перехватывается средой CLR, а фильтр возвращает значение false.</span><span class="sxs-lookup"><span data-stu-id="0259c-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="0259c-132">Это поведение не различается в результате применения фильтра и возвращает значение false явным образом и, следовательно, очень сложно отлаживать.</span><span class="sxs-lookup"><span data-stu-id="0259c-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="0259c-133">❌ Избегайте явной генерации исключений из блоков finally.</span><span class="sxs-lookup"><span data-stu-id="0259c-133">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="0259c-134">Неявные исключения создаются в результате вызова вызывающих методов, которые являются приемлемыми.</span><span class="sxs-lookup"><span data-stu-id="0259c-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="0259c-135">*Части © 2005, 2009 Корпорация Майкрософт. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="0259c-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="0259c-136">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="0259c-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="0259c-137">См. также статью</span><span class="sxs-lookup"><span data-stu-id="0259c-137">See also</span></span>

- [<span data-ttu-id="0259c-138">Рекомендации по проектированию платформы</span><span class="sxs-lookup"><span data-stu-id="0259c-138">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="0259c-139">Правила разработки исключений</span><span class="sxs-lookup"><span data-stu-id="0259c-139">Design Guidelines for Exceptions</span></span>](exceptions.md)
