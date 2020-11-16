---
title: Общие сведения о кодировании символов в .NET
description: Сведения о кодировании и декодировании символов в .NET.
ms.date: 03/09/2020
no-loc:
- 'Rune'
- 'char'
- 'string'
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 572fcd289eea720873d94e7fc71f3b4a030d1d70
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282313"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="65da6-103">Кодировка символов в .NET</span><span class="sxs-lookup"><span data-stu-id="65da6-103">Character encoding in .NET</span></span>

<span data-ttu-id="65da6-104">В этой статье содержатся общие сведения о системах кодирования символов, которые используются в .NET.</span><span class="sxs-lookup"><span data-stu-id="65da6-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="65da6-105">В этой статье описывается, как типы <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune> и <xref:System.Globalization.StringInfo> работают с кодировками Юникод, UTF-16 и UTF-8.</span><span class="sxs-lookup"><span data-stu-id="65da6-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="65da6-106">Термин *символ* используется здесь в общем смысле того, *что читатель воспринимает как отдельный отображаемый элемент*.</span><span class="sxs-lookup"><span data-stu-id="65da6-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="65da6-107">Распространенными примерами являются буква "а", символ "@" и эмодзи "🐂".</span><span class="sxs-lookup"><span data-stu-id="65da6-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="65da6-108">Иногда то, что выглядит как один символ, на самом деле состоит из нескольких независимых отображаемых элементов, как описано в разделе о [кластерах графем](#grapheme-clusters).</span><span class="sxs-lookup"><span data-stu-id="65da6-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-no-locstring-and-no-locchar-types"></a><span data-ttu-id="65da6-109">Типы string и char</span><span class="sxs-lookup"><span data-stu-id="65da6-109">The string and char types</span></span>

<span data-ttu-id="65da6-110">Экземпляр класса [string](xref:System.String) представляет некоторый текст.</span><span class="sxs-lookup"><span data-stu-id="65da6-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="65da6-111">Экземпляр `string` логически является последовательностью 16-разрядных значений, каждое из которых представляет собой экземпляр структуры [char](xref:System.Char).</span><span class="sxs-lookup"><span data-stu-id="65da6-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="65da6-112">Свойство [string.Length](xref:System.String.Length) возвращает количество экземпляров `char` в экземпляре `string`.</span><span class="sxs-lookup"><span data-stu-id="65da6-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="65da6-113">Следующий пример функции выводит значения в шестнадцатеричной нотации всех экземпляров `char` в `string`:</span><span class="sxs-lookup"><span data-stu-id="65da6-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

<span data-ttu-id="65da6-114">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::</span><span class="sxs-lookup"><span data-stu-id="65da6-114">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::</span></span>

<span data-ttu-id="65da6-115">Передайте string "Hello" в эту функцию, и вы получите следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="65da6-115">Pass the string "Hello" to this function, and you get the following output:</span></span>

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

<span data-ttu-id="65da6-116">Каждый символ представлен одним значением `char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-116">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="65da6-117">Этот шаблон применяется для большинства языков мира.</span><span class="sxs-lookup"><span data-stu-id="65da6-117">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="65da6-118">Например, вот выходные данные для двух китайских символов, которые звучат как *nǐ hǎo* и означают *привет* :</span><span class="sxs-lookup"><span data-stu-id="65da6-118">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello* :</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="65da6-119">Однако для некоторых языков, символов и эмодзи, чтобы представить один символ, потребуется два экземпляра `char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-119">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="65da6-120">Например, сравните символы и экземпляры `char` в слове, которое означает *осейдж* на языке осейдж:</span><span class="sxs-lookup"><span data-stu-id="65da6-120">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

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

<span data-ttu-id="65da6-121">В приведенном выше примере каждый символ, кроме пробела, представлен двумя экземплярами `char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-121">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="65da6-122">Один эмодзи в Юникоде также представлен двумя экземплярами `char`, как показано в следующем примере с эмодзи вола:</span><span class="sxs-lookup"><span data-stu-id="65da6-122">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```output
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="65da6-123">В этих примерах показано, что значение `string.Length`, которое указывает количество экземпляров `char`, не обязательно указывает количество отображаемых символов.</span><span class="sxs-lookup"><span data-stu-id="65da6-123">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="65da6-124">Один экземпляр `char` сам по себе не обязательно представляет один символ.</span><span class="sxs-lookup"><span data-stu-id="65da6-124">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="65da6-125">Пары `char`, которые сопоставляются с одним символом, называются *суррогатными парами*.</span><span class="sxs-lookup"><span data-stu-id="65da6-125">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="65da6-126">Чтобы понять принцип их работы, вам нужно ознакомиться с кодировкой Юникод и UTF-16.</span><span class="sxs-lookup"><span data-stu-id="65da6-126">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="65da6-127">Кодовые точки Юникода</span><span class="sxs-lookup"><span data-stu-id="65da6-127">Unicode code points</span></span>

<span data-ttu-id="65da6-128">Юникод — это международный стандарт кодирования, используемый на различных платформах и с различными языками и скриптами.</span><span class="sxs-lookup"><span data-stu-id="65da6-128">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="65da6-129">Стандарт Юникода определяет более 1,1 миллиона [кодовых точек](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="65da6-129">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="65da6-130">Кодовая точка — это целочисленное значение, которое может быть в диапазоне от 0 до `U+10FFFF` (десятичное число 1 114 111).</span><span class="sxs-lookup"><span data-stu-id="65da6-130">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="65da6-131">Некоторые кодовые точки назначаются буквам, символам или эмодзи.</span><span class="sxs-lookup"><span data-stu-id="65da6-131">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="65da6-132">Другие назначаются действиям, которые определяют способ отображения текста или символов, например переход на новую строку.</span><span class="sxs-lookup"><span data-stu-id="65da6-132">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="65da6-133">Многие кодовые точки еще не назначены.</span><span class="sxs-lookup"><span data-stu-id="65da6-133">Many code points are not yet assigned.</span></span>

<span data-ttu-id="65da6-134">Вот несколько примеров назначения кодовых точек со ссылками на диаграммы Юникода, в которых они появляются:</span><span class="sxs-lookup"><span data-stu-id="65da6-134">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="65da6-135">Decimal</span><span class="sxs-lookup"><span data-stu-id="65da6-135">Decimal</span></span>|<span data-ttu-id="65da6-136">Hex</span><span class="sxs-lookup"><span data-stu-id="65da6-136">Hex</span></span>       |<span data-ttu-id="65da6-137">Пример</span><span class="sxs-lookup"><span data-stu-id="65da6-137">Example</span></span>|<span data-ttu-id="65da6-138">Описание</span><span class="sxs-lookup"><span data-stu-id="65da6-138">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="65da6-139">10</span><span class="sxs-lookup"><span data-stu-id="65da6-139">10</span></span>     | `U+000A` |<span data-ttu-id="65da6-140">Н/Д</span><span class="sxs-lookup"><span data-stu-id="65da6-140">N/A</span></span>| <span data-ttu-id="65da6-141">[Перевод строки](https://www.unicode.org/charts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="65da6-141">[LINE FEED](https://www.unicode.org/charts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="65da6-142">97</span><span class="sxs-lookup"><span data-stu-id="65da6-142">97</span></span>     | `U+0061` | <span data-ttu-id="65da6-143">а</span><span class="sxs-lookup"><span data-stu-id="65da6-143">a</span></span> | <span data-ttu-id="65da6-144">[Латинская строчная буква A](https://www.unicode.org/charts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="65da6-144">[LATIN SMALL LETTER A](https://www.unicode.org/charts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="65da6-145">562</span><span class="sxs-lookup"><span data-stu-id="65da6-145">562</span></span>    | `U+0232` | <span data-ttu-id="65da6-146">Ȳ</span><span class="sxs-lookup"><span data-stu-id="65da6-146">Ȳ</span></span> | <span data-ttu-id="65da6-147">[Латинская заглавная буква Y со знаком долготы](https://www.unicode.org/charts/PDF/U0180.pdf)</span><span class="sxs-lookup"><span data-stu-id="65da6-147">[LATIN CAPITAL LETTER Y WITH MACRON](https://www.unicode.org/charts/PDF/U0180.pdf)</span></span> |
|<span data-ttu-id="65da6-148">68 675</span><span class="sxs-lookup"><span data-stu-id="65da6-148">68,675</span></span> | `U+10C43`| <span data-ttu-id="65da6-149">𐱃</span><span class="sxs-lookup"><span data-stu-id="65da6-149">𐱃</span></span> | <span data-ttu-id="65da6-150">[Древнетюркская буква (язык орхоно-енисейских надписей)](https://www.unicode.org/charts/PDF/U10C00.pdf)</span><span class="sxs-lookup"><span data-stu-id="65da6-150">[OLD TURKIC LETTER ORKHON AT](https://www.unicode.org/charts/PDF/U10C00.pdf)</span></span> |
|<span data-ttu-id="65da6-151">127 801</span><span class="sxs-lookup"><span data-stu-id="65da6-151">127,801</span></span>| `U+1F339`| <span data-ttu-id="65da6-152">🌹</span><span class="sxs-lookup"><span data-stu-id="65da6-152">🌹</span></span> | <span data-ttu-id="65da6-153">[Эмодзи "Роза"](https://www.unicode.org/charts/PDF/U1F300.pdf)</span><span class="sxs-lookup"><span data-stu-id="65da6-153">[ROSE emoji](https://www.unicode.org/charts/PDF/U1F300.pdf)</span></span> |

<span data-ttu-id="65da6-154">Кодовые точки обычно определяются с использованием синтаксиса `U+xxxx`, где `xxxx` — это шестнадцатеричное целочисленное значение.</span><span class="sxs-lookup"><span data-stu-id="65da6-154">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="65da6-155">В пределах всего диапазона кодовых точек существует два поддиапазона:</span><span class="sxs-lookup"><span data-stu-id="65da6-155">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="65da6-156">**Основная многоязыковая плоскость (BMP)** в диапазоне `U+0000..U+FFFF`.</span><span class="sxs-lookup"><span data-stu-id="65da6-156">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="65da6-157">Этот 16-разрядный диапазон предоставляет 65 536 кодовых точек. Их достаточно для охвата большинства мировых систем письма.</span><span class="sxs-lookup"><span data-stu-id="65da6-157">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="65da6-158">**Дополнительные кодовые точки** в диапазоне `U+10000..U+10FFFF`.</span><span class="sxs-lookup"><span data-stu-id="65da6-158">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="65da6-159">Этот 21-разрядный диапазон предоставляет более миллиона дополнительных кодовых точек, которые можно использовать для менее известных языков и для других целей, таких как эмодзи.</span><span class="sxs-lookup"><span data-stu-id="65da6-159">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="65da6-160">На следующей схеме показана взаимосвязь между BMP и дополнительными кодовыми точками.</span><span class="sxs-lookup"><span data-stu-id="65da6-160">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP and supplementary code points":::

## <a name="utf-16-code-units"></a><span data-ttu-id="65da6-162">Единицы кода UTF-16</span><span class="sxs-lookup"><span data-stu-id="65da6-162">UTF-16 code units</span></span>

<span data-ttu-id="65da6-163">16-разрядный формат преобразования Юникода ( [UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) — это система кодирования символов, которая использует 16-разрядные *единицы кода* для представления кодовых точек Юникода.</span><span class="sxs-lookup"><span data-stu-id="65da6-163">16-bit Unicode Transformation Format ( [UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="65da6-164">.NET использует UTF-16 для кодирования текста в `string`.</span><span class="sxs-lookup"><span data-stu-id="65da6-164">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="65da6-165">Экземпляр `char` представляет собой 16-разрядную единицу кода.</span><span class="sxs-lookup"><span data-stu-id="65da6-165">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="65da6-166">Одна 16-разрядная единица кода может представлять любую кодовую точку в 16-разрядном диапазоне основной многоязыковой плоскости.</span><span class="sxs-lookup"><span data-stu-id="65da6-166">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="65da6-167">Однако для кодовой точки в дополнительном диапазоне необходимы два экземпляра `char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-167">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="65da6-168">Суррогатные пары</span><span class="sxs-lookup"><span data-stu-id="65da6-168">Surrogate pairs</span></span>

<span data-ttu-id="65da6-169">Преобразование двух 16-разрядных значений в одно 21-разрядное значение обеспечивается специальным диапазоном, который называется *суррогатными кодовыми точками* , от `U+D800` до `U+DFFF` (десятичное число от 55 296 до 57 343) включительно.</span><span class="sxs-lookup"><span data-stu-id="65da6-169">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points* , from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="65da6-170">На следующей схеме показана взаимосвязь между BMP и суррогатными кодовыми точками.</span><span class="sxs-lookup"><span data-stu-id="65da6-170">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP and surrogate code points":::

<span data-ttu-id="65da6-172">Когда за *старшей заменяющей* кодовой точкой (`U+D800..U+DBFF`) сразу же следует *младшая заменяющая* кодовая точка (`U+DC00..U+DFFF`), пара интерпретируется как дополнительная кодовая точка с помощью следующей формулы:</span><span class="sxs-lookup"><span data-stu-id="65da6-172">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="65da6-173">Вот та же формула, но с использованием десятичной нотации:</span><span class="sxs-lookup"><span data-stu-id="65da6-173">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="65da6-174">*Старшая* заменяющая кодовая точка не имеет значения числа выше, чем *младшая* заменяющая кодовая точка.</span><span class="sxs-lookup"><span data-stu-id="65da6-174">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="65da6-175">Старшая заменяющая кодовая точка называется "старшей", потому что она используется для вычисления 11 разрядов высшего порядка полного 21-разрядного диапазона кодовых точек.</span><span class="sxs-lookup"><span data-stu-id="65da6-175">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="65da6-176">Младшая заменяющая кодовая точка используется для вычисления 10 разрядов низшего порядка.</span><span class="sxs-lookup"><span data-stu-id="65da6-176">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="65da6-177">Например, фактическая кодовая точка, которая соответствует суррогатной паре `0xD83C` и `0xDF39`, вычисляется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="65da6-177">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="65da6-178">Вот тот же расчет, но с использованием десятичной нотации:</span><span class="sxs-lookup"><span data-stu-id="65da6-178">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="65da6-179">В предыдущем примере показано, что `"\ud83c\udf39"` является кодировкой UTF-16 кодовой точки `U+1F339 ROSE ('🌹')`, упомянутой ранее.</span><span class="sxs-lookup"><span data-stu-id="65da6-179">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="65da6-180">Скалярные значения Юникода</span><span class="sxs-lookup"><span data-stu-id="65da6-180">Unicode scalar values</span></span>

<span data-ttu-id="65da6-181">Термин [скалярное значение Юникода](https://www.unicode.org/glossary/#unicode_scalar_value) относится ко всем кодовым точкам, кроме суррогатных.</span><span class="sxs-lookup"><span data-stu-id="65da6-181">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="65da6-182">Другими словами, скалярное значение — это любая кодовая точка, которой присвоен символ или которой может быть присвоен символ в будущем.</span><span class="sxs-lookup"><span data-stu-id="65da6-182">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="65da6-183">Слово "символ" здесь относится ко всему, что может быть назначено кодовой точке, включая действия, которые определяют способ отображения текста или символов.</span><span class="sxs-lookup"><span data-stu-id="65da6-183">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="65da6-184">На приведенной ниже схеме показаны точки кода скалярного значения.</span><span class="sxs-lookup"><span data-stu-id="65da6-184">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Scalar values":::

### <a name="the-no-locrune-type-as-a-scalar-value"></a><span data-ttu-id="65da6-186">Тип Rune как скалярное значение</span><span class="sxs-lookup"><span data-stu-id="65da6-186">The Rune type as a scalar value</span></span>

<span data-ttu-id="65da6-187">Начиная с версии .NET Core 3.0, тип <xref:System.Text.Rune?displayProperty=fullName> представляет скалярное значение Юникода.</span><span class="sxs-lookup"><span data-stu-id="65da6-187">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="65da6-188">**Тип `Rune` недоступен в .NET Core 2.x или .NET Framework 4.x.**</span><span class="sxs-lookup"><span data-stu-id="65da6-188">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="65da6-189">Конструкторы `Rune` проверяют, является ли полученный экземпляр допустимым скалярным значением Юникода. В противном случае они создают исключение.</span><span class="sxs-lookup"><span data-stu-id="65da6-189">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="65da6-190">В следующем примере показан код, который создает экземпляры `Rune`, так как входные данные представляют допустимые скалярные значения:</span><span class="sxs-lookup"><span data-stu-id="65da6-190">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

<span data-ttu-id="65da6-191">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::</span><span class="sxs-lookup"><span data-stu-id="65da6-191">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::</span></span>

<span data-ttu-id="65da6-192">В следующем примере создается исключение, так как кодовая точка находится в суррогатном диапазоне и не является частью суррогатной пары:</span><span class="sxs-lookup"><span data-stu-id="65da6-192">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

<span data-ttu-id="65da6-193">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::</span><span class="sxs-lookup"><span data-stu-id="65da6-193">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::</span></span>

<span data-ttu-id="65da6-194">В следующем примере создается исключение, так как кодовая точка находится за пределами дополнительного диапазона:</span><span class="sxs-lookup"><span data-stu-id="65da6-194">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

<span data-ttu-id="65da6-195">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::</span><span class="sxs-lookup"><span data-stu-id="65da6-195">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::</span></span>

### <a name="no-locrune-usage-example-changing-letter-case"></a><span data-ttu-id="65da6-196">Пример использования Rune: изменение регистра букв</span><span class="sxs-lookup"><span data-stu-id="65da6-196">Rune usage example: changing letter case</span></span>

<span data-ttu-id="65da6-197">API, который принимает `char` и предполагает, что работает с кодовой точкой, которая является скалярным значением, работает неправильно, если `char` принадлежит суррогатной паре.</span><span class="sxs-lookup"><span data-stu-id="65da6-197">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="65da6-198">Например, рассмотрим следующий метод, который вызывает <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> для каждого экземпляра char в string:</span><span class="sxs-lookup"><span data-stu-id="65da6-198">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

<span data-ttu-id="65da6-199">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::</span><span class="sxs-lookup"><span data-stu-id="65da6-199">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="65da6-200">Если `input` string содержит строчную букву дезерет `er` (`𐑉`), этот код не преобразует ее в прописную букву (`𐐡`).</span><span class="sxs-lookup"><span data-stu-id="65da6-200">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="65da6-201">Код вызывает `char.ToUpperInvariant` отдельно для каждой суррогатной кодовой точки `U+D801` и `U+DC49`.</span><span class="sxs-lookup"><span data-stu-id="65da6-201">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="65da6-202">Однако в самой кодовой точке `U+D801` информации недостаточно, чтобы идентифицировать ее как строчную букву. Таким образом `char.ToUpperInvariant` оставляет ее как есть.</span><span class="sxs-lookup"><span data-stu-id="65da6-202">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="65da6-203">И таким же образом обрабатывает `U+DC49`.</span><span class="sxs-lookup"><span data-stu-id="65da6-203">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="65da6-204">В результате буква "𐑉" нижнего регистра в `input` string не преобразуется в букву "𐐡" верхнего регистра.</span><span class="sxs-lookup"><span data-stu-id="65da6-204">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="65da6-205">Вот два варианта правильного преобразования string в верхний регистр:</span><span class="sxs-lookup"><span data-stu-id="65da6-205">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="65da6-206">Вызовите <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> для входного экземпляра string, а не в итерации `char`-by-`char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-206">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="65da6-207">Метод `string.ToUpperInvariant` имеет доступ к обеим частям каждой суррогатной пары, поэтому он может правильно обрабатывать все кодовые точки Юникода.</span><span class="sxs-lookup"><span data-stu-id="65da6-207">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="65da6-208">Выполните итерацию скалярных значений Юникода в качестве экземпляров `Rune`, а не экземпляров `char`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="65da6-208">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="65da6-209">Так как экземпляр `Rune` является допустимым скалярным значением Юникода, его можно передать в API-интерфейсы, которые должны работать со скалярным значением.</span><span class="sxs-lookup"><span data-stu-id="65da6-209">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="65da6-210">Например, вызвав <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType>, как показано в следующем примере, вы получите правильные результаты:</span><span class="sxs-lookup"><span data-stu-id="65da6-210">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  <span data-ttu-id="65da6-211">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::</span><span class="sxs-lookup"><span data-stu-id="65da6-211">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::</span></span>

### <a name="other-no-locrune-apis"></a><span data-ttu-id="65da6-212">Другие API-интерфейсы Rune</span><span class="sxs-lookup"><span data-stu-id="65da6-212">Other Rune APIs</span></span>

<span data-ttu-id="65da6-213">Тип `Rune` предоставляет аналоги многих API-интерфейсов `char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-213">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="65da6-214">Например, приведенные ниже методы отражают статические API-интерфейсы для типа `char`:</span><span class="sxs-lookup"><span data-stu-id="65da6-214">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="65da6-215">Чтобы получить необработанное скалярное значение из экземпляра `Rune`, используйте свойство <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65da6-215">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="65da6-216">Чтобы преобразовать экземпляр `Rune` обратно в последовательность типов `char`, используйте метод <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> или <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65da6-216">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="65da6-217">Так как любое скалярное значение Юникода может быть представлено одним экземпляром `char` или суррогатной парой, любой экземпляр `Rune` может быть представлен не более чем двумя экземплярами `char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-217">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="65da6-218">Используйте <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType>, чтобы узнать количество экземпляров `char`, требуемых для представления экземпляра `Rune`.</span><span class="sxs-lookup"><span data-stu-id="65da6-218">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="65da6-219">Дополнительные сведения о типе `Rune` .NET см. в [справочнике по API для `Rune`](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="65da6-219">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="65da6-220">Кластеры графем</span><span class="sxs-lookup"><span data-stu-id="65da6-220">Grapheme clusters</span></span>

<span data-ttu-id="65da6-221">То, что выглядит как один символ, может быть результатом комбинации нескольких кодовых точек. Таким образом, более описательным термином, который часто используется вместо термина "символ", является [кластер графем](https://www.unicode.org/glossary/#grapheme_cluster).</span><span class="sxs-lookup"><span data-stu-id="65da6-221">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="65da6-222">В .NET эквивалентным термином является [текстовый элемент](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="65da6-222">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="65da6-223">Рассмотрим экземпляры `string` "a", "á", "á" и "`👩🏽‍🚒`".</span><span class="sxs-lookup"><span data-stu-id="65da6-223">Consider the `string` instances "a", "á", "á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="65da6-224">Если операционная система обрабатывает их в соответствии со стандартом Юникода, каждый из этих экземпляров `string` отображается в виде одного текстового элемента или кластера графем.</span><span class="sxs-lookup"><span data-stu-id="65da6-224">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="65da6-225">Однако последние два представлены более чем одной кодовой точкой скалярного значения.</span><span class="sxs-lookup"><span data-stu-id="65da6-225">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="65da6-226">Экземпляр string "a" представлен одним скалярным значением и содержит один экземпляр `char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-226">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="65da6-227">Экземпляр string "á" представлен одним скалярным значением и содержит один экземпляр `char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-227">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="65da6-228">Экземпляр string "á" выглядит так же, как "á", но представлен двумя скалярными значениями и содержит два экземпляра `char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-228">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="65da6-229">Наконец, экземпляр string "`👩🏽‍🚒`" представлен четырьмя скалярными значениями и содержит семь экземпляров `char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-229">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="65da6-230">`U+1F469 WOMAN` (дополнительный диапазон, требуется суррогатная пара);</span><span class="sxs-lookup"><span data-stu-id="65da6-230">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="65da6-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (дополнительный диапазон, требуется суррогатная пара);</span><span class="sxs-lookup"><span data-stu-id="65da6-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="65da6-232">`U+1F692 FIRE ENGINE` (дополнительный диапазон, требуется суррогатная пара).</span><span class="sxs-lookup"><span data-stu-id="65da6-232">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="65da6-233">В некоторых из приведенных выше примерах, таких как комбинированный модификатор диакритических знаков или модификатор тона кожи, кодовая точка не отображается как отдельный элемент на экране.</span><span class="sxs-lookup"><span data-stu-id="65da6-233">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="65da6-234">Вместо этого она служит для изменения внешнего вида текстового элемента, который был до него.</span><span class="sxs-lookup"><span data-stu-id="65da6-234">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="65da6-235">В этих примерах показано, что может потребоваться несколько скалярных значений, чтобы составить один "символ" или "кластер графем".</span><span class="sxs-lookup"><span data-stu-id="65da6-235">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="65da6-236">Чтобы перечислить кластеры графем для `string`, используйте класс <xref:System.Globalization.StringInfo>, как показано в приведенном ниже примере.</span><span class="sxs-lookup"><span data-stu-id="65da6-236">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="65da6-237">Если вы знакомы с Swift, тип `StringInfo` .NET концептуально похож на [тип `character` Swift](https://developer.apple.com/documentation/swift/character).</span><span class="sxs-lookup"><span data-stu-id="65da6-237">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-no-locchar-no-locrune-and-text-element-instances"></a><span data-ttu-id="65da6-238">Пример: количество char, Rune и экземпляров текстовых элементов</span><span class="sxs-lookup"><span data-stu-id="65da6-238">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="65da6-239">В интерфейсах API .NET кластер графем называется *текстовым элементом*.</span><span class="sxs-lookup"><span data-stu-id="65da6-239">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="65da6-240">Приведенный ниже метод демонстрирует различия между `char`, `Rune` и экземплярами текстового элемента в `string`:</span><span class="sxs-lookup"><span data-stu-id="65da6-240">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

<span data-ttu-id="65da6-241">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::</span><span class="sxs-lookup"><span data-stu-id="65da6-241">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::</span></span>

<span data-ttu-id="65da6-242">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::</span><span class="sxs-lookup"><span data-stu-id="65da6-242">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::</span></span>

<span data-ttu-id="65da6-243">Если вы запустите этот код в .NET Framework или .NET Core 3.1 или более ранней версии, для эмодзи отобразится `4` текстовых элемента.</span><span class="sxs-lookup"><span data-stu-id="65da6-243">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="65da6-244">Это связано с ошибкой в классе `StringInfo`, которая исправлена в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="65da6-244">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-no-locstring-instances"></a><span data-ttu-id="65da6-245">Пример: разделение экземпляров string</span><span class="sxs-lookup"><span data-stu-id="65da6-245">Example: splitting string instances</span></span>

<span data-ttu-id="65da6-246">При разделении экземпляров `string` не разделяйте суррогатные пары и кластеры графем.</span><span class="sxs-lookup"><span data-stu-id="65da6-246">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="65da6-247">Рассмотрим приведенный ниже пример неправильного кода, который будет вставлять разрывы строк через каждые 10 символов в string.</span><span class="sxs-lookup"><span data-stu-id="65da6-247">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

<span data-ttu-id="65da6-248">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::</span><span class="sxs-lookup"><span data-stu-id="65da6-248">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="65da6-249">Так как этот код перечисляет экземпляры `char`, суррогатная пара, которая пересекает границу 10-`char`, будет разделена и между ними будет введена новая строка.</span><span class="sxs-lookup"><span data-stu-id="65da6-249">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="65da6-250">Эта вставка представляет собой повреждение данных, так как суррогатные кодовые точки имеют смысл только как пары.</span><span class="sxs-lookup"><span data-stu-id="65da6-250">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="65da6-251">При перечислении экземпляров `Rune` (скалярные значения) вместо экземпляров `char` возможность повреждения данных не исключается.</span><span class="sxs-lookup"><span data-stu-id="65da6-251">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="65da6-252">Набор экземпляров `Rune` может составлять кластер графем, который выходит за границу 10-`char`.</span><span class="sxs-lookup"><span data-stu-id="65da6-252">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="65da6-253">Если набор кластеров графем разделен, он не может быть правильно интерпретирован.</span><span class="sxs-lookup"><span data-stu-id="65da6-253">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="65da6-254">Лучшим подходом является разделение string путем подсчета кластеров графем или текстовых элементов, как показано в приведенном ниже примере.</span><span class="sxs-lookup"><span data-stu-id="65da6-254">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

<span data-ttu-id="65da6-255">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::</span><span class="sxs-lookup"><span data-stu-id="65da6-255">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::</span></span>

<span data-ttu-id="65da6-256">Однако, как упоминалось ранее, в реализациях .NET, отличных от .NET 5, класс `StringInfo` может некорректно обрабатывать некоторые кластеры графем.</span><span class="sxs-lookup"><span data-stu-id="65da6-256">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="65da6-257">UTF-8 и UTF-32</span><span class="sxs-lookup"><span data-stu-id="65da6-257">UTF-8 and UTF-32</span></span>

<span data-ttu-id="65da6-258">В предыдущих разделах основное внимание уделялось UTF-16, потому что именно эту кодировку .NET использует для кодирования экземпляров `string`.</span><span class="sxs-lookup"><span data-stu-id="65da6-258">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="65da6-259">Существуют и другие системы кодирования для Юникода: [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) и [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span><span class="sxs-lookup"><span data-stu-id="65da6-259">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="65da6-260">Эти кодировки используют 8-разрядные и 32-разрядные единицы кода соответственно.</span><span class="sxs-lookup"><span data-stu-id="65da6-260">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="65da6-261">Как и в системе UTF-16, для UTF-8 требуется несколько единиц кода, чтобы предоставить некоторые скалярные значения Юникода.</span><span class="sxs-lookup"><span data-stu-id="65da6-261">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="65da6-262">UTF-32 может представлять любое скалярное значение в одной 32-разрядной единице кода.</span><span class="sxs-lookup"><span data-stu-id="65da6-262">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="65da6-263">Ниже приведено несколько примеров, показывающих, как одна и та же кодовая точка Юникода представлена в каждой из этих трех систем кодирования Юникода.</span><span class="sxs-lookup"><span data-stu-id="65da6-263">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

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

<span data-ttu-id="65da6-264">Как упоминалось ранее, одна единица кода UTF-16 из [суррогатной пары](#surrogate-pairs) сама по себе не имеет смысла.</span><span class="sxs-lookup"><span data-stu-id="65da6-264">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="65da6-265">Таким же образом одна единица кода UTF-8 сама по себе не имеет смысла, если она находится в последовательности из двух, трех или четырех единиц, используемых для вычисления скалярных значений.</span><span class="sxs-lookup"><span data-stu-id="65da6-265">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="65da6-266">Порядок байтов</span><span class="sxs-lookup"><span data-stu-id="65da6-266">Endianness</span></span>

<span data-ttu-id="65da6-267">В .NET единицы кода UTF-16 string хранятся в непрерывной памяти в виде последовательности 16-разрядных целых чисел (экземпляров `char`).</span><span class="sxs-lookup"><span data-stu-id="65da6-267">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="65da6-268">Разряды отдельных единиц кода размещаются в соответствии с [порядком байтов](https://en.wikipedia.org/wiki/Endianness) текущей архитектуры.</span><span class="sxs-lookup"><span data-stu-id="65da6-268">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="65da6-269">В архитектуре с прямым порядком байтов экземпляр string, состоящий из кодовых точек UTF-16 `[ D801 DCCC ]`, будет размещен в памяти в виде байтов `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span><span class="sxs-lookup"><span data-stu-id="65da6-269">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="65da6-270">В архитектуре с обратным порядком байтов тот же экземпляр string будет размещен в памяти в виде байтов `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span><span class="sxs-lookup"><span data-stu-id="65da6-270">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="65da6-271">Компьютерные системы, которые взаимодействуют друг с другом, должны согласовать представление передаваемых данных.</span><span class="sxs-lookup"><span data-stu-id="65da6-271">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="65da6-272">Большинство сетевых протоколов используют систему UTF-8 в качестве стандарта при передаче текста, частично во избежание проблем, которые могут возникнуть из-за того, что компьютер с обратным порядком байтов взаимодействует с компьютером с прямым порядком байтов.</span><span class="sxs-lookup"><span data-stu-id="65da6-272">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="65da6-273">Экземпляр string, состоящий из кодовых точек UTF-8 `[ F0 90 93 8C ]`, всегда будет представлен в виде байтов `[ 0xF0, 0x90, 0x93, 0x8C ]`, независимо от порядка байтов.</span><span class="sxs-lookup"><span data-stu-id="65da6-273">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="65da6-274">Чтобы использовать систему UTF-8 для передачи текста, приложения .NET часто применяют код, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="65da6-274">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="65da6-275">В предыдущем примере метод [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) декодирует экземпляр `string`UTF-16 обратно в ряд скалярных значений Юникода, затем он повторно кодирует эти скалярные значения в UTF-8 и помещает полученную последовательность в массив `byte`.</span><span class="sxs-lookup"><span data-stu-id="65da6-275">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="65da6-276">Метод [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) выполняет обратное преобразование, преобразовывая массив `byte` UTF-8 в `string` UTF-16.</span><span class="sxs-lookup"><span data-stu-id="65da6-276">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="65da6-277">Так как система UTF-8 очень часто используется в Интернете, очевидным решением может показаться считывать необработанные байты из сети и обрабатывать данные, как если бы это была система кодировки UTF-8.</span><span class="sxs-lookup"><span data-stu-id="65da6-277">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="65da6-278">Однако вы должны проверить, что она действительно имеет правильный формат.</span><span class="sxs-lookup"><span data-stu-id="65da6-278">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="65da6-279">Вредоносный клиент может отправить в службу неверно сформированную кодировку UTF-8.</span><span class="sxs-lookup"><span data-stu-id="65da6-279">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="65da6-280">Если вы выполняете операции с этими данными так, как если бы они были правильно сформированы, это может вызвать ошибки или бреши в системе безопасности приложения.</span><span class="sxs-lookup"><span data-stu-id="65da6-280">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="65da6-281">Чтобы проверить данные UTF-8, вы можете использовать метод, например `Encoding.UTF8.GetString`, который при преобразовании входящих данных в `string` будет выполнять проверку.</span><span class="sxs-lookup"><span data-stu-id="65da6-281">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="65da6-282">Кодирование с правильным форматом</span><span class="sxs-lookup"><span data-stu-id="65da6-282">Well-formed encoding</span></span>

<span data-ttu-id="65da6-283">Кодировка Юникод с правильным форматом — это экземпляр string кодовых единиц, который может быть однозначно и без ошибок декодирован в последовательность скалярных значений Юникода.</span><span class="sxs-lookup"><span data-stu-id="65da6-283">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="65da6-284">Данные с правильным форматом могут быть свободно перекодированы между UTF-8, UTF-16 и UTF-32.</span><span class="sxs-lookup"><span data-stu-id="65da6-284">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="65da6-285">Вопрос в том, имеет ли последовательность кодирования правильный формат или нет, независимо от порядка байтов в архитектуре компьютера.</span><span class="sxs-lookup"><span data-stu-id="65da6-285">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="65da6-286">Неверно сформированная последовательность UTF-8 имеет неправильный формат как на компьютерах с обратным порядком байтов, так и на компьютерах с прямым порядком байтов.</span><span class="sxs-lookup"><span data-stu-id="65da6-286">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="65da6-287">Вот несколько примеров кодировок с неправильным форматом:</span><span class="sxs-lookup"><span data-stu-id="65da6-287">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="65da6-288">В UTF-8 последовательность `[ 6C C2 61 ]` имеет неправильный формат, потому что за `C2` не может следовать `61`.</span><span class="sxs-lookup"><span data-stu-id="65da6-288">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="65da6-289">В UTF-16 последовательность `[ DC00 DD00 ]` (или, в C#, string `"\udc00\udd00"`) имеет неправильный формат, потому что за младшей заменяющей кодовой точкой `DC00` не может следовать другая младшая заменяющая точка `DD00`.</span><span class="sxs-lookup"><span data-stu-id="65da6-289">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="65da6-290">В UTF-32 последовательность `[ 0011ABCD ]` имеет неправильный формат, так как `0011ABCD` находится вне диапазона скалярных значений Юникода.</span><span class="sxs-lookup"><span data-stu-id="65da6-290">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="65da6-291">В .NET экземпляры `string` почти всегда содержат данные UTF-16 с правильным форматом, но это не гарантировано.</span><span class="sxs-lookup"><span data-stu-id="65da6-291">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="65da6-292">В следующих примерах показан допустимый код C#, который создает данные UTF-16 с неправильным форматом в экземплярах `string`.</span><span class="sxs-lookup"><span data-stu-id="65da6-292">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="65da6-293">Литерал с неправильным форматом:</span><span class="sxs-lookup"><span data-stu-id="65da6-293">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="65da6-294">Подстрока, которая разделяет суррогатную пару:</span><span class="sxs-lookup"><span data-stu-id="65da6-294">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="65da6-295">API-интерфейсы, такие как [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A), никогда не возвращают экземпляры `string` с неправильным форматом.</span><span class="sxs-lookup"><span data-stu-id="65da6-295">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="65da6-296">Методы `Encoding.GetString` и `Encoding.GetBytes` обнаруживают последовательности с неправильным форматом во входных данных и выполняют замену символов при формировании выходных данных.</span><span class="sxs-lookup"><span data-stu-id="65da6-296">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="65da6-297">Например, если для метода [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) во входных данных отображается байт, отличный от ASCII (вне диапазона U+0000–U+007F), он вставляет символ "?" в возвращенный экземпляр `string`.</span><span class="sxs-lookup"><span data-stu-id="65da6-297">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="65da6-298">Метод [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) заменяет последовательности UTF-8 с неправильным форматом на `U+FFFD REPLACEMENT CHARACTER ('�')` в возвращаемом экземпляре `string`.</span><span class="sxs-lookup"><span data-stu-id="65da6-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="65da6-299">Дополнительные сведения см. в разделах 5.22 и 3.9 [стандарта Юникода](https://www.unicode.org/versions/latest/).</span><span class="sxs-lookup"><span data-stu-id="65da6-299">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="65da6-300">Встроенные классы `Encoding` также можно настроить для создания исключения, а не для замены символов, когда отображаются последовательности с неправильным форматом.</span><span class="sxs-lookup"><span data-stu-id="65da6-300">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="65da6-301">Этот подход часто используется в приложениях, требующих особых мер безопасности, где замена символов может быть неприемлемой.</span><span class="sxs-lookup"><span data-stu-id="65da6-301">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="65da6-302">Сведения о том, как использовать встроенные классы `Encoding`, см. в статье [Кодировка символов в .NET](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="65da6-302">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="65da6-303">См. также</span><span class="sxs-lookup"><span data-stu-id="65da6-303">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="65da6-304">Глобализация и локализация</span><span class="sxs-lookup"><span data-stu-id="65da6-304">Globalization and Localization</span></span>](../globalization-localization/index.md)
