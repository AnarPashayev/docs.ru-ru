---
title: Тип данных String (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 11c4f119360af386fa2c5609ea7815b9ae7a64f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647007"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="bd210-102">Тип данных String (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd210-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="bd210-103">Содержит последовательности точек неподписанный код 16-разрядное (2-байтовое) этого диапазона, в диапазоне от 0 до 65535.</span><span class="sxs-lookup"><span data-stu-id="bd210-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="bd210-104">Каждый *кодовую точку*, или код символа, представляющего отдельный символ Юникода.</span><span class="sxs-lookup"><span data-stu-id="bd210-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="bd210-105">Строки могут содержать от 0 до двух миллиардов (2 ^ 31) символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="bd210-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd210-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="bd210-106">Remarks</span></span>  
 <span data-ttu-id="bd210-107">Используйте `String` тип данных для хранения нескольких знаков, без издержек на управление массива `Char()`, массив `Char` элементов.</span><span class="sxs-lookup"><span data-stu-id="bd210-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="bd210-108">Значение по умолчанию `String` является `Nothing` (ссылкой на null).</span><span class="sxs-lookup"><span data-stu-id="bd210-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="bd210-109">Обратите внимание, что это не так же, как пустая строка (значение `""`).</span><span class="sxs-lookup"><span data-stu-id="bd210-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="bd210-110">Символы Юникода</span><span class="sxs-lookup"><span data-stu-id="bd210-110">Unicode Characters</span></span>  
 <span data-ttu-id="bd210-111">Первые 128 кодовых точек (от 0 до 127) Юникода соответствуют буквы и символы на стандартной клавиатуре США.</span><span class="sxs-lookup"><span data-stu-id="bd210-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="bd210-112">Эти первые 128 кодовых точек являются те же определяет набор символов ASCII.</span><span class="sxs-lookup"><span data-stu-id="bd210-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="bd210-113">128 кодовых точек (128-255) представляют специальные символы, такие как буквы латинского алфавита, диакритические знаки, символы валют и дроби.</span><span class="sxs-lookup"><span data-stu-id="bd210-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="bd210-114">Юникод использует остальные кодовые точки (от 256 до 65535) для широкого набора символов.</span><span class="sxs-lookup"><span data-stu-id="bd210-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="bd210-115">Сюда входят международные текстовые знаки, математические и технические символы и диакритические знаки.</span><span class="sxs-lookup"><span data-stu-id="bd210-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="bd210-116">Можно использовать методы, такие как <xref:System.Char.IsDigit%2A> и <xref:System.Char.IsPunctuation%2A> на отдельный символ в `String` переменной, можно определить ее классификации Юникода.</span><span class="sxs-lookup"><span data-stu-id="bd210-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="bd210-117">Требования к формату</span><span class="sxs-lookup"><span data-stu-id="bd210-117">Format Requirements</span></span>  
 <span data-ttu-id="bd210-118">Необходимо заключить `String` литерал в кавычках (`" "`).</span><span class="sxs-lookup"><span data-stu-id="bd210-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="bd210-119">Если необходимо включить знак кавычек, среди символов в строке, используется двух последовательных кавычек (`""`).</span><span class="sxs-lookup"><span data-stu-id="bd210-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="bd210-120">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="bd210-120">The following example illustrates this.</span></span>  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="bd210-121">Обратите внимание, что парные кавычки, которые представляют кавычки в строке не зависят от кавычек в начале и конце `String` литерала.</span><span class="sxs-lookup"><span data-stu-id="bd210-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="bd210-122">Операции со строками</span><span class="sxs-lookup"><span data-stu-id="bd210-122">String Manipulations</span></span>  
 <span data-ttu-id="bd210-123">После того как строка, `String` переменной, эта строка является *неизменяемый*, который означает, что нельзя изменить его длину или содержимое.</span><span class="sxs-lookup"><span data-stu-id="bd210-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="bd210-124">При изменении строки любым способом, Visual Basic создает новую строку и закрывает предыдущую.</span><span class="sxs-lookup"><span data-stu-id="bd210-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="bd210-125">`String` Переменная затем указывает на новую строку.</span><span class="sxs-lookup"><span data-stu-id="bd210-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="bd210-126">Можно управлять содержимым `String` переменной с помощью различных строковых функций.</span><span class="sxs-lookup"><span data-stu-id="bd210-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="bd210-127">В следующем примере показано <xref:Microsoft.VisualBasic.Strings.Left%2A> функции</span><span class="sxs-lookup"><span data-stu-id="bd210-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="bd210-128">Строка, созданная другим компонентом может быть дополняются начальные или конечные пробелы.</span><span class="sxs-lookup"><span data-stu-id="bd210-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="bd210-129">Если вы получаете такие строки, можно использовать <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, и <xref:Microsoft.VisualBasic.Strings.RTrim%2A> функции для удаления этих пробелов.</span><span class="sxs-lookup"><span data-stu-id="bd210-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="bd210-130">Дополнительные сведения об операции со строками, см. в разделе [строки](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="bd210-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="bd210-131">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="bd210-131">Programming Tips</span></span>  
  
- <span data-ttu-id="bd210-132">**Отрицательные числа.**</span><span class="sxs-lookup"><span data-stu-id="bd210-132">**Negative Numbers.**</span></span> <span data-ttu-id="bd210-133">Помните, что символы удерживаемые `String` не подписаны и не может представлять отрицательные значения.</span><span class="sxs-lookup"><span data-stu-id="bd210-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="bd210-134">В любом случае не следует использовать `String` для хранения числовых значений.</span><span class="sxs-lookup"><span data-stu-id="bd210-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
- <span data-ttu-id="bd210-135">**Вопросы взаимодействия.**</span><span class="sxs-lookup"><span data-stu-id="bd210-135">**Interop Considerations.**</span></span> <span data-ttu-id="bd210-136">При взаимодействии с компонентами, которые не написаны для платформы .NET Framework, например, автоматизация или COM-объекты, помните, что символы строки имеют другой размер (8 бит) в других средах.</span><span class="sxs-lookup"><span data-stu-id="bd210-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="bd210-137">Если вы передаете 8-разрядных символов строкового аргумента такому компоненту, объявите ее в качестве `Byte()`, массив `Byte` элементов, вместо `String` в новом коде Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bd210-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="bd210-138">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="bd210-138">**Type Characters.**</span></span> <span data-ttu-id="bd210-139">Добавление знак типа идентификатора `$` к любому идентификатору производится принудительное для `String` тип данных.</span><span class="sxs-lookup"><span data-stu-id="bd210-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="bd210-140">`String` не имеет тип литерала символа.</span><span class="sxs-lookup"><span data-stu-id="bd210-140">`String` has no literal type character.</span></span> <span data-ttu-id="bd210-141">Однако компилятор обрабатывает литералы, заключенные в кавычки (`" "`) как `String`.</span><span class="sxs-lookup"><span data-stu-id="bd210-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
- <span data-ttu-id="bd210-142">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="bd210-142">**Framework Type.**</span></span> <span data-ttu-id="bd210-143">Соответствующий тип в .NET Framework — <xref:System.String?displayProperty=nameWithType> класса.</span><span class="sxs-lookup"><span data-stu-id="bd210-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd210-144">См. также</span><span class="sxs-lookup"><span data-stu-id="bd210-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="bd210-145">Типы данных</span><span class="sxs-lookup"><span data-stu-id="bd210-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="bd210-146">Тип данных Char</span><span class="sxs-lookup"><span data-stu-id="bd210-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="bd210-147">Функции преобразования типов</span><span class="sxs-lookup"><span data-stu-id="bd210-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="bd210-148">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="bd210-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="bd210-149">Практическое руководство. Вызов функции Windows, принимающей значение беззнакового типа</span><span class="sxs-lookup"><span data-stu-id="bd210-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="bd210-150">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="bd210-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
