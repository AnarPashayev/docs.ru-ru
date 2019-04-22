---
title: long. Справочник по C#
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: 997ce7399dc9742076932b213811abd1f847e60b
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613295"
---
# <a name="long-c-reference"></a><span data-ttu-id="7ca7c-102">long (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="7ca7c-102">long (C# Reference)</span></span>

<span data-ttu-id="7ca7c-103">`long` обозначает целочисленный тип данных, в котором хранятся значения, размер и диапазон которых приведен в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="7ca7c-104">Тип</span><span class="sxs-lookup"><span data-stu-id="7ca7c-104">Type</span></span>|<span data-ttu-id="7ca7c-105">Диапазон</span><span class="sxs-lookup"><span data-stu-id="7ca7c-105">Range</span></span>|<span data-ttu-id="7ca7c-106">Размер</span><span class="sxs-lookup"><span data-stu-id="7ca7c-106">Size</span></span>|<span data-ttu-id="7ca7c-107">Тип .NET</span><span class="sxs-lookup"><span data-stu-id="7ca7c-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`long`|<span data-ttu-id="7ca7c-108">От -9 223 372 036 854 775 808 до 9 223 372 036 854 775 807</span><span class="sxs-lookup"><span data-stu-id="7ca7c-108">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="7ca7c-109">64-разрядное целое число со знаком</span><span class="sxs-lookup"><span data-stu-id="7ca7c-109">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="7ca7c-110">Литералы</span><span class="sxs-lookup"><span data-stu-id="7ca7c-110">Literals</span></span>

