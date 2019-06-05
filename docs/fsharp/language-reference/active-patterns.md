---
title: Активные шаблоны
description: Узнайте, как использовать активные шаблоны для определять именованные разделы, на которые подразделяются входные данные в F# языка программирования.
ms.date: 05/16/2016
ms.openlocfilehash: 25ab255574390d3761fe788aeb413c8ee04fda2a
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690408"
---
# <a name="active-patterns"></a><span data-ttu-id="7d38f-103">Активные шаблоны</span><span class="sxs-lookup"><span data-stu-id="7d38f-103">Active Patterns</span></span>

<span data-ttu-id="7d38f-104">*Активные шаблоны* позволяют определять именованные разделы, которые подразделяются входные данные, таким образом, эти имена можно использовать в выражении шаблона так же, как и для размеченного объединения.</span><span class="sxs-lookup"><span data-stu-id="7d38f-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="7d38f-105">Активные шаблоны можно использовать для разложения данных в настраиваемом порядке для каждого раздела.</span><span class="sxs-lookup"><span data-stu-id="7d38f-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d38f-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7d38f-106">Syntax</span></span>

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a><span data-ttu-id="7d38f-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="7d38f-107">Remarks</span></span>

<span data-ttu-id="7d38f-108">В приведенном выше синтаксисе идентификаторы — это имена разделов входных данных, представленного *аргументы*, или, другими словами, имена подмножеств набора значений всех аргументов.</span><span class="sxs-lookup"><span data-stu-id="7d38f-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="7d38f-109">В определении активный шаблон может быть до семи разделов.</span><span class="sxs-lookup"><span data-stu-id="7d38f-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="7d38f-110">*Выражение* описывает форму для разложения данных.</span><span class="sxs-lookup"><span data-stu-id="7d38f-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="7d38f-111">Определение активный шаблон можно использовать для определения правила определения, какие из именованных секций значения, заданного в качестве аргументы принадлежат.</span><span class="sxs-lookup"><span data-stu-id="7d38f-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="7d38f-112">(| И |) символы называются *скобками с вертикальной чертой* и вызывается функция, созданная этим типом привязки let *active распознаватель*.</span><span class="sxs-lookup"><span data-stu-id="7d38f-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="7d38f-113">Например рассмотрим следующий активный шаблон с аргументом.</span><span class="sxs-lookup"><span data-stu-id="7d38f-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="7d38f-114">Активный шаблон можно использовать в выражении шаблона, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="7d38f-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="7d38f-115">Выходные данные этой программы выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7d38f-115">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="7d38f-116">Другой активных шаблонов используется для разложения типов данных несколькими способами, например, когда те же базовые данные имеют несколько возможных представлений.</span><span class="sxs-lookup"><span data-stu-id="7d38f-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="7d38f-117">Например `Color` объект можно разложить на представления RGB или HSB.</span><span class="sxs-lookup"><span data-stu-id="7d38f-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="7d38f-118">Выходные данные выше программы выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7d38f-118">The output of the above program is as follows:</span></span>

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="7d38f-119">В сочетании эти два способа использования активные шаблоны позволяют создавать секции и разложения данных на нужной форме и выполните соответствующие вычисления на соответствующие данные в форме, наиболее удобным для вычисления.</span><span class="sxs-lookup"><span data-stu-id="7d38f-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="7d38f-120">Результирующее выражения сопоставления шаблонов включают данные будут записываться в удобный способ, который является очень удобным для чтения, упрощая потенциально сложное ветвление и код анализа данных.</span><span class="sxs-lookup"><span data-stu-id="7d38f-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="7d38f-121">Частичные активные шаблоны</span><span class="sxs-lookup"><span data-stu-id="7d38f-121">Partial Active Patterns</span></span>

