---
title: Общие сведения о кодировании символов в .NET
description: Сведения о кодировании и декодировании символов в .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 85349e1e1c4eca4dd3ef7980f48350a4145fca24
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599871"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="02451-103">Кодировка символов в .NET</span><span class="sxs-lookup"><span data-stu-id="02451-103">Character encoding in .NET</span></span>

<span data-ttu-id="02451-104">В этой статье содержатся общие сведения о системах кодирования символов, которые используются в .NET.</span><span class="sxs-lookup"><span data-stu-id="02451-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="02451-105">В этой статье описывается, как типы <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune> и <xref:System.Globalization.StringInfo> работают с кодировками Юникод, UTF-16 и UTF-8.</span><span class="sxs-lookup"><span data-stu-id="02451-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="02451-106">Термин *символ* используется здесь в общем смысле того, *что читатель воспринимает как отдельный отображаемый элемент*.</span><span class="sxs-lookup"><span data-stu-id="02451-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="02451-107">Распространенными примерами являются буква "а", символ "@" и эмодзи "🐂".</span><span class="sxs-lookup"><span data-stu-id="02451-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="02451-108">Иногда то, что выглядит как один символ, на самом деле состоит из нескольких независимых отображаемых элементов, как описано в разделе о [кластерах графем](#grapheme-clusters).</span><span class="sxs-lookup"><span data-stu-id="02451-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="02451-109">Типы string и char</span><span class="sxs-lookup"><span data-stu-id="02451-109">The string and char types</span></span>

<span data-ttu-id="02451-110">Экземпляр класса [string](xref:System.String) представляет некоторый текст.</span><span class="sxs-lookup"><span data-stu-id="02451-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="02451-111">Экземпляр `string` логически является последовательностью 16-разрядных значений, каждое из которых представляет собой экземпляр структуры [char](xref:System.Char).</span><span class="sxs-lookup"><span data-stu-id="02451-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="02451-112">Свойство [string.Length](xref:System.String.Length) возвращает количество экземпляров `char` в экземпляре `string`.</span><span class="sxs-lookup"><span data-stu-id="02451-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="02451-113">Следующий пример функции выводит значения в шестнадцатеричной нотации всех экземпляров `char` в `string`:</span><span class="sxs-lookup"><span data-stu-id="02451-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="02451-114">Передайте string "Hello" в эту функцию, и вы получите следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="02451-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

<span data-ttu-id="02451-115">Каждый символ представлен одним значением `char`.</span><span class="sxs-lookup"><span data-stu-id="02451-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="02451-116">Этот шаблон применяется для большинства языков мира.</span><span class="sxs-lookup"><span data-stu-id="02451-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="02451-117">Например, вот выходные данные для двух китайских символов, которые звучат как *nǐ hǎo* и означают *Hello*:</span><span class="sxs-lookup"><span data-stu-id="02451-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="02451-118">Однако для некоторых языков, символов и эмодзи, чтобы представить один символ, потребуется два экземпляра `char`.</span><span class="sxs-lookup"><span data-stu-id="02451-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="02451-119">Например, сравните символы и экземпляры `char` в слове, которое означает *Osage* на языке осейдж:</span><span class="sxs-lookup"><span data-stu-id="02451-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

<span data-ttu-id="02451-120">В приведенном выше примере каждый символ, кроме пробела, представлен двумя экземплярами `char`.</span><span class="sxs-lookup"><span data-stu-id="02451-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="02451-121">Один эмодзи в Юникоде также представлен двумя экземплярами `char`, как показано в следующем примере с эмодзи вола:</span><span class="sxs-lookup"><span data-stu-id="02451-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="02451-122">В этих примерах показано, что значение `string.Length`, которое указывает количество экземпляров `char`, не обязательно указывает количество отображаемых символов.</span><span class="sxs-lookup"><span data-stu-id="02451-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="02451-123">Один экземпляр `char` сам по себе не обязательно представляет символ.</span><span class="sxs-lookup"><span data-stu-id="02451-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="02451-124">Пары `char`, которые сопоставляются с одним символом, называются *суррогатными парами*.</span><span class="sxs-lookup"><span data-stu-id="02451-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="02451-125">Чтобы понять принцип их работы, вам нужно ознакомиться с кодировкой Юникод и UTF-16.</span><span class="sxs-lookup"><span data-stu-id="02451-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="02451-126">Кодовые точки Юникода</span><span class="sxs-lookup"><span data-stu-id="02451-126">Unicode code points</span></span>

<span data-ttu-id="02451-127">Юникод — это международный стандарт кодирования, используемый на различных платформах и с различными языками и скриптами.</span><span class="sxs-lookup"><span data-stu-id="02451-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="02451-128">Стандарт Юникода определяет более 1,1 миллиона [кодовых точек](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="02451-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="02451-129">Кодовая точка — это целочисленное значение, которое может быть в диапазоне от 0 до `U+10FFFF` (десятичное число 1 114 111).</span><span class="sxs-lookup"><span data-stu-id="02451-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="02451-130">Некоторые кодовые точки назначаются буквам, символам или эмодзи.</span><span class="sxs-lookup"><span data-stu-id="02451-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="02451-131">Другие назначаются действиям, которые определяют способ отображения текста или символов, например переход на новую строку.</span><span class="sxs-lookup"><span data-stu-id="02451-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="02451-132">Многие кодовые точки еще не назначены.</span><span class="sxs-lookup"><span data-stu-id="02451-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="02451-133">Вот несколько примеров назначения кодовых точек со ссылками на диаграммы Юникода, в которых они появляются:</span><span class="sxs-lookup"><span data-stu-id="02451-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="02451-134">Decimal</span><span class="sxs-lookup"><span data-stu-id="02451-134">Decimal</span></span>|<span data-ttu-id="02451-135">Hex</span><span class="sxs-lookup"><span data-stu-id="02451-135">Hex</span></span>       |<span data-ttu-id="02451-136">Пример</span><span class="sxs-lookup"><span data-stu-id="02451-136">Example</span></span>|<span data-ttu-id="02451-137">Описание</span><span class="sxs-lookup"><span data-stu-id="02451-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="02451-138">10</span><span class="sxs-lookup"><span data-stu-id="02451-138">10</span></span>     | `U+000A` |<span data-ttu-id="02451-139">Н/Д</span><span class="sxs-lookup"><span data-stu-id="02451-139">N/A</span></span>| [<span data-ttu-id="02451-140">Перевод строки</span><span class="sxs-lookup"><span data-stu-id="02451-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="02451-141">65</span><span class="sxs-lookup"><span data-stu-id="02451-141">65</span></span>     | `U+0061` | <span data-ttu-id="02451-142">а</span><span class="sxs-lookup"><span data-stu-id="02451-142">a</span></span> | [<span data-ttu-id="02451-143">Латинская строчная буква A</span><span class="sxs-lookup"><span data-stu-id="02451-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="02451-144">562</span><span class="sxs-lookup"><span data-stu-id="02451-144">562</span></span>    | `U+0232` | <span data-ttu-id="02451-145">Ȳ</span><span class="sxs-lookup"><span data-stu-id="02451-145">Ȳ</span></span> | [<span data-ttu-id="02451-146">Латинская заглавная буква Y со знаком долготы</span><span class="sxs-lookup"><span data-stu-id="02451-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="02451-147">68 675</span><span class="sxs-lookup"><span data-stu-id="02451-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="02451-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="02451-148">𐱃</span></span> | [<span data-ttu-id="02451-149">Древнетюркская буква (язык орхоно-енисейских надписей)</span><span class="sxs-lookup"><span data-stu-id="02451-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="02451-150">127 801</span><span class="sxs-lookup"><span data-stu-id="02451-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="02451-151">🌹</span><span class="sxs-lookup"><span data-stu-id="02451-151">🌹</span></span> | [<span data-ttu-id="02451-152">Эмодзи "Роза"</span><span class="sxs-lookup"><span data-stu-id="02451-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="02451-153">Кодовые точки обычно определяются с использованием синтаксиса `U+xxxx`, где `xxxx` — это шестнадцатеричное целочисленное значение.</span><span class="sxs-lookup"><span data-stu-id="02451-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="02451-154">В пределах всего диапазона кодовых точек существует два поддиапазона:</span><span class="sxs-lookup"><span data-stu-id="02451-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="02451-155">**Основная многоязыковая плоскость (BMP)** в диапазоне `U+0000..U+FFFF`.</span><span class="sxs-lookup"><span data-stu-id="02451-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="02451-156">Этот 16-разрядный диапазон предоставляет 65 536 кодовых точек. Их достаточно для охвата большинства мировых систем письма.</span><span class="sxs-lookup"><span data-stu-id="02451-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="02451-157">**Дополнительные кодовые точки** в диапазоне `U+10000..U+10FFFF`.</span><span class="sxs-lookup"><span data-stu-id="02451-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="02451-158">Этот 21-разрядный диапазон предоставляет более миллиона дополнительных кодовых точек, которые можно использовать для менее известных языков и для других целей, таких как эмодзи.</span><span class="sxs-lookup"><span data-stu-id="02451-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="02451-159">На следующей схеме показана взаимосвязь между BMP и дополнительными кодовыми точками.</span><span class="sxs-lookup"><span data-stu-id="02451-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP и дополнительные кодовые точки":::

## <a name="utf-16-code-units"></a><span data-ttu-id="02451-161">Единицы кода UTF-16</span><span class="sxs-lookup"><span data-stu-id="02451-161">UTF-16 code units</span></span>

<span data-ttu-id="02451-162">16-разрядный формат преобразования Юникода ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) — это система кодирования символов, которая использует 16-разрядные *единицы кода* для представления кодовых точек Юникода.</span><span class="sxs-lookup"><span data-stu-id="02451-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="02451-163">.NET использует UTF-16 для кодирования текста в `string`.</span><span class="sxs-lookup"><span data-stu-id="02451-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="02451-164">Экземпляр `char` представляет собой 16-разрядную единицу кода.</span><span class="sxs-lookup"><span data-stu-id="02451-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="02451-165">Одна 16-разрядная единица кода может представлять любую кодовую точку в 16-разрядном диапазоне основной многоязыковой плоскости.</span><span class="sxs-lookup"><span data-stu-id="02451-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="02451-166">Однако для кодовой точки в дополнительном диапазоне необходимы два экземпляра `char`.</span><span class="sxs-lookup"><span data-stu-id="02451-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="02451-167">Суррогатные пары</span><span class="sxs-lookup"><span data-stu-id="02451-167">Surrogate pairs</span></span>

<span data-ttu-id="02451-168">Преобразование двух 16-разрядных значений в одно 21-разрядное значение обеспечивается специальным диапазоном, который называется *суррогатными кодовыми точками*, от `U+D800` до `U+DFFF` (десятичное число от 55 296 до 57 343) включительно.</span><span class="sxs-lookup"><span data-stu-id="02451-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="02451-169">На следующей схеме показана взаимосвязь между BMP и суррогатными кодовыми точками.</span><span class="sxs-lookup"><span data-stu-id="02451-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP и суррогатные кодовые точки":::

<span data-ttu-id="02451-171">Когда за *старшей заменяющей* кодовой точкой (`U+D800..U+DBFF`) сразу же следует *младшая заменяющая* кодовая точка (`U+DC00..U+DFFF`), пара интерпретируется как дополнительная кодовая точка с помощью следующей формулы:</span><span class="sxs-lookup"><span data-stu-id="02451-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="02451-172">Вот та же формула, но с использованием десятичной нотации:</span><span class="sxs-lookup"><span data-stu-id="02451-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="02451-173">*Старшая* заменяющая кодовая точка не имеет значения числа выше, чем *младшая* заменяющая кодовая точка.</span><span class="sxs-lookup"><span data-stu-id="02451-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="02451-174">Старшая заменяющая кодовая точка называется "старшей", потому что она используется для вычисления 11 разрядов высшего порядка полного 21-разрядного диапазона кодовых точек.</span><span class="sxs-lookup"><span data-stu-id="02451-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="02451-175">Младшая заменяющая кодовая точка используется для вычисления 10 разрядов низшего порядка.</span><span class="sxs-lookup"><span data-stu-id="02451-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="02451-176">Например, фактическая кодовая точка, которая соответствует суррогатной паре `0xD83C` и `0xDF39`, вычисляется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="02451-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="02451-177">Вот тот же расчет, но с использованием десятичной нотации:</span><span class="sxs-lookup"><span data-stu-id="02451-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="02451-178">В предыдущем примере показано, что `"\ud83c\udf39"` является кодировкой UTF-16 кодовой точки `U+1F339 ROSE ('🌹')`, упомянутой ранее.</span><span class="sxs-lookup"><span data-stu-id="02451-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="02451-179">Скалярные значения Юникода</span><span class="sxs-lookup"><span data-stu-id="02451-179">Unicode scalar values</span></span>

<span data-ttu-id="02451-180">Термин [скалярное значение Юникода](https://www.unicode.org/glossary/#unicode_scalar_value) относится ко всем кодовым точкам, кроме суррогатных.</span><span class="sxs-lookup"><span data-stu-id="02451-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="02451-181">Другими словами, скалярное значение — это любая кодовая точка, которой присвоен символ или которой может быть присвоен символ в будущем.</span><span class="sxs-lookup"><span data-stu-id="02451-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="02451-182">Слово "символ" здесь относится ко всему, что может быть назначено кодовой точке, включая действия, которые определяют способ отображения текста или символов.</span><span class="sxs-lookup"><span data-stu-id="02451-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="02451-183">На приведенной ниже схеме показаны точки кода скалярного значения.</span><span class="sxs-lookup"><span data-stu-id="02451-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Скалярные значения":::

### <a name="the-rune-type-as-a-scalar-value"></a><span data-ttu-id="02451-185">Тип Rune как скалярное значение</span><span class="sxs-lookup"><span data-stu-id="02451-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="02451-186">Начиная с версии .NET Core 3.0, тип <xref:System.Text.Rune?displayProperty=fullName> представляет скалярное значение Юникода.</span><span class="sxs-lookup"><span data-stu-id="02451-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="02451-187">**Тип `Rune` недоступен в .NET Core 2.x или .NET Framework 4.x.**</span><span class="sxs-lookup"><span data-stu-id="02451-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="02451-188">Конструкторы `Rune` проверяют, является ли полученный экземпляр допустимым скалярным значением Юникода. В противном случае они создают исключение.</span><span class="sxs-lookup"><span data-stu-id="02451-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="02451-189">В следующем примере показан код, который создает экземпляры `Rune`, так как входные данные представляют допустимые скалярные значения:</span><span class="sxs-lookup"><span data-stu-id="02451-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="02451-190">В следующем примере создается исключение, так как кодовая точка находится в суррогатном диапазоне и не является частью суррогатной пары:</span><span class="sxs-lookup"><span data-stu-id="02451-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="02451-191">В следующем примере создается исключение, так как кодовая точка находится за пределами дополнительного диапазона:</span><span class="sxs-lookup"><span data-stu-id="02451-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="rune-usage-example-changing-letter-case"></a><span data-ttu-id="02451-192">Пример использования Rune: изменение регистра букв</span><span class="sxs-lookup"><span data-stu-id="02451-192">Rune usage example: changing letter case</span></span>

<span data-ttu-id="02451-193">API, который принимает `char` и предполагает, что работает с кодовой точкой, которая является скалярным значением, работает неправильно, если `char` принадлежит суррогатной паре.</span><span class="sxs-lookup"><span data-stu-id="02451-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="02451-194">Например, рассмотрим следующий метод, который вызывает <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> для каждого экземпляра char в string:</span><span class="sxs-lookup"><span data-stu-id="02451-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="02451-195">Если `input` string содержит строчную букву дезерет `er` (`𐑉`), этот код не преобразует ее в прописную букву (`𐐡`).</span><span class="sxs-lookup"><span data-stu-id="02451-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="02451-196">Код вызывает `char.ToUpperInvariant` отдельно для каждой суррогатной кодовой точки `U+D801` и `U+DC49`.</span><span class="sxs-lookup"><span data-stu-id="02451-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="02451-197">Однако в самой кодовой точке `U+D801` информации недостаточно, чтобы идентифицировать ее как строчную букву. Таким образом `char.ToUpperInvariant` оставляет ее как есть.</span><span class="sxs-lookup"><span data-stu-id="02451-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="02451-198">И таким же образом обрабатывает `U+DC49`.</span><span class="sxs-lookup"><span data-stu-id="02451-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="02451-199">В результате буква "𐑉" нижнего регистра в `input` string не преобразуется в букву "𐐡" верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="02451-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="02451-200">Вот два варианта правильного преобразования string в верхний регистр:</span><span class="sxs-lookup"><span data-stu-id="02451-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="02451-201">Вызовите <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> для входного экземпляра string, а не в итерации `char`-by-`char`.</span><span class="sxs-lookup"><span data-stu-id="02451-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="02451-202">Метод `string.ToUpperInvariant` имеет доступ к обеим частям каждой суррогатной пары, поэтому он может правильно обрабатывать все кодовые точки Юникода.</span><span class="sxs-lookup"><span data-stu-id="02451-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="02451-203">Выполните итерацию скалярных значений Юникода в качестве экземпляров `Rune`, а не экземпляров `char`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="02451-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="02451-204">Так как экземпляр `Rune` является допустимым скалярным значением Юникода, его можно передать в API-интерфейсы, которые должны работать со скалярным значением.</span><span class="sxs-lookup"><span data-stu-id="02451-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="02451-205">Например, вызвав <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType>, как показано в следующем примере, вы получите правильные результаты:</span><span class="sxs-lookup"><span data-stu-id="02451-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-rune-apis"></a><span data-ttu-id="02451-206">Другие API-интерфейсы Rune</span><span class="sxs-lookup"><span data-stu-id="02451-206">Other Rune APIs</span></span>

<span data-ttu-id="02451-207">Тип `Rune` предоставляет аналоги многих API-интерфейсов `char`.</span><span class="sxs-lookup"><span data-stu-id="02451-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="02451-208">Например, приведенные ниже методы отражают статические API-интерфейсы для типа `char`:</span><span class="sxs-lookup"><span data-stu-id="02451-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="02451-209">Чтобы получить необработанное скалярное значение из экземпляра `Rune`, используйте свойство <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02451-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="02451-210">Чтобы преобразовать экземпляр `Rune` обратно в последовательность типов `char`, используйте метод <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> или <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="02451-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="02451-211">Так как любое скалярное значение Юникода может быть представлено одним экземпляром `char` или суррогатной парой, любой экземпляр `Rune` может быть представлен не более чем двумя экземплярами `char`.</span><span class="sxs-lookup"><span data-stu-id="02451-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="02451-212">Используйте <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType>, чтобы узнать количество экземпляров `char`, требуемых для представления экземпляра `Rune`.</span><span class="sxs-lookup"><span data-stu-id="02451-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="02451-213">Дополнительные сведения о типе `Rune` .NET см. в [справочнике по API для `Rune`](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="02451-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="02451-214">Кластеры графем</span><span class="sxs-lookup"><span data-stu-id="02451-214">Grapheme clusters</span></span>

<span data-ttu-id="02451-215">То, что выглядит как один символ, может быть результатом комбинации нескольких кодовых точек. Таким образом, более описательным термином, который часто используется вместо термина "символ", является [кластер графем](https://www.unicode.org/glossary/#grapheme_cluster).</span><span class="sxs-lookup"><span data-stu-id="02451-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="02451-216">В .NET эквивалентным термином является [текстовый элемент](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="02451-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="02451-217">Рассмотрим экземпляры `string` "а", "á".</span><span class="sxs-lookup"><span data-stu-id="02451-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="02451-218">"á" и "`👩🏽‍🚒`".</span><span class="sxs-lookup"><span data-stu-id="02451-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="02451-219">Если операционная система обрабатывает их в соответствии со стандартом Юникода, каждый из этих экземпляров `string` отображается в виде одного текстового элемента или кластера графем.</span><span class="sxs-lookup"><span data-stu-id="02451-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="02451-220">Однако последние два представлены более чем одной кодовой точкой скалярного значения.</span><span class="sxs-lookup"><span data-stu-id="02451-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="02451-221">Экземпляр string "a" представлен одним скалярным значением и содержит один экземпляр `char`.</span><span class="sxs-lookup"><span data-stu-id="02451-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="02451-222">Экземпляр string "á" представлен одним скалярным значением и содержит один экземпляр `char`.</span><span class="sxs-lookup"><span data-stu-id="02451-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="02451-223">Экземпляр string "á" выглядит так же, как "á", но представлен двумя скалярными значениями и содержит два экземпляра `char`.</span><span class="sxs-lookup"><span data-stu-id="02451-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="02451-224">Наконец, экземпляр string "`👩🏽‍🚒`" представлен четырьмя скалярными значениями и содержит семь экземпляров `char`.</span><span class="sxs-lookup"><span data-stu-id="02451-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="02451-225">`U+1F469 WOMAN` (дополнительный диапазон, требуется суррогатная пара);</span><span class="sxs-lookup"><span data-stu-id="02451-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="02451-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (дополнительный диапазон, требуется суррогатная пара);</span><span class="sxs-lookup"><span data-stu-id="02451-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="02451-227">`U+1F692 FIRE ENGINE` (дополнительный диапазон, требуется суррогатная пара).</span><span class="sxs-lookup"><span data-stu-id="02451-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="02451-228">В некоторых из приведенных выше примерах, таких как комбинированный модификатор диакритических знаков или модификатор тона кожи, кодовая точка не отображается как отдельный элемент на экране.</span><span class="sxs-lookup"><span data-stu-id="02451-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="02451-229">Вместо этого она служит для изменения внешнего вида текстового элемента, который был до него.</span><span class="sxs-lookup"><span data-stu-id="02451-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="02451-230">В этих примерах показано, что может потребоваться несколько скалярных значений, чтобы составить один "символ" или "кластер графем".</span><span class="sxs-lookup"><span data-stu-id="02451-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="02451-231">Чтобы перечислить кластеры графем для `string`, используйте класс <xref:System.Globalization.StringInfo>, как показано в приведенном ниже примере.</span><span class="sxs-lookup"><span data-stu-id="02451-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="02451-232">Если вы знакомы с Swift, тип `StringInfo` .NET концептуально похож на [тип `character` Swift](https://developer.apple.com/documentation/swift/character).</span><span class="sxs-lookup"><span data-stu-id="02451-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-char-rune-and-text-element-instances"></a><span data-ttu-id="02451-233">Пример: количество char, Rune и экземпляров текстовых элементов</span><span class="sxs-lookup"><span data-stu-id="02451-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="02451-234">В интерфейсах API .NET кластер графем называется *текстовым элементом*.</span><span class="sxs-lookup"><span data-stu-id="02451-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="02451-235">Приведенный ниже метод демонстрирует различия между `char`, `Rune` и экземплярами текстового элемента в `string`:</span><span class="sxs-lookup"><span data-stu-id="02451-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="02451-236">Если вы запустите этот код в .NET Framework или .NET Core 3.1 или более ранней версии, для эмодзи отобразится `4` текстовых элемента.</span><span class="sxs-lookup"><span data-stu-id="02451-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="02451-237">Это связано с ошибкой в классе `StringInfo`, которая исправлена в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="02451-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-string-instances"></a><span data-ttu-id="02451-238">Пример: разделение экземпляров string</span><span class="sxs-lookup"><span data-stu-id="02451-238">Example: splitting string instances</span></span>

<span data-ttu-id="02451-239">При разделении экземпляров `string` не разделяйте суррогатные пары и кластеры графем.</span><span class="sxs-lookup"><span data-stu-id="02451-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="02451-240">Рассмотрим приведенный ниже пример неправильного кода, который будет вставлять разрывы строк через каждые 10 символов в string.</span><span class="sxs-lookup"><span data-stu-id="02451-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="02451-241">Так как этот код перечисляет экземпляры `char`, суррогатная пара, которая пересекает границу 10-`char`, будет разделена и между ними будет введена новая строка.</span><span class="sxs-lookup"><span data-stu-id="02451-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="02451-242">Эта вставка представляет собой повреждение данных, так как суррогатные кодовые точки имеют смысл только как пары.</span><span class="sxs-lookup"><span data-stu-id="02451-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="02451-243">При перечислении экземпляров `Rune` (скалярные значения) вместо экземпляров `char` возможность повреждения данных не исключается.</span><span class="sxs-lookup"><span data-stu-id="02451-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="02451-244">Набор экземпляров `Rune` может составлять кластер графем, который выходит за границу 10-`char`.</span><span class="sxs-lookup"><span data-stu-id="02451-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="02451-245">Если набор кластеров графем разделен, он не может быть правильно интерпретирован.</span><span class="sxs-lookup"><span data-stu-id="02451-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="02451-246">Лучшим подходом является разделение string путем подсчета кластеров графем или текстовых элементов, как показано в приведенном ниже примере.</span><span class="sxs-lookup"><span data-stu-id="02451-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="02451-247">Однако, как упоминалось ранее, в реализациях .NET, отличных от .NET 5, класс `StringInfo` может некорректно обрабатывать некоторые кластеры графем.</span><span class="sxs-lookup"><span data-stu-id="02451-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="02451-248">UTF-8 и UTF-32</span><span class="sxs-lookup"><span data-stu-id="02451-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="02451-249">В предыдущих разделах основное внимание уделялось UTF-16, потому что именно эту кодировку .NET использует для кодирования экземпляров `string`.</span><span class="sxs-lookup"><span data-stu-id="02451-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="02451-250">Существуют и другие системы кодирования для Юникода: [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) и [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span><span class="sxs-lookup"><span data-stu-id="02451-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="02451-251">Эти кодировки используют 8-разрядные и 32-разрядные единицы кода соответственно.</span><span class="sxs-lookup"><span data-stu-id="02451-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="02451-252">Как и в системе UTF-16, для UTF-8 требуется несколько единиц кода, чтобы предоставить некоторые скалярные значения Юникода.</span><span class="sxs-lookup"><span data-stu-id="02451-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="02451-253">UTF-32 может представлять любое скалярное значение в одной 32-разрядной единице кода.</span><span class="sxs-lookup"><span data-stu-id="02451-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="02451-254">Ниже приведено несколько примеров, показывающих, как одна и та же кодовая точка Юникода представлена в каждой из этих трех систем кодирования Юникода.</span><span class="sxs-lookup"><span data-stu-id="02451-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

<span data-ttu-id="02451-255">Как упоминалось ранее, одна единица кода UTF-16 из [суррогатной пары](#surrogate-pairs) сама по себе не имеет смысла.</span><span class="sxs-lookup"><span data-stu-id="02451-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="02451-256">Таким же образом одна единица кода UTF-8 сама по себе не имеет смысла, если она находится в последовательности из двух, трех или четырех единиц, используемых для вычисления скалярных значений.</span><span class="sxs-lookup"><span data-stu-id="02451-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="02451-257">Порядок байтов</span><span class="sxs-lookup"><span data-stu-id="02451-257">Endianness</span></span>

<span data-ttu-id="02451-258">В .NET единицы кода UTF-16 string хранятся в непрерывной памяти в виде последовательности 16-разрядных целых чисел (экземпляров `char`).</span><span class="sxs-lookup"><span data-stu-id="02451-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="02451-259">Разряды отдельных единиц кода размещаются в соответствии с [порядком байтов](https://en.wikipedia.org/wiki/Endianness) текущей архитектуры.</span><span class="sxs-lookup"><span data-stu-id="02451-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="02451-260">В архитектуре с прямым порядком байтов экземпляр string, состоящий из кодовых точек UTF-16 `[ D801 DCCC ]`, будет размещен в памяти в виде байтов `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span><span class="sxs-lookup"><span data-stu-id="02451-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="02451-261">В архитектуре с обратным порядком байтов тот же экземпляр string будет размещен в памяти в виде байтов `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span><span class="sxs-lookup"><span data-stu-id="02451-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="02451-262">Компьютерные системы, которые взаимодействуют друг с другом, должны согласовать представление передаваемых данных.</span><span class="sxs-lookup"><span data-stu-id="02451-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="02451-263">Большинство сетевых протоколов используют систему UTF-8 в качестве стандарта при передаче текста, частично во избежание проблем, которые могут возникнуть из-за того, что компьютер с обратным порядком байтов взаимодействует с компьютером с прямым порядком байтов.</span><span class="sxs-lookup"><span data-stu-id="02451-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="02451-264">Экземпляр string, состоящий из кодовых точек UTF-8 `[ F0 90 93 8C ]`, всегда будет представлен в виде байтов `[ 0xF0, 0x90, 0x93, 0x8C ]`, независимо от порядка байтов.</span><span class="sxs-lookup"><span data-stu-id="02451-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="02451-265">Чтобы использовать систему UTF-8 для передачи текста, приложения .NET часто применяют код, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="02451-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="02451-266">В предыдущем примере метод [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) декодирует экземпляр `string`UTF-16 обратно в ряд скалярных значений Юникода, затем он повторно кодирует эти скалярные значения в UTF-8 и помещает полученную последовательность в массив `byte`.</span><span class="sxs-lookup"><span data-stu-id="02451-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="02451-267">Метод [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) выполняет обратное преобразование, преобразовывая массив `byte` UTF-8 в `string` UTF-16.</span><span class="sxs-lookup"><span data-stu-id="02451-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="02451-268">Так как система UTF-8 очень часто используется в Интернете, очевидным решением может показаться считывать необработанные байты из сети и обрабатывать данные, как если бы это была система кодировки UTF-8.</span><span class="sxs-lookup"><span data-stu-id="02451-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="02451-269">Однако вы должны проверить, что она действительно имеет правильный формат.</span><span class="sxs-lookup"><span data-stu-id="02451-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="02451-270">Вредоносный клиент может отправить в службу неверно сформированную кодировку UTF-8.</span><span class="sxs-lookup"><span data-stu-id="02451-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="02451-271">Если вы выполняете операции с этими данными так, как если бы они были правильно сформированы, это может вызвать ошибки или бреши в системе безопасности приложения.</span><span class="sxs-lookup"><span data-stu-id="02451-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="02451-272">Чтобы проверить данные UTF-8, вы можете использовать метод, например `Encoding.UTF8.GetString`, который при преобразовании входящих данных в `string` будет выполнять проверку.</span><span class="sxs-lookup"><span data-stu-id="02451-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="02451-273">Кодирование с правильным форматом</span><span class="sxs-lookup"><span data-stu-id="02451-273">Well-formed encoding</span></span>

<span data-ttu-id="02451-274">Кодировка Юникод с правильным форматом — это экземпляр string кодовых единиц, который может быть однозначно и без ошибок декодирован в последовательность скалярных значений Юникода.</span><span class="sxs-lookup"><span data-stu-id="02451-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="02451-275">Данные с правильным форматом могут быть свободно перекодированы между UTF-8, UTF-16 и UTF-32.</span><span class="sxs-lookup"><span data-stu-id="02451-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="02451-276">Вопрос в том, имеет ли последовательность кодирования правильный формат или нет, независимо от порядка байтов в архитектуре компьютера.</span><span class="sxs-lookup"><span data-stu-id="02451-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="02451-277">Неверно сформированная последовательность UTF-8 имеет неправильный формат как на компьютерах с обратным порядком байтов, так и на компьютерах с прямым порядком байтов.</span><span class="sxs-lookup"><span data-stu-id="02451-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="02451-278">Вот несколько примеров кодировок с неправильным форматом:</span><span class="sxs-lookup"><span data-stu-id="02451-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="02451-279">В UTF-8 последовательность `[ 6C C2 61 ]` имеет неправильный формат, потому что за `C2` не может следовать `61`.</span><span class="sxs-lookup"><span data-stu-id="02451-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="02451-280">В UTF-16 последовательность `[ DC00 DD00 ]` (или, в C#, string `"\udc00\udd00"`) имеет неправильный формат, потому что за младшей заменяющей кодовой точкой `DC00` не может следовать другая младшая заменяющая точка `DD00`.</span><span class="sxs-lookup"><span data-stu-id="02451-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="02451-281">В UTF-32 последовательность `[ 0011ABCD ]` имеет неправильный формат, так как `0011ABCD` находится вне диапазона скалярных значений Юникода.</span><span class="sxs-lookup"><span data-stu-id="02451-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="02451-282">В .NET экземпляры `string` почти всегда содержат данные UTF-16 с правильным форматом, но это не гарантировано.</span><span class="sxs-lookup"><span data-stu-id="02451-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="02451-283">В следующих примерах показан допустимый код C#, который создает данные UTF-16 с неправильным форматом в экземплярах `string`.</span><span class="sxs-lookup"><span data-stu-id="02451-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="02451-284">Литерал с неправильным форматом:</span><span class="sxs-lookup"><span data-stu-id="02451-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="02451-285">Подстрока, которая разделяет суррогатную пару:</span><span class="sxs-lookup"><span data-stu-id="02451-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="02451-286">API-интерфейсы, такие как [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A), никогда не возвращают экземпляры `string` с неправильным форматом.</span><span class="sxs-lookup"><span data-stu-id="02451-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="02451-287">Методы `Encoding.GetString` и `Encoding.GetBytes` обнаруживают последовательности с неправильным форматом во входных данных и выполняют замену символов при формировании выходных данных.</span><span class="sxs-lookup"><span data-stu-id="02451-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="02451-288">Например, если для метода [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) во входных данных отображается байт, отличный от ASCII (вне диапазона U+0000–U+007F), он вставляет символ "?" в возвращенный экземпляр `string`.</span><span class="sxs-lookup"><span data-stu-id="02451-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="02451-289">Метод [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) заменяет последовательности UTF-8 с неправильным форматом на `U+FFFD REPLACEMENT CHARACTER ('�')` в возвращаемом экземпляре `string`.</span><span class="sxs-lookup"><span data-stu-id="02451-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="02451-290">Дополнительные сведения см. в разделах 5.22 и 3.9 [стандарта Юникода](https://www.unicode.org/versions/latest/).</span><span class="sxs-lookup"><span data-stu-id="02451-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="02451-291">Встроенные классы `Encoding` также можно настроить для создания исключения, а не для замены символов, когда отображаются последовательности с неправильным форматом.</span><span class="sxs-lookup"><span data-stu-id="02451-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="02451-292">Этот подход часто используется в приложениях, требующих особых мер безопасности, где замена символов может быть неприемлемой.</span><span class="sxs-lookup"><span data-stu-id="02451-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="02451-293">Сведения о том, как использовать встроенные классы `Encoding`, см. в статье [Кодировка символов в .NET](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="02451-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="02451-294">См. также</span><span class="sxs-lookup"><span data-stu-id="02451-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="02451-295">Глобализация и локализация</span><span class="sxs-lookup"><span data-stu-id="02451-295">Globalization and Localization</span></span>](../globalization-localization/index.md)
