---
title: Параметры и аргументы
description: Дополнительные сведения о F# поддержка языков для определения параметров и передачи аргументов в функции, методы и свойства.
ms.date: 05/16/2016
ms.openlocfilehash: b68b3fdd14a66a7312efa5adb709adaeceaae282
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666265"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="990a8-103">Параметры и аргументы</span><span class="sxs-lookup"><span data-stu-id="990a8-103">Parameters and Arguments</span></span>

<span data-ttu-id="990a8-104">В этом разделе описывается поддержка языка определения параметров и передачи аргументов в функции, методы и свойства.</span><span class="sxs-lookup"><span data-stu-id="990a8-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="990a8-105">Он содержит сведения о передаче по ссылке и как определить и использовать методы, которые могут принимать переменное число аргументов.</span><span class="sxs-lookup"><span data-stu-id="990a8-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="990a8-106">Параметры и аргументы</span><span class="sxs-lookup"><span data-stu-id="990a8-106">Parameters and Arguments</span></span>

<span data-ttu-id="990a8-107">Термин *параметр* используется для описания имена для значений, которые требуется предоставить.</span><span class="sxs-lookup"><span data-stu-id="990a8-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="990a8-108">Термин *аргумент* используется для значения, предоставляемые для каждого параметра.</span><span class="sxs-lookup"><span data-stu-id="990a8-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="990a8-109">Параметры можно указать в кортеж или каррированные или в сочетание двух.</span><span class="sxs-lookup"><span data-stu-id="990a8-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="990a8-110">Можно передать аргументы с помощью явно указанного имени параметра.</span><span class="sxs-lookup"><span data-stu-id="990a8-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="990a8-111">Параметры методов можно указан как необязательный и задано значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="990a8-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="990a8-112">Шаблоны параметров</span><span class="sxs-lookup"><span data-stu-id="990a8-112">Parameter Patterns</span></span>

