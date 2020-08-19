---
title: Гибкие типы
description: 'Узнайте, как использовать аннотацию гибкого типа F #, которая указывает, что параметр, переменная или значение имеют тип, совместимый с указанным типом.'
ms.date: 08/15/2020
ms.openlocfilehash: 44241ad082cd7f3de9e0cc6a48b8a8946e7b33d3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557754"
---
# <a name="flexible-types"></a><span data-ttu-id="f7d33-103">Гибкие типы</span><span class="sxs-lookup"><span data-stu-id="f7d33-103">Flexible Types</span></span>

<span data-ttu-id="f7d33-104">*Заметка гибкого типа* указывает, что параметр, переменная или значение имеют тип, совместимый с указанным типом, где совместимость определяется положением в объектно-ориентированной иерархии классов или интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="f7d33-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="f7d33-105">Гибкие типы полезны в частности, если автоматическое преобразование в типы выше в иерархии типов не выполняется, но все равно требуется обеспечить работу функций с любым типом в иерархии или любым типом, реализующим интерфейс.</span><span class="sxs-lookup"><span data-stu-id="f7d33-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7d33-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f7d33-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="f7d33-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="f7d33-107">Remarks</span></span>

<span data-ttu-id="f7d33-108">В предыдущем синтаксисе *тип* представляет базовый тип или интерфейс.</span><span class="sxs-lookup"><span data-stu-id="f7d33-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="f7d33-109">Гибкий тип эквивалентен универсальному типу, имеющему ограничение, которое ограничивает допустимые типы типами, совместимыми с базовым или интерфейсным типом.</span><span class="sxs-lookup"><span data-stu-id="f7d33-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="f7d33-110">То есть следующие две строки кода эквивалентны.</span><span class="sxs-lookup"><span data-stu-id="f7d33-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="f7d33-111">Гибкие типы полезны в ситуациях нескольких типов.</span><span class="sxs-lookup"><span data-stu-id="f7d33-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="f7d33-112">Например, если имеется функция более высокого порядка (функция, которая принимает функцию в качестве аргумента), часто бывает полезно, чтобы функция возвращала гибкий тип.</span><span class="sxs-lookup"><span data-stu-id="f7d33-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="f7d33-113">В следующем примере использование гибкого типа с аргументом последовательности в `iterate2` позволяет функции более высокого порядка работать с функциями, создающими последовательности, массивы, списки и любые другие перечислимые типы.</span><span class="sxs-lookup"><span data-stu-id="f7d33-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="f7d33-114">Рассмотрим следующие две функции, одна из которых возвращает последовательность, а другая — гибкий тип.</span><span class="sxs-lookup"><span data-stu-id="f7d33-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="f7d33-115">В качестве другого примера рассмотрим функцию [Seq. Concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#concat) Library:</span><span class="sxs-lookup"><span data-stu-id="f7d33-115">As another example, consider the [Seq.concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#concat) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="f7d33-116">В эту функцию можно передать любую из следующих перечислимых последовательностей:</span><span class="sxs-lookup"><span data-stu-id="f7d33-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="f7d33-117">Список списков</span><span class="sxs-lookup"><span data-stu-id="f7d33-117">A list of lists</span></span>
- <span data-ttu-id="f7d33-118">Список массивов</span><span class="sxs-lookup"><span data-stu-id="f7d33-118">A list of arrays</span></span>
- <span data-ttu-id="f7d33-119">Массив списков</span><span class="sxs-lookup"><span data-stu-id="f7d33-119">An array of lists</span></span>
- <span data-ttu-id="f7d33-120">Массив последовательностей</span><span class="sxs-lookup"><span data-stu-id="f7d33-120">An array of sequences</span></span>
- <span data-ttu-id="f7d33-121">Любое другое сочетание перечислимых последовательностей</span><span class="sxs-lookup"><span data-stu-id="f7d33-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="f7d33-122">В следующем коде используется `Seq.concat` для демонстрации сценариев, которые можно поддерживать с помощью гибких типов.</span><span class="sxs-lookup"><span data-stu-id="f7d33-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="f7d33-123">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="f7d33-123">The output is as follows.</span></span>

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="f7d33-124">В F #, как и в других объектно-ориентированных языках, существуют контексты, в которых производные типы или типы, реализующие интерфейсы, автоматически преобразуются в базовый тип или тип интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f7d33-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="f7d33-125">Эти автоматические преобразования происходят в прямых аргументах, но не в том случае, если тип находится в подчиненной положении, как часть более сложного типа, например тип возвращаемого значения типа функции, или как аргумент типа.</span><span class="sxs-lookup"><span data-stu-id="f7d33-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="f7d33-126">Таким образом, нотация гибкого типа особенно полезна, когда тип, к которому он применяется, является частью более сложного типа.</span><span class="sxs-lookup"><span data-stu-id="f7d33-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7d33-127">См. также</span><span class="sxs-lookup"><span data-stu-id="f7d33-127">See also</span></span>

- [<span data-ttu-id="f7d33-128">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="f7d33-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f7d33-129">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="f7d33-129">Generics</span></span>](./generics/index.md)
