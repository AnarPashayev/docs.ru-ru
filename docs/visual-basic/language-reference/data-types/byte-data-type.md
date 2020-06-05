---
title: Тип данных Byte
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
ms.openlocfilehash: 97acd1bc2ff29bac6588216b9ee4a4f187078815
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374321"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="a445a-102">Тип данных Byte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a445a-102">Byte data type (Visual Basic)</span></span>

<span data-ttu-id="a445a-103">Содержит 8-битные (1-байтные) целые числа без знака в диапазоне от 0 до 255.</span><span class="sxs-lookup"><span data-stu-id="a445a-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="a445a-104">Комментарии</span><span class="sxs-lookup"><span data-stu-id="a445a-104">Remarks</span></span>

<span data-ttu-id="a445a-105">Используйте `Byte` тип данных для хранения двоичных данных.</span><span class="sxs-lookup"><span data-stu-id="a445a-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="a445a-106">Значение по умолчанию для типа `Byte` — 0.</span><span class="sxs-lookup"><span data-stu-id="a445a-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="a445a-107">Присваивания литералов</span><span class="sxs-lookup"><span data-stu-id="a445a-107">Literal assignments</span></span>

<span data-ttu-id="a445a-108">Можно объявить и инициализировать `Byte` переменную, назначив ей десятичный литерал, шестнадцатеричный литерал, Восьмеричный литерал или (начиная с Visual Basic 2017) двоичный литерал.</span><span class="sxs-lookup"><span data-stu-id="a445a-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="a445a-109">Если целочисленный литерал находится вне диапазона `Byte` (то есть если он меньше <xref:System.Byte.MinValue?displayProperty=nameWithType> или больше <xref:System.Byte.MaxValue?displayProperty=nameWithType> ), возникает ошибка компиляции.</span><span class="sxs-lookup"><span data-stu-id="a445a-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="a445a-110">В следующем примере целые числа, равные 201, представленные в виде десятичных, шестнадцатеричных и двоичных литералов, неявно преобразуются из [типа Integer](integer-data-type.md) в `byte` значения.</span><span class="sxs-lookup"><span data-stu-id="a445a-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="a445a-111">Используйте префикс `&h` или `&H` , чтобы обозначить шестнадцатеричный литерал, префикс `&b` или `&B` обозначить двоичный литерал, а также префикс `&o` или `&O` обозначить Восьмеричный литерал.</span><span class="sxs-lookup"><span data-stu-id="a445a-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="a445a-112">У десятичных литералов префиксов нет.</span><span class="sxs-lookup"><span data-stu-id="a445a-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="a445a-113">Начиная с Visual Basic 2017, можно также использовать символ подчеркивания () в `_` качестве разделителя цифр, чтобы улучшить удобочитаемость, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a445a-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="a445a-114">Начиная с Visual Basic 15,5, можно также использовать символ подчеркивания () в `_` качестве начального разделителя между префиксом и шестнадцатеричными, двоичными или восьмеричными цифрами.</span><span class="sxs-lookup"><span data-stu-id="a445a-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="a445a-115">Пример:</span><span class="sxs-lookup"><span data-stu-id="a445a-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="a445a-116">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="a445a-116">Programming tips</span></span>

- <span data-ttu-id="a445a-117">**Отрицательные числа.**</span><span class="sxs-lookup"><span data-stu-id="a445a-117">**Negative Numbers.**</span></span> <span data-ttu-id="a445a-118">Так как `Byte` является неподписанным типом, он не может представлять отрицательное число.</span><span class="sxs-lookup"><span data-stu-id="a445a-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="a445a-119">При использовании оператора унарного минуса ( `-` ) в выражении, результатом которого является тип `Byte` , Visual Basic преобразует выражение в `Short` First.</span><span class="sxs-lookup"><span data-stu-id="a445a-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
- <span data-ttu-id="a445a-120">**Преобразования формата.**</span><span class="sxs-lookup"><span data-stu-id="a445a-120">**Format Conversions.**</span></span> <span data-ttu-id="a445a-121">Когда Visual Basic считывает или записывает файлы или вызывает библиотеки DLL, методы и свойства, он может автоматически выполнять преобразование между форматами данных.</span><span class="sxs-lookup"><span data-stu-id="a445a-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="a445a-122">Двоичные данные, хранящиеся в `Byte` переменных и массивах, сохраняются во время таких преобразований формата.</span><span class="sxs-lookup"><span data-stu-id="a445a-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="a445a-123">Не следует использовать `String` переменную для двоичных данных, так как ее содержимое может быть повреждено во время преобразования между форматами ANSI и Юникод.</span><span class="sxs-lookup"><span data-stu-id="a445a-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

- <span data-ttu-id="a445a-124">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="a445a-124">**Widening.**</span></span> <span data-ttu-id="a445a-125">`Byte`Тип данных расширяется до `Short` , `UShort` ,,, `Integer` `UInteger` `Long` , `ULong` , `Decimal` , `Single` или `Double` .</span><span class="sxs-lookup"><span data-stu-id="a445a-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="a445a-126">Это означает, что можно преобразовать `Byte` в любой из этих типов без возникновения <xref:System.OverflowException?displayProperty=nameWithType> ошибки.</span><span class="sxs-lookup"><span data-stu-id="a445a-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
- <span data-ttu-id="a445a-127">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="a445a-127">**Type Characters.**</span></span> <span data-ttu-id="a445a-128">`Byte`не имеет символа типа литерала или символа типа идентификатора.</span><span class="sxs-lookup"><span data-stu-id="a445a-128">`Byte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="a445a-129">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="a445a-129">**Framework Type.**</span></span> <span data-ttu-id="a445a-130">В .NET Framework данный тип соответствует структуре <xref:System.Byte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a445a-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="a445a-131">Пример</span><span class="sxs-lookup"><span data-stu-id="a445a-131">Example</span></span>

 <span data-ttu-id="a445a-132">В следующем примере `b` — это `Byte` переменная.</span><span class="sxs-lookup"><span data-stu-id="a445a-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="a445a-133">Инструкции демонстрируют диапазон переменных и применение к нему операторов побитового сдвига.</span><span class="sxs-lookup"><span data-stu-id="a445a-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

 [!code-vb[VbVbalrDataTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#16)]  

## <a name="see-also"></a><span data-ttu-id="a445a-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a445a-134">See also</span></span>

- <xref:System.Byte?displayProperty=nameWithType>
- [<span data-ttu-id="a445a-135">Типы данных</span><span class="sxs-lookup"><span data-stu-id="a445a-135">Data Types</span></span>](index.md)
- [<span data-ttu-id="a445a-136">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="a445a-136">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="a445a-137">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="a445a-137">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="a445a-138">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="a445a-138">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
