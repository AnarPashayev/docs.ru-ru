---
title: Рекурсивные функции. Ключевое слово rec
description: 'Узнайте, как ключевое слово F # REC используется с ключевым словом let для определения рекурсивной функции.'
ms.date: 05/16/2016
ms.openlocfilehash: c9a3b7dc27f4ed86948a08b7783d7e8e8b60e57f
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2020
ms.locfileid: "87426980"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="604bf-103">Рекурсивные функции. Ключевое слово rec</span><span class="sxs-lookup"><span data-stu-id="604bf-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="604bf-104">`rec`Ключевое слово используется вместе с `let` ключевым словом для определения рекурсивной функции.</span><span class="sxs-lookup"><span data-stu-id="604bf-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="604bf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="604bf-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="604bf-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="604bf-106">Remarks</span></span>

<span data-ttu-id="604bf-107">Рекурсивные функции — функции, которые вызывают сами себя, определяются явно на языке F #.</span><span class="sxs-lookup"><span data-stu-id="604bf-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="604bf-108">Это делает определяемый идентификатор доступным в области действия функции.</span><span class="sxs-lookup"><span data-stu-id="604bf-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="604bf-109">В следующем примере кода показана рекурсивная функция, которая выполняет вычисление *n*-<sup>го</sup> числа Фибоначчи с помощью математического определения.</span><span class="sxs-lookup"><span data-stu-id="604bf-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="604bf-110">На практике код, подобный предыдущему примеру, не является идеальным, поскольку он унецессарили повторно выполняет вычисление значений, которые уже были вычислены.</span><span class="sxs-lookup"><span data-stu-id="604bf-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="604bf-111">Это обусловлено тем, что не является рекурсивным, что объясняется далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="604bf-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="604bf-112">Методы неявно являются рекурсивными в пределах типа; нет необходимости добавлять `rec` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="604bf-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="604bf-113">Привязки let в классах не являются неявно рекурсивными.</span><span class="sxs-lookup"><span data-stu-id="604bf-113">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="604bf-114">Заключительная рекурсия</span><span class="sxs-lookup"><span data-stu-id="604bf-114">Tail recursion</span></span>

<span data-ttu-id="604bf-115">Для некоторых рекурсивных функций необходимо выполнить рефакторинг более "чистого" определения до первого [рекурсивного](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span><span class="sxs-lookup"><span data-stu-id="604bf-115">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="604bf-116">Это предотвращает лишнихные перевычисления.</span><span class="sxs-lookup"><span data-stu-id="604bf-116">This prevents unecessary recomputations.</span></span> <span data-ttu-id="604bf-117">Например, предыдущий генератор чисел Фибоначчи можно перезаписывать следующим образом:</span><span class="sxs-lookup"><span data-stu-id="604bf-117">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

<span data-ttu-id="604bf-118">Это более сложная реализация.</span><span class="sxs-lookup"><span data-stu-id="604bf-118">This is a more complicated implementation.</span></span> <span data-ttu-id="604bf-119">Создание числа Фибоначчи — отличный пример алгоритма "упрощенного", который математически является чистым, но неэффективным на практике.</span><span class="sxs-lookup"><span data-stu-id="604bf-119">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="604bf-120">Некоторые аспекты делают его эффективным в F #, хотя и по-прежнему рекурсивно определяются:</span><span class="sxs-lookup"><span data-stu-id="604bf-120">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="604bf-121">Рекурсивная внутренняя функция с именем `loop` , которая является шаблоном идиоматическим F #.</span><span class="sxs-lookup"><span data-stu-id="604bf-121">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="604bf-122">Два агрегатных параметра, которые передают значения накопления рекурсивным вызовам.</span><span class="sxs-lookup"><span data-stu-id="604bf-122">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="604bf-123">Проверка значения, `n` возвращающего определенную совокупность.</span><span class="sxs-lookup"><span data-stu-id="604bf-123">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="604bf-124">Если этот пример был написан итеративно с помощью цикла, код будет выглядеть аналогично двум различным значениям, которые суммируют числа до тех пор, пока не будет выполнено определенное условие.</span><span class="sxs-lookup"><span data-stu-id="604bf-124">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="604bf-125">Причина этого состоит в том, что рекурсивный вызов не требует сохранения каких-либо значений в стеке вызовов.</span><span class="sxs-lookup"><span data-stu-id="604bf-125">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="604bf-126">Все вычисляемые промежуточные значения накапливаются с помощью входных данных внутренней функции.</span><span class="sxs-lookup"><span data-stu-id="604bf-126">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="604bf-127">Это также позволяет компилятору F # оптимизировать код так же быстро, как если бы вы написали нечто вроде `while` цикла.</span><span class="sxs-lookup"><span data-stu-id="604bf-127">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="604bf-128">Часто написание кода на F # позволяет рекурсивно обрабатывать что-то с внутренней и внешней функцией, как показано в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="604bf-128">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="604bf-129">Внутренняя функция использует хвостовую рекурсию, а внешняя функция — лучший интерфейс для вызывающих объектов.</span><span class="sxs-lookup"><span data-stu-id="604bf-129">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="604bf-130">Взаимные рекурсивные функции</span><span class="sxs-lookup"><span data-stu-id="604bf-130">Mutually Recursive Functions</span></span>

<span data-ttu-id="604bf-131">Иногда функции являются *взаимно рекурсивными*, то есть вызывают форму круга, где одна функция вызывает другую, которая, в свою очередь, вызывает первую, с любым числом вызовов между.</span><span class="sxs-lookup"><span data-stu-id="604bf-131">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="604bf-132">Необходимо определить такие функции вместе в одной `let` привязке, используя `and` ключевое слово, чтобы связать их вместе.</span><span class="sxs-lookup"><span data-stu-id="604bf-132">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="604bf-133">В следующем примере показаны две взаимно рекурсивные функции.</span><span class="sxs-lookup"><span data-stu-id="604bf-133">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="604bf-134">См. также</span><span class="sxs-lookup"><span data-stu-id="604bf-134">See also</span></span>

- [<span data-ttu-id="604bf-135">Функции</span><span class="sxs-lookup"><span data-stu-id="604bf-135">Functions</span></span>](index.md)
