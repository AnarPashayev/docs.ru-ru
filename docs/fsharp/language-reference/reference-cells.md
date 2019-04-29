---
title: Ссылочные ячейки
description: Узнайте, как F# ссылочные ячейки являются места хранения, которые позволяют создавать изменяющиеся значения с семантикой ссылок.
ms.date: 05/16/2016
ms.openlocfilehash: e4fcd3cf1abcf5f5e3b4d5439c9215b79ff8dbcd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795409"
---
# <a name="reference-cells"></a><span data-ttu-id="09d5f-103">Ссылочные ячейки</span><span class="sxs-lookup"><span data-stu-id="09d5f-103">Reference Cells</span></span>

<span data-ttu-id="09d5f-104">*Ссылочные ячейки* — это места хранения, которые позволяют создавать изменяющиеся значения с семантикой ссылок.</span><span class="sxs-lookup"><span data-stu-id="09d5f-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="09d5f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="09d5f-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="09d5f-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="09d5f-106">Remarks</span></span>

<span data-ttu-id="09d5f-107">Для создания новой ссылочной ячейки, инкапсулирующей значение, перед значением ставится оператор `ref`.</span><span class="sxs-lookup"><span data-stu-id="09d5f-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="09d5f-108">Базовое значение затем можно изменить, так как оно является изменяемым.</span><span class="sxs-lookup"><span data-stu-id="09d5f-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="09d5f-109">Ссылочная ячейка содержит фактическое значение; это не просто адрес.</span><span class="sxs-lookup"><span data-stu-id="09d5f-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="09d5f-110">При создании ссылочной ячейки с помощью оператора `ref` создается копия базового значения в качестве инкапсулированного изменяемого значения.</span><span class="sxs-lookup"><span data-stu-id="09d5f-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="09d5f-111">Разыменовать ссылочную ячейку можно с помощью оператора `!` (восклицательного знака).</span><span class="sxs-lookup"><span data-stu-id="09d5f-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="09d5f-112">Следующий пример кода иллюстрирует объявление и использование ссылочных ячеек.</span><span class="sxs-lookup"><span data-stu-id="09d5f-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="09d5f-113">В результате получается `50`.</span><span class="sxs-lookup"><span data-stu-id="09d5f-113">The output is `50`.</span></span>

<span data-ttu-id="09d5f-114">Ссылочные ячейки являются экземплярами универсального типа записей `Ref`, который объявляется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="09d5f-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="09d5f-115">Тип `'a ref` является синонимом `Ref<'a>`.</span><span class="sxs-lookup"><span data-stu-id="09d5f-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="09d5f-116">В интегрированной среде разработки в компиляторе и в IntelliSense отображается первое обозначение данного типа, однако базовым определением является второе.</span><span class="sxs-lookup"><span data-stu-id="09d5f-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="09d5f-117">Оператор `ref` создает новую ссылочную ячейку.</span><span class="sxs-lookup"><span data-stu-id="09d5f-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="09d5f-118">Следующий код представляет собой объявление оператора `ref`.</span><span class="sxs-lookup"><span data-stu-id="09d5f-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="09d5f-119">В следующей таблице перечислены возможности, доступные для ссылочной ячейки.</span><span class="sxs-lookup"><span data-stu-id="09d5f-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="09d5f-120">Оператор, член или поле</span><span class="sxs-lookup"><span data-stu-id="09d5f-120">Operator, member, or field</span></span>|<span data-ttu-id="09d5f-121">Описание</span><span class="sxs-lookup"><span data-stu-id="09d5f-121">Description</span></span>|<span data-ttu-id="09d5f-122">Тип</span><span class="sxs-lookup"><span data-stu-id="09d5f-122">Type</span></span>|<span data-ttu-id="09d5f-123">Определение</span><span class="sxs-lookup"><span data-stu-id="09d5f-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="09d5f-124">`!` (оператор разыменования)</span><span class="sxs-lookup"><span data-stu-id="09d5f-124">`!` (dereference operator)</span></span>|<span data-ttu-id="09d5f-125">Возвращает базовое значение.</span><span class="sxs-lookup"><span data-stu-id="09d5f-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="09d5f-126">`:=` (оператор присваивания)</span><span class="sxs-lookup"><span data-stu-id="09d5f-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="09d5f-127">Изменяет базовое значение.</span><span class="sxs-lookup"><span data-stu-id="09d5f-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="09d5f-128">`ref` (оператор)</span><span class="sxs-lookup"><span data-stu-id="09d5f-128">`ref` (operator)</span></span>|<span data-ttu-id="09d5f-129">Инкапсулирует значение в новую ссылочную ячейку.</span><span class="sxs-lookup"><span data-stu-id="09d5f-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="09d5f-130">`Value` (свойство)</span><span class="sxs-lookup"><span data-stu-id="09d5f-130">`Value` (property)</span></span>|<span data-ttu-id="09d5f-131">Получает или задает базовое значение.</span><span class="sxs-lookup"><span data-stu-id="09d5f-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="09d5f-132">`contents` (поле записи)</span><span class="sxs-lookup"><span data-stu-id="09d5f-132">`contents` (record field)</span></span>|<span data-ttu-id="09d5f-133">Получает или задает базовое значение.</span><span class="sxs-lookup"><span data-stu-id="09d5f-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|

