---
title: Практическое руководство. Сцепка нескольких строк (руководство по C#)
description: C# поддерживает различные способы сцепки строк. Узнайте, какие доступны варианты и как выбирать между ними.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: bbdeba4ee3526140de29ac0d7c97e9a593729d47
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389526"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="8d76f-104">Практическое руководство. Сцепка нескольких строк (руководство по C#)</span><span class="sxs-lookup"><span data-stu-id="8d76f-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="8d76f-105">*Объединение* подразумевает добавление одной строки к концу другой.</span><span class="sxs-lookup"><span data-stu-id="8d76f-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="8d76f-106">Вы можете сцеплять строки с помощью оператора `+`.</span><span class="sxs-lookup"><span data-stu-id="8d76f-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="8d76f-107">Строковые литералы и константы сцепляются во время компиляции, а не во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="8d76f-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="8d76f-108">Строковые переменные сцепляются только во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="8d76f-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="8d76f-109">Следующий пример показывает использование сцепки для разделения длинного строкового литерала на строки меньшего размера, чтобы повысить удобочитаемость исходного кода.</span><span class="sxs-lookup"><span data-stu-id="8d76f-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="8d76f-110">Эти части объединяются в одну строку во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="8d76f-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="8d76f-111">Количество строк не влияет на производительность во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="8d76f-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="8d76f-112">Для сцепки строковых переменных вы можете использовать операторы `+` или `+=`, [интерполяцию строк](../language-reference/tokens/interpolated.md), а также методы <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> или <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d76f-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="8d76f-113">Оператор `+` прост в использовании и позволяет получить интуитивно понятный код.</span><span class="sxs-lookup"><span data-stu-id="8d76f-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="8d76f-114">Даже если в одном выражении используется несколько операторов `+`, содержимое строки копируется только один раз.</span><span class="sxs-lookup"><span data-stu-id="8d76f-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="8d76f-115">В следующем коде показаны примеры использования операторов `+` и `+=` для сцепки строк:</span><span class="sxs-lookup"><span data-stu-id="8d76f-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="8d76f-116">В некоторых выражениях строки проще сцепить с помощью интерполяции, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="8d76f-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="8d76f-117">В операциях сцепки строк компилятор C# обрабатывает строки NULL так же, как пустые строки.</span><span class="sxs-lookup"><span data-stu-id="8d76f-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="8d76f-118">Другие методы сцепки строк: <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d76f-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8d76f-119">Этот метод лучше использовать при создании строки из небольшого числа строк-компонентов.</span><span class="sxs-lookup"><span data-stu-id="8d76f-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="8d76f-120">В других случаях вы можете сцеплять строки во время цикла и не знать, сколько исходных строк вы сцепляете. При этом фактическое число исходных строк может быть большим.</span><span class="sxs-lookup"><span data-stu-id="8d76f-120">In other cases, you may be combining strings in a loop where you don't know how many source strings you're combining, and the actual number of source strings may be large.</span></span> <span data-ttu-id="8d76f-121">Для этих сценариев предназначен класс <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="8d76f-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="8d76f-122">В следующем коде для сцепки строк используется метод <xref:System.Text.StringBuilder.Append%2A> класса <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="8d76f-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="8d76f-123">См. дополнительные сведения о [причинах для выбора объединения строк или класса `StringBuilder` ](xref:System.Text.StringBuilder#StringAndSB).</span><span class="sxs-lookup"><span data-stu-id="8d76f-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB).</span></span>

<span data-ttu-id="8d76f-124">Другой вариант объединения строк из коллекции — использовать метод <xref:System.String.Concat%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d76f-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8d76f-125">Используйте метод <xref:System.String.Join%2A?displayProperty=nameWithType>, если исходные строки должны быть разделены разделителем.</span><span class="sxs-lookup"><span data-stu-id="8d76f-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimiter.</span></span> <span data-ttu-id="8d76f-126">Следующий код объединяет массив слов с помощью обоих методов:</span><span class="sxs-lookup"><span data-stu-id="8d76f-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="8d76f-127">Другой вариант объединения строк из коллекции — использовать [LINQ](../programming-guide/concepts/linq/index.md) и метод <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d76f-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="8d76f-128">Этот метод объединяет исходные строки с помощью лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="8d76f-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="8d76f-129">Лямбда-выражение добавляет каждую строку к существующему накоплению.</span><span class="sxs-lookup"><span data-stu-id="8d76f-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="8d76f-130">Следующий пример показывает объединение массива слов путем добавления пробелов между словами.</span><span class="sxs-lookup"><span data-stu-id="8d76f-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="8d76f-131">Вы можете оценить эти примеры, просмотрев [пример кода](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="8d76f-131">You can try these samples by looking at the [sample code](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="8d76f-132">Или можете скачать примеры [в виде ZIP-файла](../../../samples/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="8d76f-132">Or, you can download the samples [as a zip file](../../../samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d76f-133">См. также</span><span class="sxs-lookup"><span data-stu-id="8d76f-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="8d76f-134">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="8d76f-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="8d76f-135">Строки</span><span class="sxs-lookup"><span data-stu-id="8d76f-135">Strings</span></span>](../programming-guide/strings/index.md)
