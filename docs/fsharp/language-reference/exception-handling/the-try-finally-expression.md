---
title: 'Исключения: Выражение try...finally'
description: Узнайте, как F# "try... finally" выражение позволяет выполнять код очистки, даже если блок кода вызывает исключение.
ms.date: 05/16/2016
ms.openlocfilehash: 24613185818c8ea30b27dcf639b22af320c4b401
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772701"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="b2873-103">Исключения: Выражение try...finally</span><span class="sxs-lookup"><span data-stu-id="b2873-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="b2873-104">`try...finally` Выражение позволяет выполнять код очистки, даже если блок кода вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="b2873-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2873-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b2873-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="b2873-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="b2873-106">Remarks</span></span>

<span data-ttu-id="b2873-107">`try...finally` Выражение можно использовать для выполнения кода в *expression2* приведенный выше синтаксис, независимо от того, создается ли исключение во время выполнения *expression1*.</span><span class="sxs-lookup"><span data-stu-id="b2873-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="b2873-108">Тип *expression2* не влияет на значение всего выражения; Если исключение не возникло, возвращаемым типом является последнее значение в *expression1*.</span><span class="sxs-lookup"><span data-stu-id="b2873-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="b2873-109">При возникновении исключения, значение не возвращается, и поток управления переходит Далее соответствующего обработчика исключений вверх по стеку вызовов.</span><span class="sxs-lookup"><span data-stu-id="b2873-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="b2873-110">Если не обнаруживается, выполнение программы прекращается.</span><span class="sxs-lookup"><span data-stu-id="b2873-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="b2873-111">Прежде чем выполняется код в соответствующий обработчик или завершении работы программы, код в `finally` исполняется ветвь.</span><span class="sxs-lookup"><span data-stu-id="b2873-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="b2873-112">В следующем коде показано использование `try...finally` выражение.</span><span class="sxs-lookup"><span data-stu-id="b2873-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="b2873-113">Выходные данные в консоль выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b2873-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="b2873-114">Как видно из выходных данных потока было закрыто до внешнее исключение было обработано и файл `test.txt` текстом `test1`, который указывает, что буферы были записаны на диск и записываются на диск, несмотря на то, что исключения передаются Управление внешнему обработчику исключений.</span><span class="sxs-lookup"><span data-stu-id="b2873-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="b2873-115">Обратите внимание, что `try...with` конструкция — это отдельные конструкции `try...finally` построения.</span><span class="sxs-lookup"><span data-stu-id="b2873-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="b2873-116">Таким образом Если код требует оба `with` блока и `finally` блока, вам нужно вложить две конструкции, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="b2873-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="b2873-117">В контексте выражения вычисления, в том числе выражения последовательности и асинхронные рабочие потоки, **try... finally** выражения могут иметь собственную реализацию.</span><span class="sxs-lookup"><span data-stu-id="b2873-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="b2873-118">Дополнительные сведения см. в разделе [выражения вычисления](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b2873-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2873-119">См. также</span><span class="sxs-lookup"><span data-stu-id="b2873-119">See also</span></span>

- [<span data-ttu-id="b2873-120">Обработка исключений</span><span class="sxs-lookup"><span data-stu-id="b2873-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="b2873-121">Исключения. `try...with` Выражение</span><span class="sxs-lookup"><span data-stu-id="b2873-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)