<span data-ttu-id="990a8-113">Параметры, передаваемые функции и методы, как правило, шаблоны, разделяя их пробелами.</span><span class="sxs-lookup"><span data-stu-id="990a8-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="990a8-114">Это означает, что, в принципе, один из шаблонов, описанных в [выражения сопоставления](match-expressions.md) может использоваться в списке параметров для функции или члена.</span><span class="sxs-lookup"><span data-stu-id="990a8-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="990a8-115">Методы обычно используют форме кортежа передача аргументов.</span><span class="sxs-lookup"><span data-stu-id="990a8-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="990a8-116">Это обеспечивает более четкие результаты с точки зрения других языков .NET, так как в кортеже способ аргументы передаются в методы .NET.</span><span class="sxs-lookup"><span data-stu-id="990a8-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="990a8-117">Каррированные чаще всего используется с функциями, созданными с помощью `let` привязки.</span><span class="sxs-lookup"><span data-stu-id="990a8-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="990a8-118">Следующий псевдокод отображает примеры кортежа и каррированными аргументами.</span><span class="sxs-lookup"><span data-stu-id="990a8-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="990a8-119">Комбинированные формы возможны, когда некоторые аргументы имеют кортежей, а некоторые — нет.</span><span class="sxs-lookup"><span data-stu-id="990a8-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="990a8-120">Другие шаблоны могут также использоваться в списках параметров, но если параметр шаблона не соответствует всех возможных входных значений, может существовать неполное соответствие во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="990a8-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="990a8-121">Исключение `MatchFailureException` создается, когда значение аргумента не соответствует шаблону, указанному в списке параметров.</span><span class="sxs-lookup"><span data-stu-id="990a8-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="990a8-122">Компилятор выдает предупреждение в случае, если шаблон параметров неполные совпадений.</span><span class="sxs-lookup"><span data-stu-id="990a8-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="990a8-123">Хотя бы один шаблон часто имеет смысл использовать списки параметров, и Шаблон подстановочного знака.</span><span class="sxs-lookup"><span data-stu-id="990a8-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="990a8-124">Вы можете использовать этот шаблон в списке параметров, если нужно просто игнорировать любые аргументы, передаваемые.</span><span class="sxs-lookup"><span data-stu-id="990a8-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="990a8-125">Следующий код иллюстрирует использование Шаблон подстановочного знака в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="990a8-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="990a8-126">Шаблон подстановочного знака может быть полезен всякий раз, когда нет необходимости аргументы, передаваемые в, например главную точку входа в программу, если вы не заинтересованы в аргументы командной строки, которые обычно передаются как массив строк, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="990a8-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="990a8-127">Другие шаблоны, которые иногда используются в аргументы являются `as` шаблон и идентификатор шаблоны, связанные с размеченные объединения и активные шаблоны.</span><span class="sxs-lookup"><span data-stu-id="990a8-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="990a8-128">Шаблон размеченного объединения одиночным можно использовать следующим образом.</span><span class="sxs-lookup"><span data-stu-id="990a8-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="990a8-129">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="990a8-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="990a8-130">Активные шаблоны можно использовать как параметры, например, при преобразовании аргумента в нужный формат, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="990a8-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="990a8-131">Можно использовать `as` шаблон для хранения совпадающее значение как локальное значение, как показано в следующей строке кода.</span><span class="sxs-lookup"><span data-stu-id="990a8-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="990a8-132">Другой шаблон, который иногда используется — функция, которая остается последний аргумент без имени, предоставляя в теле функции, лямбда-выражения и немедленно выполняет сопоставление шаблона неявный аргумент.</span><span class="sxs-lookup"><span data-stu-id="990a8-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="990a8-133">Примером этого является следующий код.</span><span class="sxs-lookup"><span data-stu-id="990a8-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="990a8-134">Этот код определяет функцию, которая принимает список и возвращает `true` Если список пуст, и `false` в противном случае.</span><span class="sxs-lookup"><span data-stu-id="990a8-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="990a8-135">Использование таких приемов может сделать код более трудным для чтения.</span><span class="sxs-lookup"><span data-stu-id="990a8-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="990a8-136">В некоторых случаях шаблоны, включающие неполные совпадения полезны, например, если вы знаете, что списки в программе имеют только три элемента, можно использовать шаблон, как показано ниже в списке параметров.</span><span class="sxs-lookup"><span data-stu-id="990a8-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="990a8-137">Использование шаблонов с неполным совпадением вариант лучше всего подходит для быстрого создания прототипов и других временных задач.</span><span class="sxs-lookup"><span data-stu-id="990a8-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="990a8-138">Компилятор выдаст предупреждение для такой код.</span><span class="sxs-lookup"><span data-stu-id="990a8-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="990a8-139">Такие шаблоны не может охватывать из всех возможных входных значений и следовательно, не подходят для компонента API-интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="990a8-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="990a8-140">Именованные аргументы</span><span class="sxs-lookup"><span data-stu-id="990a8-140">Named Arguments</span></span>

<span data-ttu-id="990a8-141">Аргументы методов могут указываться по позиции в список аргументов с разделителями запятыми, или они могут передаваться в метод явно указав имя, за которым следует знак равенства и значение должны быть переданы в.</span><span class="sxs-lookup"><span data-stu-id="990a8-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="990a8-142">Если указано, указав имя, они могут отображаться в порядке, отличном от используемого в объявлении.</span><span class="sxs-lookup"><span data-stu-id="990a8-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="990a8-143">Именованные аргументы может сделать код более читаемым и более адаптируемым к определенным типам изменений в API, такие как изменение порядка параметров метода.</span><span class="sxs-lookup"><span data-stu-id="990a8-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="990a8-144">Именованные аргументы можно использовать только для методов, не для `let`-связанные функции, значения функции или лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="990a8-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="990a8-145">В следующем примере кода показано использование именованных аргументов.</span><span class="sxs-lookup"><span data-stu-id="990a8-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="990a8-146">В вызове конструктора класса можно задать значения свойств класса с помощью синтаксиса, аналогичного синтаксису именованных аргументов.</span><span class="sxs-lookup"><span data-stu-id="990a8-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="990a8-147">В следующем примере этот синтаксис.</span><span class="sxs-lookup"><span data-stu-id="990a8-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="990a8-148">Дополнительные сведения см. в разделе [конструкторы (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="990a8-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="990a8-149">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="990a8-149">Optional Parameters</span></span>

