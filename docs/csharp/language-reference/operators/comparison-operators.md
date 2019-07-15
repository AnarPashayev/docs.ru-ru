---
title: Операторы сравнения. Справочник по C#
description: Дополнительные сведения об операторах сравнения C#, которые можно использовать для проверки очередности числовых значений.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: d3e9bf1356218f223f959b423dfc048972b075d3
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661508"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="c96aa-103">Операторы сравнения (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="c96aa-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="c96aa-104">Операторы сравнения [`<` (меньше чем)](#less-than-operator-), [`>` (больше чем)](#greater-than-operator-), [`<=` (меньше или равно)](#less-than-or-equal-operator-) и [`>=` (больше или равно)](#greater-than-or-equal-operator-) (или реляционные операторы) сравнивают операнды.</span><span class="sxs-lookup"><span data-stu-id="c96aa-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="c96aa-105">Эти операторы поддерживают все [целочисленные](../builtin-types/integral-numeric-types.md) типы и типы с [плавающей запятой](../builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="c96aa-105">Those operators support all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="c96aa-106">Если какой-то из операндов операторов `==`, `<`, `>`, `<=` и `>=` не является числом (<xref:System.Double.NaN?displayProperty=nameWithType> или <xref:System.Single.NaN?displayProperty=nameWithType>), результатом операции будет `false`.</span><span class="sxs-lookup"><span data-stu-id="c96aa-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="c96aa-107">Это означает, что значение `NaN` не больше, не меньше и не равно любому другому значению `double` (или `float`), включая `NaN`.</span><span class="sxs-lookup"><span data-stu-id="c96aa-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="c96aa-108">Дополнительные сведения и примеры см. в справочных статьях по <xref:System.Double.NaN?displayProperty=nameWithType> или <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c96aa-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="c96aa-109">Типы перечисления также поддерживают операторы сравнения.</span><span class="sxs-lookup"><span data-stu-id="c96aa-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="c96aa-110">Если операнды имеют одинаковый тип [enum](../keywords/enum.md), сравниваются соответствующие значения базового целочисленного типа.</span><span class="sxs-lookup"><span data-stu-id="c96aa-110">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="c96aa-111">Операторы [`==` и `!=`](equality-operators.md) проверяют равенство или неравенство своих операндов.</span><span class="sxs-lookup"><span data-stu-id="c96aa-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="c96aa-112">Оператор "меньше чем" \<</span><span class="sxs-lookup"><span data-stu-id="c96aa-112">Less than operator \<</span></span>

<span data-ttu-id="c96aa-113">Оператор `<` возвращает `true`, если его левый операнд меньше правого. В противном случае возвращается `false`:</span><span class="sxs-lookup"><span data-stu-id="c96aa-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="c96aa-114">Оператор "больше чем" ></span><span class="sxs-lookup"><span data-stu-id="c96aa-114">Greater than operator ></span></span>

<span data-ttu-id="c96aa-115">Оператор `>` возвращает `true`, если его левый операнд больше правого. В противном случае возвращается `false`:</span><span class="sxs-lookup"><span data-stu-id="c96aa-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="c96aa-116">Оператор "меньше или равно" \<=</span><span class="sxs-lookup"><span data-stu-id="c96aa-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="c96aa-117">Оператор `<=` возвращает `true`, если его левый операнд меньше правого или равен ему. В противном случае возвращается `false`:</span><span class="sxs-lookup"><span data-stu-id="c96aa-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="c96aa-118">Оператор "больше или равно" >=</span><span class="sxs-lookup"><span data-stu-id="c96aa-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="c96aa-119">Оператор `>=` возвращает `true`, если его левый операнд больше правого или равен ему. В противном случае возвращается `false`:</span><span class="sxs-lookup"><span data-stu-id="c96aa-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="c96aa-120">Возможность перегрузки оператора</span><span class="sxs-lookup"><span data-stu-id="c96aa-120">Operator overloadability</span></span>

<span data-ttu-id="c96aa-121">Определяемый пользователем тип может [перегружать](operator-overloading.md) операторы `<`, `>`, `<=` и `>=`.</span><span class="sxs-lookup"><span data-stu-id="c96aa-121">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="c96aa-122">Если тип перегружает один из операторов `<` и `>`, он должен также перегружать операторы `<` и `>`.</span><span class="sxs-lookup"><span data-stu-id="c96aa-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="c96aa-123">Если тип перегружает один из операторов `<=` и `>=`, он должен также перегружать операторы `<=` и `>=`.</span><span class="sxs-lookup"><span data-stu-id="c96aa-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c96aa-124">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="c96aa-124">C# language specification</span></span>

<span data-ttu-id="c96aa-125">Дополнительные сведения см. в разделе [Операторы отношения и проверки типа](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) в статье по [спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c96aa-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c96aa-126">См. также</span><span class="sxs-lookup"><span data-stu-id="c96aa-126">See also</span></span>

- [<span data-ttu-id="c96aa-127">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="c96aa-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c96aa-128">Операторы в C#</span><span class="sxs-lookup"><span data-stu-id="c96aa-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="c96aa-129">Операторы равенства</span><span class="sxs-lookup"><span data-stu-id="c96aa-129">Equality operators</span></span>](equality-operators.md)
