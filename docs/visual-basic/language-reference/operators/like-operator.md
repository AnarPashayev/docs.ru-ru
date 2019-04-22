---
title: Оператор Like (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 38e56b8c0ec6bab89052ee42a2cd9c24053c658e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835704"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="979b3-102">Оператор Like (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="979b3-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="979b3-103">Сравнивает строку с шаблоном.</span><span class="sxs-lookup"><span data-stu-id="979b3-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="979b3-104">`Like` Оператор в настоящее время не поддерживается в проектах .NET Core и .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="979b3-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="979b3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="979b3-105">Syntax</span></span>  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="979b3-106">Части</span><span class="sxs-lookup"><span data-stu-id="979b3-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="979b3-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="979b3-107">Required.</span></span> <span data-ttu-id="979b3-108">Любой `Boolean` переменной.</span><span class="sxs-lookup"><span data-stu-id="979b3-108">Any `Boolean` variable.</span></span> <span data-ttu-id="979b3-109">В результате `Boolean` значение, указывающее, является ли `string` удовлетворяет `pattern`.</span><span class="sxs-lookup"><span data-stu-id="979b3-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="979b3-110">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="979b3-110">Required.</span></span> <span data-ttu-id="979b3-111">Произвольное выражение `String` .</span><span class="sxs-lookup"><span data-stu-id="979b3-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="979b3-112">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="979b3-112">Required.</span></span> <span data-ttu-id="979b3-113">Любой `String` выражения, согласующееся с правилами соответствия шаблону описано в подразделе «Примечания».</span><span class="sxs-lookup"><span data-stu-id="979b3-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="979b3-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="979b3-114">Remarks</span></span>  
 <span data-ttu-id="979b3-115">Если значение в `string` соответствует шаблону в `pattern`, `result` является `True`.</span><span class="sxs-lookup"><span data-stu-id="979b3-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="979b3-116">Если строка соответствует шаблону, `result` является `False`.</span><span class="sxs-lookup"><span data-stu-id="979b3-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="979b3-117">Если оба `string` и `pattern` представляют собой пустые строки, в результате `True`.</span><span class="sxs-lookup"><span data-stu-id="979b3-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="979b3-118">Метод сравнения</span><span class="sxs-lookup"><span data-stu-id="979b3-118">Comparison Method</span></span>  
 <span data-ttu-id="979b3-119">Поведение `Like` зависит от оператора [оператор Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="979b3-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="979b3-120">Метод сравнения строк по умолчанию для каждого файла исходного кода является `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="979b3-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="979b3-121">Параметры шаблона</span><span class="sxs-lookup"><span data-stu-id="979b3-121">Pattern Options</span></span>  
 <span data-ttu-id="979b3-122">Сопоставление встроенных шаблонов представляет собой универсальный инструмент для сравнения строк.</span><span class="sxs-lookup"><span data-stu-id="979b3-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="979b3-123">Функции поиска совпадения с шаблоном позволяют сопоставлять каждый символ в `string` от определенный символ, символом-шаблоном, список символ или диапазон символов.</span><span class="sxs-lookup"><span data-stu-id="979b3-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="979b3-124">В следующей таблице показаны символов, разрешенных в `pattern` и их соответствия.</span><span class="sxs-lookup"><span data-stu-id="979b3-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="979b3-125">Символов в `pattern`</span><span class="sxs-lookup"><span data-stu-id="979b3-125">Characters in `pattern`</span></span>|<span data-ttu-id="979b3-126">Соответствует в `string`</span><span class="sxs-lookup"><span data-stu-id="979b3-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="979b3-127">Любой отдельный знак</span><span class="sxs-lookup"><span data-stu-id="979b3-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="979b3-128">Ноль или более символов</span><span class="sxs-lookup"><span data-stu-id="979b3-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="979b3-129">Любая цифра (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="979b3-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="979b3-130">Любому одиночному символу в `charlist`</span><span class="sxs-lookup"><span data-stu-id="979b3-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="979b3-131">Любой единичный символ, не в `charlist`</span><span class="sxs-lookup"><span data-stu-id="979b3-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="979b3-132">Список знаков</span><span class="sxs-lookup"><span data-stu-id="979b3-132">Character Lists</span></span>  
 <span data-ttu-id="979b3-133">Группа из одного или нескольких символов (`charlist`) заключена в квадратные скобки (`[ ]`) может использоваться в соответствии с любым одиночным символом в `string` и могут включать практически любой код символа, включая цифр.</span><span class="sxs-lookup"><span data-stu-id="979b3-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="979b3-134">Восклицательный знак (`!`) в начале `charlist` означает, что соответствие установлено, если для какого-либо знака, за исключением символов в `charlist` находится в `string`.</span><span class="sxs-lookup"><span data-stu-id="979b3-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="979b3-135">При использовании вне скобок восклицательный знак соответствует самому себе.</span><span class="sxs-lookup"><span data-stu-id="979b3-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="979b3-136">Специальные символы</span><span class="sxs-lookup"><span data-stu-id="979b3-136">Special Characters</span></span>  
 <span data-ttu-id="979b3-137">Сопоставляется левая скобка специальные символы (`[`), вопросительный знак (`?`), решетка (`#`) и звездочка (`*`), заключите их в скобки.</span><span class="sxs-lookup"><span data-stu-id="979b3-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="979b3-138">Закрывающая квадратная скобка (`]`) не может использоваться в пределах группы в соответствии с, но он может использоваться за пределами группы как отдельный символ.</span><span class="sxs-lookup"><span data-stu-id="979b3-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="979b3-139">Последовательность символов `[]` считается строкой нулевой длины (`""`).</span><span class="sxs-lookup"><span data-stu-id="979b3-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="979b3-140">Тем не менее он не может быть включено в список символов, заключенные в квадратные скобки.</span><span class="sxs-lookup"><span data-stu-id="979b3-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="979b3-141">Если вы хотите проверить, является ли позиция в `string` содержит один из нескольких символов вообще, можно использовать `Like` дважды.</span><span class="sxs-lookup"><span data-stu-id="979b3-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="979b3-142">Пример см. в статье [Практическое руководство. Сравнение строки на соответствие шаблону](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="979b3-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="979b3-143">Диапазоны символов</span><span class="sxs-lookup"><span data-stu-id="979b3-143">Character Ranges</span></span>  
 <span data-ttu-id="979b3-144">С помощью дефиса (`–`) для разделения нижнюю и верхнюю границу диапазона, `charlist` можно указать диапазон символов.</span><span class="sxs-lookup"><span data-stu-id="979b3-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="979b3-145">Например `[A–Z]` приводит к совпадению, в соответствующий символ позиционирование в `string` может содержать любые символы в диапазоне `A`—`Z`, и `[!H–L]` приводит к совпадению, в соответствующий символ позиции может содержать любые символы за пределами диапазона `H`—`L`.</span><span class="sxs-lookup"><span data-stu-id="979b3-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="979b3-146">При указании диапазона символов, они должны располагаться в порядке возрастания, то есть от меньшего к большему.</span><span class="sxs-lookup"><span data-stu-id="979b3-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="979b3-147">Таким образом `[A–Z]` является допустимым шаблоном, но `[Z–A]` не является.</span><span class="sxs-lookup"><span data-stu-id="979b3-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="979b3-148">Несколько диапазонов символов</span><span class="sxs-lookup"><span data-stu-id="979b3-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="979b3-149">Чтобы указать несколько диапазонов для одной и той же позиции символа, поместите их в фигурных скобках же без разделителей.</span><span class="sxs-lookup"><span data-stu-id="979b3-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="979b3-150">Например `[A–CX–Z]` приводит к совпадению, в соответствующий символ позиционирование в `string` может содержать любые символы, либо диапазона `A`—`C` или диапазоне `X`—`Z`.</span><span class="sxs-lookup"><span data-stu-id="979b3-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="979b3-151">Использование дефиса</span><span class="sxs-lookup"><span data-stu-id="979b3-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="979b3-152">Дефис (`–`) может находиться в начале (после восклицательный знак, если таковые имеются) или в конце `charlist` для сопоставления с самим собой.</span><span class="sxs-lookup"><span data-stu-id="979b3-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="979b3-153">В любом другом месте дефис обозначает диапазон символов, разделенных символы с обеих сторон от дефис.</span><span class="sxs-lookup"><span data-stu-id="979b3-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="979b3-154">Порядок сортировки</span><span class="sxs-lookup"><span data-stu-id="979b3-154">Collating Sequence</span></span>  
 <span data-ttu-id="979b3-155">Значение указанного диапазона зависит от порядка во время выполнения, что определяется знаков `Option Compare` и параметре языкового стандарта системы выполняется код.</span><span class="sxs-lookup"><span data-stu-id="979b3-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="979b3-156">С помощью `Option Compare Binary`, диапазон `[A–E]` соответствует `A`, `B`, `C`, `D`, и `E`.</span><span class="sxs-lookup"><span data-stu-id="979b3-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="979b3-157">С помощью `Option Compare Text`, `[A–E]` соответствует `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, и `e`.</span><span class="sxs-lookup"><span data-stu-id="979b3-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="979b3-158">Диапазон не соответствует `Ê` или `ê` так, как диакритические знаки сортируются после стандартных в порядке сортировки.</span><span class="sxs-lookup"><span data-stu-id="979b3-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="979b3-159">Диграф символов</span><span class="sxs-lookup"><span data-stu-id="979b3-159">Digraph Characters</span></span>  
 <span data-ttu-id="979b3-160">В некоторых языках есть буквенные символы, представляющие два отдельных символов.</span><span class="sxs-lookup"><span data-stu-id="979b3-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="979b3-161">Например, несколько языков используйте символ `æ` для представления символов `a` и `e` при отображении друг с другом.</span><span class="sxs-lookup"><span data-stu-id="979b3-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="979b3-162">`Like` Оператор распознает, что один диграф и два отдельных знака эквивалентны.</span><span class="sxs-lookup"><span data-stu-id="979b3-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="979b3-163">Если указан язык, который используется диграф в региональных параметрах системы, вхождение один диграф в любом `pattern` или `string` соответствует эквивалентный последовательности двух знаков в другой строке.</span><span class="sxs-lookup"><span data-stu-id="979b3-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="979b3-164">Аналогичным образом диграф в `pattern` заключена в квадратные скобки (сам по себе, в списке или в диапазоне) соответствует эквивалентный последовательности двух знаков в `string`.</span><span class="sxs-lookup"><span data-stu-id="979b3-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="979b3-165">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="979b3-165">Overloading</span></span>  
 <span data-ttu-id="979b3-166">`Like` Оператор может быть *перегружены*, что означает, что класс или структура может переопределить его поведение, если операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="979b3-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="979b3-167">Если ваш код использует этот оператор для такого класса или структуры, убедитесь, что его переопределенное.</span><span class="sxs-lookup"><span data-stu-id="979b3-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="979b3-168">Для получения дополнительной информации см. [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="979b3-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="979b3-169">Пример</span><span class="sxs-lookup"><span data-stu-id="979b3-169">Example</span></span>  
 <span data-ttu-id="979b3-170">В этом примере используется `Like` оператор для сравнения строк с различными шаблонами.</span><span class="sxs-lookup"><span data-stu-id="979b3-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="979b3-171">Результаты направляются в `Boolean` переменной, показывающей, удовлетворяет ли каждая строка шаблону.</span><span class="sxs-lookup"><span data-stu-id="979b3-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="979b3-172">См. также</span><span class="sxs-lookup"><span data-stu-id="979b3-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="979b3-173">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="979b3-173">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="979b3-174">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="979b3-174">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="979b3-175">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="979b3-175">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="979b3-176">Оператор Option Compare</span><span class="sxs-lookup"><span data-stu-id="979b3-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="979b3-177">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="979b3-177">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="979b3-178">Практическое руководство. Сравнение строки на соответствие шаблону</span><span class="sxs-lookup"><span data-stu-id="979b3-178">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