<span data-ttu-id="990a8-150">Можно указать необязательный параметр для метода, используя знак вопроса перед именем параметра.</span><span class="sxs-lookup"><span data-stu-id="990a8-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="990a8-151">Необязательные параметры, интерпретируются как F# параметр типа, поэтому их можно запросить его обычным образом, что запрашиваются типы параметров, с помощью `match` выражение с `Some` и `None`.</span><span class="sxs-lookup"><span data-stu-id="990a8-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="990a8-152">Необязательные параметры можно использовать только для членов, не для функций, созданных с помощью `let` привязки.</span><span class="sxs-lookup"><span data-stu-id="990a8-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="990a8-153">Можно передать существующий необязательных значений метода по имени параметра, такие как `?arg=None` или `?arg=Some(3)` или `?arg=arg`.</span><span class="sxs-lookup"><span data-stu-id="990a8-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="990a8-154">Это может быть полезно, когда построение метод, который передает необязательные аргументы другому методу.</span><span class="sxs-lookup"><span data-stu-id="990a8-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="990a8-155">Можно также использовать функцию `defaultArg`, который устанавливает значение по умолчанию для необязательного аргумента.</span><span class="sxs-lookup"><span data-stu-id="990a8-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="990a8-156">`defaultArg` Функция принимает необязательный параметр в качестве первого аргумента и значение по умолчанию в качестве второго.</span><span class="sxs-lookup"><span data-stu-id="990a8-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="990a8-157">Следующий пример иллюстрирует использование необязательных параметров.</span><span class="sxs-lookup"><span data-stu-id="990a8-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="990a8-158">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="990a8-158">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="990a8-159">В рамках C# и взаимодействие Visual Basic, можно использовать атрибуты `[<Optional; DefaultParameterValue<(...)>]` в F#, таким образом, чтобы вызывающие объекты будут видеть аргумента как необязательные.</span><span class="sxs-lookup"><span data-stu-id="990a8-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="990a8-160">Это эквивалентно определения аргумента как необязательные в C# как в `MyMethod(int i = 3)`.</span><span class="sxs-lookup"><span data-stu-id="990a8-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="990a8-161">Можно также указать новый объект как значение параметра по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="990a8-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="990a8-162">Например `Foo` член может иметь необязательный `CancellationToken` как входной вместо:</span><span class="sxs-lookup"><span data-stu-id="990a8-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="990a8-163">Значение, заданное в качестве аргумента `DefaultParameterValue` должен соответствовать типу параметра.</span><span class="sxs-lookup"><span data-stu-id="990a8-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="990a8-164">Например ниже не допускается:</span><span class="sxs-lookup"><span data-stu-id="990a8-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="990a8-165">В этом случае компилятор создает предупреждение и будет полностью игнорировать оба атрибута.</span><span class="sxs-lookup"><span data-stu-id="990a8-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="990a8-166">Обратите внимание, что значение по умолчанию `null` должен быть аннотацией типа, как в противном случае компилятор выводит неверный тип, т. е. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span><span class="sxs-lookup"><span data-stu-id="990a8-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="990a8-167">Передача по ссылке</span><span class="sxs-lookup"><span data-stu-id="990a8-167">Passing by Reference</span></span>

<span data-ttu-id="990a8-168">Передачи F# значению по ссылке включает в себя [byrefs](byrefs.md), которые являются типами управляемый указатель.</span><span class="sxs-lookup"><span data-stu-id="990a8-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="990a8-169">Рекомендации для используемого типа выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="990a8-169">Guidance for which type to use is as follows:</span></span>

