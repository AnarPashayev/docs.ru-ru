---
title: Оператор Do…Loop
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: a9ec6caccbe161a39b592a642a938b81bae911a6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404788"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="f2835-102">Оператор Do...Loop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2835-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="f2835-103">Повторяет блок инструкций `Boolean` , пока условие находится `True` в состоянии или до тех пор, пока условие не станет `True` .</span><span class="sxs-lookup"><span data-stu-id="f2835-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2835-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f2835-104">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="f2835-105">Компоненты</span><span class="sxs-lookup"><span data-stu-id="f2835-105">Parts</span></span>  
  
|<span data-ttu-id="f2835-106">Термин</span><span class="sxs-lookup"><span data-stu-id="f2835-106">Term</span></span>|<span data-ttu-id="f2835-107">Определение</span><span class="sxs-lookup"><span data-stu-id="f2835-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="f2835-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="f2835-108">Required.</span></span> <span data-ttu-id="f2835-109">Запускает определение `Do` цикла.</span><span class="sxs-lookup"><span data-stu-id="f2835-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="f2835-110">Является обязательным, если используется параметр `Until`.</span><span class="sxs-lookup"><span data-stu-id="f2835-110">Required unless `Until` is used.</span></span> <span data-ttu-id="f2835-111">Повторите цикл, пока `condition` не будет `False` .</span><span class="sxs-lookup"><span data-stu-id="f2835-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="f2835-112">Является обязательным, если используется параметр `While`.</span><span class="sxs-lookup"><span data-stu-id="f2835-112">Required unless `While` is used.</span></span> <span data-ttu-id="f2835-113">Повторите цикл, пока `condition` не будет `True` .</span><span class="sxs-lookup"><span data-stu-id="f2835-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="f2835-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="f2835-114">Optional.</span></span> <span data-ttu-id="f2835-115">Выражение `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="f2835-115">`Boolean` expression.</span></span> <span data-ttu-id="f2835-116">Если `condition` имеет значение `Nothing` , Visual Basic обрабатывает его как `False` .</span><span class="sxs-lookup"><span data-stu-id="f2835-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="f2835-117">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="f2835-117">Optional.</span></span> <span data-ttu-id="f2835-118">Одна или несколько инструкций, повторяемых в, или до, `condition` имеют `True` .</span><span class="sxs-lookup"><span data-stu-id="f2835-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="f2835-119">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="f2835-119">Optional.</span></span> <span data-ttu-id="f2835-120">Передает управление следующей итерации `Do` цикла.</span><span class="sxs-lookup"><span data-stu-id="f2835-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="f2835-121">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="f2835-121">Optional.</span></span> <span data-ttu-id="f2835-122">Передает управление за пределы `Do` цикла.</span><span class="sxs-lookup"><span data-stu-id="f2835-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="f2835-123">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="f2835-123">Required.</span></span> <span data-ttu-id="f2835-124">Завершает определение `Do` цикла.</span><span class="sxs-lookup"><span data-stu-id="f2835-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2835-125">Комментарии</span><span class="sxs-lookup"><span data-stu-id="f2835-125">Remarks</span></span>  
 <span data-ttu-id="f2835-126">Используйте `Do...Loop` структуру, если нужно повторить набор инструкций неопределенное число раз, пока не будет удовлетворено условие.</span><span class="sxs-lookup"><span data-stu-id="f2835-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="f2835-127">Если нужно повторить инструкции заданное число раз, то [для... ](for-next-statement.md)Обычно лучше подходит следующий оператор.</span><span class="sxs-lookup"><span data-stu-id="f2835-127">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="f2835-128">Можно использовать либо `While` , либо `Until` , чтобы указать `condition` , но не оба.</span><span class="sxs-lookup"><span data-stu-id="f2835-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="f2835-129">Тест можно выполнять `condition` только один раз, в начале или в конце цикла.</span><span class="sxs-lookup"><span data-stu-id="f2835-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="f2835-130">Если проверка выполняется в `condition` начале цикла (в `Do` операторе), цикл может не выполняться даже один раз.</span><span class="sxs-lookup"><span data-stu-id="f2835-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="f2835-131">Если протестировать в конце цикла (в `Loop` операторе), цикл всегда выполняется по крайней мере один раз.</span><span class="sxs-lookup"><span data-stu-id="f2835-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="f2835-132">Условие обычно является результатом сравнения двух значений, но может быть любым выражением, результатом вычисления которого является [логическое значение типа данных](../data-types/boolean-data-type.md) ( `True` или `False` ).</span><span class="sxs-lookup"><span data-stu-id="f2835-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="f2835-133">Сюда относятся значения других типов данных, например числовые типы, которые были преобразованы в `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f2835-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="f2835-134">Можно вложить `Do` циклы, поместив один цикл в другой.</span><span class="sxs-lookup"><span data-stu-id="f2835-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="f2835-135">Можно также вкладывать различные виды управляющих структур друг в друга.</span><span class="sxs-lookup"><span data-stu-id="f2835-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="f2835-136">Дополнительные сведения см. в разделе [вложенные структуры управления](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="f2835-136">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2835-137">Эта `Do...Loop` структура обеспечивает большую гибкость, чем [while... Оператор End While](while-end-while-statement.md) , так как он позволяет решить, следует ли завершать цикл при `condition` остановке `True` или при первом преобразовании `True` .</span><span class="sxs-lookup"><span data-stu-id="f2835-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="f2835-138">Он также позволяет тестироваться `condition` как в начале, так и в конце цикла.</span><span class="sxs-lookup"><span data-stu-id="f2835-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="f2835-139">Выйти</span><span class="sxs-lookup"><span data-stu-id="f2835-139">Exit Do</span></span>  
 <span data-ttu-id="f2835-140">Оператор [Exit Do](exit-statement.md) может предоставить альтернативный способ выхода из `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="f2835-140">The [Exit Do](exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="f2835-141">`Exit Do`немедленно передает управление оператору, следующему за `Loop` оператором.</span><span class="sxs-lookup"><span data-stu-id="f2835-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="f2835-142">`Exit Do`часто используется после вычисления некоторого условия, например в `If...Then...Else` структуре.</span><span class="sxs-lookup"><span data-stu-id="f2835-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="f2835-143">Может потребоваться выйти из цикла, если обнаруживается условие, которое делает ненужным или невозможным продолжение итераций, например ошибочное значение или запрос на завершение.</span><span class="sxs-lookup"><span data-stu-id="f2835-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="f2835-144">Одно из них `Exit Do` — Проверка на наличие условия, которое может вызвать *бесконечный цикл*, то есть цикл, который может выполнять большое или даже бесконечное число раз.</span><span class="sxs-lookup"><span data-stu-id="f2835-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="f2835-145">`Exit Do`Для экранирования цикла можно использовать.</span><span class="sxs-lookup"><span data-stu-id="f2835-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="f2835-146">В можно включить любое количество `Exit Do` операторов в любом месте `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="f2835-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="f2835-147">При использовании внутри вложенных `Do` циклов `Exit Do` передает управление за пределы самого внутреннего цикла и в следующий более высокий уровень вложенности.</span><span class="sxs-lookup"><span data-stu-id="f2835-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2835-148">Пример</span><span class="sxs-lookup"><span data-stu-id="f2835-148">Example</span></span>  
 <span data-ttu-id="f2835-149">В следующем примере операторы в цикле продолжают выполняться до тех пор, пока `index` переменная не будет больше 10.</span><span class="sxs-lookup"><span data-stu-id="f2835-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="f2835-150">`Until`Предложение находится в конце цикла.</span><span class="sxs-lookup"><span data-stu-id="f2835-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="f2835-151">Пример</span><span class="sxs-lookup"><span data-stu-id="f2835-151">Example</span></span>  
 <span data-ttu-id="f2835-152">В следующем примере `While` вместо предложения используется предложение, которое `Until` `condition` проверяется в начале цикла, а не в конце.</span><span class="sxs-lookup"><span data-stu-id="f2835-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="f2835-153">Пример</span><span class="sxs-lookup"><span data-stu-id="f2835-153">Example</span></span>  
 <span data-ttu-id="f2835-154">В следующем примере `condition` останавливается цикл, если `index` переменная больше 100.</span><span class="sxs-lookup"><span data-stu-id="f2835-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="f2835-155">`If`Однако инструкция в цикле приводит к `Exit Do` остановке цикла, если переменная индекса больше 10.</span><span class="sxs-lookup"><span data-stu-id="f2835-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="f2835-156">Пример</span><span class="sxs-lookup"><span data-stu-id="f2835-156">Example</span></span>  
 <span data-ttu-id="f2835-157">В следующем примере считываются все строки в текстовом файле.</span><span class="sxs-lookup"><span data-stu-id="f2835-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="f2835-158"><xref:System.IO.File.OpenText%2A>Метод открывает файл и возвращает объект <xref:System.IO.StreamReader> , считывающий символы.</span><span class="sxs-lookup"><span data-stu-id="f2835-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="f2835-159">В `Do...Loop` условии <xref:System.IO.StreamReader.Peek%2A> метод `StreamReader` определяет наличие дополнительных символов.</span><span class="sxs-lookup"><span data-stu-id="f2835-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="f2835-160">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f2835-160">See also</span></span>

- [<span data-ttu-id="f2835-161">Циклические структуры</span><span class="sxs-lookup"><span data-stu-id="f2835-161">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="f2835-162">Оператор For…Next</span><span class="sxs-lookup"><span data-stu-id="f2835-162">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="f2835-163">Логический тип данных</span><span class="sxs-lookup"><span data-stu-id="f2835-163">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="f2835-164">Вложенные структуры управления</span><span class="sxs-lookup"><span data-stu-id="f2835-164">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="f2835-165">Оператор Exit</span><span class="sxs-lookup"><span data-stu-id="f2835-165">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="f2835-166">Оператор While…End While</span><span class="sxs-lookup"><span data-stu-id="f2835-166">While...End While Statement</span></span>](while-end-while-statement.md)
