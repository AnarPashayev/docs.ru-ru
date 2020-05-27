---
ms.openlocfilehash: c0c1c9c9d8e3aeb6f689f754d09b50b208b54112
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702306"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="fd03d-101">Теперь StringInfo и TextElementEnumerator совместимы с UAX29</span><span class="sxs-lookup"><span data-stu-id="fd03d-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="fd03d-102">До этого изменения <xref:System.Globalization.StringInfo?displayProperty=fullName> и <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> обрабатывали все кластеры графем неправильно.</span><span class="sxs-lookup"><span data-stu-id="fd03d-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="fd03d-103">Некоторые графемы были разбиты на составные компоненты, а не объединялись.</span><span class="sxs-lookup"><span data-stu-id="fd03d-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="fd03d-104">Теперь <xref:System.Globalization.StringInfo> и <xref:System.Globalization.TextElementEnumerator> обрабатывают кластеры графем в соответствии с последней версией стандарта Юникода.</span><span class="sxs-lookup"><span data-stu-id="fd03d-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="fd03d-105">Кроме того, метод <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>, который меняет порядок символов строки в Visual Basic на обратный, теперь также соответствует стандарту Юникода для кластеров графем.</span><span class="sxs-lookup"><span data-stu-id="fd03d-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fd03d-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="fd03d-106">Change description</span></span>

<span data-ttu-id="fd03d-107">[Графема](https://www.unicode.org/glossary/#grapheme) или [расширенный кластер графем](https://www.unicode.org/glossary/#extended_grapheme_cluster) — это отдельный воспринимаемый пользователем символ, который может состоять из нескольких кодовых точек Юникода.</span><span class="sxs-lookup"><span data-stu-id="fd03d-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="fd03d-108">Например, строка, содержащая тайский символ "кам" (:::no-loc text="กำ":::), состоит из двух следующих символов:</span><span class="sxs-lookup"><span data-stu-id="fd03d-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="fd03d-109">:::no-loc text="ก"::: (= '\u0e01') — тайский символ "ко кай"</span><span class="sxs-lookup"><span data-stu-id="fd03d-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="fd03d-110">:::no-loc text=" ำ"::: (= '\u0e33') — тайский символ "сара ам"</span><span class="sxs-lookup"><span data-stu-id="fd03d-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="fd03d-111">При отображении пользователю операционная система объединяет эти два символа для формирования одного отображаемого символа (или графемы) "кам" или :::no-loc text="กำ":::.</span><span class="sxs-lookup"><span data-stu-id="fd03d-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="fd03d-112">Эмодзи также могут состоять из нескольких символов, объединенных для единообразного отображения.</span><span class="sxs-lookup"><span data-stu-id="fd03d-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="fd03d-113">В документации по .NET при ссылке на графему иногда применяется термин "текстовый элемент".</span><span class="sxs-lookup"><span data-stu-id="fd03d-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="fd03d-114">Классы <xref:System.Globalization.StringInfo> и <xref:System.Globalization.TextElementEnumerator> проверяют строки и возвращают сведения о содержащихся в них графемах.</span><span class="sxs-lookup"><span data-stu-id="fd03d-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="fd03d-115">В .NET Framework (все версии) и .NET Core 3.x и более ранних версий эти два класса используют пользовательскую логику, которая обрабатывает некоторые комбинирующие классы, но не полностью соответствует [стандарту Юникода](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span><span class="sxs-lookup"><span data-stu-id="fd03d-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="fd03d-116">Например, классы <xref:System.Globalization.StringInfo> и <xref:System.Globalization.TextElementEnumerator> ошибочно разделяют один тайский символ "кам" на составляющие компоненты вместо того, чтобы объединить их.</span><span class="sxs-lookup"><span data-stu-id="fd03d-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="fd03d-117">Эти классы также ошибочно разбивают символ эмодзи "🤷🏽‍♀️" на четыре кластера (пожимание плечами, модификатор тона кожи, модификатор пола и невидимый объединяющий блок) вместо того, чтобы объединить их в один кластер графем.</span><span class="sxs-lookup"><span data-stu-id="fd03d-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="fd03d-118">Начиная с .NET 5 классы <xref:System.Globalization.StringInfo> и <xref:System.Globalization.TextElementEnumerator> удовлетворяют требованиям стандарта Юникода, как указано в [приложении к стандарту Юникод \#29, редакция 35, раздел 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span><span class="sxs-lookup"><span data-stu-id="fd03d-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="fd03d-119">В частности, теперь они возвращают [расширенные кластеры графем](https://www.unicode.org/glossary/#extended_grapheme_cluster) для всех комбинирующих классов.</span><span class="sxs-lookup"><span data-stu-id="fd03d-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="fd03d-120">Рассмотрим следующий код C#:</span><span class="sxs-lookup"><span data-stu-id="fd03d-120">Consider the following C# code:</span></span>

```cs
using System.Globalization;

static void Main(string[] args)
{
    PrintGraphemes("กำ");
    PrintGraphemes("🤷🏽‍♀️");
}

static void PrintGraphemes(string str)
{
    Console.WriteLine($"Printing graphemes of \"{str}\"...");
    int i = 0;

    TextElementEnumerator enumerator = StringInfo.GetTextElementEnumerator(str);
    while (enumerator.MoveNext())
    {
        Console.WriteLine($"Grapheme {++i}: \"{enumerator.Current}\"");
    }

    Console.WriteLine($"({i} grapheme(s) total.)");
    Console.WriteLine();
}
```

<span data-ttu-id="fd03d-121">В .NET Framework и .NET Core 3.x и более ранних версий графемы разделяются, а выходные данные в консоли выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="fd03d-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "ก"
Grapheme 2: "ำ"
(2 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷"
Grapheme 2: "🏽"
Grapheme 3: "‍"
Grapheme 4: "♀️"
(4 grapheme(s) total.)
```

<span data-ttu-id="fd03d-122">В .NET 5 и более поздних версий графемы объединяются, а выходные данные в консоли выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="fd03d-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="fd03d-123">Кроме того, начиная с .NET 5 метод <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>, который меняет порядок символов строки в Visual Basic на обратный, также соответствует стандарту Юникода для кластеров графем.</span><span class="sxs-lookup"><span data-stu-id="fd03d-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="fd03d-124">Эти изменения являются частью более обширного набора улучшений для Юникода и UTF-8 в .NET, включая API перечисления расширенных кластеров графем, который дополняет интерфейсы API перечисления скалярных значений Юникода, появившиеся с типом <xref:System.Text.Rune?displayProperty=fullName> в .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="fd03d-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fd03d-125">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="fd03d-125">Version introduced</span></span>

<span data-ttu-id="fd03d-126">Предварительная версия 1 .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="fd03d-126">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fd03d-127">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="fd03d-127">Recommended action</span></span>

<span data-ttu-id="fd03d-128">Никаких дополнительных действий от вас не требуется.</span><span class="sxs-lookup"><span data-stu-id="fd03d-128">You don't need to take any action.</span></span> <span data-ttu-id="fd03d-129">Ваши приложения будут автоматически обеспечивать более полное соответствие стандартам в различных сценариях, связанных с глобализацией.</span><span class="sxs-lookup"><span data-stu-id="fd03d-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

#### <a name="category"></a><span data-ttu-id="fd03d-130">Категория</span><span class="sxs-lookup"><span data-stu-id="fd03d-130">Category</span></span>

<span data-ttu-id="fd03d-131">Глобализация</span><span class="sxs-lookup"><span data-stu-id="fd03d-131">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fd03d-132">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="fd03d-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
