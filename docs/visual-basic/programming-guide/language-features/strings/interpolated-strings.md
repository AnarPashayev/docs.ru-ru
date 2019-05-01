---
title: Интерполированные строки (Visual Basic)
ms.date: 10/31/2017
ms.openlocfilehash: 408f3232258b3b4c7fe6ec160149f8ac70b84b03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024564"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="3f8e6-102">Интерполированные строки (Справочник по языку Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f8e6-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="3f8e6-103">Используется для создания строк.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-103">Used to construct strings.</span></span>  <span data-ttu-id="3f8e6-104">Интерполированное строковое выражение выглядит как строка шаблона, которая содержит *интерполированные выражения*.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="3f8e6-105">Интерполированная строка возвращает строку, которая заменяет содержащиеся в ней интерполированные выражения строковыми представлениями.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="3f8e6-106">Эта функция доступна в Visual Basic 14 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="3f8e6-107">Аргументы интерполированной строки понять проще, чем [строку составного формата](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="3f8e6-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="3f8e6-108">Например, интерполированная строка</span><span class="sxs-lookup"><span data-stu-id="3f8e6-108">For example, the interpolated string</span></span>

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

<span data-ttu-id="3f8e6-109">содержит два интерполированных выражения "{name}" и "{hours:hh}".</span><span class="sxs-lookup"><span data-stu-id="3f8e6-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="3f8e6-110">Эквивалентная строка составного формата имеет следующий вид:</span><span class="sxs-lookup"><span data-stu-id="3f8e6-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);
```

<span data-ttu-id="3f8e6-111">Структура интерполированной строки выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3f8e6-111">The structure of an interpolated string is:</span></span>

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

<span data-ttu-id="3f8e6-112">где:</span><span class="sxs-lookup"><span data-stu-id="3f8e6-112">where:</span></span>

- <span data-ttu-id="3f8e6-113">*field-width* — это целое число со знаком, указывающее количество символов в поле.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="3f8e6-114">Если оно является положительным, поле выравнивается по правому краю, если оно отрицательное — по левому краю.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span>

- <span data-ttu-id="3f8e6-115">*format-string* — это строка формата, соответствующая типу форматируемого объекта.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="3f8e6-116">Например, для <xref:System.DateTime> значение, это может быть [стандартных форматов даты и времени строковое](~/docs/standard/base-types/standard-date-and-time-format-strings.md) например «D» или «d».</span><span class="sxs-lookup"><span data-stu-id="3f8e6-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](~/docs/standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3f8e6-117">Между `$` и `"` в начале строки не может быть пробела.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-117">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="3f8e6-118">Это приводит к ошибке компилятора.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-118">Doing so causes a compiler error.</span></span>

<span data-ttu-id="3f8e6-119">Интерполированную строку можно использовать везде, где допустимо применять строковый литерал.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="3f8e6-120">Интерполированная строка вычисляется каждый раз, когда выполняется код с интерполированной строкой.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="3f8e6-121">Это позволяет разделить определение и вычисление интерполированной строки.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>

<span data-ttu-id="3f8e6-122">Чтобы включить в интерполированную строку фигурные скобки ("{" или "}"), используйте две фигурные скобки — "{{" или "}}".</span><span class="sxs-lookup"><span data-stu-id="3f8e6-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="3f8e6-123">Дополнительные сведения см в разделе «Неявные преобразования».</span><span class="sxs-lookup"><span data-stu-id="3f8e6-123">See the Implicit Conversions section for more details.</span></span>

<span data-ttu-id="3f8e6-124">Если интерполированная строка содержит другие символы со специальным значением в интерполированной строке, например, знак кавычки ("), двоеточие (:) или запятая (,), их необходимо экранировать, если они встречаются в обычном тексте, или они должны быть включены в выражение, разделенное круглыми скобками, если они являются языковыми элементами, включенными в интерполированное выражение.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="3f8e6-125">В следующем примере показано экранирование кавычек, чтобы включить их в результирующую строку, и использование скобок для разделения выражения `(age == 1 ? "" : "s")`, чтобы двоеточие не интерпретировалось как начало строки формата.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a><span data-ttu-id="3f8e6-126">Неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="3f8e6-126">Implicit Conversions</span></span>

<span data-ttu-id="3f8e6-127">Существует три преобразования неявных типов из интерполированных строк.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-127">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="3f8e6-128">Преобразование интерполированной строки в <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="3f8e6-129">В следующем примере возвращается строка, интерполированные строковые выражения которой были заменены их строковыми представлениями.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="3f8e6-130">Пример:</span><span class="sxs-lookup"><span data-stu-id="3f8e6-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   <span data-ttu-id="3f8e6-131">Это окончательный результат интерпретации строк.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="3f8e6-132">Все вхождения двойных фигурных скобок ("{{" и "}}") преобразуются в одиночную фигурную скобку.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span>

2. <span data-ttu-id="3f8e6-133">Преобразование интерполированной строки в переменную <xref:System.IFormattable>, которая позволяет создавать несколько результирующих строк с содержимым для конкретного языка из одного экземпляра <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="3f8e6-134">Это полезно для включения правильных форматов чисел и дат для отдельных языков.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="3f8e6-135">Все вхождения двойных фигурных скобок ("{{" и "}}") остаются двойными фигурными скобками до тех пор, пока строка не будет отформатирована путем явного или неявного вызова метода <xref:System.Object.ToString>.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="3f8e6-136">Все выражения автономной интерполяции преобразуются в {0}, {1}, и т. д.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   <span data-ttu-id="3f8e6-137">В следующем примере используется отражение для отображения членов, а также значений поля и свойства переменной <xref:System.IFormattable>, созданной из интерполированной строки.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="3f8e6-138">Кроме того, переменная <xref:System.IFormattable> передается в метод <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   <span data-ttu-id="3f8e6-139">Обратите внимание, что интерполированную строку можно проверить только с помощью отражения.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="3f8e6-140">Если она передается методу форматирования строк, например <xref:System.Console.WriteLine(System.String)>, элементы формата разрешаются и возвращается результирующая строка.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span>

3. <span data-ttu-id="3f8e6-141">Преобразование интерполированной строки в <xref:System.FormattableString> переменную, которая представляет строку составного формата.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="3f8e6-142">Проверка строки составного формата и способа ее отрисовки в виде результирующей строки может, например, обеспечивать защиту от атак путем внедрения кода, если выполнялось построение запроса.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="3f8e6-143">Объект <xref:System.FormattableString> также включает в себя:</span><span class="sxs-lookup"><span data-stu-id="3f8e6-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="3f8e6-144">Перегрузка <xref:System.FormattableString.ToString>, которая формирует результирующую строку для <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>

      - <span data-ttu-id="3f8e6-145">Объект <xref:System.FormattableString.Invariant%2A> метод, который формирует строку для <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>

      - <span data-ttu-id="3f8e6-146">Метод <xref:System.FormattableString.ToString(System.IFormatProvider)>, который формирует результирующую строку для указанного языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="3f8e6-147">Все вхождения двойных фигурных скобок ("{{» и «}}») остаются двойными фигурными скобками, пока не будет выбрано форматирование.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="3f8e6-148">Все выражения автономной интерполяции преобразуются в {0}, {1}, и т. д.</span><span class="sxs-lookup"><span data-stu-id="3f8e6-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a><span data-ttu-id="3f8e6-149">См. также</span><span class="sxs-lookup"><span data-stu-id="3f8e6-149">See also</span></span>

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [<span data-ttu-id="3f8e6-150">Справочник по языку Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3f8e6-150">Visual Basic Language Reference</span></span>](index.md)