<span data-ttu-id="7d38f-122">В некоторых случаях необходимо секционировать только часть пространства входных данных.</span><span class="sxs-lookup"><span data-stu-id="7d38f-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="7d38f-123">В этом случае набор частичных шаблонов записи из которых соответствует некоторых входных данных, но не соответствует других входных данных.</span><span class="sxs-lookup"><span data-stu-id="7d38f-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="7d38f-124">Активные шаблоны, которые не всегда производят значение называются *частичные активные шаблоны*; они имеют возвращаемое значение, которое имеет тип option.</span><span class="sxs-lookup"><span data-stu-id="7d38f-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="7d38f-125">Для определения частичной активный шаблон, можно использовать подстановочный знак (\_) в конце списка шаблонов скобками с вертикальной чертой.</span><span class="sxs-lookup"><span data-stu-id="7d38f-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="7d38f-126">Следующий код иллюстрирует использование частичного активного шаблона.</span><span class="sxs-lookup"><span data-stu-id="7d38f-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="7d38f-127">Выходные данные приведенного выше примера выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7d38f-127">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="7d38f-128">При использовании частичной активные шаблоны, иногда отдельные параметры могут быть несвязанными или взаимно исключают друг друга, но не обязательно.</span><span class="sxs-lookup"><span data-stu-id="7d38f-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="7d38f-129">В следующем примере шаблон квадрата и куба шаблон связаны между собой, так как некоторые числа квадраты и кубов, например 64.</span><span class="sxs-lookup"><span data-stu-id="7d38f-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="7d38f-130">Следующая программа использует шаблона для объединения шаблоны квадрата и куба.</span><span class="sxs-lookup"><span data-stu-id="7d38f-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="7d38f-131">Распечатать все целые числа до 1000, как квадраты и кубы, а также те, которые только в кубах.</span><span class="sxs-lookup"><span data-stu-id="7d38f-131">It print out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span> 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="7d38f-132">Выходные данные выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7d38f-132">The output is as follows:</span></span>

```
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="7d38f-133">Параметризованные активные шаблоны</span><span class="sxs-lookup"><span data-stu-id="7d38f-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="7d38f-134">Активные шаблоны всегда имеют по крайней мере один аргумент для сопоставляемого элемента, но могут стать дополнительные аргументы, в этом случае имя *параметризованный активный шаблон* применяется.</span><span class="sxs-lookup"><span data-stu-id="7d38f-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="7d38f-135">Дополнительные аргументы позволяют общий шаблон, который специализации.</span><span class="sxs-lookup"><span data-stu-id="7d38f-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="7d38f-136">Например, активные шаблоны, которые используют регулярные выражения для анализа строк, часто включают регулярное выражение в качестве дополнительного параметра, как в следующем коде, который также использует частичного активный шаблон `Integer` определенный в предыдущем примере кода.</span><span class="sxs-lookup"><span data-stu-id="7d38f-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="7d38f-137">В этом примере строки, которые используют регулярные выражения для различных форматов даты, предоставленные настроить общий активный шаблон ParseRegex.</span><span class="sxs-lookup"><span data-stu-id="7d38f-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="7d38f-138">Активный шаблон целое число используется для преобразования соответствующие строки в целые числа, которые могут быть переданы в конструктор даты и времени.</span><span class="sxs-lookup"><span data-stu-id="7d38f-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="7d38f-139">Результат выполнения предыдущего кода выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7d38f-139">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="7d38f-140">Активные шаблоны не ограничиваются только выражения сопоставления шаблонов, их также можно использовать в привязках let.</span><span class="sxs-lookup"><span data-stu-id="7d38f-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="7d38f-141">Результат выполнения предыдущего кода выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7d38f-141">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="7d38f-142">См. также</span><span class="sxs-lookup"><span data-stu-id="7d38f-142">See also</span></span>

- [<span data-ttu-id="7d38f-143">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="7d38f-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="7d38f-144">Выражения match</span><span class="sxs-lookup"><span data-stu-id="7d38f-144">Match Expressions</span></span>](match-expressions.md)
