---
title: Автоматическое обобщение
description: Узнайте, F# как автоматически обобщает аргументы и типы функций, чтобы они работали с несколькими типами, когда это возможно.
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630622"
---
# <a name="automatic-generalization"></a><span data-ttu-id="a288e-103">Автоматическое обобщение</span><span class="sxs-lookup"><span data-stu-id="a288e-103">Automatic Generalization</span></span>

<span data-ttu-id="a288e-104">F#использует определение типа для вычисления типов функций и выражений.</span><span class="sxs-lookup"><span data-stu-id="a288e-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="a288e-105">В этом разделе описывается F# , как автоматически обобщает аргументы и типы функций, чтобы они работали с несколькими типами, когда это возможно.</span><span class="sxs-lookup"><span data-stu-id="a288e-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="a288e-106">Автоматическое обобщение</span><span class="sxs-lookup"><span data-stu-id="a288e-106">Automatic Generalization</span></span>

<span data-ttu-id="a288e-107">F# Компилятор при выполнении определения типа для функции определяет, может ли заданный параметр быть универсальным.</span><span class="sxs-lookup"><span data-stu-id="a288e-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="a288e-108">Компилятор проверяет каждый параметр и определяет, зависит ли функция от конкретного типа этого параметра.</span><span class="sxs-lookup"><span data-stu-id="a288e-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="a288e-109">Если это не так, тип выводится как универсальный.</span><span class="sxs-lookup"><span data-stu-id="a288e-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="a288e-110">В следующем примере кода показана функция, которую компилятор выводит как универсальный.</span><span class="sxs-lookup"><span data-stu-id="a288e-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="a288e-111">Тип выводится `'a -> 'a -> 'a`как.</span><span class="sxs-lookup"><span data-stu-id="a288e-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="a288e-112">Тип указывает, что это функция, принимающая два аргумента одного и того же неизвестного типа и возвращающая значение того же типа.</span><span class="sxs-lookup"><span data-stu-id="a288e-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="a288e-113">Одна из причин, по которой функция Previous может быть универсальной, заключается в том, что оператор`>`«больше» () является универсальным.</span><span class="sxs-lookup"><span data-stu-id="a288e-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="a288e-114">Оператор "больше чем" имеет сигнатуру `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="a288e-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="a288e-115">Не все операторы являются универсальными, и если код в функции использует тип параметра вместе с неуниверсальной функцией или оператором, этот тип параметра не может быть обобщенным.</span><span class="sxs-lookup"><span data-stu-id="a288e-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="a288e-116">Поскольку `max` является универсальным, его можно использовать с типами, такими `int`как `float`, и т. д., как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="a288e-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="a288e-117">Однако оба аргумента должны иметь один и тот же тип.</span><span class="sxs-lookup"><span data-stu-id="a288e-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="a288e-118">Сигнатура — `'a -> 'a -> 'a`, а `'a -> 'b -> 'a`не.</span><span class="sxs-lookup"><span data-stu-id="a288e-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="a288e-119">Поэтому следующий код выдает ошибку, так как типы не совпадают.</span><span class="sxs-lookup"><span data-stu-id="a288e-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="a288e-120">`max` Функция также работает с любым типом, поддерживающим оператор "больше чем".</span><span class="sxs-lookup"><span data-stu-id="a288e-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="a288e-121">Таким образом, его также можно использовать в строке, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="a288e-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="a288e-122">Ограничение значения</span><span class="sxs-lookup"><span data-stu-id="a288e-122">Value Restriction</span></span>

<span data-ttu-id="a288e-123">Компилятор выполняет автоматическое обобщение только для полных определений функций, имеющих явные аргументы, и для простых неизменяемых значений.</span><span class="sxs-lookup"><span data-stu-id="a288e-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="a288e-124">Это означает, что компилятор выдает ошибку при попытке компиляции кода, который не ограничен конкретным типом, но также не является обобщением.</span><span class="sxs-lookup"><span data-stu-id="a288e-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="a288e-125">Сообщение об ошибке для этой проблемы связано с этим ограничением на автоматическую обобщение значений в качестве *ограничения*по значению.</span><span class="sxs-lookup"><span data-stu-id="a288e-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="a288e-126">Как правило, ошибка ограничения значения возникает либо в том случае, если требуется, чтобы конструкция была универсальной, но компилятор имеет недостаточную информацию для его обобщения, или если непреднамеренно опустить достаточно сведений о типе в неуниверсальной конструкции.</span><span class="sxs-lookup"><span data-stu-id="a288e-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="a288e-127">Решением для ошибки ограничения значения является предоставление более явных сведений для более полного ограничения проблемы вывода типа одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="a288e-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="a288e-128">Ограничьте тип как неуниверсальный, добавив явную аннотацию типа к значению или параметру.</span><span class="sxs-lookup"><span data-stu-id="a288e-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="a288e-129">Если проблема заключается в использовании необобщенной конструкции для определения универсальной функции, например композиции функций или неполностью примененных аргументов функции, попробуйте переписать функцию как обычное определение функции.</span><span class="sxs-lookup"><span data-stu-id="a288e-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="a288e-130">Если проблема является выражением, которое является слишком сложным для обобщенного типа, сделайте его функцией, добавив дополнительный неиспользуемый параметр.</span><span class="sxs-lookup"><span data-stu-id="a288e-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="a288e-131">Добавьте явные параметры универсального типа.</span><span class="sxs-lookup"><span data-stu-id="a288e-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="a288e-132">Этот параметр редко используется.</span><span class="sxs-lookup"><span data-stu-id="a288e-132">This option is rarely used.</span></span>

- <span data-ttu-id="a288e-133">В следующих примерах кода демонстрируется каждый из этих сценариев.</span><span class="sxs-lookup"><span data-stu-id="a288e-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="a288e-134">Вариант 1. Слишком сложное выражение.</span><span class="sxs-lookup"><span data-stu-id="a288e-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="a288e-135">В этом примере список `counter` должен быть `int option ref`, но не определен как простое неизменяемое значение.</span><span class="sxs-lookup"><span data-stu-id="a288e-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="a288e-136">Вариант 2. Использование необобщенной конструкции для определения универсальной функции.</span><span class="sxs-lookup"><span data-stu-id="a288e-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="a288e-137">В этом примере конструкция не является обобщением, так как она включает в себя частичное применение аргументов функции.</span><span class="sxs-lookup"><span data-stu-id="a288e-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="a288e-138">Вариант 3. Добавление дополнительного неиспользуемого параметра.</span><span class="sxs-lookup"><span data-stu-id="a288e-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="a288e-139">Поскольку это выражение недостаточно просто для обобщения, компилятор выдает ошибку ограничения значения.</span><span class="sxs-lookup"><span data-stu-id="a288e-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="a288e-140">Вариант 4. Добавление параметров типа.</span><span class="sxs-lookup"><span data-stu-id="a288e-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="a288e-141">В последнем случае значение превращается в функцию типа, которая может использоваться для создания значений различных типов, например следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a288e-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="a288e-142">См. также</span><span class="sxs-lookup"><span data-stu-id="a288e-142">See also</span></span>

- [<span data-ttu-id="a288e-143">Вывод типа</span><span class="sxs-lookup"><span data-stu-id="a288e-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="a288e-144">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="a288e-144">Generics</span></span>](index.md)
- [<span data-ttu-id="a288e-145">Статически разрешаемые параметры типов</span><span class="sxs-lookup"><span data-stu-id="a288e-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="a288e-146">Ограничения</span><span class="sxs-lookup"><span data-stu-id="a288e-146">Constraints</span></span>](constraints.md)
