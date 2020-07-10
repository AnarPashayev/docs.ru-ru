---
title: Кортежи
description: 'Сведения о кортеже F #, группировании неименованных, но упорядоченных значений, возможно, различных типов.'
ms.date: 05/16/2016
ms.openlocfilehash: 5d26fd5d7ec5b4939a895a6d2a6a0d7fc6c6c733
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173293"
---
# <a name="tuples"></a><span data-ttu-id="77e0d-103">Кортежи</span><span class="sxs-lookup"><span data-stu-id="77e0d-103">Tuples</span></span>

<span data-ttu-id="77e0d-104">*Кортеж* — это группирование неименованных, но упорядоченных значений, возможно, для разных типов.</span><span class="sxs-lookup"><span data-stu-id="77e0d-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="77e0d-105">Кортежи могут быть либо ссылочными типами, либо структурами.</span><span class="sxs-lookup"><span data-stu-id="77e0d-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="77e0d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77e0d-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="77e0d-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="77e0d-107">Remarks</span></span>

<span data-ttu-id="77e0d-108">Каждый *элемент* в предыдущем синтаксисе может быть любым допустимым выражением F #.</span><span class="sxs-lookup"><span data-stu-id="77e0d-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="77e0d-109">Примеры</span><span class="sxs-lookup"><span data-stu-id="77e0d-109">Examples</span></span>

<span data-ttu-id="77e0d-110">Примеры кортежей включают пары, триадные и т. д. одни и те же или разные типы.</span><span class="sxs-lookup"><span data-stu-id="77e0d-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="77e0d-111">Некоторые примеры иллюстрируются в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="77e0d-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="77e0d-112">Получение отдельных значений</span><span class="sxs-lookup"><span data-stu-id="77e0d-112">Obtaining Individual Values</span></span>

<span data-ttu-id="77e0d-113">Можно использовать сопоставление шаблонов для доступа и назначения имен для элементов кортежа, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="77e0d-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="77e0d-114">Можно также деконструировать кортеж с помощью сопоставления шаблонов вне `match` выражения с помощью `let` привязки:</span><span class="sxs-lookup"><span data-stu-id="77e0d-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="77e0d-115">Можно также обозначить совпадение кортежей в качестве входных данных для функций:</span><span class="sxs-lookup"><span data-stu-id="77e0d-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="77e0d-116">Если требуется только один элемент кортежа, можно использовать подстановочный знак (символ подчеркивания), чтобы не создавать новое имя для ненужного значения.</span><span class="sxs-lookup"><span data-stu-id="77e0d-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="77e0d-117">Копирование элементов из ссылочного кортежа в кортеж структуры также является простым:</span><span class="sxs-lookup"><span data-stu-id="77e0d-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="77e0d-118">Функции `fst` и `snd` (только ссылочные кортежи) возвращают первый и второй элементы кортежа соответственно.</span><span class="sxs-lookup"><span data-stu-id="77e0d-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="77e0d-119">Встроенная функция, которая возвращает третий элемент Triple, не существует, но ее можно легко написать следующим образом.</span><span class="sxs-lookup"><span data-stu-id="77e0d-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="77e0d-120">Как правило, лучше использовать сопоставление шаблонов для доступа к отдельным элементам кортежа.</span><span class="sxs-lookup"><span data-stu-id="77e0d-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="77e0d-121">Использование кортежей</span><span class="sxs-lookup"><span data-stu-id="77e0d-121">Using Tuples</span></span>

<span data-ttu-id="77e0d-122">Кортежи предоставляют удобный способ возвращения нескольких значений из функции, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="77e0d-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="77e0d-123">Этот пример выполняет деление целых чисел и возвращает округленный результат операции как первый элемент пары кортежей и остаток как второй элемент пары.</span><span class="sxs-lookup"><span data-stu-id="77e0d-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="77e0d-124">Кортежи также можно использовать в качестве аргументов функции, если нужно избежать неявного карринг аргументов функции, который подразумевается обычным синтаксисом функции.</span><span class="sxs-lookup"><span data-stu-id="77e0d-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="77e0d-125">Обычный синтаксис для определения функции `let sum a b = a + b` позволяет определить функцию, которая является частичным приложением первого аргумента функции, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="77e0d-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="77e0d-126">Использование кортежа в качестве параметра отключает карринг.</span><span class="sxs-lookup"><span data-stu-id="77e0d-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="77e0d-127">Дополнительные сведения см. в разделе "частичное применение аргументов" в [функциях](./functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="77e0d-127">For more information, see "Partial Application of Arguments" in [Functions](./functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="77e0d-128">Имена типов кортежей</span><span class="sxs-lookup"><span data-stu-id="77e0d-128">Names of Tuple Types</span></span>