* <span data-ttu-id="990a8-170">Используйте `inref<'T>` Если вам нужно только считывать указатель.</span><span class="sxs-lookup"><span data-stu-id="990a8-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
* <span data-ttu-id="990a8-171">Используйте `outref<'T>` Если требуется только для записи указателя.</span><span class="sxs-lookup"><span data-stu-id="990a8-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
* <span data-ttu-id="990a8-172">Используйте `byref<'T>` Если вам нужно как для чтения, так и для записи к указателю.</span><span class="sxs-lookup"><span data-stu-id="990a8-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

// No need to make it mutable, since it's read-only
let x = 1
example1 &x

// Needs to be mutable, since we write to it
let mutable y = 2
example2 &y
example3 &y // Now 'y' is 3
```

<span data-ttu-id="990a8-173">Поскольку параметр является указателем, а значение является изменяемым, любые изменения значения сохраняются после выполнения функции.</span><span class="sxs-lookup"><span data-stu-id="990a8-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="990a8-174">Кортеж можно использовать как возвращаемое значение для хранения `out` параметров в методы библиотеки .NET.</span><span class="sxs-lookup"><span data-stu-id="990a8-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="990a8-175">Кроме того, вы можете рассматривать `out` параметра в виде `byref` параметра.</span><span class="sxs-lookup"><span data-stu-id="990a8-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="990a8-176">В следующем примере кода показаны оба способа.</span><span class="sxs-lookup"><span data-stu-id="990a8-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="990a8-177">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="990a8-177">Parameter Arrays</span></span>

<span data-ttu-id="990a8-178">Иногда бывает необходимо определить функцию, которая принимает произвольное число параметров различных типов.</span><span class="sxs-lookup"><span data-stu-id="990a8-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="990a8-179">Не было бы смысл создать все возможные перегруженные методы для учетной записи для всех типов, которые могут использоваться.</span><span class="sxs-lookup"><span data-stu-id="990a8-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="990a8-180">Реализации .NET обеспечивают поддержку таких методов за счет функции массивов параметров.</span><span class="sxs-lookup"><span data-stu-id="990a8-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="990a8-181">Метод, который принимает массив параметров сигнатура можно предоставить произвольное число параметров.</span><span class="sxs-lookup"><span data-stu-id="990a8-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="990a8-182">Параметры помещаются в массив.</span><span class="sxs-lookup"><span data-stu-id="990a8-182">The parameters are put into an array.</span></span> <span data-ttu-id="990a8-183">Тип элементов массива определяет типы параметров, которые могут быть переданы в функцию.</span><span class="sxs-lookup"><span data-stu-id="990a8-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="990a8-184">Если определить массив параметров с `System.Object` как тип элемента, клиентский код может передавать значения любого типа.</span><span class="sxs-lookup"><span data-stu-id="990a8-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="990a8-185">В F#, массивы параметров можно задавать только в методах.</span><span class="sxs-lookup"><span data-stu-id="990a8-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="990a8-186">Они не может использоваться в отдельные функции или функции, определенные в модулях.</span><span class="sxs-lookup"><span data-stu-id="990a8-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="990a8-187">Массив параметров определяется с помощью `ParamArray` атрибута.</span><span class="sxs-lookup"><span data-stu-id="990a8-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="990a8-188">`ParamArray` Атрибут может применяться только к последнему параметру.</span><span class="sxs-lookup"><span data-stu-id="990a8-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="990a8-189">В следующем коде показан вызов метода .NET, который принимает массив параметров и определение типа в F# , имеющий метод, принимающий массив параметров.</span><span class="sxs-lookup"><span data-stu-id="990a8-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="990a8-190">При запуске проекта, выходные данные приведенного выше кода выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="990a8-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="990a8-191">См. также</span><span class="sxs-lookup"><span data-stu-id="990a8-191">See also</span></span>

- [<span data-ttu-id="990a8-192">Члены</span><span class="sxs-lookup"><span data-stu-id="990a8-192">Members</span></span>](members/index.md)
