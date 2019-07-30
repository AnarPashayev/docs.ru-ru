---
title: 'Циклы: выражение for...in'
description: См. раздел F# о... в циклической конструкции выражения используется для перебора совпадений шаблона в перечислимой коллекции.
ms.date: 05/16/2016
ms.openlocfilehash: 640b0f91f6c641f3b49a99dc67abe7e4c31911ea
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630713"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="81a46-103">Циклы: выражение for...in</span><span class="sxs-lookup"><span data-stu-id="81a46-103">Loops: for...in Expression</span></span>

<span data-ttu-id="81a46-104">Эта Циклическая конструкция используется для перебора совпадений шаблона в перечислимой коллекции, такой как выражение диапазона, последовательность, список, массив или другая конструкция, поддерживающая перечисление.</span><span class="sxs-lookup"><span data-stu-id="81a46-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>

## <a name="syntax"></a><span data-ttu-id="81a46-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="81a46-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="81a46-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="81a46-106">Remarks</span></span>

<span data-ttu-id="81a46-107">Выражение можно сравнить `for each` с инструкцией в других языках .NET, так как она используется для циклического перебора значений в перечислимой коллекции. `for...in`</span><span class="sxs-lookup"><span data-stu-id="81a46-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="81a46-108">`for...in` Однако также поддерживает сопоставление шаблонов для коллекции вместо просто итерации по всей коллекции.</span><span class="sxs-lookup"><span data-stu-id="81a46-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="81a46-109">Перечислимое выражение можно указать как перечисляемую коллекцию или с помощью `..` оператора в качестве диапазона для целочисленного типа.</span><span class="sxs-lookup"><span data-stu-id="81a46-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="81a46-110">Перечислимые коллекции включают списки, последовательности, массивы, наборы, карты и т. д.</span><span class="sxs-lookup"><span data-stu-id="81a46-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="81a46-111">Можно использовать любой тип `System.Collections.IEnumerable` , реализующий реализацию.</span><span class="sxs-lookup"><span data-stu-id="81a46-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="81a46-112">При выражении диапазона с помощью `..` оператора можно использовать следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="81a46-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="81a46-113">*Запуск* .</span><span class="sxs-lookup"><span data-stu-id="81a46-113">*start* ..</span></span> <span data-ttu-id="81a46-114">*Финишер*</span><span class="sxs-lookup"><span data-stu-id="81a46-114">*finish*</span></span>

<span data-ttu-id="81a46-115">Можно также использовать версию, которая включает инкремент, который называется *Skip*, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="81a46-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="81a46-116">*Запуск* .</span><span class="sxs-lookup"><span data-stu-id="81a46-116">*start* ..</span></span> <span data-ttu-id="81a46-117">*пропустить* .</span><span class="sxs-lookup"><span data-stu-id="81a46-117">*skip* ..</span></span> <span data-ttu-id="81a46-118">*Финишер*</span><span class="sxs-lookup"><span data-stu-id="81a46-118">*finish*</span></span>

<span data-ttu-id="81a46-119">При использовании целочисленных диапазонов и простой переменной счетчика в качестве шаблона типичное поведение заключается в том, чтобы увеличить переменную счетчика на 1 при каждой итерации, но если диапазон включает значение Skip, счетчик увеличивается на значение Skip.</span><span class="sxs-lookup"><span data-stu-id="81a46-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="81a46-120">Значения, соответствующие шаблону, можно также использовать в выражении тела.</span><span class="sxs-lookup"><span data-stu-id="81a46-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="81a46-121">В следующих примерах кода показано использование `for...in` выражения.</span><span class="sxs-lookup"><span data-stu-id="81a46-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="81a46-122">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="81a46-122">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="81a46-123">В следующем примере показано, как выполнить цикл по последовательности и как использовать шаблон кортежа вместо простой переменной.</span><span class="sxs-lookup"><span data-stu-id="81a46-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="81a46-124">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="81a46-124">The output is as follows.</span></span>

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="81a46-125">В следующем примере показано, как выполнить цикл над простым целочисленным диапазоном.</span><span class="sxs-lookup"><span data-stu-id="81a46-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="81a46-126">Выходные данные функция1 выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="81a46-126">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="81a46-127">В следующем примере показано, как выполнить цикл над диапазоном с пропуском 2, который включает все остальные элементы диапазона.</span><span class="sxs-lookup"><span data-stu-id="81a46-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="81a46-128">Выходные данные `function2` имеют следующий вид.</span><span class="sxs-lookup"><span data-stu-id="81a46-128">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="81a46-129">В следующем примере показано, как использовать диапазон символов.</span><span class="sxs-lookup"><span data-stu-id="81a46-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="81a46-130">Выходные данные `function3` имеют следующий вид.</span><span class="sxs-lookup"><span data-stu-id="81a46-130">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="81a46-131">В следующем примере показано, как использовать отрицательное значение Skip для обратных итераций.</span><span class="sxs-lookup"><span data-stu-id="81a46-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="81a46-132">Выходные данные `function4` имеют следующий вид.</span><span class="sxs-lookup"><span data-stu-id="81a46-132">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="81a46-133">Начало и конец диапазона также могут быть выражениями, такими как функции, как в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="81a46-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="81a46-134">Выходные данные `function5` со следующими входными данными выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="81a46-134">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="81a46-135">В следующем примере показано использование подстановочного знака (\_), если элемент не требуется в цикле.</span><span class="sxs-lookup"><span data-stu-id="81a46-135">The next example shows the use of a wildcard character (\_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="81a46-136">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="81a46-136">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="81a46-137">`Note`Можно использовать `for...in` в выражениях последовательности и других вычислительных выражениях. в этом случае используется настроенная `for...in` версия выражения.</span><span class="sxs-lookup"><span data-stu-id="81a46-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="81a46-138">Дополнительные сведения см. в разделе [последовательности](sequences.md), [асинхронные рабочие процессы](asynchronous-workflows.md)и [вычислительные выражения](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="81a46-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81a46-139">См. также</span><span class="sxs-lookup"><span data-stu-id="81a46-139">See also</span></span>

- [<span data-ttu-id="81a46-140">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="81a46-140">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="81a46-141">Бираются `for...to`Выражение</span><span class="sxs-lookup"><span data-stu-id="81a46-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
- [<span data-ttu-id="81a46-142">Бираются `while...do`Выражение</span><span class="sxs-lookup"><span data-stu-id="81a46-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
