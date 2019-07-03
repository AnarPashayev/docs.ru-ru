---
title: Справочник по C#. Тип dynamic
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: c8748f1869e8e2d5246910fac0100a6c70790579
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306636"
---
# <a name="dynamic-c-reference"></a><span data-ttu-id="d735b-102">dynamic (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="d735b-102">dynamic (C# Reference)</span></span>

<span data-ttu-id="d735b-103">Тип `dynamic` включает операции, в которых он применяется для обхода проверки типов во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="d735b-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="d735b-104">Такие операции разрешаются во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d735b-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="d735b-105">Тип `dynamic` упрощает доступ к API COM, таким как API автоматизации Office, а также к динамическим API, таким как библиотеки IronPython, и к HTML-модели DOM.</span><span class="sxs-lookup"><span data-stu-id="d735b-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="d735b-106">Тип `dynamic` в большинстве случаев ведет себя как тип `object`.</span><span class="sxs-lookup"><span data-stu-id="d735b-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="d735b-107">При этом операции, содержащие выражения типа `dynamic`, не разрешаются или тип проверяется компилятором.</span><span class="sxs-lookup"><span data-stu-id="d735b-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="d735b-108">Компилятор объединяет сведения об операции, которые впоследствии будут использоваться для оценки этой операции во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d735b-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="d735b-109">В рамках этого процесса переменные типа `dynamic` компилируются в переменные типа `object`.</span><span class="sxs-lookup"><span data-stu-id="d735b-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="d735b-110">Таким образом, тип `dynamic` существует только во время компиляции, но не во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d735b-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="d735b-111">В следующем примере переменной типа `dynamic` противопоставляется переменная типа `object`.</span><span class="sxs-lookup"><span data-stu-id="d735b-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="d735b-112">Чтобы проверить тип каждой переменной во время компиляции, наведите указатель мыши на `dyn` или `obj` в операторах `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="d735b-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="d735b-113">IntelliSense отображает **dynamic** для `dyn` и **object** для `obj`.</span><span class="sxs-lookup"><span data-stu-id="d735b-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="d735b-114">Операторы `WriteLine` отображают типы времени выполнения `dyn` и `obj`.</span><span class="sxs-lookup"><span data-stu-id="d735b-114">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="d735b-115">На этом этапе оба имеют один и тот же тип — целое число.</span><span class="sxs-lookup"><span data-stu-id="d735b-115">At that point, both have the same type, integer.</span></span> <span data-ttu-id="d735b-116">Выводятся следующие результаты.</span><span class="sxs-lookup"><span data-stu-id="d735b-116">The following output is produced:</span></span>

`System.Int32`

`System.Int32`

<span data-ttu-id="d735b-117">Чтобы увидеть разницу между `dyn` и `obj` во время компиляции, добавьте между объявлениями и операторами `WriteLine` в предыдущем примере следующие две строки:</span><span class="sxs-lookup"><span data-stu-id="d735b-117">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="d735b-118">При попытке добавления целого числа и объекта в выражение `obj + 3` выдается ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="d735b-118">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="d735b-119">При этом для `dyn + 3` ошибка не возникает.</span><span class="sxs-lookup"><span data-stu-id="d735b-119">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="d735b-120">Выражение, которое содержит `dyn`, не проверяется во время компиляции, поскольку тип `dyn` имеет значение `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="d735b-120">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

## <a name="context"></a><span data-ttu-id="d735b-121">Контекст</span><span class="sxs-lookup"><span data-stu-id="d735b-121">Context</span></span>

<span data-ttu-id="d735b-122">В следующих ситуациях ключевое слово `dynamic` может отображаться как есть или как компонент сконструированного типа:</span><span class="sxs-lookup"><span data-stu-id="d735b-122">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>

- <span data-ttu-id="d735b-123">В объявлениях: как тип свойства, поля, индексатора, параметра возвращаемого значения, локальной переменной или ограничения типа.</span><span class="sxs-lookup"><span data-stu-id="d735b-123">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="d735b-124">В представленном ниже определении класса ключевое слово `dynamic` используется сразу в нескольких различных объявлениях.</span><span class="sxs-lookup"><span data-stu-id="d735b-124">The following class definition uses `dynamic` in several different declarations.</span></span>

    [!code-csharp[csrefKeywordsTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#22)]

- <span data-ttu-id="d735b-125">В явных преобразованиях типа: как целевой тип преобразования.</span><span class="sxs-lookup"><span data-stu-id="d735b-125">In explicit type conversions, as the target type of a conversion.</span></span>

    [!code-csharp[csrefKeywordsTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#23)]

- <span data-ttu-id="d735b-126">В любом контексте, где типы служат в качестве значений, например справа от оператора `is` или `as`, либо в качестве аргумента для `typeof` в рамках сконструированного типа.</span><span class="sxs-lookup"><span data-stu-id="d735b-126">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="d735b-127">Например, ключевое слово `dynamic` можно использовать в следующих выражениях:</span><span class="sxs-lookup"><span data-stu-id="d735b-127">For example, `dynamic` can be used in the following expressions.</span></span>

    [!code-csharp[csrefKeywordsTypes#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#24)]

## <a name="example"></a><span data-ttu-id="d735b-128">Пример</span><span class="sxs-lookup"><span data-stu-id="d735b-128">Example</span></span>

<span data-ttu-id="d735b-129">В следующем примере `dynamic` используется в нескольких объявлениях.</span><span class="sxs-lookup"><span data-stu-id="d735b-129">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="d735b-130">Метод `Main` также противопоставляет проверку типов во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="d735b-130">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

<span data-ttu-id="d735b-131">Дополнительные сведения и примеры см. в разделе [Использование типа dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="d735b-131">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d735b-132">См. также</span><span class="sxs-lookup"><span data-stu-id="d735b-132">See also</span></span>

- <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [<span data-ttu-id="d735b-133">Использование типа dynamic</span><span class="sxs-lookup"><span data-stu-id="d735b-133">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="d735b-134">object</span><span class="sxs-lookup"><span data-stu-id="d735b-134">object</span></span>](object.md)
- [<span data-ttu-id="d735b-135">is</span><span class="sxs-lookup"><span data-stu-id="d735b-135">is</span></span>](../operators/type-testing-and-conversion-operators.md#is-operator)
- [<span data-ttu-id="d735b-136">as</span><span class="sxs-lookup"><span data-stu-id="d735b-136">as</span></span>](../operators/type-testing-and-conversion-operators.md#as-operator)
- [<span data-ttu-id="d735b-137">typeof</span><span class="sxs-lookup"><span data-stu-id="d735b-137">typeof</span></span>](../operators/type-testing-and-conversion-operators.md#typeof-operator)
- [<span data-ttu-id="d735b-138">Практическое руководство. Безопасное приведение с помощью сопоставления шаблонов и операторы is и as</span><span class="sxs-lookup"><span data-stu-id="d735b-138">How to: safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="d735b-139">Пошаговое руководство. Создание и использование динамических объектов (C# и Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d735b-139">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
