---
title: Лямбда-выражения (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: c43739e098a91d54d300fa7074d1563da179c0e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665797"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="65da4-102">Лямбда-выражения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65da4-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="65da4-103">Объект *лямбда-выражение* является функцией или подпрограммой без имени, который может использоваться везде, где допустим делегат.</span><span class="sxs-lookup"><span data-stu-id="65da4-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="65da4-104">Лямбда-выражения могут быть функции или подпрограммы и может быть одной или нескольких линий.</span><span class="sxs-lookup"><span data-stu-id="65da4-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="65da4-105">Можно передавать значения из текущей области в лямбда-выражение.</span><span class="sxs-lookup"><span data-stu-id="65da4-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65da4-106">`RemoveHandler` Инструкция является исключением.</span><span class="sxs-lookup"><span data-stu-id="65da4-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="65da4-107">Невозможно передать лямбда-выражение в для параметра делегата `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="65da4-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="65da4-108">Лямбда-выражения можно создавать с помощью `Function` или `Sub` ключевое слово, точно так же, как стандартные функции или подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="65da4-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="65da4-109">Тем не менее лямбда-выражения включаются в инструкции.</span><span class="sxs-lookup"><span data-stu-id="65da4-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="65da4-110">Следующий пример является лямбда-выражения и увеличивает значение своего аргумента и возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="65da4-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="65da4-111">В этом примере синтаксис однострочные и многострочные лямбда-выражений для функции.</span><span class="sxs-lookup"><span data-stu-id="65da4-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 <span data-ttu-id="65da4-112">Следующий пример является лямбда-выражения и записывает значение в консоль.</span><span class="sxs-lookup"><span data-stu-id="65da4-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="65da4-113">В примере синтаксиса однострочные и многострочные лямбда-выражения для подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="65da4-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 <span data-ttu-id="65da4-114">Обратите внимание на то, что в предыдущих примерах лямбда-выражения относятся к имени переменной.</span><span class="sxs-lookup"><span data-stu-id="65da4-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="65da4-115">При ссылке на эту переменную, можно вызвать лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="65da4-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="65da4-116">Можно также объявить и вызвать лямбда-выражение, в то же время, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="65da4-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 <span data-ttu-id="65da4-117">Лямбда-выражения могут быть возвращены для параметра вызов функции (как показано в примере в [контекст](#context) разделе этой статьи), или передаваться в качестве аргумента параметр, принимающий тип делегата, как показано ниже Пример.</span><span class="sxs-lookup"><span data-stu-id="65da4-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="65da4-118">Синтаксис лямбда-выражений</span><span class="sxs-lookup"><span data-stu-id="65da4-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="65da4-119">Синтаксис лямбда-выражения похож стандартные функции или подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="65da4-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="65da4-120">Ниже приведены различия.</span><span class="sxs-lookup"><span data-stu-id="65da4-120">The differences are as follows:</span></span>  
  
- <span data-ttu-id="65da4-121">Лямбда-выражение не имеет имени.</span><span class="sxs-lookup"><span data-stu-id="65da4-121">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="65da4-122">Лямбда-выражения не может иметь модификаторы, такие как `Overloads` или `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="65da4-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="65da4-123">Не используйте однострочное лямбда-функции `As` предложение, чтобы указать тип возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="65da4-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="65da4-124">Вместо этого тип выводится из значения, тело лямбда-выражение, результатом которого является.</span><span class="sxs-lookup"><span data-stu-id="65da4-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="65da4-125">Например, если тело лямбда-выражения — `cust.City = "London"`, его возвращаемый тип — `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="65da4-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="65da4-126">В функциях многострочные лямбда-выражения, можно указать тип возвращаемого значения с помощью `As` предложения, или пропустите `As` предложение, чтобы вывести тип возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="65da4-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="65da4-127">Когда `As` предложение опущено для многострочного лямбда-функцию, тип возвращаемого значения определяется как главный тип из всех `Return` инструкций в многострочные лямбда-функции.</span><span class="sxs-lookup"><span data-stu-id="65da4-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="65da4-128">*Главным типом* — это уникальный тип, могут быть расширены все другие типы.</span><span class="sxs-lookup"><span data-stu-id="65da4-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="65da4-129">Если такой уникальный тип нельзя определить, главным типом является тип, до которого можно сузить все другие типы массива.</span><span class="sxs-lookup"><span data-stu-id="65da4-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="65da4-130">Если ни один из указанных уникальных типов нельзя определить, главным типом будет `Object`.</span><span class="sxs-lookup"><span data-stu-id="65da4-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="65da4-131">В этом случае если `Option Strict` присваивается `On`, возникает ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="65da4-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="65da4-132">Например, если выражения `Return` инструкция содержит значения типа `Integer`, `Long`, и `Double`, результирующий массив будет иметь тип `Double`.</span><span class="sxs-lookup"><span data-stu-id="65da4-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="65da4-133">Оба `Integer` и `Long` расширяющего преобразования к `Double` и только `Double`.</span><span class="sxs-lookup"><span data-stu-id="65da4-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="65da4-134">Поэтому `Double` является главным типом.</span><span class="sxs-lookup"><span data-stu-id="65da4-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="65da4-135">Для получения дополнительной информации см. [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="65da4-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
- <span data-ttu-id="65da4-136">Тело функции однострочный должно быть выражение, возвращающее значение, не являющийся оператором.</span><span class="sxs-lookup"><span data-stu-id="65da4-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="65da4-137">Существует не `Return` инструкции для однострочных функций.</span><span class="sxs-lookup"><span data-stu-id="65da4-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="65da4-138">Значение, возвращаемое функцией однострочный значение выражения в теле функции.</span><span class="sxs-lookup"><span data-stu-id="65da4-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
- <span data-ttu-id="65da4-139">Подпрограммы однострочный текст должен быть одинарная оператором.</span><span class="sxs-lookup"><span data-stu-id="65da4-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
- <span data-ttu-id="65da4-140">Не используйте однострочных функций и подпрограмм `End Function` или `End Sub` инструкции.</span><span class="sxs-lookup"><span data-stu-id="65da4-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="65da4-141">Можно указать тип данных параметра лямбда-выражения с помощью `As` ключевое слово или тип данных параметра может быть выведен.</span><span class="sxs-lookup"><span data-stu-id="65da4-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="65da4-142">Необходимо заранее указать все параметры, что необходимо определить типы данных или все.</span><span class="sxs-lookup"><span data-stu-id="65da4-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="65da4-143">`Optional` и `Paramarray` параметров не разрешены.</span><span class="sxs-lookup"><span data-stu-id="65da4-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
- <span data-ttu-id="65da4-144">Универсальные параметры не допускаются.</span><span class="sxs-lookup"><span data-stu-id="65da4-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="65da4-145">Асинхронные лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="65da4-145">Async Lambdas</span></span>  
 <span data-ttu-id="65da4-146">Можно легко создавать лямбда-выражения и операторы, включающие асинхронную обработку с помощью [Async](../../../../visual-basic/language-reference/modifiers/async.md) и [оператор Await](../../../../visual-basic/language-reference/operators/await-operator.md) ключевые слова.</span><span class="sxs-lookup"><span data-stu-id="65da4-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="65da4-147">Например, в следующем примере Windows Forms содержится обработчик событий, который вызывает асинхронный метод `ExampleMethodAsync`и ожидает его.</span><span class="sxs-lookup"><span data-stu-id="65da4-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="65da4-148">Можно добавить один и тот же обработчик событий с помощью асинхронного лямбда-выражения в [оператор AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="65da4-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="65da4-149">Чтобы добавить этот обработчик, поставьте модификатор `Async` перед списком параметров лямбда-выражения, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="65da4-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="65da4-150">Дополнительные сведения о том, как создать и использовать асинхронные методы, см. в разделе [асинхронное программирование с использованием Async и Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="65da4-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="context"></a> <span data-ttu-id="65da4-151">Контекст</span><span class="sxs-lookup"><span data-stu-id="65da4-151">Context</span></span>  
 <span data-ttu-id="65da4-152">Лямбда-выражение использует общий контекст с областью, в котором он определен.</span><span class="sxs-lookup"><span data-stu-id="65da4-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="65da4-153">Он имеет те же права доступа, что любой код, написанный в содержащей области.</span><span class="sxs-lookup"><span data-stu-id="65da4-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="65da4-154">Это включает доступ к переменным-членам, функции и подпрограммы, `Me`и параметры, так и локальные переменные в содержащей области.</span><span class="sxs-lookup"><span data-stu-id="65da4-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="65da4-155">Доступ к локальным переменным и параметрам в содержащей области можно расширить за время существования этой области.</span><span class="sxs-lookup"><span data-stu-id="65da4-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="65da4-156">До тех пор, пока делегат, ссылающийся на лямбда-выражение не доступен в сборку мусора, можно сохранить доступ к переменным в исходной среде.</span><span class="sxs-lookup"><span data-stu-id="65da4-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="65da4-157">В следующем примере переменной `target` является локальным для `makeTheGame`, метод, в котором лямбда-выражение `playTheGame` определен.</span><span class="sxs-lookup"><span data-stu-id="65da4-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="65da4-158">Обратите внимание, что возвращенный лямбда-выражения, назначенный `takeAGuess` в `Main`, по-прежнему имеет доступ к локальной переменной `target`.</span><span class="sxs-lookup"><span data-stu-id="65da4-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 <span data-ttu-id="65da4-159">В следующем примере показано широкий спектр прав доступа вложенных лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="65da4-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="65da4-160">При выполнении возвращаемого лямбда-выражения из `Main` как `aDel`, он обращается к следующим элементам:</span><span class="sxs-lookup"><span data-stu-id="65da4-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
- <span data-ttu-id="65da4-161">Поле класса, в котором он определен: `aField`</span><span class="sxs-lookup"><span data-stu-id="65da4-161">A field of the class in which it is defined: `aField`</span></span>  
  
- <span data-ttu-id="65da4-162">Свойство класса, в котором он определен: `aProp`</span><span class="sxs-lookup"><span data-stu-id="65da4-162">A property of the class in which it is defined: `aProp`</span></span>  
  
- <span data-ttu-id="65da4-163">Параметр метода `functionWithNestedLambda`, в котором она была определена: `level1`</span><span class="sxs-lookup"><span data-stu-id="65da4-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
- <span data-ttu-id="65da4-164">Локальная переменная `functionWithNestedLambda`: `localVar`</span><span class="sxs-lookup"><span data-stu-id="65da4-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
- <span data-ttu-id="65da4-165">Параметр лямбда-выражения, в который он вложен: `level2`</span><span class="sxs-lookup"><span data-stu-id="65da4-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="65da4-166">Преобразование в тип делегата</span><span class="sxs-lookup"><span data-stu-id="65da4-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="65da4-167">Лямбда-выражения могут быть неявно преобразованы совместимого типа делегата.</span><span class="sxs-lookup"><span data-stu-id="65da4-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="65da4-168">Сведения об общих требованиях для обеспечения совместимости, см. в разделе [неявное преобразование делегата](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="65da4-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="65da4-169">Например, в следующем примере кода показано лямбда-выражение, которое неявно преобразуется к `Func(Of Integer, Boolean)` или соответствующий сигнатуре делегата.</span><span class="sxs-lookup"><span data-stu-id="65da4-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 <span data-ttu-id="65da4-170">В следующем примере кода показано лямбда-выражение, которое неявно преобразуется к `Sub(Of Double, String, Double)` или соответствующий сигнатуре делегата.</span><span class="sxs-lookup"><span data-stu-id="65da4-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 <span data-ttu-id="65da4-171">Когда назначать делегатам лямбда-выражения или передавать их в качестве аргументов для процедуры, можно указать имена параметров, но опустить их типы, позволяя принимать типы из делегата.</span><span class="sxs-lookup"><span data-stu-id="65da4-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="65da4-172">Примеры</span><span class="sxs-lookup"><span data-stu-id="65da4-172">Examples</span></span>  
  
- <span data-ttu-id="65da4-173">В следующем примере определяется лямбда-выражение, возвращающее `True` Если присвоено значение, допускающее значение NULL аргумент и `False` имеет значение `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="65da4-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
- <span data-ttu-id="65da4-174">В следующем примере определяется лямбда-выражение, которое возвращает индекс последнего элемента в массиве.</span><span class="sxs-lookup"><span data-stu-id="65da4-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="65da4-175">См. также</span><span class="sxs-lookup"><span data-stu-id="65da4-175">See also</span></span>

- [<span data-ttu-id="65da4-176">Процедуры</span><span class="sxs-lookup"><span data-stu-id="65da4-176">Procedures</span></span>](./index.md)
- <span data-ttu-id="65da4-177">[Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65da4-177">[Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="65da4-178">Делегаты</span><span class="sxs-lookup"><span data-stu-id="65da4-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="65da4-179">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="65da4-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="65da4-180">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="65da4-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="65da4-181">Типы значений, допускающие значение NULL</span><span class="sxs-lookup"><span data-stu-id="65da4-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="65da4-182">Практическое руководство. Передача процедур другой процедуре в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65da4-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="65da4-183">Практическое руководство. Создать лямбда-выражение</span><span class="sxs-lookup"><span data-stu-id="65da4-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="65da4-184">Неявное преобразование делегата</span><span class="sxs-lookup"><span data-stu-id="65da4-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
