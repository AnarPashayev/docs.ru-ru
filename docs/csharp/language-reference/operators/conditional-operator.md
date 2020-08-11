---
title: Оператор ?:. Справочник по C#
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: fcde0476935108122d7f7e825d701e48952873f6
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916851"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ad30a-102">Оператор ?: (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="ad30a-102">?: operator (C# reference)</span></span>

<span data-ttu-id="ad30a-103">Условный оператор `?:`, известный как тернарный условный оператор, вычисляет логическое выражение и возвращает результат вычисления одного из двух выражений в зависимости от того, чему равно значение логического выражения: `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="ad30a-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="ad30a-104">Для условного оператора используется следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="ad30a-104">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="ad30a-105">Выражение `condition` должно принимать значение `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="ad30a-105">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="ad30a-106">Если `condition` принимает значение `true`, вычисляется выражение `consequent`, а результат становится результатом операции.</span><span class="sxs-lookup"><span data-stu-id="ad30a-106">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="ad30a-107">Если `condition` принимает значение `false`, вычисляется выражение `alternative`, а результат становится результатом операции.</span><span class="sxs-lookup"><span data-stu-id="ad30a-107">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="ad30a-108">Вычисляется только выражение `consequent` или `alternative`.</span><span class="sxs-lookup"><span data-stu-id="ad30a-108">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="ad30a-109">Параметры `consequent` и `alternative` должны быть одинакового типа, или должно существовать неявное преобразование из одного типа в другой.</span><span class="sxs-lookup"><span data-stu-id="ad30a-109">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="ad30a-110">Условный оператор имеет правую ассоциативность, то есть выражение формы.</span><span class="sxs-lookup"><span data-stu-id="ad30a-110">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="ad30a-111">вычисляется как</span><span class="sxs-lookup"><span data-stu-id="ad30a-111">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="ad30a-112">Вы можете использовать следующий мнемонический прием, чтобы запомнить, как оценивается условный оператор:</span><span class="sxs-lookup"><span data-stu-id="ad30a-112">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="ad30a-113">В следующем примере иллюстрируется использование условного оператора:</span><span class="sxs-lookup"><span data-stu-id="ad30a-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="ad30a-114">Условное выражение REF</span><span class="sxs-lookup"><span data-stu-id="ad30a-114">Conditional ref expression</span></span>

<span data-ttu-id="ad30a-115">Начиная с версии C# 7.2, [ссылочные локальные](../keywords/ref.md#ref-locals) и [предназначенные только для чтения ссылочные локальные](../keywords/ref.md#ref-readonly-locals) переменные можно присваивать условным образом с использованием условного ссылочного выражения.</span><span class="sxs-lookup"><span data-stu-id="ad30a-115">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="ad30a-116">Кроме того, условное ссылочное выражение можно использовать как [возвращаемое ссылочное значение](../keywords/ref.md#reference-return-values) или как [аргумент метода `ref`](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="ad30a-116">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="ad30a-117">Для условного выражения REF используется следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="ad30a-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="ad30a-118">Подобно исходному условному оператору, условное выражение REF вычисляет только одно из двух выражений: `consequent` или `alternative`.</span><span class="sxs-lookup"><span data-stu-id="ad30a-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="ad30a-119">Для условного выражения REF тип `consequent` и `alternative` должны совпадать.</span><span class="sxs-lookup"><span data-stu-id="ad30a-119">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="ad30a-120">В следующем примере иллюстрируется использование условного выражения REF:</span><span class="sxs-lookup"><span data-stu-id="ad30a-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="ad30a-121">Условный оператор и оператор `if..else`</span><span class="sxs-lookup"><span data-stu-id="ad30a-121">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="ad30a-122">Если использовать условный оператор с оператором [if-else](../keywords/if-else.md), может получиться более лаконичный код в случаях, когда необходимо условно вычислить значение.</span><span class="sxs-lookup"><span data-stu-id="ad30a-122">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="ad30a-123">В следующем примере иллюстрируются два вида классификации целого числа как положительного или отрицательного:</span><span class="sxs-lookup"><span data-stu-id="ad30a-123">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="ad30a-124">Возможность перегрузки оператора</span><span class="sxs-lookup"><span data-stu-id="ad30a-124">Operator overloadability</span></span>

<span data-ttu-id="ad30a-125">Определяемый пользователем тип не может перегружать условный оператор.</span><span class="sxs-lookup"><span data-stu-id="ad30a-125">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ad30a-126">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="ad30a-126">C# language specification</span></span>

<span data-ttu-id="ad30a-127">Дополнительные сведения см. в разделе [Условный оператор](~/_csharplang/spec/expressions.md#conditional-operator) статьи [Предварительная спецификация C# 6.0](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ad30a-127">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="ad30a-128">См. сведения об условном ссылочном выражении в [примечании к функциям](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span><span class="sxs-lookup"><span data-stu-id="ad30a-128">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad30a-129">См. также</span><span class="sxs-lookup"><span data-stu-id="ad30a-129">See also</span></span>

- [<span data-ttu-id="ad30a-130">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="ad30a-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ad30a-131">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="ad30a-131">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="ad30a-132">if-else (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="ad30a-132">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="ad30a-133">[Операторы ?. и ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="ad30a-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="ad30a-134">Операторы ?? и ??=</span><span class="sxs-lookup"><span data-stu-id="ad30a-134">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="ad30a-135">Ключевое слово ref</span><span class="sxs-lookup"><span data-stu-id="ad30a-135">ref keyword</span></span>](../keywords/ref.md)
