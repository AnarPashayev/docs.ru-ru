---
title: Логические операторы. Справочник по C#
description: Узнайте об операторах C#, которые выполняют такие логические операции, как отрицание, конъюнкция (И), а также инклюзивная и эксклюзивная дизъюнкция (ИЛИ), с использованием соответствующих операндов.
ms.date: 09/27/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: 5f85b88236c2e643f97453c64173a3f4f7159a35
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795005"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="8e07a-103">Логические операторы (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="8e07a-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="8e07a-104">Следующие операторы выполняют логические операции с использованием [логических](../builtin-types/bool.md) операндов:</span><span class="sxs-lookup"><span data-stu-id="8e07a-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="8e07a-105">Унарный [`!` (логическое отрицание)](#logical-negation-operator-) оператор.</span><span class="sxs-lookup"><span data-stu-id="8e07a-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="8e07a-106">Бинарные [`&` (логическое И)](#logical-and-operator-), [`|` (логическое ИЛИ)](#logical-or-operator-), а также [`^` (логическое исключающее ИЛИ)](#logical-exclusive-or-operator-) операторы.</span><span class="sxs-lookup"><span data-stu-id="8e07a-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="8e07a-107">Эти операторы всегда обрабатывают оба операнда.</span><span class="sxs-lookup"><span data-stu-id="8e07a-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="8e07a-108">Бинарные [`&&` (условное логическое И)](#conditional-logical-and-operator-) и [`||` (условное логическое ИЛИ)](#conditional-logical-or-operator-) операторы.</span><span class="sxs-lookup"><span data-stu-id="8e07a-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="8e07a-109">Эти операторы вычисляют правый операнд, только если это необходимо.</span><span class="sxs-lookup"><span data-stu-id="8e07a-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="8e07a-110">Для операндов [целочисленных](../builtin-types/integral-numeric-types.md) типов операторы `&`, `|` и `^` выполняют побитовые логические операции.</span><span class="sxs-lookup"><span data-stu-id="8e07a-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="8e07a-111">Дополнительные сведения см. в разделе [Побитовые операторы и операторы сдвига](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="8e07a-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="8e07a-112">Оператор логического отрицания !</span><span class="sxs-lookup"><span data-stu-id="8e07a-112">Logical negation operator !</span></span>

<span data-ttu-id="8e07a-113">Унарный префиксный оператор `!` выполняет логическое отрицание операнда,</span><span class="sxs-lookup"><span data-stu-id="8e07a-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="8e07a-114">возвращая `true`, если операнд имеет значение `false`, и `false`, если операнд имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="8e07a-115">Начиная с версии C# 8.0, унарный постфиксный оператор `!`[допускает значение NULL](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="8e07a-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a> <span data-ttu-id="8e07a-116">Оператор логического И &amp;</span><span class="sxs-lookup"><span data-stu-id="8e07a-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="8e07a-117">Оператор `&` вычисляет логическое И для всех своих операндов.</span><span class="sxs-lookup"><span data-stu-id="8e07a-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="8e07a-118">Результат операции `x & y` принимает значение `true`, если оба оператора `x` и `y` имеют значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="8e07a-119">В противном случае результат будет `false`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="8e07a-120">Оператор `&` вычисляет оба операнда, даже если левый операнд имеет значение `false`. При этом операция должна вернуть значение `false`, независимо от значения правого операнда.</span><span class="sxs-lookup"><span data-stu-id="8e07a-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="8e07a-121">В следующем примере правый операнд оператора `&` является вызовом метода, который выполняется независимо от значения левого операнда:</span><span class="sxs-lookup"><span data-stu-id="8e07a-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="8e07a-122">[Условный оператор логического И](#conditional-logical-and-operator-) `&&` также вычисляет логическое И для своих операндов, но не вычисляет правый операнд, если левый операнд имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="8e07a-123">Для операндов [целочисленных типов](../builtin-types/integral-numeric-types.md) оператор `&` вычисляет [побитовое логическое И](bitwise-and-shift-operators.md#logical-and-operator-) своих операндов.</span><span class="sxs-lookup"><span data-stu-id="8e07a-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="8e07a-124">Унарный оператор `&` является оператором [AddressOf](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="8e07a-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="8e07a-125">Оператор логического исключения ИЛИ ^</span><span class="sxs-lookup"><span data-stu-id="8e07a-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="8e07a-126">Оператор `^` вычисляет логическое исключение ИЛИ для всех своих операндов,</span><span class="sxs-lookup"><span data-stu-id="8e07a-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="8e07a-127">возвращая `true` для `x ^ y`, если `x` имеет значение `true` и `y` имеет значение `false` или `x` имеет значение `false` и `y` имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="8e07a-128">В противном случае результат будет `false`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="8e07a-129">То есть для операндов `bool` оператор `^` возвращает тот же результат, что и [оператор неравенства](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="8e07a-130">Для операндов [целочисленных типов](../builtin-types/integral-numeric-types.md) оператор `^` вычисляет [побитовое исключающее ИЛИ](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) своих операндов.</span><span class="sxs-lookup"><span data-stu-id="8e07a-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="8e07a-131">Оператор логического ИЛИ |</span><span class="sxs-lookup"><span data-stu-id="8e07a-131">Logical OR operator |</span></span>

<span data-ttu-id="8e07a-132">Оператор `|` вычисляет логическое ИЛИ для всех своих операндов.</span><span class="sxs-lookup"><span data-stu-id="8e07a-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="8e07a-133">Результат операции `x | y` принимает значение `true`, если хотя бы один из операторов `x` или `y` имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="8e07a-134">В противном случае результат будет `false`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="8e07a-135">Оператор `|` вычисляет оба операнда, даже если левый операнд имеет значение `true`. При этом операция должна вернуть значение `true`, независимо от значения правого операнда.</span><span class="sxs-lookup"><span data-stu-id="8e07a-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="8e07a-136">В следующем примере правый операнд оператора `|` является вызовом метода, который выполняется независимо от значения левого операнда:</span><span class="sxs-lookup"><span data-stu-id="8e07a-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="8e07a-137">[Условный оператор логического ИЛИ](#conditional-logical-or-operator-) `||` также вычисляет логическое ИЛИ для своих операндов, но не вычисляет правый операнд, если левый операнд имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="8e07a-138">Для операндов [целочисленных типов](../builtin-types/integral-numeric-types.md) оператор `|` вычисляет [побитовое логическое ИЛИ](bitwise-and-shift-operators.md#logical-or-operator-) своих операндов.</span><span class="sxs-lookup"><span data-stu-id="8e07a-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a> <span data-ttu-id="8e07a-139">Условный оператор логического И &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="8e07a-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="8e07a-140">Условный оператор логического И `&&` (оператор короткого замыкания) вычисляет логическое И для своих операндов.</span><span class="sxs-lookup"><span data-stu-id="8e07a-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="8e07a-141">Результат операции `x && y` принимает значение `true`, если оба оператора `x` и `y` имеют значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="8e07a-142">В противном случае результат будет `false`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="8e07a-143">Если `x` имеет значение `false`, `y` не вычисляется.</span><span class="sxs-lookup"><span data-stu-id="8e07a-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="8e07a-144">В следующем примере правый операнд оператора `&&` является вызовом метода, который не выполняется, если левый операнд имеет значение `false`:</span><span class="sxs-lookup"><span data-stu-id="8e07a-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="8e07a-145">[Оператор логического И](#logical-and-operator-) `&` также вычисляет логическое И для своих операндов, но он всегда вычисляет оба операнда.</span><span class="sxs-lookup"><span data-stu-id="8e07a-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="8e07a-146">Условный оператор логического ИЛИ ||</span><span class="sxs-lookup"><span data-stu-id="8e07a-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="8e07a-147">Условный оператор логического ИЛИ `||` (оператор короткого замыкания) вычисляет логическое ИЛИ для своих операндов.</span><span class="sxs-lookup"><span data-stu-id="8e07a-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="8e07a-148">Результат операции `x || y` принимает значение `true`, если хотя бы один из операторов `x` или `y` имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="8e07a-149">В противном случае результат будет `false`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="8e07a-150">Если `x` имеет значение `true`, `y` не вычисляется.</span><span class="sxs-lookup"><span data-stu-id="8e07a-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="8e07a-151">В следующем примере правый операнд оператора `||` является вызовом метода, который не выполняется, если левый операнд имеет значение `true`:</span><span class="sxs-lookup"><span data-stu-id="8e07a-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="8e07a-152">[Оператор логического ИЛИ](#logical-or-operator-) `|` также вычисляет логическое ИЛИ для своих операндов, но всегда вычисляет оба операнда.</span><span class="sxs-lookup"><span data-stu-id="8e07a-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="8e07a-153">Операторы, допускающие логическое значение NULL</span><span class="sxs-lookup"><span data-stu-id="8e07a-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="8e07a-154">Для операндов `bool?` операторы `&` и `|` поддерживают троичную логику.</span><span class="sxs-lookup"><span data-stu-id="8e07a-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="8e07a-155">Семантика этих операторов определяется по следующей таблице:</span><span class="sxs-lookup"><span data-stu-id="8e07a-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="8e07a-156">x</span><span class="sxs-lookup"><span data-stu-id="8e07a-156">x</span></span>|<span data-ttu-id="8e07a-157">y</span><span class="sxs-lookup"><span data-stu-id="8e07a-157">y</span></span>|<span data-ttu-id="8e07a-158">x&y</span><span class="sxs-lookup"><span data-stu-id="8e07a-158">x&y</span></span>|<span data-ttu-id="8e07a-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="8e07a-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="8e07a-160">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-160">true</span></span>|<span data-ttu-id="8e07a-161">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-161">true</span></span>|<span data-ttu-id="8e07a-162">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-162">true</span></span>|<span data-ttu-id="8e07a-163">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-163">true</span></span>|  
|<span data-ttu-id="8e07a-164">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-164">true</span></span>|<span data-ttu-id="8e07a-165">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-165">false</span></span>|<span data-ttu-id="8e07a-166">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-166">false</span></span>|<span data-ttu-id="8e07a-167">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-167">true</span></span>|  
|<span data-ttu-id="8e07a-168">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-168">true</span></span>|<span data-ttu-id="8e07a-169">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-169">null</span></span>|<span data-ttu-id="8e07a-170">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-170">null</span></span>|<span data-ttu-id="8e07a-171">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-171">true</span></span>|  
|<span data-ttu-id="8e07a-172">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-172">false</span></span>|<span data-ttu-id="8e07a-173">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-173">true</span></span>|<span data-ttu-id="8e07a-174">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-174">false</span></span>|<span data-ttu-id="8e07a-175">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-175">true</span></span>|  
|<span data-ttu-id="8e07a-176">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-176">false</span></span>|<span data-ttu-id="8e07a-177">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-177">false</span></span>|<span data-ttu-id="8e07a-178">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-178">false</span></span>|<span data-ttu-id="8e07a-179">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-179">false</span></span>|  
|<span data-ttu-id="8e07a-180">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-180">false</span></span>|<span data-ttu-id="8e07a-181">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-181">null</span></span>|<span data-ttu-id="8e07a-182">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-182">false</span></span>|<span data-ttu-id="8e07a-183">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-183">null</span></span>|  
|<span data-ttu-id="8e07a-184">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-184">null</span></span>|<span data-ttu-id="8e07a-185">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-185">true</span></span>|<span data-ttu-id="8e07a-186">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-186">null</span></span>|<span data-ttu-id="8e07a-187">true</span><span class="sxs-lookup"><span data-stu-id="8e07a-187">true</span></span>|  
|<span data-ttu-id="8e07a-188">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-188">null</span></span>|<span data-ttu-id="8e07a-189">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-189">false</span></span>|<span data-ttu-id="8e07a-190">false</span><span class="sxs-lookup"><span data-stu-id="8e07a-190">false</span></span>|<span data-ttu-id="8e07a-191">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-191">null</span></span>|  
|<span data-ttu-id="8e07a-192">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-192">null</span></span>|<span data-ttu-id="8e07a-193">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-193">null</span></span>|<span data-ttu-id="8e07a-194">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-194">null</span></span>|<span data-ttu-id="8e07a-195">null</span><span class="sxs-lookup"><span data-stu-id="8e07a-195">null</span></span>|  

<span data-ttu-id="8e07a-196">Поведение этих операторов отличается от типичного поведения операторов, допускающих значение NULL.</span><span class="sxs-lookup"><span data-stu-id="8e07a-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="8e07a-197">Как правило, оператор, который определяется для операндов типа значения, можно также использовать с соответствующими операндами типа, допускающего значение NULL.</span><span class="sxs-lookup"><span data-stu-id="8e07a-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="8e07a-198">Такой оператор возвращает `null`, если какой-либо из операндов имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="8e07a-199">При этом операторы `&` и `|` могут возвращать отличное от NULL значение, даже если один из операндов имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="8e07a-200">См. подробнее о поведении операторов, допускающих значение NULL, в разделе [Операторы с нулификацией](../builtin-types/nullable-value-types.md#lifted-operators) в статье [Типы, допускающие значение NULL](../builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="8e07a-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="8e07a-201">Вы также можете также использовать операторы `!` и `^` с операндами `bool?`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="8e07a-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="8e07a-202">Условные логические операторы `&&` и `||` не поддерживают операнды типа `bool?`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="8e07a-203">Составное присваивание</span><span class="sxs-lookup"><span data-stu-id="8e07a-203">Compound assignment</span></span>

<span data-ttu-id="8e07a-204">Для бинарного оператора `op` выражение составного присваивания в форме</span><span class="sxs-lookup"><span data-stu-id="8e07a-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="8e07a-205">эквивалентно</span><span class="sxs-lookup"><span data-stu-id="8e07a-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="8e07a-206">за исключением того, что `x` вычисляется только один раз.</span><span class="sxs-lookup"><span data-stu-id="8e07a-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="8e07a-207">Операторы `&`, `|` и `^` поддерживают составное присваивание, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="8e07a-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> <span data-ttu-id="8e07a-208">Условные логические операторы `&&` и `||` не поддерживают составное присваивание.</span><span class="sxs-lookup"><span data-stu-id="8e07a-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="8e07a-209">Приоритет операторов</span><span class="sxs-lookup"><span data-stu-id="8e07a-209">Operator precedence</span></span>

<span data-ttu-id="8e07a-210">В следующем списке перечислены логические операторы в порядке убывания приоритета:</span><span class="sxs-lookup"><span data-stu-id="8e07a-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="8e07a-211">Оператор логического отрицания `!`</span><span class="sxs-lookup"><span data-stu-id="8e07a-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="8e07a-212">Оператор логического И `&`</span><span class="sxs-lookup"><span data-stu-id="8e07a-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="8e07a-213">Оператор логического исключающего ИЛИ `^`</span><span class="sxs-lookup"><span data-stu-id="8e07a-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="8e07a-214">Оператор логического ИЛИ `|`</span><span class="sxs-lookup"><span data-stu-id="8e07a-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="8e07a-215">Условный оператор логического И `&&`</span><span class="sxs-lookup"><span data-stu-id="8e07a-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="8e07a-216">Условный оператор логического ИЛИ `||`</span><span class="sxs-lookup"><span data-stu-id="8e07a-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="8e07a-217">Порядок вычисления, определяемый приоритетом операторов, можно изменить с помощью скобок (`()`).</span><span class="sxs-lookup"><span data-stu-id="8e07a-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="8e07a-218">Полный список операторов C#, упорядоченный по уровню приоритета, можно найти в разделе [Приоритет операторов](index.md#operator-precedence) статьи [Операторы C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="8e07a-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="8e07a-219">Возможность перегрузки оператора</span><span class="sxs-lookup"><span data-stu-id="8e07a-219">Operator overloadability</span></span>

<span data-ttu-id="8e07a-220">Определяемый пользователем тип может [перегружать](operator-overloading.md) операторы `!`, `&`, `|` и `^`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="8e07a-221">При перегрузке бинарного оператора соответствующий оператор составного присваивания также неявно перегружается.</span><span class="sxs-lookup"><span data-stu-id="8e07a-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="8e07a-222">Определяемый пользователем тип не может перегружать оператор составного присваивания явным образом.</span><span class="sxs-lookup"><span data-stu-id="8e07a-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="8e07a-223">Определяемый пользователем тип не может перегружать условные логические операторы `&&` и `||`.</span><span class="sxs-lookup"><span data-stu-id="8e07a-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="8e07a-224">При этом, если определяемый пользователем тип каким-либо образом перегружает операторы [true и false](true-false-operators.md) и операторы `&` и `|`, операция `&&` или `||` может быть применена для операндов этого типа.</span><span class="sxs-lookup"><span data-stu-id="8e07a-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="8e07a-225">Дополнительные сведения см. в разделе [Пользовательские условные логические операторы](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) в [Спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="8e07a-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8e07a-226">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="8e07a-226">C# language specification</span></span>

<span data-ttu-id="8e07a-227">Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="8e07a-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8e07a-228">Оператор логического отрицания</span><span class="sxs-lookup"><span data-stu-id="8e07a-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="8e07a-229">Логические операторы</span><span class="sxs-lookup"><span data-stu-id="8e07a-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="8e07a-230">Условные логические операторы</span><span class="sxs-lookup"><span data-stu-id="8e07a-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="8e07a-231">Составное присваивание</span><span class="sxs-lookup"><span data-stu-id="8e07a-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="8e07a-232">См. также</span><span class="sxs-lookup"><span data-stu-id="8e07a-232">See also</span></span>

- [<span data-ttu-id="8e07a-233">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="8e07a-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8e07a-234">Операторы в C#</span><span class="sxs-lookup"><span data-stu-id="8e07a-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="8e07a-235">Побитовые операторы и операторы сдвига</span><span class="sxs-lookup"><span data-stu-id="8e07a-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