<span data-ttu-id="7ca7c-111">Переменную `long` можно объявить и инициализировать, назначив ей десятичный, шестнадцатеричный или (начиная с C# 7.0) двоичный литерал.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-111">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>

<span data-ttu-id="7ca7c-112">В следующем примере целые числа, равные 4 294 967 296 и представленные в виде десятичного, шестнадцатеричного и двоичного литерала, назначаются значениям `long`.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-112">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]

> [!NOTE]
> <span data-ttu-id="7ca7c-113">Для обозначения шестнадцатеричного литерала используйте префикс `0x` или `0X`, а для обозначения двоичного литерала — префикс `0b` или `0B`.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="7ca7c-114">У десятичных литералов префиксов нет.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="7ca7c-115">Начиная с C# 7.0 было добавлено несколько возможностей для повышения удобства чтения.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span>
- <span data-ttu-id="7ca7c-116">В C# 7.0 поддерживается использование символа подчеркивания (`_`) в качестве разделителя цифр.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="7ca7c-117">В C# 7.2 поддерживается использование `_` (после префикса) в качестве разделителя для двоичного или шестнадцатеричного литерала.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="7ca7c-118">Десятичный литерал не может начинаться с символа подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="7ca7c-119">Ниже приведено несколько примеров.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-119">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

<span data-ttu-id="7ca7c-120">Целочисленные литералы могут также содержать суффикс, обозначающий тип.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-120">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="7ca7c-121">Суффикс `L` обозначает `long`.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-121">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="7ca7c-122">В следующем примере суффикс `L` используется для обозначения длинного целого числа:</span><span class="sxs-lookup"><span data-stu-id="7ca7c-122">The following example uses the `L` suffix to denote a long integer:</span></span>

```csharp
long value = 4294967296L;
```

> [!NOTE]
> <span data-ttu-id="7ca7c-123">Также в качестве суффикса можно использовать строчную букву "I".</span><span class="sxs-lookup"><span data-stu-id="7ca7c-123">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="7ca7c-124">Однако при этом выдается предупреждение компилятора, так как букву "l" легко перепутать с цифрой "1".</span><span class="sxs-lookup"><span data-stu-id="7ca7c-124">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="7ca7c-125">Для ясности используйте "L".</span><span class="sxs-lookup"><span data-stu-id="7ca7c-125">Use "L" for clarity.</span></span>

<span data-ttu-id="7ca7c-126">При использовании суффикса `L` тип целочисленного литерала определяется как `long` или [ulong](../../../csharp/language-reference/keywords/ulong.md) в зависимости от его размера.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-126">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="7ca7c-127">В данном случае это тип `long`, поскольку его диапазон меньше, чем требуется для типа [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="7ca7c-127">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>

<span data-ttu-id="7ca7c-128">Обычно суффикс используется для вызова перегруженных методов.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-128">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="7ca7c-129">Например, следующие перегруженные методы имеют параметры типов `long` и [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="7ca7c-129">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(long l) {}
```

<span data-ttu-id="7ca7c-130">Суффикс `L` обеспечивает вызов нужной перегрузки:</span><span class="sxs-lookup"><span data-stu-id="7ca7c-130">The `L` suffix guarantees that the correct overload is called:</span></span>

```csharp
SampleMethod(5);    // Calls the method with the int parameter
SampleMethod(5L);   // Calls the method with the long parameter
```

<span data-ttu-id="7ca7c-131">Если целочисленный литерал не имеет суффикса, его типом будет первый из следующих типов, в котором может быть представлено его значение:</span><span class="sxs-lookup"><span data-stu-id="7ca7c-131">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="7ca7c-132">int</span><span class="sxs-lookup"><span data-stu-id="7ca7c-132">int</span></span>](int.md)
2. [<span data-ttu-id="7ca7c-133">uint</span><span class="sxs-lookup"><span data-stu-id="7ca7c-133">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="7ca7c-134">ulong</span><span class="sxs-lookup"><span data-stu-id="7ca7c-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)

<span data-ttu-id="7ca7c-135">Литерал 4294967296 в предыдущем примере имеет тип `long`, поскольку выходит за пределы типа [uint](../../../csharp/language-reference/keywords/uint.md) (объемы хранения целочисленных типов см. в [таблице целых типов](../../../csharp/language-reference/keywords/integral-types-table.md)).</span><span class="sxs-lookup"><span data-stu-id="7ca7c-135">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>

<span data-ttu-id="7ca7c-136">Тип `long` можно использовать с другими целочисленными типами в том же выражении, в случае чего выражение вычисляется как `long` (или [bool](../../../csharp/language-reference/keywords/bool.md) для реляционных или логических выражений).</span><span class="sxs-lookup"><span data-stu-id="7ca7c-136">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="7ca7c-137">Например, следующее выражение вычисляется как `long`:</span><span class="sxs-lookup"><span data-stu-id="7ca7c-137">For example, the following expression evaluates as `long`:</span></span>

```csharp
898L + 88
```

<span data-ttu-id="7ca7c-138">Сведения об арифметических выражениях, в которых одновременно используются переменные типов с плавающей запятой и целочисленных типов, см. в разделах [float](../../../csharp/language-reference/keywords/float.md) и [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="7ca7c-138">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="7ca7c-139">Преобразования</span><span class="sxs-lookup"><span data-stu-id="7ca7c-139">Conversions</span></span>

<span data-ttu-id="7ca7c-140">Существует предопределенное неявное преобразование типа `long` в тип [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) или [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="7ca7c-140">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="7ca7c-141">В противном случае необходимо использовать приведение.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-141">Otherwise a cast must be used.</span></span> <span data-ttu-id="7ca7c-142">Например, следующий оператор вызывает ошибку компиляции без явного приведения:</span><span class="sxs-lookup"><span data-stu-id="7ca7c-142">For example, the following statement will produce a compilation error without an explicit cast:</span></span>

```csharp
int x = 8L;        // Error: no implicit conversion from long to int
int y = (int)8L;   // OK: explicit conversion to int
```

<span data-ttu-id="7ca7c-143">Существует предопределенное неявное преобразование типа [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md) или [char](../../../csharp/language-reference/keywords/char.md) в `long`.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-143">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>

<span data-ttu-id="7ca7c-144">Обратите внимание, что неявного преобразования типов с плавающей запятой в тип `long` не существует.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-144">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="7ca7c-145">Например, следующая инструкция приводит к ошибке компилятора, если не выполнить явное приведение типов:</span><span class="sxs-lookup"><span data-stu-id="7ca7c-145">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
long x = 3.0;         // Error: no implicit conversion from double
long y = (long)3.0;   // OK: explicit conversion
```

## <a name="c-language-specification"></a><span data-ttu-id="7ca7c-146">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="7ca7c-146">C# Language Specification</span></span>

<span data-ttu-id="7ca7c-147">Дополнительные сведения см. в разделе [Целочисленные типы](~/_csharplang/spec/types.md#integral-types) в [Спецификации языка C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ca7c-147">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="7ca7c-148">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="7ca7c-148">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ca7c-149">См. также</span><span class="sxs-lookup"><span data-stu-id="7ca7c-149">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="7ca7c-150">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="7ca7c-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="7ca7c-151">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="7ca7c-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7ca7c-152">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="7ca7c-152">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="7ca7c-153">Таблица целых типов</span><span class="sxs-lookup"><span data-stu-id="7ca7c-153">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="7ca7c-154">Таблица встроенных типов</span><span class="sxs-lookup"><span data-stu-id="7ca7c-154">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="7ca7c-155">Таблица неявных числовых преобразований</span><span class="sxs-lookup"><span data-stu-id="7ca7c-155">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="7ca7c-156">Таблица явных числовых преобразований</span><span class="sxs-lookup"><span data-stu-id="7ca7c-156">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
