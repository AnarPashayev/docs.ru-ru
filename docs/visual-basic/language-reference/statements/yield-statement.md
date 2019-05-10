---
title: Оператор Yield (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 645b8c4908095bc8d38c47836658325c9b47a569
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615067"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="85b29-102">Оператор Yield (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85b29-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="85b29-103">Отправляет следующий элемент коллекции `For Each...Next` инструкции.</span><span class="sxs-lookup"><span data-stu-id="85b29-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85b29-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85b29-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="85b29-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="85b29-105">Parameters</span></span>  
  
|<span data-ttu-id="85b29-106">Термин</span><span class="sxs-lookup"><span data-stu-id="85b29-106">Term</span></span>|<span data-ttu-id="85b29-107">Определение</span><span class="sxs-lookup"><span data-stu-id="85b29-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="85b29-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="85b29-108">Required.</span></span> <span data-ttu-id="85b29-109">Выражение, которое может быть неявно преобразован в тип функции итератора или `Get` метод доступа, который содержит `Yield` инструкции.</span><span class="sxs-lookup"><span data-stu-id="85b29-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85b29-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="85b29-110">Remarks</span></span>  
 <span data-ttu-id="85b29-111">`Yield` Инструкция возвращает один элемент из коллекции за раз.</span><span class="sxs-lookup"><span data-stu-id="85b29-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="85b29-112">`Yield` Включаются инструкции в функции итератора или `Get` доступа, который выполнять пользовательские итерации по коллекции.</span><span class="sxs-lookup"><span data-stu-id="85b29-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="85b29-113">Использование функции итератора с помощью [для каждого... Следующий оператор](../../../visual-basic/language-reference/statements/for-each-next-statement.md) или запрос LINQ.</span><span class="sxs-lookup"><span data-stu-id="85b29-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="85b29-114">Каждая итерация `For Each` цикл вызывает функции итератора.</span><span class="sxs-lookup"><span data-stu-id="85b29-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="85b29-115">Когда `Yield` достижения оператора в функции итератора, `expression` возвращается, при этом сохраняется текущее расположение в коде.</span><span class="sxs-lookup"><span data-stu-id="85b29-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="85b29-116">При следующем вызове функции итератора выполнение возобновляется с этого места.</span><span class="sxs-lookup"><span data-stu-id="85b29-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="85b29-117">Должно существовать неявное преобразование из типа `expression` в `Yield` инструкцию, чтобы тип возвращаемого значения итератора.</span><span class="sxs-lookup"><span data-stu-id="85b29-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="85b29-118">Можно использовать `Exit Function` или `Return` инструкции для завершения итерации.</span><span class="sxs-lookup"><span data-stu-id="85b29-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="85b29-119">«Yield» не является зарезервированным словом и имеет специальное значение только в том случае, если он используется в `Iterator` функции или `Get` метода доступа.</span><span class="sxs-lookup"><span data-stu-id="85b29-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="85b29-120">Дополнительные сведения о функции итераторов и `Get` методы доступа, см. в разделе [итераторы](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="85b29-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="85b29-121">Функции итератора и методы доступа Get</span><span class="sxs-lookup"><span data-stu-id="85b29-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="85b29-122">Объявление функции итератора или `Get` метод доступа должен соответствовать следующим требованиям:</span><span class="sxs-lookup"><span data-stu-id="85b29-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="85b29-123">Она должна включать [итератор](../../../visual-basic/language-reference/modifiers/iterator.md) модификатор.</span><span class="sxs-lookup"><span data-stu-id="85b29-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="85b29-124">Возвращаемый тип должен быть <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> или <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="85b29-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="85b29-125">Он не может содержать `ByRef` параметров.</span><span class="sxs-lookup"><span data-stu-id="85b29-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="85b29-126">Функцию итератор не может содержаться события, конструкторе экземпляра, статическом конструкторе или статическом деструкторе.</span><span class="sxs-lookup"><span data-stu-id="85b29-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="85b29-127">Функции итератора может быть анонимной функции.</span><span class="sxs-lookup"><span data-stu-id="85b29-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="85b29-128">Дополнительные сведения см. в разделе [Итераторы](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="85b29-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="85b29-129">Обработка исключений</span><span class="sxs-lookup"><span data-stu-id="85b29-129">Exception Handling</span></span>  
 <span data-ttu-id="85b29-130">Объект `Yield` инструкцию можно внутри `Try` блока [попробуйте... CATCH... Оператор Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="85b29-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="85b29-131">Объект `Try` блок, который имеет `Yield` инструкция может иметь `Catch` блокируется и может иметь `Finally` блока.</span><span class="sxs-lookup"><span data-stu-id="85b29-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="85b29-132">Объект `Yield` оператор не может находиться внутри `Catch` блока или `Finally` блока.</span><span class="sxs-lookup"><span data-stu-id="85b29-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="85b29-133">Если `For Each` текст (за пределами функции итератора) вызывает исключение, `Catch` блок в функции итератора не выполняется, но `Finally` выполняется блок в функции итератора.</span><span class="sxs-lookup"><span data-stu-id="85b29-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="85b29-134">Объект `Catch` блока внутри функции итератора перехватываются только исключения, возникшие внутри функции итератора.</span><span class="sxs-lookup"><span data-stu-id="85b29-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="85b29-135">Техническая реализация</span><span class="sxs-lookup"><span data-stu-id="85b29-135">Technical Implementation</span></span>  
 <span data-ttu-id="85b29-136">В следующем коде возвращает `IEnumerable (Of String)` из функции итератора и перебирает элементы `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="85b29-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="85b29-137">Вызов `MyIteratorFunction` не выполняет тело функции.</span><span class="sxs-lookup"><span data-stu-id="85b29-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="85b29-138">Вместо этого вызов возвращает `IEnumerable(Of String)` в переменную `elements`.</span><span class="sxs-lookup"><span data-stu-id="85b29-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="85b29-139">В итерации цикла `For Each` метод <xref:System.Collections.IEnumerator.MoveNext%2A> вызывается для `elements`.</span><span class="sxs-lookup"><span data-stu-id="85b29-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="85b29-140">Этот вызов выполняет тело `MyIteratorFunction` до достижения следующего оператора `Yield`.</span><span class="sxs-lookup"><span data-stu-id="85b29-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="85b29-141">`Yield` Инструкция возвращает выражение, которое определяет не только значение `element` переменной для использования телом цикла, но также <xref:System.Collections.Generic.IEnumerator%601.Current%2A> свойства элементов, которое является `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="85b29-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="85b29-142">В каждой последующей итерации цикла `For Each` выполнение тела итератора продолжается с места остановки и при достижении оператора `Yield` оно снова останавливается.</span><span class="sxs-lookup"><span data-stu-id="85b29-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="85b29-143">`For Each` Цикл завершается, когда в конец функции итератора или `Return` или `Exit Function` оператору.</span><span class="sxs-lookup"><span data-stu-id="85b29-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85b29-144">Пример</span><span class="sxs-lookup"><span data-stu-id="85b29-144">Example</span></span>  
 <span data-ttu-id="85b29-145">В следующем примере имеется `Yield` инструкцию, которая находится внутри [для... Далее](../../../visual-basic/language-reference/statements/for-next-statement.md) цикла.</span><span class="sxs-lookup"><span data-stu-id="85b29-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="85b29-146">Каждая итерация [для каждого](../../../visual-basic/language-reference/statements/for-each-next-statement.md) тела оператора в `Main` создает вызов `Power` функции итератора.</span><span class="sxs-lookup"><span data-stu-id="85b29-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="85b29-147">При каждом вызове функции итератора происходит переход к следующему выполнению оператора `Yield`, которое осуществляется во время следующей итерации цикла `For…Next`.</span><span class="sxs-lookup"><span data-stu-id="85b29-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="85b29-148">Тип возвращаемого значения метода итератора — <xref:System.Collections.Generic.IEnumerable%601>, является типом интерфейса итератора.</span><span class="sxs-lookup"><span data-stu-id="85b29-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="85b29-149">При вызове метода итератора возвращается перечисляемый объект, содержащий степени числа.</span><span class="sxs-lookup"><span data-stu-id="85b29-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="85b29-150">Пример</span><span class="sxs-lookup"><span data-stu-id="85b29-150">Example</span></span>  
 <span data-ttu-id="85b29-151">В следующем примере демонстрируется метод доступа `Get`, представляющий собой итератор.</span><span class="sxs-lookup"><span data-stu-id="85b29-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="85b29-152">Объявление свойства содержит `Iterator` модификатор.</span><span class="sxs-lookup"><span data-stu-id="85b29-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="85b29-153">Дополнительные примеры см. в разделе [итераторы](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="85b29-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b29-154">См. также</span><span class="sxs-lookup"><span data-stu-id="85b29-154">See also</span></span>

- [<span data-ttu-id="85b29-155">Операторы</span><span class="sxs-lookup"><span data-stu-id="85b29-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
