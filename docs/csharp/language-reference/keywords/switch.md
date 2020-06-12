---
title: Оператор switch C#
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: a4e6f8e43c2ec8c867af9f78bd83b435b78c73d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446767"
---
# <a name="switch-c-reference"></a><span data-ttu-id="a8104-102">switch (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="a8104-102">switch (C# reference)</span></span>

<span data-ttu-id="a8104-103">В этой статье рассматривается инструкция `switch`.</span><span class="sxs-lookup"><span data-stu-id="a8104-103">This article covers the `switch` statement.</span></span> <span data-ttu-id="a8104-104">Сведения о выражении `switch` (представлено в C# 8.0) см. в статье [Выражение `switch`](../operators/switch-expression.md) в разделе [Выражения и операторы](../operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8104-104">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="a8104-105">`switch` — это оператор выбора, который выбирает для выполнения один *раздел switch* из списка кандидатов, сравнивая их с *выражением соответствия*.</span><span class="sxs-lookup"><span data-stu-id="a8104-105">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="a8104-106">Оператор `switch` часто используется вместо конструкции [if-else](if-else.md), если одно выражение проверяется на соответствие трем или больше условиям.</span><span class="sxs-lookup"><span data-stu-id="a8104-106">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="a8104-107">Например, следующий оператор `switch` определяет, имеет ли переменная типа `Color` одно из трех значений:</span><span class="sxs-lookup"><span data-stu-id="a8104-107">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="a8104-108">Это эквивалентно следующему примеру, в котором используется конструкция `if`-`else`.</span><span class="sxs-lookup"><span data-stu-id="a8104-108">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="a8104-109">Выражение соответствия</span><span class="sxs-lookup"><span data-stu-id="a8104-109">The match expression</span></span>

<span data-ttu-id="a8104-110">Выражение соответствия предоставляет значение для сравнения в шаблонами в метках `case`.</span><span class="sxs-lookup"><span data-stu-id="a8104-110">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="a8104-111">Он имеет следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="a8104-111">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="a8104-112">В C# 6 и более ранних версий выражение соответствия должно возвращать значение следующих типов:</span><span class="sxs-lookup"><span data-stu-id="a8104-112">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="a8104-113">[char](../builtin-types/char.md);</span><span class="sxs-lookup"><span data-stu-id="a8104-113">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="a8104-114">[string](../builtin-types/reference-types.md);</span><span class="sxs-lookup"><span data-stu-id="a8104-114">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="a8104-115">[bool](../builtin-types/bool.md);</span><span class="sxs-lookup"><span data-stu-id="a8104-115">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="a8104-116">[целочисленное](../builtin-types/integral-numeric-types.md) значение, например `int` или `long`;</span><span class="sxs-lookup"><span data-stu-id="a8104-116">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="a8104-117">значение [enum](../builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="a8104-117">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="a8104-118">Начиная с C# 7.0 выражение соответствия может быть любым выражением, отличным от NULL.</span><span class="sxs-lookup"><span data-stu-id="a8104-118">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="a8104-119">Раздел switch</span><span class="sxs-lookup"><span data-stu-id="a8104-119">The switch section</span></span>

<span data-ttu-id="a8104-120">Оператор `switch` включает один или несколько разделов switch.</span><span class="sxs-lookup"><span data-stu-id="a8104-120">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="a8104-121">Каждый раздел switch содержит одну или несколько *меток case* (меток case или меток default), за которыми следует один или несколько операторов.</span><span class="sxs-lookup"><span data-stu-id="a8104-121">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="a8104-122">Оператор `switch` может включать не более одной метки default в каждом разделе switch.</span><span class="sxs-lookup"><span data-stu-id="a8104-122">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="a8104-123">В следующем примере показан простой оператор `switch` с тремя разделами switch, каждый из которых содержит два оператора.</span><span class="sxs-lookup"><span data-stu-id="a8104-123">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="a8104-124">Второй раздел switch содержит метки `case 2:` и `case 3:`.</span><span class="sxs-lookup"><span data-stu-id="a8104-124">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="a8104-125">Оператор `switch` может содержать любое количество разделов switch, а каждый раздел может иметь одну или несколько меток case (как показано в следующем примере).</span><span class="sxs-lookup"><span data-stu-id="a8104-125">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="a8104-126">Однако две метки case не могут содержать одно и то же выражение.</span><span class="sxs-lookup"><span data-stu-id="a8104-126">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="a8104-127">Выполняет только раздел switch в операторе switch.</span><span class="sxs-lookup"><span data-stu-id="a8104-127">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="a8104-128">C# не позволяет продолжить выполнение следующего раздела switch после выполнения предыдущего.</span><span class="sxs-lookup"><span data-stu-id="a8104-128">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="a8104-129">Поэтому, например, следующий код вызовет ошибку компиляции CS0163: "Управление не может передаваться вниз от одной метки case к другой (\<case label>)".</span><span class="sxs-lookup"><span data-stu-id="a8104-129">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

<span data-ttu-id="a8104-130">Обычно для соблюдения этого требования выполняется явный выход из раздела switch с использованием оператора [break](break.md), [goto](goto.md) или [return](return.md).</span><span class="sxs-lookup"><span data-stu-id="a8104-130">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="a8104-131">При этом допустим также приведенный ниже код, так как он гарантирует, что управление программой не будет передано дальше, в раздел switch `default`.</span><span class="sxs-lookup"><span data-stu-id="a8104-131">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="a8104-132">Выполнение списка операторов в разделе switch с меткой case, соответствующей выражению сопоставления, начинается с первого оператора и продолжается по списку, обычно до достижения оператора перехода, такого как `break`, `goto case`, `goto label`, `return` или `throw`.</span><span class="sxs-lookup"><span data-stu-id="a8104-132">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="a8104-133">В этой точке управление передается за пределы оператора `switch` или к другой метке case.</span><span class="sxs-lookup"><span data-stu-id="a8104-133">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="a8104-134">Оператор `goto`, если он используется, должен передать управление константе типа метки.</span><span class="sxs-lookup"><span data-stu-id="a8104-134">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="a8104-135">Это ограничение является обязательным, поскольку попытка передачи управления переменной типа метки может иметь нежелательные побочные эффекты, такие передача управления в непредусмотренное расположение в коде или создание бесконечного цикла.</span><span class="sxs-lookup"><span data-stu-id="a8104-135">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="a8104-136">Метки case</span><span class="sxs-lookup"><span data-stu-id="a8104-136">Case labels</span></span>

<span data-ttu-id="a8104-137">Каждая метка case указывает на шаблон для сравнения с выражением сопоставления (переменная `caseSwitch` в предыдущем примере).</span><span class="sxs-lookup"><span data-stu-id="a8104-137">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="a8104-138">Если они совпадают, управление передается разделу switch, который содержит **первую** соответствующую метку case.</span><span class="sxs-lookup"><span data-stu-id="a8104-138">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="a8104-139">Если с выражением соответствия не совпадает ни один шаблон метки case, управление передается разделу с меткой case `default` при условии, что такой раздел существует.</span><span class="sxs-lookup"><span data-stu-id="a8104-139">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="a8104-140">Если метки case `default` нет, никакие операторы ни в одном из разделов switch не выполняются, а оператор `switch` теряет управление.</span><span class="sxs-lookup"><span data-stu-id="a8104-140">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="a8104-141">Дополнительные сведения об операторе `switch` и сопоставлении шаблонов см. в разделе [Сопоставление шаблонов с оператором `switch`](#pattern).</span><span class="sxs-lookup"><span data-stu-id="a8104-141">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="a8104-142">Так как C# 6 поддерживает только шаблон констант и не допускает повтор постоянных значений, метки case определяют взаимоисключающие значения. При этом выражению сопоставления может соответствовать только один шаблон.</span><span class="sxs-lookup"><span data-stu-id="a8104-142">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="a8104-143">В связи с этим порядок отображения операторов `case` не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="a8104-143">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="a8104-144">Тем не менее, поскольку в C# 7.0 поддерживаются другие шаблоны, метки case не нужно определять как взаимоисключающие значения, и выражению соответствия могут соответствовать сразу несколько шаблонов.</span><span class="sxs-lookup"><span data-stu-id="a8104-144">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="a8104-145">Поскольку в первом разделе switch выполняются только те операторы, которые содержат совпадающий шаблон, порядок операторов `case` становится важным.</span><span class="sxs-lookup"><span data-stu-id="a8104-145">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="a8104-146">Обнаружив раздел switch, оператор или операторы которого эквивалентны предыдущим операторам или являются их подмножествами, C# выдает ошибку компилятора CS8120, "Метка case оператора switch уже обработана предыдущей меткой case".</span><span class="sxs-lookup"><span data-stu-id="a8104-146">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="a8104-147">В следующем примере демонстрируется оператор `switch` с использованием различных не взаимоисключающих шаблонов.</span><span class="sxs-lookup"><span data-stu-id="a8104-147">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="a8104-148">Если раздел switch `case 0:` перемещается и перестает быть первым разделом в операторе `switch`, C# выдает ошибку компилятора, так как целое число с нулевым значением — это подмножество всех целых чисел. Такой шаблон определен оператором `case int val`.</span><span class="sxs-lookup"><span data-stu-id="a8104-148">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="a8104-149">Устранить эту проблему и предупреждение компилятора можно одним из двух способов:</span><span class="sxs-lookup"><span data-stu-id="a8104-149">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="a8104-150">изменив порядок разделов switch;</span><span class="sxs-lookup"><span data-stu-id="a8104-150">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="a8104-151">используя [предложение when](#when) в метке `case`.</span><span class="sxs-lookup"><span data-stu-id="a8104-151">By using a [when clause](#when) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="a8104-152">Метка case `default`</span><span class="sxs-lookup"><span data-stu-id="a8104-152">The `default` case</span></span>

<span data-ttu-id="a8104-153">Метка case `default` указывает на раздел switch, который будет выполнен, если выражение соответствия не совпадет ни с одной другой меткой `case`.</span><span class="sxs-lookup"><span data-stu-id="a8104-153">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="a8104-154">Если метки case `default` нет, а выражение соответствия не совпадает ни с одной другой меткой `case`, поток выполнения программы переходит к оператору `switch`.</span><span class="sxs-lookup"><span data-stu-id="a8104-154">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="a8104-155">Метка case `default` может отображаться в операторе `switch` в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="a8104-155">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="a8104-156">Она всегда оценивается после оценки всех меток `case`, независимо от их порядка.</span><span class="sxs-lookup"><span data-stu-id="a8104-156">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><a name="pattern"></a> <span data-ttu-id="a8104-157">Сопоставление шаблонов с оператором `switch`</span><span class="sxs-lookup"><span data-stu-id="a8104-157">Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="a8104-158">Каждый оператор `case` определяет шаблон, который в случае совпадения с выражением соответствия вызывает выполнение входящего в него раздела switch.</span><span class="sxs-lookup"><span data-stu-id="a8104-158">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="a8104-159">Шаблон константы поддерживают все версии C#.</span><span class="sxs-lookup"><span data-stu-id="a8104-159">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="a8104-160">Остальные шаблоны поддерживаются начиная с C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="a8104-160">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="a8104-161">Шаблон константы</span><span class="sxs-lookup"><span data-stu-id="a8104-161">Constant pattern</span></span>

<span data-ttu-id="a8104-162">Шаблон константы проверяет, равно ли выражение указанной константе.</span><span class="sxs-lookup"><span data-stu-id="a8104-162">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="a8104-163">Он имеет следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="a8104-163">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="a8104-164">здесь *constant* — это значение для проверки.</span><span class="sxs-lookup"><span data-stu-id="a8104-164">where *constant* is the value to test for.</span></span> <span data-ttu-id="a8104-165">Значением *constant* может быть любое из следующих константных выражений:</span><span class="sxs-lookup"><span data-stu-id="a8104-165">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="a8104-166">литерал [bool](../builtin-types/bool.md): `true` или `false`;</span><span class="sxs-lookup"><span data-stu-id="a8104-166">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="a8104-167">любая [целочисленная](../builtin-types/integral-numeric-types.md) константа, например `int`, `long` или `byte`;</span><span class="sxs-lookup"><span data-stu-id="a8104-167">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="a8104-168">имя объявленной переменной `const`;</span><span class="sxs-lookup"><span data-stu-id="a8104-168">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="a8104-169">константа перечисления;</span><span class="sxs-lookup"><span data-stu-id="a8104-169">An enumeration constant.</span></span>
- <span data-ttu-id="a8104-170">литерал [char](../builtin-types/char.md);</span><span class="sxs-lookup"><span data-stu-id="a8104-170">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="a8104-171">литерал [string](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="a8104-171">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="a8104-172">Константное выражение вычисляется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="a8104-172">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="a8104-173">Если *expr* и *constant* являются целочисленными типами, оператор равенства C# определяет, возвращает ли выражение `true` (то есть выполняется ли условие `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="a8104-173">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="a8104-174">В противном случае значение выражения определяется с помощью вызова статического метода [Object.Equals (expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="a8104-174">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="a8104-175">В следующем примере шаблон константы используется для того, чтобы определить, выпадает ли определенная дата на выходные, первый или последний рабочий день недели либо середину недели.</span><span class="sxs-lookup"><span data-stu-id="a8104-175">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="a8104-176">Он сравнивает свойство <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> текущего дня с членами перечисления <xref:System.DayOfWeek>.</span><span class="sxs-lookup"><span data-stu-id="a8104-176">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="a8104-177">В следующем примере шаблон констант используется для обработки данных, введенных пользователем в консольное приложение, имитирующее кофейный автомат.</span><span class="sxs-lookup"><span data-stu-id="a8104-177">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="a8104-178">Шаблон типа</span><span class="sxs-lookup"><span data-stu-id="a8104-178">Type pattern</span></span>

<span data-ttu-id="a8104-179">Шаблон типа обеспечивает точное определение и преобразование типов.</span><span class="sxs-lookup"><span data-stu-id="a8104-179">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="a8104-180">При использовании оператора `switch` для сопоставления шаблонов он проверяет, можно ли преобразовать выражение в указанный тип и, если это возможно, приводит его к переменной этого типа.</span><span class="sxs-lookup"><span data-stu-id="a8104-180">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="a8104-181">Он имеет следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="a8104-181">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="a8104-182">здесь *type* — это имя типа, в который должен быть преобразован результат *expr*, *varname* — это объект, в который преобразуется результат *expr*, если сопоставление завершается успешно.</span><span class="sxs-lookup"><span data-stu-id="a8104-182">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="a8104-183">Начиная с C# 7.1 тип времени компиляции у *expr* может быть параметром универсального типа.</span><span class="sxs-lookup"><span data-stu-id="a8104-183">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="a8104-184">Выражение `case` имеет значение `true`, если выполняется одно из следующих условий:</span><span class="sxs-lookup"><span data-stu-id="a8104-184">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="a8104-185">*expr* представляет собой экземпляр того же типа, что и *type*;</span><span class="sxs-lookup"><span data-stu-id="a8104-185">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="a8104-186">*expr* является экземпляром типа, производного от *type*.</span><span class="sxs-lookup"><span data-stu-id="a8104-186">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="a8104-187">Другими словами, результат *expr* может быть приведен с повышением к экземпляру *type*.</span><span class="sxs-lookup"><span data-stu-id="a8104-187">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="a8104-188">*expr* имеет тип времени компиляции, который является базовым классом для *type*, и *expr* имеет тип среды выполнения, который является *type* или производным от *type*.</span><span class="sxs-lookup"><span data-stu-id="a8104-188">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="a8104-189">*Тип времени компиляции* переменной представляет собой тип переменной, заданный в ее определении типа.</span><span class="sxs-lookup"><span data-stu-id="a8104-189">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="a8104-190">*Тип среды выполнения* переменной представляет собой тип экземпляра, назначенный этой переменной.</span><span class="sxs-lookup"><span data-stu-id="a8104-190">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="a8104-191">*expr* является экземпляром типа, который реализует интерфейс *type*.</span><span class="sxs-lookup"><span data-stu-id="a8104-191">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="a8104-192">Если case имеет значение true, *varname* присваивается определенным образом и получает локальную область в пределах раздела switch.</span><span class="sxs-lookup"><span data-stu-id="a8104-192">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="a8104-193">Обратите внимание на то, что `null` не соответствует типу.</span><span class="sxs-lookup"><span data-stu-id="a8104-193">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="a8104-194">Для сопоставления `null` используйте следующую метку `case`:</span><span class="sxs-lookup"><span data-stu-id="a8104-194">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="a8104-195">В следующем примере шаблон типа используется для предоставления сведений о различные видах коллекций типов.</span><span class="sxs-lookup"><span data-stu-id="a8104-195">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="a8104-196">Вместо `object` можно создать универсальный метод, используя тип коллекции в качестве параметра типа, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="a8104-196">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="a8104-197">У универсальной версии есть два отличия от первого примера.</span><span class="sxs-lookup"><span data-stu-id="a8104-197">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="a8104-198">Во-первых, нельзя использовать case `null`.</span><span class="sxs-lookup"><span data-stu-id="a8104-198">First, you can't use the `null` case.</span></span> <span data-ttu-id="a8104-199">Оператору case нельзя задать константу, так как компилятор не может преобразовать любой произвольный тип `T` в другой тип, отличный от `object`.</span><span class="sxs-lookup"><span data-stu-id="a8104-199">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="a8104-200">Прежний оператор case `default` теперь выполняет проверку `object` на значения, не равные NULL.</span><span class="sxs-lookup"><span data-stu-id="a8104-200">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="a8104-201">Это означает, что case `default` выполняет проверку только на `null`.</span><span class="sxs-lookup"><span data-stu-id="a8104-201">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="a8104-202">Без сопоставления шаблонов этот код может быть написан следующим образом.</span><span class="sxs-lookup"><span data-stu-id="a8104-202">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="a8104-203">При использовании шаблона типа создается более лаконичный и удобочитаемый код, причем проверять результат преобразования (`null`) или выполнять повторное приведение не требуется.</span><span class="sxs-lookup"><span data-stu-id="a8104-203">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="a8104-204"><a name="when" /> Оператор `case` и предложение `when`</span><span class="sxs-lookup"><span data-stu-id="a8104-204"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="a8104-205">Начиная с C# 7.0 операторы case необязательно должны быть взаимоисключающими. В связи с этим можно добавить предложение `when`, определяющее дополнительное условие, которому должен соответствовать оператор case, чтобы иметь значение true.</span><span class="sxs-lookup"><span data-stu-id="a8104-205">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="a8104-206">Предложение `when` может быть любым выражением, возвращающим логическое значение.</span><span class="sxs-lookup"><span data-stu-id="a8104-206">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="a8104-207">В следующем примере определяется базовый класс `Shape`, класс `Rectangle`, производный от `Shape`, и класс `Square`, производный от `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="a8104-207">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="a8104-208">Предложение `when` используется в нем для того, чтобы с помощью `ShowShapeInfo` обрабатывался объект `Rectangle`, которому назначена такая же длина и ширина, как у объекта `Square`, даже если он не был инициализирован как объект `Square`.</span><span class="sxs-lookup"><span data-stu-id="a8104-208">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="a8104-209">Метод не пытается отобразить сведения ни об объекте со значением `null`, ни о форме с нулевой областью.</span><span class="sxs-lookup"><span data-stu-id="a8104-209">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="a8104-210">Обратите внимание на то, что предложение `when` в этом примере, проверяющее, имеет ли объект `Shape` значение `null`, не выполняется.</span><span class="sxs-lookup"><span data-stu-id="a8104-210">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="a8104-211">Правильный шаблон пути для проверки на наличие значения `null` — `case null:`.</span><span class="sxs-lookup"><span data-stu-id="a8104-211">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a8104-212">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="a8104-212">C# language specification</span></span>

<span data-ttu-id="a8104-213">Дополнительные сведения см. в разделе [Оператор switch](~/_csharplang/spec/statements.md#the-switch-statement) в статье [Спецификации языка C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="a8104-213">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="a8104-214">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="a8104-214">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8104-215">См. также</span><span class="sxs-lookup"><span data-stu-id="a8104-215">See also</span></span>

- [<span data-ttu-id="a8104-216">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="a8104-216">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a8104-217">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="a8104-217">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a8104-218">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="a8104-218">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a8104-219">if-else</span><span class="sxs-lookup"><span data-stu-id="a8104-219">if-else</span></span>](if-else.md)
- [<span data-ttu-id="a8104-220">Соответствие шаблону</span><span class="sxs-lookup"><span data-stu-id="a8104-220">Pattern Matching</span></span>](../../pattern-matching.md)
