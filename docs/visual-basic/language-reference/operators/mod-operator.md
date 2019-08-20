---
title: Оператор Mod (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: c801facd95d93652414409549bb5ff2fa633748b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611523"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="b64f3-102">Оператор Mod (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b64f3-102">Mod operator (Visual Basic)</span></span>
<span data-ttu-id="b64f3-103">Делит два числа и возвращает только остаток.</span><span class="sxs-lookup"><span data-stu-id="b64f3-103">Divides two numbers and returns only the remainder.</span></span>

## <a name="syntax"></a><span data-ttu-id="b64f3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b64f3-104">Syntax</span></span>

```vb
result = number1 Mod number2
```
  
## <a name="parts"></a><span data-ttu-id="b64f3-105">Части</span><span class="sxs-lookup"><span data-stu-id="b64f3-105">Parts</span></span>  
 <span data-ttu-id="b64f3-106">`result` Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b64f3-106">`result` Required.</span></span> <span data-ttu-id="b64f3-107">Любая числовая переменная или свойство.</span><span class="sxs-lookup"><span data-stu-id="b64f3-107">Any numeric variable or property.</span></span>

 <span data-ttu-id="b64f3-108">`number1` Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b64f3-108">`number1` Required.</span></span> <span data-ttu-id="b64f3-109">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="b64f3-109">Any numeric expression.</span></span>

 <span data-ttu-id="b64f3-110">`number2` Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b64f3-110">`number2` Required.</span></span> <span data-ttu-id="b64f3-111">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="b64f3-111">Any numeric expression.</span></span>

## <a name="supported-types"></a><span data-ttu-id="b64f3-112">Поддерживаемые типы</span><span class="sxs-lookup"><span data-stu-id="b64f3-112">Supported types</span></span>
 <span data-ttu-id="b64f3-113">все числовые типы.</span><span class="sxs-lookup"><span data-stu-id="b64f3-113">All numeric types.</span></span> <span data-ttu-id="b64f3-114">К ним относятся типы без знака и тип с плавающей запятой `Decimal`и.</span><span class="sxs-lookup"><span data-stu-id="b64f3-114">This includes the unsigned and floating-point types and `Decimal`.</span></span>

## <a name="result"></a><span data-ttu-id="b64f3-115">Результат</span><span class="sxs-lookup"><span data-stu-id="b64f3-115">Result</span></span>

<span data-ttu-id="b64f3-116">Результат — остаток `number1` `number2`от деления на.</span><span class="sxs-lookup"><span data-stu-id="b64f3-116">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="b64f3-117">Например, выражение `14 Mod 4` принимает значение 2.</span><span class="sxs-lookup"><span data-stu-id="b64f3-117">For example, the expression `14 Mod 4` evaluates to 2.</span></span>

> [!NOTE]
> <span data-ttu-id="b64f3-118">Существует разница между остатком и *остатком* в математике с различными результатами для отрицательных чисел.</span><span class="sxs-lookup"><span data-stu-id="b64f3-118">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="b64f3-119">Оператор в Visual Basic, оператор .NET Framework `op_Modulus` и базовая инструкция [REM](<xref:System.Reflection.Emit.OpCodes.Rem>) Il выполняют операцию остатка. `Mod`</span><span class="sxs-lookup"><span data-stu-id="b64f3-119">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="b64f3-120">Результат `Mod` операции удерживает знак делимого, `number1`и поэтому он может быть положительным или отрицательным.</span><span class="sxs-lookup"><span data-stu-id="b64f3-120">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="b64f3-121">Результат всегда находится в диапазоне (-`number2`, `number2`), исключающем.</span><span class="sxs-lookup"><span data-stu-id="b64f3-121">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="b64f3-122">Например:</span><span class="sxs-lookup"><span data-stu-id="b64f3-122">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="b64f3-123">Примечания</span><span class="sxs-lookup"><span data-stu-id="b64f3-123">Remarks</span></span>
 <span data-ttu-id="b64f3-124">`number1` Если или `number2` является значением с плавающей запятой, то возвращается остаток от деления с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="b64f3-124">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="b64f3-125">Тип данных результата является наименьшим типом данных, который может содержать все возможные значения, являющиеся результатом деления с типами `number1` данных и. `number2`</span><span class="sxs-lookup"><span data-stu-id="b64f3-125">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>

 <span data-ttu-id="b64f3-126">Если `number1` или`number2` имеет значение [Nothing](../../../visual-basic/language-reference/nothing.md), оно считается нулевым.</span><span class="sxs-lookup"><span data-stu-id="b64f3-126">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>

 <span data-ttu-id="b64f3-127">К связанным операторам относятся следующие.</span><span class="sxs-lookup"><span data-stu-id="b64f3-127">Related operators include the following:</span></span>

- <span data-ttu-id="b64f3-128">[Оператор \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) возвращает целочисленное частное от деления.</span><span class="sxs-lookup"><span data-stu-id="b64f3-128">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="b64f3-129">Например, выражение `14 \ 4` принимает значение 3.</span><span class="sxs-lookup"><span data-stu-id="b64f3-129">For example, the expression `14 \ 4` evaluates to 3.</span></span>

- <span data-ttu-id="b64f3-130">[Оператор/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) возвращает полное частное, включая остаток, в виде числа с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="b64f3-130">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="b64f3-131">Например, результатом вычисления выражения `14 / 4` является 3,5.</span><span class="sxs-lookup"><span data-stu-id="b64f3-131">For example, the expression `14 / 4` evaluates to 3.5.</span></span>

## <a name="attempted-division-by-zero"></a><span data-ttu-id="b64f3-132">Попыток деления на ноль</span><span class="sxs-lookup"><span data-stu-id="b64f3-132">Attempted division by zero</span></span>
 <span data-ttu-id="b64f3-133">Если `number2` значение равно нулю, поведение `Mod` оператора зависит от типа данных операндов:</span><span class="sxs-lookup"><span data-stu-id="b64f3-133">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span></span>
 - <span data-ttu-id="b64f3-134">Целочисленное деление вызывает исключение <xref:System.DivideByZeroException> , если `number2` не может быть определено во время компиляции и вызывает ошибку `BC30542    Division by zero occurred while evaluating this expression` во время компиляции, `number2` если во время компиляции значение равно нулю.</span><span class="sxs-lookup"><span data-stu-id="b64f3-134">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542    Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span></span>
 - <span data-ttu-id="b64f3-135">Деление с плавающей запятой возвращает <xref:System.Double.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b64f3-135">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>

## <a name="equivalent-formula"></a><span data-ttu-id="b64f3-136">Эквивалентная формула</span><span class="sxs-lookup"><span data-stu-id="b64f3-136">Equivalent formula</span></span>
 <span data-ttu-id="b64f3-137">Выражение `a Mod b` эквивалентно любой из следующих формул:</span><span class="sxs-lookup"><span data-stu-id="b64f3-137">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>

 `a - (b * (a \ b))`

 `a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a><span data-ttu-id="b64f3-138">Точность чисел с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="b64f3-138">Floating-point imprecision</span></span>
 <span data-ttu-id="b64f3-139">При работе с числами с плавающей запятой Помните, что они не всегда имеют точное десятичное представление в памяти.</span><span class="sxs-lookup"><span data-stu-id="b64f3-139">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="b64f3-140">Это может привести к непредвиденным результатам некоторых операций, таких как сравнение значений и `Mod` оператор.</span><span class="sxs-lookup"><span data-stu-id="b64f3-140">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="b64f3-141">Дополнительные сведения см. в разделе [Устранение неполадок типов данных](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="b64f3-141">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="overloading"></a><span data-ttu-id="b64f3-142">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="b64f3-142">Overloading</span></span>
 <span data-ttu-id="b64f3-143">Оператор можно перегрузить, то есть класс или структура может переопределить его поведение. `Mod`</span><span class="sxs-lookup"><span data-stu-id="b64f3-143">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="b64f3-144">Если код применяется `Mod` к экземпляру класса или структуры, включающей такую перегрузку, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="b64f3-144">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b64f3-145">Для получения дополнительной информации см. [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b64f3-145">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="b64f3-146">Пример</span><span class="sxs-lookup"><span data-stu-id="b64f3-146">Example</span></span>
 <span data-ttu-id="b64f3-147">В следующем примере `Mod` оператор используется для деления двух чисел и возврата только остатка.</span><span class="sxs-lookup"><span data-stu-id="b64f3-147">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="b64f3-148">Если любое число является числом с плавающей запятой, результатом является число с плавающей запятой, представляющее остаток.</span><span class="sxs-lookup"><span data-stu-id="b64f3-148">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>

 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a><span data-ttu-id="b64f3-149">Пример</span><span class="sxs-lookup"><span data-stu-id="b64f3-149">Example</span></span>
 <span data-ttu-id="b64f3-150">В следующем примере показана потенциальная неточность операндов с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="b64f3-150">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="b64f3-151">В первой инструкции операнды имеют `Double`значение, а 0,2 — бесконечно повторяющуюся двоичную дробь с хранимым значением 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="b64f3-151">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="b64f3-152">Во второй инструкции символ `D` типа литерала принуждает оба операнда к `Decimal`, и 0,2 имеет точное представление.</span><span class="sxs-lookup"><span data-stu-id="b64f3-152">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>

 [!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a><span data-ttu-id="b64f3-153">См. также</span><span class="sxs-lookup"><span data-stu-id="b64f3-153">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="b64f3-154">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="b64f3-154">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="b64f3-155">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b64f3-155">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b64f3-156">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="b64f3-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b64f3-157">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="b64f3-157">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="b64f3-158">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b64f3-158">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="b64f3-159">Оператор \ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b64f3-159">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
