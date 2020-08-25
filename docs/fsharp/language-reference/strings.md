---
title: строк
description: 'Узнайте, как тип "строка" F # представляет неизменяемый текст как последовательность символов Юникода.'
ms.date: 08/15/2020
ms.openlocfilehash: f6ec36feeb197bf785c702e7b626cf5cf80696ab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812215"
---
# <a name="strings"></a><span data-ttu-id="d44ed-103">строк</span><span class="sxs-lookup"><span data-stu-id="d44ed-103">Strings</span></span>

<span data-ttu-id="d44ed-104">`string`Тип представляет неизменяемый текст как последовательность символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="d44ed-104">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="d44ed-105">`string` является псевдонимом для `System.String` в .NET.</span><span class="sxs-lookup"><span data-stu-id="d44ed-105">`string` is an alias for `System.String` in .NET.</span></span>

## <a name="remarks"></a><span data-ttu-id="d44ed-106">Комментарии</span><span class="sxs-lookup"><span data-stu-id="d44ed-106">Remarks</span></span>

<span data-ttu-id="d44ed-107">Строковые литералы разделяются символом кавычки (").</span><span class="sxs-lookup"><span data-stu-id="d44ed-107">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="d44ed-108">Символ обратной косой черты ( \\ ) используется для кодирования определенных специальных символов.</span><span class="sxs-lookup"><span data-stu-id="d44ed-108">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="d44ed-109">Обратная косая черта и следующий символ вместе называются *escape-последовательностью*.</span><span class="sxs-lookup"><span data-stu-id="d44ed-109">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="d44ed-110">В следующей таблице показаны escape-последовательности, поддерживаемые в строковых литералах F #.</span><span class="sxs-lookup"><span data-stu-id="d44ed-110">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="d44ed-111">Символ</span><span class="sxs-lookup"><span data-stu-id="d44ed-111">Character</span></span>|<span data-ttu-id="d44ed-112">Escape-последовательность</span><span class="sxs-lookup"><span data-stu-id="d44ed-112">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="d44ed-113">Предупреждение</span><span class="sxs-lookup"><span data-stu-id="d44ed-113">Alert</span></span>|`\a`|
|<span data-ttu-id="d44ed-114">Отмена</span><span class="sxs-lookup"><span data-stu-id="d44ed-114">Backspace</span></span>|`\b`|
|<span data-ttu-id="d44ed-115">Перевод страницы</span><span class="sxs-lookup"><span data-stu-id="d44ed-115">Form feed</span></span>|`\f`|
|<span data-ttu-id="d44ed-116">Новая строка</span><span class="sxs-lookup"><span data-stu-id="d44ed-116">Newline</span></span>|`\n`|
|<span data-ttu-id="d44ed-117">Возврат каретки</span><span class="sxs-lookup"><span data-stu-id="d44ed-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="d44ed-118">Вкладка</span><span class="sxs-lookup"><span data-stu-id="d44ed-118">Tab</span></span>|`\t`|
|<span data-ttu-id="d44ed-119">Вертикальная табуляция</span><span class="sxs-lookup"><span data-stu-id="d44ed-119">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="d44ed-120">Обратная косая черта</span><span class="sxs-lookup"><span data-stu-id="d44ed-120">Backslash</span></span>|`\\`|
|<span data-ttu-id="d44ed-121">Знак кавычек</span><span class="sxs-lookup"><span data-stu-id="d44ed-121">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="d44ed-122">Апостроф</span><span class="sxs-lookup"><span data-stu-id="d44ed-122">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="d44ed-123">символьный формат Юникода</span><span class="sxs-lookup"><span data-stu-id="d44ed-123">Unicode character</span></span>|<span data-ttu-id="d44ed-124">`\DDD` (где `D` обозначает десятичную цифру, диапазон 000-255, например `\231` = "c")</span><span class="sxs-lookup"><span data-stu-id="d44ed-124">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="d44ed-125">символьный формат Юникода</span><span class="sxs-lookup"><span data-stu-id="d44ed-125">Unicode character</span></span>|<span data-ttu-id="d44ed-126">`\xHH` (где `H` обозначает шестнадцатеричную цифру; диапазон от 00 до FF; например, `\xE7` = "c")</span><span class="sxs-lookup"><span data-stu-id="d44ed-126">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="d44ed-127">символьный формат Юникода</span><span class="sxs-lookup"><span data-stu-id="d44ed-127">Unicode character</span></span>|<span data-ttu-id="d44ed-128">`\uHHHH` (UTF-16) (где `H` обозначает шестнадцатеричную цифру, диапазон — 0000-FFFF;  Например, `\u00E7` = "c")</span><span class="sxs-lookup"><span data-stu-id="d44ed-128">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="d44ed-129">символьный формат Юникода</span><span class="sxs-lookup"><span data-stu-id="d44ed-129">Unicode character</span></span>|<span data-ttu-id="d44ed-130">`\U00HHHHHH` (UTF-32) (где `H` обозначает шестнадцатеричную цифру, диапазон 000000-10FFFF;  Например, `\U0001F47D` = " 👽 ")</span><span class="sxs-lookup"><span data-stu-id="d44ed-130">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="d44ed-131">`\DDD`Escape-последовательность — десятичная нотация, а не восьмеричная нотация, как в большинстве других языков.</span><span class="sxs-lookup"><span data-stu-id="d44ed-131">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="d44ed-132">Таким образом, цифры `8` и `9` являются допустимыми, а последовательность `\032` представляет пробел (U + 0020), тогда как в восьмеричной нотации будет использоваться та же кодовая точка `\040` .</span><span class="sxs-lookup"><span data-stu-id="d44ed-132">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="d44ed-133">Если ограничиться диапазоном 0-255 (0xFF), то `\DDD` `\x` escape-последовательности по сути являются набором символов [ISO – 8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , так как они соответствуют первым 256 кодовых позиций Юникода.</span><span class="sxs-lookup"><span data-stu-id="d44ed-133">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="d44ed-134">Буквальные строки</span><span class="sxs-lookup"><span data-stu-id="d44ed-134">Verbatim Strings</span></span>

<span data-ttu-id="d44ed-135">Если предшествует символ @, литерал является буквальной строкой.</span><span class="sxs-lookup"><span data-stu-id="d44ed-135">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="d44ed-136">Это означает, что все escape-последовательности игнорируются, за исключением того, что две кавычки считаются символом одной кавычки.</span><span class="sxs-lookup"><span data-stu-id="d44ed-136">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="d44ed-137">Строки с тройным заключенным в кавычки</span><span class="sxs-lookup"><span data-stu-id="d44ed-137">Triple Quoted Strings</span></span>

<span data-ttu-id="d44ed-138">Кроме того, строка может быть заключена в тройные кавычки.</span><span class="sxs-lookup"><span data-stu-id="d44ed-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="d44ed-139">В этом случае все escape-последовательности игнорируются, включая двойные кавычки.</span><span class="sxs-lookup"><span data-stu-id="d44ed-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="d44ed-140">Чтобы указать строку, содержащую внедренную строку в кавычках, можно использовать буквальную строку или строку с тройными кавычками.</span><span class="sxs-lookup"><span data-stu-id="d44ed-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="d44ed-141">При использовании буквальной строки необходимо указать две кавычки, чтобы указать символ одинарной кавычки.</span><span class="sxs-lookup"><span data-stu-id="d44ed-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="d44ed-142">При использовании строки, заключенной в тройные кавычки, можно использовать символы одинарной кавычки без синтаксического анализа в качестве конца строки.</span><span class="sxs-lookup"><span data-stu-id="d44ed-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="d44ed-143">Этот метод может быть полезен при работе с XML или с другими структурами, включающими в себя внедренные кавычки.</span><span class="sxs-lookup"><span data-stu-id="d44ed-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="d44ed-144">В коде строки, имеющие разрывы строк, принимаются, а разрывы строк интерпретируется как символы новой строки, если только символ обратной косой черты не является последним символом перед разрывом строки.</span><span class="sxs-lookup"><span data-stu-id="d44ed-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="d44ed-145">Начальные пробелы в следующей строке игнорируются при использовании символа обратной косой черты.</span><span class="sxs-lookup"><span data-stu-id="d44ed-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="d44ed-146">Следующий код создает строку со `str1` значением `"abc\ndef"` и строкой `str2` , имеющей значение `"abcdef"` .</span><span class="sxs-lookup"><span data-stu-id="d44ed-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="d44ed-147">Индексирование строк и создание срезов</span><span class="sxs-lookup"><span data-stu-id="d44ed-147">String Indexing and Slicing</span></span>

<span data-ttu-id="d44ed-148">Получить доступ к отдельным символам в строке можно с помощью синтаксиса, подобного массиву, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="d44ed-148">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="d44ed-149">Результат выглядит так: `b`.</span><span class="sxs-lookup"><span data-stu-id="d44ed-149">The output is `b`.</span></span>

<span data-ttu-id="d44ed-150">Кроме того, можно извлечь подстроки с помощью синтаксиса среза массива, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="d44ed-150">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="d44ed-151">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d44ed-151">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="d44ed-152">Строки ASCII можно представлять массивами беззнаковых байтов типа `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="d44ed-152">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="d44ed-153">Добавьте суффикс `B` к строковому литералу, чтобы указать, что это строка ASCII.</span><span class="sxs-lookup"><span data-stu-id="d44ed-153">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="d44ed-154">Строковые литералы ASCII, используемые с массивами байтов, поддерживают те же escape-последовательности, что и строки в Юникоде, за исключением escape-последовательностей Юникода.</span><span class="sxs-lookup"><span data-stu-id="d44ed-154">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="d44ed-155">Строковые операторы</span><span class="sxs-lookup"><span data-stu-id="d44ed-155">String Operators</span></span>

<span data-ttu-id="d44ed-156">`+`Оператор можно использовать для сцепления строк, сохраняя совместимость с функциями обработки строк .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d44ed-156">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="d44ed-157">В следующем примере показано объединение строк.</span><span class="sxs-lookup"><span data-stu-id="d44ed-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="d44ed-158">Класс String</span><span class="sxs-lookup"><span data-stu-id="d44ed-158">String Class</span></span>

<span data-ttu-id="d44ed-159">Так как тип строки в F # фактически является типом .NET Framework `System.String` , `System.String` доступны все элементы.</span><span class="sxs-lookup"><span data-stu-id="d44ed-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="d44ed-160">Сюда входит `+` оператор, который используется для сцепления строк, `Length` Свойства и `Chars` свойства, которые возвращают строку в виде массива символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="d44ed-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="d44ed-161">Дополнительные сведения о строках см. в разделе `System.String` .</span><span class="sxs-lookup"><span data-stu-id="d44ed-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="d44ed-162">С помощью `Chars` свойства объекта `System.String` можно получить доступ к отдельным символам в строке, указав индекс, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="d44ed-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="d44ed-163">Строковый модуль</span><span class="sxs-lookup"><span data-stu-id="d44ed-163">String Module</span></span>

<span data-ttu-id="d44ed-164">Дополнительные функции обработки строк включаются в `String` модуль в `FSharp.Core` пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="d44ed-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="d44ed-165">Дополнительные сведения см. в разделе [строковый модуль](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).</span><span class="sxs-lookup"><span data-stu-id="d44ed-165">For more information, see [String Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="d44ed-166">См. также</span><span class="sxs-lookup"><span data-stu-id="d44ed-166">See also</span></span>

- [<span data-ttu-id="d44ed-167">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="d44ed-167">F# Language Reference</span></span>](index.md)
