---
title: Тип данных Decimal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 4d530a8c1f85d2f0045184c05df63849047a8204
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971774"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="99427-102">Тип данных Decimal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99427-102">Decimal Data Type (Visual Basic)</span></span>
<span data-ttu-id="99427-103">Содержит знаком, 128 бит (16-байтные) значения, представляющие 96-разрядного (12-байтные) целые числа с переменной степенью 10.</span><span class="sxs-lookup"><span data-stu-id="99427-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="99427-104">Коэффициент масштабирования указывает число цифр справа от десятичного разделителя; она в диапазоне от 0 до 28.</span><span class="sxs-lookup"><span data-stu-id="99427-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="99427-105">С масштабом 0 (без десятичных разрядов), наибольшее возможное значение равно +/-79,228,162,514,264,337,593,543,950,335 (+/-7 .9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="99427-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="99427-106">Наибольшее значение равно +/-7,9228162514264337593543950335 с 28 десятичных разрядов и наименьшее ненулевое значение равно +/-0,0000000000000000000000000001, элемента (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="99427-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99427-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="99427-107">Remarks</span></span>  
 <span data-ttu-id="99427-108">`Decimal` Тип данных предоставляет наибольшее количество значащих цифр для числа.</span><span class="sxs-lookup"><span data-stu-id="99427-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="99427-109">Он поддерживает до 29 значащих цифр и может представлять значения, превышающие 7,9 228 x 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="99427-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="99427-110">Это особенно хорошо подходит для вычислений, такие как финансовые, который требуется большое количество цифр, но не допускает ошибки округления.</span><span class="sxs-lookup"><span data-stu-id="99427-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>  
  
 <span data-ttu-id="99427-111">Значение по умолчанию для типа `Decimal` — 0.</span><span class="sxs-lookup"><span data-stu-id="99427-111">The default value of `Decimal` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="99427-112">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="99427-112">Programming Tips</span></span>  
  
- <span data-ttu-id="99427-113">**Точность.**</span><span class="sxs-lookup"><span data-stu-id="99427-113">**Precision.**</span></span> <span data-ttu-id="99427-114">`Decimal` не является типом данных с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="99427-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="99427-115">`Decimal` Структура содержит значение двоичное целое число, а также бита знака и целое число, указывающее, какая часть значения является десятичной дробью коэффициент масштабирования.</span><span class="sxs-lookup"><span data-stu-id="99427-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="99427-116">По этой причине `Decimal` числа имеют более точное представление в памяти, чем типы с плавающей запятой (`Single` и `Double`).</span><span class="sxs-lookup"><span data-stu-id="99427-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>  
  
- <span data-ttu-id="99427-117">**Производительность.**</span><span class="sxs-lookup"><span data-stu-id="99427-117">**Performance.**</span></span> <span data-ttu-id="99427-118">`Decimal` Тип данных является самым медленным всех числовых типов.</span><span class="sxs-lookup"><span data-stu-id="99427-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="99427-119">Следует взвесить важность точности с производительностью, прежде чем выбрать тип данных.</span><span class="sxs-lookup"><span data-stu-id="99427-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>  
  
- <span data-ttu-id="99427-120">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="99427-120">**Widening.**</span></span> <span data-ttu-id="99427-121">`Decimal` Тип данных можно расширить до `Single` или `Double`.</span><span class="sxs-lookup"><span data-stu-id="99427-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="99427-122">Это означает, что вы можете преобразовать `Decimal` ни с одной из этих типов без возникновения <xref:System.OverflowException?displayProperty=nameWithType> ошибки.</span><span class="sxs-lookup"><span data-stu-id="99427-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="99427-123">**Замыкающие нули.**</span><span class="sxs-lookup"><span data-stu-id="99427-123">**Trailing Zeros.**</span></span> <span data-ttu-id="99427-124">Visual Basic не хранит конечные нули в `Decimal` литерала.</span><span class="sxs-lookup"><span data-stu-id="99427-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="99427-125">Тем не менее `Decimal` переменная сохраняет любые конечные нули, полученные в результате вычислений.</span><span class="sxs-lookup"><span data-stu-id="99427-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="99427-126">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="99427-126">The following example illustrates this.</span></span>  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     <span data-ttu-id="99427-127">Выходные данные `MsgBox` в предыдущем примере выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="99427-127">The output of `MsgBox` in the preceding example is as follows:</span></span>  
  
     <span data-ttu-id="99427-128">D1 = 2.375, d2 = 1.625 d3 = 4.000 d4 = 4</span><span class="sxs-lookup"><span data-stu-id="99427-128">d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4</span></span>  
  
- <span data-ttu-id="99427-129">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="99427-129">**Type Characters.**</span></span> <span data-ttu-id="99427-130">При добавлении к литералу символа типа литерала `D` производится принудительное приведение литерала к типу данных `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="99427-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="99427-131">При добавлении символа идентификатора типа `@` к любому идентификатору производится принудительное приведение этого идентификатора к типу `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="99427-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>  
  
- <span data-ttu-id="99427-132">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="99427-132">**Framework Type.**</span></span> <span data-ttu-id="99427-133">В .NET Framework данный тип соответствует структуре <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="99427-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="99427-134">Диапазон</span><span class="sxs-lookup"><span data-stu-id="99427-134">Range</span></span>  
 <span data-ttu-id="99427-135">Может потребоваться использовать `D` символ, чтобы назначить большое значение для типа `Decimal` переменная или константа.</span><span class="sxs-lookup"><span data-stu-id="99427-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="99427-136">Это требование обусловлено тем, компилятор интерпретирует литерал как `Long` Если знак типа литерала следует литерал, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="99427-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 <span data-ttu-id="99427-137">Объявление `bigDec1` не приводит к переполнению, так как значение, которое ему присваивается попадает в диапазон для `Long`.</span><span class="sxs-lookup"><span data-stu-id="99427-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="99427-138">`Long` Значения могут быть назначены `Decimal` переменной.</span><span class="sxs-lookup"><span data-stu-id="99427-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="99427-139">Объявление `bigDec2` возникает ошибка переполнения, поскольку, ему присваивается значение слишком велико для `Long`.</span><span class="sxs-lookup"><span data-stu-id="99427-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="99427-140">Так как сначала числовой литерал не может интерпретироваться как `Long`, он не может быть назначен `Decimal` переменной.</span><span class="sxs-lookup"><span data-stu-id="99427-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="99427-141">Для `bigDec3`, знак типа литерала `D` решает проблему, заставив компилятор литерал как `Decimal` вместо как `Long`.</span><span class="sxs-lookup"><span data-stu-id="99427-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99427-142">См. также</span><span class="sxs-lookup"><span data-stu-id="99427-142">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="99427-143">Типы данных</span><span class="sxs-lookup"><span data-stu-id="99427-143">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="99427-144">Тип данных Single</span><span class="sxs-lookup"><span data-stu-id="99427-144">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [<span data-ttu-id="99427-145">Тип данных Double</span><span class="sxs-lookup"><span data-stu-id="99427-145">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="99427-146">Функции преобразования типов</span><span class="sxs-lookup"><span data-stu-id="99427-146">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="99427-147">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="99427-147">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="99427-148">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="99427-148">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
