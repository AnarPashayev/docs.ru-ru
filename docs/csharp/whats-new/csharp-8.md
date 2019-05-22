---
title: Новые возможности C# 8.0. Руководство по языку C#
description: Обзор новых функций, доступных в C# 8.0. В этой статье представлены возможности предварительной версии 2.
ms.date: 02/12/2019
ms.openlocfilehash: 16723894d87526972b692a098a57ef3726b252dd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754375"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="8e905-104">Новые возможности C# 8.0</span><span class="sxs-lookup"><span data-stu-id="8e905-104">What's new in C# 8.0</span></span>

<span data-ttu-id="8e905-105">Для языка C# представлено множество улучшений, которые вы можете опробовать уже в предварительной версии 2.</span><span class="sxs-lookup"><span data-stu-id="8e905-105">There are many enhancements to the C# language that you can try out already with preview 2.</span></span> <span data-ttu-id="8e905-106">Ниже приведены новые возможности, добавленные в предварительной версии 2.</span><span class="sxs-lookup"><span data-stu-id="8e905-106">The new features added in preview 2 are:</span></span>

- <span data-ttu-id="8e905-107">[Улучшения сопоставления шаблонов](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="8e905-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  * <span data-ttu-id="8e905-108">[выражения switch](#switch-expressions);</span><span class="sxs-lookup"><span data-stu-id="8e905-108">[Switch expressions](#switch-expressions)</span></span>
  * <span data-ttu-id="8e905-109">[шаблоны свойств](#property-patterns);</span><span class="sxs-lookup"><span data-stu-id="8e905-109">[Property patterns](#property-patterns)</span></span>
  * <span data-ttu-id="8e905-110">[шаблоны кортежей](#tuple-patterns);</span><span class="sxs-lookup"><span data-stu-id="8e905-110">[Tuple patterns](#tuple-patterns)</span></span>
  * <span data-ttu-id="8e905-111">[позиционные шаблоны](#positional-patterns).</span><span class="sxs-lookup"><span data-stu-id="8e905-111">[Positional patterns](#positional-patterns)</span></span>
- <span data-ttu-id="8e905-112">[Объявления using](#using-declarations).</span><span class="sxs-lookup"><span data-stu-id="8e905-112">[Using declarations](#using-declarations)</span></span>
- <span data-ttu-id="8e905-113">[Статические локальные функции](#static-local-functions).</span><span class="sxs-lookup"><span data-stu-id="8e905-113">[Static local functions](#static-local-functions)</span></span>
- <span data-ttu-id="8e905-114">[Удаляемые ссылочные структуры](#disposable-ref-structs).</span><span class="sxs-lookup"><span data-stu-id="8e905-114">[Disposable ref structs](#disposable-ref-structs)</span></span>

<span data-ttu-id="8e905-115">Перечисленные ниже возможности языка впервые появились в предварительной версии 1 C# 8.0:</span><span class="sxs-lookup"><span data-stu-id="8e905-115">The following language features first appeared in C# 8.0 preview 1:</span></span>

- [<span data-ttu-id="8e905-116">Ссылочные типы, допускающие значение NULL</span><span class="sxs-lookup"><span data-stu-id="8e905-116">Nullable reference types</span></span>](#nullable-reference-types)
- <span data-ttu-id="8e905-117">[Асинхронные потоки](#asynchronous-streams).</span><span class="sxs-lookup"><span data-stu-id="8e905-117">[Asynchronous streams](#asynchronous-streams)</span></span>
- <span data-ttu-id="8e905-118">[Индексы и диапазоны](#indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="8e905-118">[Indices and ranges](#indices-and-ranges)</span></span>

> [!NOTE]
> <span data-ttu-id="8e905-119">Эта статья последний раз обновлялась для предварительной версии 2 C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="8e905-119">This article was last updated for C# 8.0 preview 2.</span></span>

<span data-ttu-id="8e905-120">В остальных разделах этой статьи кратко описываются эти возможности.</span><span class="sxs-lookup"><span data-stu-id="8e905-120">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="8e905-121">Здесь приведены ссылки на эти подробные руководства и обзоры (если они доступны).</span><span class="sxs-lookup"><span data-stu-id="8e905-121">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="8e905-122">Дополнительные шаблоны в нескольких расположениях</span><span class="sxs-lookup"><span data-stu-id="8e905-122">More patterns in more places</span></span>

<span data-ttu-id="8e905-123">Возможность **сопоставления шаблонов** позволяет работать с шаблонами в зависимости от формата в связанных, но различных типах данных.</span><span class="sxs-lookup"><span data-stu-id="8e905-123">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="8e905-124">В C# 7.0 появился синтаксис для шаблонов типа и шаблонов константы, использующий выражение [`is`](../language-reference/keywords/is.md) и инструкцию [`switch`](../language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="8e905-124">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="8e905-125">Эти функции представляют первые пробные шаги на пути к поддержке парадигм программирования, где данные и функции разделены.</span><span class="sxs-lookup"><span data-stu-id="8e905-125">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="8e905-126">По мере того как отрасль переходит на использование микрослужб и других облачных архитектур, необходимы также средства других языков.</span><span class="sxs-lookup"><span data-stu-id="8e905-126">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="8e905-127">В C# 8.0 расширены эти возможности, так что вы можете использовать дополнительные выражения шаблонов в нескольких расположениях в коде.</span><span class="sxs-lookup"><span data-stu-id="8e905-127">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="8e905-128">Учитывайте эти функции, когда данные и функциональные возможности представлены отдельно.</span><span class="sxs-lookup"><span data-stu-id="8e905-128">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="8e905-129">Рассмотрите возможность сопоставления шаблонов, когда алгоритмы зависят от фактов, отличных от типа среды выполнения объекта.</span><span class="sxs-lookup"><span data-stu-id="8e905-129">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="8e905-130">Эти методы предоставляют другой способ выражения проектов.</span><span class="sxs-lookup"><span data-stu-id="8e905-130">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="8e905-131">Помимо новых шаблонов в новых расположениях, в C# 8.0 добавлены **рекурсивные шаблоны**.</span><span class="sxs-lookup"><span data-stu-id="8e905-131">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="8e905-132">Результат выражения любого шаблона — это выражение языка.</span><span class="sxs-lookup"><span data-stu-id="8e905-132">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="8e905-133">Рекурсивный шаблон является просто выражением шаблона, которое применяется к результатам другого выражения шаблона.</span><span class="sxs-lookup"><span data-stu-id="8e905-133">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="8e905-134">Выражения switch</span><span class="sxs-lookup"><span data-stu-id="8e905-134">switch expressions</span></span>

<span data-ttu-id="8e905-135">Часто инструкция [`switch`](../language-reference/keywords/switch.md) возвращает значение в каждом из блоков `case`.</span><span class="sxs-lookup"><span data-stu-id="8e905-135">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="8e905-136">**Выражения switch** позволяет использовать более краткий синтаксис выражения.</span><span class="sxs-lookup"><span data-stu-id="8e905-136">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="8e905-137">В нем меньше повторяющихся ключевых слов `case` и `break`, а также меньше фигурных скобок.</span><span class="sxs-lookup"><span data-stu-id="8e905-137">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="8e905-138">Например, рассмотрим следующее перечисление, которое выводит список цветов радуги:</span><span class="sxs-lookup"><span data-stu-id="8e905-138">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

<span data-ttu-id="8e905-139">Если для приложения определен тип `RGBColor`, который создается на основе компонентов `R`, `G` и `B`, вы можете преобразовать значение `Rainbow` в RGB-значение, используя следующий метод, содержащий выражение switch:</span><span class="sxs-lookup"><span data-stu-id="8e905-139">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

<span data-ttu-id="8e905-140">Здесь представлено несколько улучшений синтаксиса:</span><span class="sxs-lookup"><span data-stu-id="8e905-140">There are several syntax improvements here:</span></span>

- <span data-ttu-id="8e905-141">Переменная расположена перед ключевым словом `switch`.</span><span class="sxs-lookup"><span data-stu-id="8e905-141">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="8e905-142">Другой порядок позволяет визуально легко отличить выражение switch от инструкции switch.</span><span class="sxs-lookup"><span data-stu-id="8e905-142">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="8e905-143">Элементы `case` и `:` заменяются на `=>`.</span><span class="sxs-lookup"><span data-stu-id="8e905-143">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="8e905-144">Это более лаконично и интуитивно понятно.</span><span class="sxs-lookup"><span data-stu-id="8e905-144">It's more concise and intuitive.</span></span>
- <span data-ttu-id="8e905-145">Случай `default` заменяется пустой переменной `_`.</span><span class="sxs-lookup"><span data-stu-id="8e905-145">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="8e905-146">Тексты являются выражениями, а не инструкциями.</span><span class="sxs-lookup"><span data-stu-id="8e905-146">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="8e905-147">Сравните это с эквивалентным кодом, где используется классическая инструкция `switch`:</span><span class="sxs-lookup"><span data-stu-id="8e905-147">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a><span data-ttu-id="8e905-148">Шаблоны свойств</span><span class="sxs-lookup"><span data-stu-id="8e905-148">Property patterns</span></span>

<span data-ttu-id="8e905-149">**Шаблон свойств** позволяет сопоставлять свойства исследуемого объекта.</span><span class="sxs-lookup"><span data-stu-id="8e905-149">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="8e905-150">Рассмотрим сайт электронной коммерции, на котором должен вычисляться налог с продаж по адресу покупателя.</span><span class="sxs-lookup"><span data-stu-id="8e905-150">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="8e905-151">Это вычисление не является основной задачей класса `Address`.</span><span class="sxs-lookup"><span data-stu-id="8e905-151">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="8e905-152">Оно меняется со временем и, скорее всего, чаще, чем изменения формата адреса.</span><span class="sxs-lookup"><span data-stu-id="8e905-152">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="8e905-153">Сумма налога с продаж зависит от свойства `State` адреса.</span><span class="sxs-lookup"><span data-stu-id="8e905-153">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="8e905-154">В следующем методе используется шаблон свойства для вычисления налога с продаж по адресу и цене:</span><span class="sxs-lookup"><span data-stu-id="8e905-154">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

<span data-ttu-id="8e905-155">При сопоставлении шаблонов создается сокращенный синтаксис для выражения этого алгоритма.</span><span class="sxs-lookup"><span data-stu-id="8e905-155">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="8e905-156">Шаблоны кортежей</span><span class="sxs-lookup"><span data-stu-id="8e905-156">Tuple patterns</span></span>

<span data-ttu-id="8e905-157">Некоторые алгоритмы зависят от нескольких наборов входных данных.</span><span class="sxs-lookup"><span data-stu-id="8e905-157">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="8e905-158">**Шаблоны кортежей** позволяют переключаться между несколькими значениями, выраженными как [кортежи](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="8e905-158">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="8e905-159">В следующем примере кода показано выражение switch для игры *камень, ножницы, бумага*:</span><span class="sxs-lookup"><span data-stu-id="8e905-159">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

<span data-ttu-id="8e905-160">В сообщении указан победитель.</span><span class="sxs-lookup"><span data-stu-id="8e905-160">The messages indicate the winner.</span></span> <span data-ttu-id="8e905-161">В случае отклонения представляются три комбинации, ведущие к ничьей, или другие текстовые входные данные.</span><span class="sxs-lookup"><span data-stu-id="8e905-161">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="8e905-162">Позиционные шаблоны</span><span class="sxs-lookup"><span data-stu-id="8e905-162">Positional patterns</span></span>

<span data-ttu-id="8e905-163">Некоторые типы включают метод `Deconstruct`, свойства которого деконструируются на дискретные переменные.</span><span class="sxs-lookup"><span data-stu-id="8e905-163">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="8e905-164">Если метод `Deconstruct` доступен, можно использовать **позиционные шаблоны** для проверки свойств объекта и использовать эти свойства для шаблона.</span><span class="sxs-lookup"><span data-stu-id="8e905-164">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="8e905-165">Рассмотрим следующий класс `Point`, который содержит метод `Deconstruct` для создания дискретных переменных для `X` и `Y`:</span><span class="sxs-lookup"><span data-stu-id="8e905-165">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

<span data-ttu-id="8e905-166">Кроме того, нужно учитывать следующее перечисление, представляющее различные позиции квадранта:</span><span class="sxs-lookup"><span data-stu-id="8e905-166">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

<span data-ttu-id="8e905-167">В следующем методе используется **позиционный шаблон** для извлечения значений `x` и `y`.</span><span class="sxs-lookup"><span data-stu-id="8e905-167">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="8e905-168">Затем используется предложение `when` для определения `Quadrant` точки:</span><span class="sxs-lookup"><span data-stu-id="8e905-168">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

<span data-ttu-id="8e905-169">Шаблон пустой переменной в предыдущем операторе switch совпадает с выражением, если `x` или `y`, но не оба, имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="8e905-169">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="8e905-170">Выражение switch должно создавать значение или исключение.</span><span class="sxs-lookup"><span data-stu-id="8e905-170">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="8e905-171">Если ни один из вариантов не совпадает, выражение switch создает исключение.</span><span class="sxs-lookup"><span data-stu-id="8e905-171">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="8e905-172">Компилятор создает предупреждение, если в выражении switch не охватываются все возможные случаи.</span><span class="sxs-lookup"><span data-stu-id="8e905-172">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="8e905-173">Ознакомиться с методами сопоставления шаблонов можно в [этом подробном учебнике](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="8e905-173">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="8e905-174">Объявления using</span><span class="sxs-lookup"><span data-stu-id="8e905-174">using declarations</span></span>

<span data-ttu-id="8e905-175">**Объявление using** — это объявление переменной, которому предшествует ключевое слово `using`.</span><span class="sxs-lookup"><span data-stu-id="8e905-175">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="8e905-176">Оно сообщает компилятору, что объявляемая переменная должна быть удалена в конце области видимости.</span><span class="sxs-lookup"><span data-stu-id="8e905-176">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="8e905-177">Для примера рассмотрим следующий код, в котором записывается текстовый файл:</span><span class="sxs-lookup"><span data-stu-id="8e905-177">For example, consider the following code that writes a text file:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

<span data-ttu-id="8e905-178">В приведенном выше примере файл удаляется при достижении закрывающей фигурной скобки метода.</span><span class="sxs-lookup"><span data-stu-id="8e905-178">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="8e905-179">Это конец области, в котором объявляется `file`.</span><span class="sxs-lookup"><span data-stu-id="8e905-179">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="8e905-180">Приведенный выше код эквивалентен следующему коду, в котором используется классическая инструкция [using](../language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="8e905-180">The preceding code is equivalent to the following code using the classic [using statements](../language-reference/keywords/using-statement.md) statement:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

<span data-ttu-id="8e905-181">В приведенном выше примере файл удаляется при достижении закрывающей фигурной скобки, связанной с инструкцией `using`.</span><span class="sxs-lookup"><span data-stu-id="8e905-181">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="8e905-182">В обоих случаях компилятор создает вызов метода `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="8e905-182">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="8e905-183">Компилятор создает ошибку, если выражение в инструкции using не может быть удалено.</span><span class="sxs-lookup"><span data-stu-id="8e905-183">The compiler generates an error if the expression in the using statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="8e905-184">Статические локальные функции</span><span class="sxs-lookup"><span data-stu-id="8e905-184">Static local functions</span></span>

<span data-ttu-id="8e905-185">Теперь вы можете добавить модификатор `static` для локальных функций, чтобы убедиться, что локальная функция не захватывает (не ссылается на) какие-либо переменные из области видимости.</span><span class="sxs-lookup"><span data-stu-id="8e905-185">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="8e905-186">Это приводит к возникновению ошибки `CS8421`: "A static local function can't contain a reference to \<variable>" (Статическая локальная функция не может содержать ссылку на <переменная>).</span><span class="sxs-lookup"><span data-stu-id="8e905-186">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="8e905-187">Рассмотрим следующий код.</span><span class="sxs-lookup"><span data-stu-id="8e905-187">Consider the following code.</span></span> <span data-ttu-id="8e905-188">Локальная функция `LocalFunction` обращается к переменной `y`, объявленной в области видимости (метод `M`).</span><span class="sxs-lookup"><span data-stu-id="8e905-188">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="8e905-189">Таким образом `LocalFunction` не может объявляться с помощью модификатора `static`:</span><span class="sxs-lookup"><span data-stu-id="8e905-189">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="8e905-190">Следующий код содержит статическую локальную функцию.</span><span class="sxs-lookup"><span data-stu-id="8e905-190">The following code contains a static local function.</span></span> <span data-ttu-id="8e905-191">Она может быть статической, так как она не обращается ко всем переменным в области видимости:</span><span class="sxs-lookup"><span data-stu-id="8e905-191">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="8e905-192">Удаляемые ссылочные структуры</span><span class="sxs-lookup"><span data-stu-id="8e905-192">Disposable ref structs</span></span>

<span data-ttu-id="8e905-193">Объект `struct`, объявленный с помощью модификатора `ref`, не может реализовывать интерфейсы и поэтому не может реализовать <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="8e905-193">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="8e905-194">Таким образом, чтобы объект `ref struct` можно было удалить, у него должен быть доступный метод `void Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="8e905-194">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="8e905-195">Это также относится к объявлениям `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="8e905-195">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="8e905-196">Ссылочные типы, допускающие значение null</span><span class="sxs-lookup"><span data-stu-id="8e905-196">Nullable reference types</span></span>

<span data-ttu-id="8e905-197">Внутри контекста заметок, допускающих значение null, любая переменная ссылочного типа считается переменной **ссылочного типа, не допускающего значения null**.</span><span class="sxs-lookup"><span data-stu-id="8e905-197">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="8e905-198">Если вы хотите указать, что переменная может принимать значение null, необходимо добавить к имени типа `?`, чтобы объявить переменную как переменную **ссылочного типа, допускающего значения null**.</span><span class="sxs-lookup"><span data-stu-id="8e905-198">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="8e905-199">Для ссылочных типов, не допускающих значение null, компилятор использует анализ потока, чтобы убедиться, что локальные переменные инициализируются в значение, отличное от null, при объявлении.</span><span class="sxs-lookup"><span data-stu-id="8e905-199">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="8e905-200">Поля должны быть инициализированы во время построения.</span><span class="sxs-lookup"><span data-stu-id="8e905-200">Fields must be initialized during construction.</span></span> <span data-ttu-id="8e905-201">Компилятор создает предупреждение, если переменная не задана с помощью вызова любого из доступных конструкторов или с помощью инициализатора.</span><span class="sxs-lookup"><span data-stu-id="8e905-201">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="8e905-202">Кроме того, ссылочным типам, не допускающим значение null, нельзя задать значение, которое может быть null.</span><span class="sxs-lookup"><span data-stu-id="8e905-202">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="8e905-203">Ссылочные типы, допускающие значение null, не проверяются на предмет того, назначено ли им значение null или получили ли они его после инициализации.</span><span class="sxs-lookup"><span data-stu-id="8e905-203">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="8e905-204">Тем не менее, компилятор использует анализ потока, чтобы убедиться, что любая переменная ссылочного типа, допускающего значение null, проверяется на наличие значения null, прежде чем обратиться к ней или назначить ей ссылочный тип, не допускающий значение null.</span><span class="sxs-lookup"><span data-stu-id="8e905-204">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="8e905-205">Дополнительные сведения о функции см. в обзоре [ссылочных типов, допускающих значение null](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="8e905-205">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="8e905-206">Попробуйте самостоятельно применить эту возможность в новом приложении в этом [руководстве по ссылочным типам, допускающим значение null](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="8e905-206">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="8e905-207">Дополнительные сведения о шагах переноса существующей базы кода для использования ссылочных типов, допускающих значение null, см. в [этом руководстве](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="8e905-207">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="8e905-208">Асинхронные потоки</span><span class="sxs-lookup"><span data-stu-id="8e905-208">Asynchronous streams</span></span>

<span data-ttu-id="8e905-209">Начиная с C# версии 8.0 можно создавать и использовать потоки асинхронно.</span><span class="sxs-lookup"><span data-stu-id="8e905-209">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="8e905-210">В методе, который возвращает асинхронный поток, есть три свойства:</span><span class="sxs-lookup"><span data-stu-id="8e905-210">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="8e905-211">Он объявлен с помощью модификатора `async`.</span><span class="sxs-lookup"><span data-stu-id="8e905-211">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="8e905-212">Он возвращает интерфейс <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="8e905-212">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="8e905-213">Метод содержит инструкции `yield return` для возвращения последовательных элементов в асинхронном потоке.</span><span class="sxs-lookup"><span data-stu-id="8e905-213">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="8e905-214">Для использования асинхронного потока требуется добавить ключевое слово `await` перед ключевым словом `foreach` при перечислении элементов потока.</span><span class="sxs-lookup"><span data-stu-id="8e905-214">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="8e905-215">Для добавления ключевого слова `await` требуется, чтобы метод, который перечисляет асинхронный поток, был объявлен с помощью модификатора `async` и возвращал тип, допустимый для метода `async`.</span><span class="sxs-lookup"><span data-stu-id="8e905-215">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="8e905-216">Обычно это означает возвращение структуры <xref:System.Threading.Tasks.Task> или <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="8e905-216">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="8e905-217">Это также может быть структура <xref:System.Threading.Tasks.ValueTask> или <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="8e905-217">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="8e905-218">Метод может использовать и создавать асинхронный поток. Это означает, что будет возвращен интерфейс <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="8e905-218">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="8e905-219">Следующий код создает последовательность чисел от 0 до 19 с интервалом 100 мс между генерированием каждого числа:</span><span class="sxs-lookup"><span data-stu-id="8e905-219">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

<span data-ttu-id="8e905-220">Вы бы перечислили последовательность с использованием инструкции `await foreach`:</span><span class="sxs-lookup"><span data-stu-id="8e905-220">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="8e905-221">Вы можете попробовать асинхронные потоки самостоятельно в нашем руководстве по [созданию и использованию асинхронных потоков](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="8e905-221">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="8e905-222">Индексы и диапазоны</span><span class="sxs-lookup"><span data-stu-id="8e905-222">Indices and ranges</span></span>

<span data-ttu-id="8e905-223">Диапазоны и индексы обеспечивают лаконичный синтаксис для указания поддиапазонов массива: <xref:System.Span%601> или <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="8e905-223">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="8e905-224">Можно указать индекс **с конца**, вставив перед индексом символ `^`.</span><span class="sxs-lookup"><span data-stu-id="8e905-224">You can specify an index **from the end** using the `^` character before the index.</span></span> <span data-ttu-id="8e905-225">Индексирование с конца начинается с правила, которое `0..^0` указывает весь диапазон.</span><span class="sxs-lookup"><span data-stu-id="8e905-225">Indexing from the end starts from the rule that `0..^0` specifies the entire range.</span></span> <span data-ttu-id="8e905-226">Чтобы перечислить полный массив, начните *с первого элемента* и продолжайте, пока не пройдете *последний элемент*.</span><span class="sxs-lookup"><span data-stu-id="8e905-226">To enumerate an entire array, you start *at the first element*, and continue until you are *past the last element*.</span></span> <span data-ttu-id="8e905-227">Можно рассмотреть поведение метода `MoveNext` перечислителя: он возвращает значение false по прохождении последнего элемента перечисления.</span><span class="sxs-lookup"><span data-stu-id="8e905-227">Think of the behavior of the `MoveNext` method on an enumerator: it returns false when the enumeration passes the last element.</span></span> <span data-ttu-id="8e905-228">Индекс `^0` означает "конец", `array[array.Length]` или индекс, который следует за последним элементом.</span><span class="sxs-lookup"><span data-stu-id="8e905-228">The index `^0` means "the end", `array[array.Length]`, or the index that follows the last element.</span></span> <span data-ttu-id="8e905-229">Вы знакомы с выражением `array[2]`, то есть элемент "2 с самого начала".</span><span class="sxs-lookup"><span data-stu-id="8e905-229">You are familiar with `array[2]` meaning the element "2 from the start".</span></span> <span data-ttu-id="8e905-230">Теперь выражение `array[^2]` означает элемент "2 с конца".</span><span class="sxs-lookup"><span data-stu-id="8e905-230">Now, `array[^2]` means the element "2 from the end".</span></span> 

<span data-ttu-id="8e905-231">Вы можете указать **диапазон** с помощью **оператора диапазона**: `..`.</span><span class="sxs-lookup"><span data-stu-id="8e905-231">You can specify a **range** with the **range operator**: `..`.</span></span> <span data-ttu-id="8e905-232">Например, оператор `0..^0` указывает весь диапазон массива: 0 от начала до, но не включая 0 с конца.</span><span class="sxs-lookup"><span data-stu-id="8e905-232">For example, `0..^0` specifies the entire range of the array: 0 from the start up to, but not including 0 from the end.</span></span> <span data-ttu-id="8e905-233">Любой операнд может использовать элемент "от начала" или "с конца".</span><span class="sxs-lookup"><span data-stu-id="8e905-233">Either operand may use "from the start" or "from the end".</span></span> <span data-ttu-id="8e905-234">Кроме того, можно опустить один из операндов.</span><span class="sxs-lookup"><span data-stu-id="8e905-234">Furthermore, either operand may be omitted.</span></span> <span data-ttu-id="8e905-235">По умолчанию оператор `0` используется для начального индекса, а `^0` — для конечного индекса.</span><span class="sxs-lookup"><span data-stu-id="8e905-235">The defaults are `0` for the start index, and `^0` for the end index.</span></span>

<span data-ttu-id="8e905-236">Рассмотрим несколько примеров.</span><span class="sxs-lookup"><span data-stu-id="8e905-236">Let's look at a few examples.</span></span> <span data-ttu-id="8e905-237">Обратите внимание на следующий массив, который помечен индексом от начала и от конца:</span><span class="sxs-lookup"><span data-stu-id="8e905-237">Consider the following array, annotated with its index from the start and from the end:</span></span>

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="8e905-238">Индекс каждого элемента вводит понятие "от начала" и "от конца", и диапазоны указаны без учета конца диапазона.</span><span class="sxs-lookup"><span data-stu-id="8e905-238">The index of each element reinforces the concept of "from the start", and "from the end", and that ranges are exclusive of the end of the range.</span></span> <span data-ttu-id="8e905-239">"Начало" всего массива является первым элементом.</span><span class="sxs-lookup"><span data-stu-id="8e905-239">The "start" of the entire array is the first element.</span></span> <span data-ttu-id="8e905-240">"Конец" всего массива следует *после* последнего элемента.</span><span class="sxs-lookup"><span data-stu-id="8e905-240">The "end" of the entire array is *past* the last element.</span></span>

<span data-ttu-id="8e905-241">Вы можете получить последнее слово с помощью индекса `^1`:</span><span class="sxs-lookup"><span data-stu-id="8e905-241">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="8e905-242">Следующий код создает поддиапазон со словами "quick", "brown" и "fox".</span><span class="sxs-lookup"><span data-stu-id="8e905-242">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="8e905-243">Он включает в себя элементы от `words[1]` до `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="8e905-243">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="8e905-244">Элемент `words[4]` находится вне диапазона.</span><span class="sxs-lookup"><span data-stu-id="8e905-244">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="8e905-245">Следующий код создает поддиапазон со словами "lazy" и "dog".</span><span class="sxs-lookup"><span data-stu-id="8e905-245">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="8e905-246">Он включает элементы `words[^2]` и `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="8e905-246">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="8e905-247">Конечный индекс `words[^0]` не включен:</span><span class="sxs-lookup"><span data-stu-id="8e905-247">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="8e905-248">В следующих примерах создаются диапазоны, которые должны быть открыты для начала, конца или в обоих случаях:</span><span class="sxs-lookup"><span data-stu-id="8e905-248">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

<span data-ttu-id="8e905-249">Вы также можете объявить диапазоны как переменные:</span><span class="sxs-lookup"><span data-stu-id="8e905-249">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="8e905-250">Затем вы можете использовать диапазон внутри символов `[` и `]`:</span><span class="sxs-lookup"><span data-stu-id="8e905-250">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="8e905-251">Вы можете изучить сведения об индексах и диапазонах адресов в руководстве [Индексы и диапазоны](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="8e905-251">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>