<span data-ttu-id="77e0d-129">При записи имени типа, который является кортежем, `*` для разделения элементов используется символ.</span><span class="sxs-lookup"><span data-stu-id="77e0d-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="77e0d-130">Для кортежа, состоящего из `int` ,, `float` и `string` , например `(10, 10.0, "ten")` , тип будет записан следующим образом.</span><span class="sxs-lookup"><span data-stu-id="77e0d-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="77e0d-131">Взаимодействие с кортежами C#</span><span class="sxs-lookup"><span data-stu-id="77e0d-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="77e0d-132">В C# 7,0 появились кортежи для языка.</span><span class="sxs-lookup"><span data-stu-id="77e0d-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="77e0d-133">Кортежи в C# — это структуры, которые эквивалентны кортежам структуры в F #.</span><span class="sxs-lookup"><span data-stu-id="77e0d-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="77e0d-134">При необходимости взаимодействия с C# необходимо использовать кортежи структуры.</span><span class="sxs-lookup"><span data-stu-id="77e0d-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="77e0d-135">Это легко сделать.</span><span class="sxs-lookup"><span data-stu-id="77e0d-135">This is easy to do.</span></span>  <span data-ttu-id="77e0d-136">Например, представьте, что необходимо передать кортеж в класс C#, а затем использовать его результат, который также является кортежем:</span><span class="sxs-lookup"><span data-stu-id="77e0d-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="77e0d-137">В коде F # можно передать кортеж структуры в качестве параметра и использовать результат в качестве кортежа структуры.</span><span class="sxs-lookup"><span data-stu-id="77e0d-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="77e0d-138">Преобразование между кортежами ссылок и Кортежями структуры</span><span class="sxs-lookup"><span data-stu-id="77e0d-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="77e0d-139">Поскольку эталонные кортежи и кортежи структур имеют совершенно другое базовое представление, они не могут быть неявно преобразованы.</span><span class="sxs-lookup"><span data-stu-id="77e0d-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="77e0d-140">Таким образом, код, подобный приведенному ниже, не будет компилироваться:</span><span class="sxs-lookup"><span data-stu-id="77e0d-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="77e0d-141">Необходимо зашаблонировать совпадение в одном кортеже и создать другой с составляющими частями.</span><span class="sxs-lookup"><span data-stu-id="77e0d-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="77e0d-142">Пример.</span><span class="sxs-lookup"><span data-stu-id="77e0d-142">For example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="77e0d-143">Скомпилированная форма ссылочных кортежей</span><span class="sxs-lookup"><span data-stu-id="77e0d-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="77e0d-144">В этом разделе объясняется форма кортежей при их компиляции.</span><span class="sxs-lookup"><span data-stu-id="77e0d-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="77e0d-145">Информация здесь не требуется для чтения, если не используется целевая версия .NET Framework 3,5 или ниже.</span><span class="sxs-lookup"><span data-stu-id="77e0d-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="77e0d-146">Кортежи компилируются в объекты одного из нескольких универсальных типов с именами, `System.Tuple` которые перегружены по арности или количество параметров типа.</span><span class="sxs-lookup"><span data-stu-id="77e0d-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="77e0d-147">Типы кортежей отображаются в этой форме при их просмотре на другом языке, например C# или Visual Basic, или при использовании средства, не осведомленного о конструкциях F #.</span><span class="sxs-lookup"><span data-stu-id="77e0d-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="77e0d-148">`Tuple`Типы были введены в .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="77e0d-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="77e0d-149">При использовании более ранней версии .NET Framework компилятор использует версии [System. кортежа](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) из версии 2,0 основной библиотеки F #.</span><span class="sxs-lookup"><span data-stu-id="77e0d-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="77e0d-150">Типы в этой библиотеке используются только для приложений, предназначенных для версий 2,0, 3,0 и 3,5 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77e0d-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="77e0d-151">Пересылка типов используется для обеспечения совместимости двоичных компонентов между .NET Framework 2,0 и .NET Framework 4-компонентами F #.</span><span class="sxs-lookup"><span data-stu-id="77e0d-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="77e0d-152">Скомпилированная форма кортежей структур</span><span class="sxs-lookup"><span data-stu-id="77e0d-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="77e0d-153">Кортежи структуры (например, `struct (x, y)` ) являются фундаментально отличающимися от ссылочных кортежей.</span><span class="sxs-lookup"><span data-stu-id="77e0d-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="77e0d-154">Они компилируются в <xref:System.ValueTuple> тип, перегружается по арности или в число параметров типа.</span><span class="sxs-lookup"><span data-stu-id="77e0d-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="77e0d-155">Они эквивалентны [кортежам C# 7,0](../../csharp/language-reference/builtin-types/value-tuples.md) и [Visual Basicным кортежам 2017](../../visual-basic/programming-guide/language-features/data-types/tuples.md)и взаимодействуют с двунаправленным письмом.</span><span class="sxs-lookup"><span data-stu-id="77e0d-155">They are equivalent to [C# 7.0 Tuples](../../csharp/language-reference/builtin-types/value-tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="77e0d-156">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="77e0d-156">See also</span></span>

- [<span data-ttu-id="77e0d-157">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="77e0d-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="77e0d-158">Типы языка F#</span><span class="sxs-lookup"><span data-stu-id="77e0d-158">F# Types</span></span>](fsharp-types.md)
