---
title: Оператор While... End While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965816"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="ee118-102">Оператор While... End While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee118-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="ee118-103">Выполняет последовательность операторов, если заданное условие имеет значение `True`.</span><span class="sxs-lookup"><span data-stu-id="ee118-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee118-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ee118-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="ee118-105">Части</span><span class="sxs-lookup"><span data-stu-id="ee118-105">Parts</span></span>  
  
|<span data-ttu-id="ee118-106">Термин</span><span class="sxs-lookup"><span data-stu-id="ee118-106">Term</span></span>|<span data-ttu-id="ee118-107">Определение</span><span class="sxs-lookup"><span data-stu-id="ee118-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="ee118-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="ee118-108">Required.</span></span> <span data-ttu-id="ee118-109">`Boolean`выражение.</span><span class="sxs-lookup"><span data-stu-id="ee118-109">`Boolean` expression.</span></span> <span data-ttu-id="ee118-110">Если `condition` имеет `Nothing`значение, Visual Basic обрабатывает его `False`как.</span><span class="sxs-lookup"><span data-stu-id="ee118-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="ee118-111">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="ee118-111">Optional.</span></span> <span data-ttu-id="ee118-112">Один или несколько следующих `While`инструкций, которые выполняются каждый раз `condition` , —. `True`</span><span class="sxs-lookup"><span data-stu-id="ee118-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="ee118-113">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="ee118-113">Optional.</span></span> <span data-ttu-id="ee118-114">Передает управление следующей итерации `While` блока.</span><span class="sxs-lookup"><span data-stu-id="ee118-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="ee118-115">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="ee118-115">Optional.</span></span> <span data-ttu-id="ee118-116">Передает управление за пределы `While` блока.</span><span class="sxs-lookup"><span data-stu-id="ee118-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="ee118-117">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="ee118-117">Required.</span></span> <span data-ttu-id="ee118-118">Завершает определение блока `While`.</span><span class="sxs-lookup"><span data-stu-id="ee118-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee118-119">Примечания</span><span class="sxs-lookup"><span data-stu-id="ee118-119">Remarks</span></span>  
 <span data-ttu-id="ee118-120">Используйте структуру, если необходимо повторить набор инструкций неопределенное количество раз, если условие остается `True`. `While...End While`</span><span class="sxs-lookup"><span data-stu-id="ee118-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="ee118-121">Если вы хотите обеспечить большую гибкость при тестировании условия или результата тестирования, вы можете предпочесть оператору [Do... Loop, инструкция](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ee118-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="ee118-122">Если нужно повторить инструкции заданное число раз, то [для... ](../../../visual-basic/language-reference/statements/for-next-statement.md)Обычно лучше подходит следующий оператор.</span><span class="sxs-lookup"><span data-stu-id="ee118-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee118-123">`While` Ключевое слово также используется в [инструкции Do... Оператор Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), [предложение Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) и [предложение Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ee118-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="ee118-124">Если `condition` имеет `True`значение, все `statements` выполняется до тех пор `End While` , пока не будет обнаружен оператор.</span><span class="sxs-lookup"><span data-stu-id="ee118-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="ee118-125">Затем элемент управления возвращается в `While` инструкцию и `condition` снова проверяется.</span><span class="sxs-lookup"><span data-stu-id="ee118-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="ee118-126">Если `condition` по- `True`прежнему, процесс повторяется.</span><span class="sxs-lookup"><span data-stu-id="ee118-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="ee118-127">Если это `False`так, управление передается оператору, `End While` следующему за оператором.</span><span class="sxs-lookup"><span data-stu-id="ee118-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="ee118-128">`While` Оператор всегда проверяет условие перед началом цикла.</span><span class="sxs-lookup"><span data-stu-id="ee118-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="ee118-129">Цикл продолжается, пока условие остается `True`.</span><span class="sxs-lookup"><span data-stu-id="ee118-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="ee118-130">Если `condition` параметр `False` имеет значение при первом входе в цикл, он не выполняется даже один раз.</span><span class="sxs-lookup"><span data-stu-id="ee118-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="ee118-131">Обычно результат сравнения двух значений, но может быть любым выражением, результатом вычисления которого является [логическое значение типа данных](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` или `False`). `condition`</span><span class="sxs-lookup"><span data-stu-id="ee118-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="ee118-132">Это выражение может включать в себя значение другого типа данных, например числовой тип, который был преобразован в `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="ee118-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="ee118-133">Можно вложить `While` циклы, поместив один цикл в другой.</span><span class="sxs-lookup"><span data-stu-id="ee118-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="ee118-134">Можно также вкладывать различные виды управляющих структур друг в друга.</span><span class="sxs-lookup"><span data-stu-id="ee118-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="ee118-135">Дополнительные сведения см. в разделе [вложенные структуры управления](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="ee118-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="ee118-136">Выйти, пока</span><span class="sxs-lookup"><span data-stu-id="ee118-136">Exit While</span></span>  
 <span data-ttu-id="ee118-137">Оператор [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) может предоставить другой способ выхода из `While` цикла.</span><span class="sxs-lookup"><span data-stu-id="ee118-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="ee118-138">`Exit While`немедленно передает управление оператору, который следует за `End While` оператором.</span><span class="sxs-lookup"><span data-stu-id="ee118-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="ee118-139">Обычно используется `Exit While` после вычисления некоторого условия (например, `If...Then...Else` в структуре).</span><span class="sxs-lookup"><span data-stu-id="ee118-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="ee118-140">Может потребоваться выйти из цикла, если обнаруживается условие, которое делает ненужным или невозможным продолжение итераций, например ошибочное значение или запрос на завершение.</span><span class="sxs-lookup"><span data-stu-id="ee118-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="ee118-141">Можно использовать `Exit While` при проверке условия, которое может вызвать бесконечный *цикл*, что является циклом, который может выполнять очень большое или даже бесконечное число раз.</span><span class="sxs-lookup"><span data-stu-id="ee118-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="ee118-142">Затем можно использовать `Exit While` для экранирования цикла.</span><span class="sxs-lookup"><span data-stu-id="ee118-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="ee118-143">Любое количество `Exit While` операторов можно разместить `While` в любом месте цикла.</span><span class="sxs-lookup"><span data-stu-id="ee118-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="ee118-144">При использовании внутри вложенных `While` `Exit While` циклов передает управление за пределы самого внутреннего цикла и в следующий более высокий уровень вложенности.</span><span class="sxs-lookup"><span data-stu-id="ee118-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="ee118-145">`Continue While` Оператор немедленно передает управление следующей итерации цикла.</span><span class="sxs-lookup"><span data-stu-id="ee118-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="ee118-146">Дополнительные сведения см. в разделе [оператор continue](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ee118-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee118-147">Пример</span><span class="sxs-lookup"><span data-stu-id="ee118-147">Example</span></span>  
 <span data-ttu-id="ee118-148">В следующем примере операторы в цикле продолжают выполняться до тех пор, пока `index` переменная не будет больше 10.</span><span class="sxs-lookup"><span data-stu-id="ee118-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="ee118-149">Пример</span><span class="sxs-lookup"><span data-stu-id="ee118-149">Example</span></span>  
 <span data-ttu-id="ee118-150">В следующем примере показано использование `Continue While` операторов и. `Exit While`</span><span class="sxs-lookup"><span data-stu-id="ee118-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="ee118-151">Пример</span><span class="sxs-lookup"><span data-stu-id="ee118-151">Example</span></span>  
 <span data-ttu-id="ee118-152">В следующем примере считываются все строки в текстовом файле.</span><span class="sxs-lookup"><span data-stu-id="ee118-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="ee118-153">Метод открывает файл и возвращает объект <xref:System.IO.StreamReader> , считывающий символы. <xref:System.IO.File.OpenText%2A></span><span class="sxs-lookup"><span data-stu-id="ee118-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="ee118-154">В условии <xref:System.IO.StreamReader.Peek%2A> метод`StreamReader` определяет, содержит ли файл дополнительные символы. `While`</span><span class="sxs-lookup"><span data-stu-id="ee118-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="ee118-155">См. также</span><span class="sxs-lookup"><span data-stu-id="ee118-155">See also</span></span>

- [<span data-ttu-id="ee118-156">Циклические структуры</span><span class="sxs-lookup"><span data-stu-id="ee118-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="ee118-157">Оператор Do...Loop</span><span class="sxs-lookup"><span data-stu-id="ee118-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="ee118-158">Оператор For...Next</span><span class="sxs-lookup"><span data-stu-id="ee118-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="ee118-159">Логический тип данных</span><span class="sxs-lookup"><span data-stu-id="ee118-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="ee118-160">Вложенные структуры управления</span><span class="sxs-lookup"><span data-stu-id="ee118-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="ee118-161">Оператор Exit</span><span class="sxs-lookup"><span data-stu-id="ee118-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="ee118-162">Оператор Continue</span><span class="sxs-lookup"><span data-stu-id="ee118-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