<span data-ttu-id="09d5f-134">Существует несколько способов доступа к базовому значению.</span><span class="sxs-lookup"><span data-stu-id="09d5f-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="09d5f-135">Значение, возвращаемое оператором разыменования (`!`), не является присваиваемым значением.</span><span class="sxs-lookup"><span data-stu-id="09d5f-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="09d5f-136">Следовательно, при изменении базового значения нужно вместо этого оператора использовать оператор присваивания (`:=`).</span><span class="sxs-lookup"><span data-stu-id="09d5f-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="09d5f-137">И свойство `Value`, и поле `contents` являются присваиваемыми значениями.</span><span class="sxs-lookup"><span data-stu-id="09d5f-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="09d5f-138">Следовательно, их можно использовать для доступа к базовому значению или его изменения, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="09d5f-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="09d5f-139">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="09d5f-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="09d5f-140">Поле `contents` предусмотрено для совместимости с другими версиями языка ML, и его наличие приводит к выводу предупреждения в процессе компиляции.</span><span class="sxs-lookup"><span data-stu-id="09d5f-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="09d5f-141">Для отключения этого предупреждения используется параметр компилятора `--mlcompatibility`.</span><span class="sxs-lookup"><span data-stu-id="09d5f-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="09d5f-142">Дополнительные сведения см. в разделе [Параметры компилятора](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="09d5f-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="09d5f-143">C#Программисты должны знать, что `ref` в C# не то же самое `ref` в F#.</span><span class="sxs-lookup"><span data-stu-id="09d5f-143">C# programmers should know that `ref` in C# is not the same thing as `ref` in F#.</span></span> <span data-ttu-id="09d5f-144">Эквивалент конструкции в F# являются [byrefs](byrefs.md), которые являются отношения из ссылочные ячейки.</span><span class="sxs-lookup"><span data-stu-id="09d5f-144">The equivalent constructs in F# are [byrefs](byrefs.md), which are a different concept from reference cells.</span></span>

<span data-ttu-id="09d5f-145">Значения с пометкой `mutable`может быть автоматически повышена до `'a ref` Если отслеживается замыкание; см. в разделе [значения](values/index.md).</span><span class="sxs-lookup"><span data-stu-id="09d5f-145">Values marked as `mutable`may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="09d5f-146">См. также</span><span class="sxs-lookup"><span data-stu-id="09d5f-146">See also</span></span>

- [<span data-ttu-id="09d5f-147">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="09d5f-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="09d5f-148">Параметры и аргументы</span><span class="sxs-lookup"><span data-stu-id="09d5f-148">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="09d5f-149">Справочник символов и операторов</span><span class="sxs-lookup"><span data-stu-id="09d5f-149">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
- [<span data-ttu-id="09d5f-150">Значения</span><span class="sxs-lookup"><span data-stu-id="09d5f-150">Values</span></span>](values/index.md)
