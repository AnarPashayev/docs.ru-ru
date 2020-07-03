---
title: Практическое руководство. Поиск по строкам (руководство по C#)
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: 34f9f2df11f9b7c51fcec2f8475a50ccf4c5e220
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324128"
---
# <a name="how-to-search-strings"></a>Практическое руководство. Поиск по строкам

Существует две основные стратегии для поиска текста в строках. Методы класса <xref:System.String> выполняют поиск определенного текста. Регулярные выражения используются для поиска шаблонов в тексте.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Тип [string](../language-reference/builtin-types/reference-types.md#the-string-type) является псевдонимом класса <xref:System.String?displayProperty=nameWithType> и реализует ряд полезных методов для поиска содержимого строк. Среди них: <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>. Класс <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> предоставляет широкие возможности словаря для поиска шаблонов в тексте. В этой статье вы узнаете, как применять эти методы и как выбрать наилучший способ в зависимости от ваших потребностей.

## <a name="does-a-string-contain-text"></a>Содержит ли строка текст?

Методы <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> и <xref:System.String.EndsWith%2A?displayProperty=nameWithType> выполняют поиск определенного текста в строке. В следующем примере показано использование каждого из этих методов, а также сценарии поиска без учета регистра:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet1":::

В предыдущем примере показано важное правило использования этих методов. По умолчанию поиск выполняется **с учетом регистра**. Чтобы выполнить поиск без учета регистра, используйте значение перечисления <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>.

## <a name="where-does-the-sought-text-occur-in-a-string"></a>Где искомый текст находится в строке?

Методы <xref:System.String.IndexOf%2A> и <xref:System.String.LastIndexOf%2A> также ищут текст в строках. Эти методы возвращают расположение текста, поиск которого выполняется. Если текст не найден, возвращается `-1`. В следующем примере происходит поиск первого и последнего вхождения слова "methods" и отображение текста, находящегося между ними.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet2":::

## <a name="finding-specific-text-using-regular-expressions"></a>Поиск определенного текста с помощью регулярных выражений

Класс <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> можно использовать для поиска строк. Такой поиск может отличаться по сложности от самых простых до очень сложных текстовых шаблонов.

В следующем примере кода выполняется поиск слов "the" и "their" в предложении без учета регистра. Статический метод <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> выполняет поиск. В метод передается строка и шаблон поиска. В нашем примере третий аргумент задает поиск без учета регистра. Для получения дополнительной информации см. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.

Шаблон поиска описывает текст для поиска. Следующая таблица описывает каждый элемент шаблона поиска. (В таблице ниже используется один `\`, который в строке C# необходимо экранировать как `\\`).

| Шаблон  | Значение                          |
|----------|----------------------------------|
| `the`    | соответствует тексту "the"             |
| `(eir)?` | Соответствует 0 или 1 вхождению "eir" |
| `\s`     | Соответствует пробелу.    |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet3":::

> [!TIP]
> Методы `string` обычно удобнее при поиске точного совпадения со строкой. Регулярные выражения больше подходят при поиске определенных шаблонов в исходной строке.

## <a name="does-a-string-follow-a-pattern"></a>Соответствует ли строка шаблону?

В следующем коде реализуется проверка формата каждой строки в массиве с использованием регулярных выражений. По условиям проверки каждая строка должна иметь формат номера телефона: три группы цифр, разделенных дефисами. Первые две группы содержат по три цифры, и третья группа состоит из четырех цифр. Шаблон поиска использует регулярное выражение `^\\d{3}-\\d{3}-\\d{4}$`. Дополнительные сведения см. в разделе [Элементы языка регулярных выражений. Краткий справочник](../../standard/base-types/regular-expression-language-quick-reference.md).

| Шаблон | Значение                             |
|---------|-------------------------------------|
| `^`     | соответствует началу строки |
| `\d{3}` | соответствует в точности 3 цифрам  |
| `-`     | соответствует символу "–"           |
| `\d{3}` | соответствует в точности 3 цифрам  |
| `-`     | соответствует символу "–"           |
| `\d{4}` | соответствует в точности 4 цифрам  |
| `$`     | соответствует концу строки       |

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs" id="Snippet4":::

Один шаблон поиска соответствует множеству допустимых строк. Регулярные выражения больше подходят для поиска или проверки соответствия шаблону, а не для поиска отдельной строки текста.

## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../programming-guide/index.md)
- [Строки](../programming-guide/strings/index.md)
- [LINQ и строки](../programming-guide/concepts/linq/linq-and-strings.md)
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- [Регулярные выражения в .NET Framework](../../standard/base-types/regular-expressions.md)
- [Элементы языка регулярных выражений — краткий справочник](../../standard/base-types/regular-expression-language-quick-reference.md)
- [Рекомендации по использованию строк в .NET](../../standard/base-types/best-practices-strings.md)
