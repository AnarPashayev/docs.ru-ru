---
title: Синтаксис, используемый свойством DebugView (Visual Basic)
description: Описание синтаксиса, используемого свойством DebugView для получения строкового представления деревьев выражений
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 1b2a1164f02208cc7578820d8f8ed3bc145fb5b8
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196534"
---
# <a name="debugview-syntax"></a><span data-ttu-id="877e2-103">Синтаксис `DebugView`</span><span class="sxs-lookup"><span data-stu-id="877e2-103">`DebugView` syntax</span></span> 

<span data-ttu-id="877e2-104">`DebugView` Свойство (доступно только в том случае, при отладке) предоставляет визуализации строка деревьев выражений.</span><span class="sxs-lookup"><span data-stu-id="877e2-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="877e2-105">Большую часть синтаксиса достаточно прост для понимания; в следующих разделах описываются особые случаи.</span><span class="sxs-lookup"><span data-stu-id="877e2-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="877e2-106">Каждый пример сопровождается типа блока комментария, содержащее `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="877e2-106">Each example is followed by a comment block containing the `DebugView`.</span></span> 

## <a name="parameterexpression"></a><span data-ttu-id="877e2-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="877e2-107">ParameterExpression</span></span>

<span data-ttu-id="877e2-108">В начале имен переменных <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> отображается символ "$".</span><span class="sxs-lookup"><span data-stu-id="877e2-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="877e2-109">Если параметр не имеет имени, оно назначается автоматически, например `$var1` или `$var2`.</span><span class="sxs-lookup"><span data-stu-id="877e2-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="877e2-110">Примеры</span><span class="sxs-lookup"><span data-stu-id="877e2-110">Examples</span></span>

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a><span data-ttu-id="877e2-111">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="877e2-111">ConstantExpressions</span></span>

<span data-ttu-id="877e2-112">Для объектов <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType>, представляющих целочисленные значения, строки и `null`, отображается значение константы.</span><span class="sxs-lookup"><span data-stu-id="877e2-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="877e2-113">Для некоторых числовых типов суффикс добавляется к значению:</span><span class="sxs-lookup"><span data-stu-id="877e2-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="877e2-114">Тип</span><span class="sxs-lookup"><span data-stu-id="877e2-114">Type</span></span> | <span data-ttu-id="877e2-115">Ключевое слово</span><span class="sxs-lookup"><span data-stu-id="877e2-115">Keyword</span></span> | <span data-ttu-id="877e2-116">Суффикс</span><span class="sxs-lookup"><span data-stu-id="877e2-116">Suffix</span></span> |  
|--|--|--|
| <xref:System.UInt32> | [<span data-ttu-id="877e2-117">UInteger</span><span class="sxs-lookup"><span data-stu-id="877e2-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="877e2-118">U</span><span class="sxs-lookup"><span data-stu-id="877e2-118">U</span></span> |
| <xref:System.Int64> | [<span data-ttu-id="877e2-119">Long</span><span class="sxs-lookup"><span data-stu-id="877e2-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="877e2-120">L</span><span class="sxs-lookup"><span data-stu-id="877e2-120">L</span></span> |
| <xref:System.UInt64> | [<span data-ttu-id="877e2-121">ULong</span><span class="sxs-lookup"><span data-stu-id="877e2-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="877e2-122">UL</span><span class="sxs-lookup"><span data-stu-id="877e2-122">UL</span></span> |
| <xref:System.Double> | [<span data-ttu-id="877e2-123">Double</span><span class="sxs-lookup"><span data-stu-id="877e2-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="877e2-124">D</span><span class="sxs-lookup"><span data-stu-id="877e2-124">D</span></span> |
| <xref:System.Single> | [<span data-ttu-id="877e2-125">Single</span><span class="sxs-lookup"><span data-stu-id="877e2-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="877e2-126">C</span><span class="sxs-lookup"><span data-stu-id="877e2-126">F</span></span> | 
| <xref:System.Decimal> | [<span data-ttu-id="877e2-127">Decimal</span><span class="sxs-lookup"><span data-stu-id="877e2-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="877e2-128">M</span><span class="sxs-lookup"><span data-stu-id="877e2-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="877e2-129">Примеры</span><span class="sxs-lookup"><span data-stu-id="877e2-129">Examples</span></span>

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a><span data-ttu-id="877e2-130">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="877e2-130">BlockExpression</span></span>

<span data-ttu-id="877e2-131">Если тип <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> объекта отличается от типа последнего выражения в блоке, то тип отображается в угловые скобки (`<` и `>`).</span><span class="sxs-lookup"><span data-stu-id="877e2-131">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="877e2-132">В противном случае тип объекта <xref:System.Linq.Expressions.BlockExpression> не отображается.</span><span class="sxs-lookup"><span data-stu-id="877e2-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="877e2-133">Примеры</span><span class="sxs-lookup"><span data-stu-id="877e2-133">Examples</span></span>

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object), 
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a><span data-ttu-id="877e2-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="877e2-134">LambdaExpression</span></span>

<span data-ttu-id="877e2-135">Объекты <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> отображаются вместе со своими типами делегатов.</span><span class="sxs-lookup"><span data-stu-id="877e2-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="877e2-136">Если лямбда-выражение не имеет имени, оно назначается автоматически, например `#Lambda1` или `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="877e2-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="877e2-137">Примеры</span><span class="sxs-lookup"><span data-stu-id="877e2-137">Examples</span></span>

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a><span data-ttu-id="877e2-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="877e2-138">LabelExpression</span></span>

<span data-ttu-id="877e2-139">Если указать значение по умолчанию для объекта <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, оно будет отображаться перед объектом <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="877e2-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="877e2-140">Маркер `.Label` указывает начало метки.</span><span class="sxs-lookup"><span data-stu-id="877e2-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="877e2-141">Маркер `.LabelTarget` задает конечную цель перехода для целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="877e2-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="877e2-142">Если метка не имеет имени, оно назначается автоматически, например `#Label1` или `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="877e2-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="877e2-143">Примеры</span><span class="sxs-lookup"><span data-stu-id="877e2-143">Examples</span></span>

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), 
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a><span data-ttu-id="877e2-144">Проверяемые операторы</span><span class="sxs-lookup"><span data-stu-id="877e2-144">Checked Operators</span></span>

<span data-ttu-id="877e2-145">Проверяемые операторы отображаются с `#` символа перед оператором.</span><span class="sxs-lookup"><span data-stu-id="877e2-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="877e2-146">Например, проверяемый оператор сложения отображается как `#+`.</span><span class="sxs-lookup"><span data-stu-id="877e2-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="877e2-147">Примеры</span><span class="sxs-lookup"><span data-stu-id="877e2-147">Examples</span></span>

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```