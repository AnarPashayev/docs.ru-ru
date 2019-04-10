---
title: Практическое руководство. Создание процедуры (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 56099d334a03e85b816cf48983cbbead0784ef5b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320396"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="fb876-102">Практическое руководство. Создание процедуры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb876-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="fb876-103">Заключите процедуру между начальной оператор объявления (`Sub` или `Function`) и окончания оператор объявления (`End Sub` или `End Function`).</span><span class="sxs-lookup"><span data-stu-id="fb876-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="fb876-104">Код процедуры находится в диапазоне от этих инструкций.</span><span class="sxs-lookup"><span data-stu-id="fb876-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="fb876-105">Процедура не может содержать другую процедуру, поэтому его начала и конца инструкции должны быть вне любых других процедур.</span><span class="sxs-lookup"><span data-stu-id="fb876-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="fb876-106">Если у вас есть код, который выполняет ту же задачу в разных местах, можно написать задачу один раз как процедуру и затем вызывать из различных мест в коде.</span><span class="sxs-lookup"><span data-stu-id="fb876-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="fb876-107">Чтобы создать процедуру, которая не возвращает значение</span><span class="sxs-lookup"><span data-stu-id="fb876-107">To create a procedure that does not return a value</span></span>  
  
1. <span data-ttu-id="fb876-108">Вне любых других процедур используйте `Sub` , применив инструкцию `End Sub` инструкции.</span><span class="sxs-lookup"><span data-stu-id="fb876-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="fb876-109">В `Sub` инструкции, следуйте `Sub` ключевое слово с именем процедуры, затем список параметров в круглых скобках.</span><span class="sxs-lookup"><span data-stu-id="fb876-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="fb876-110">Поместите операторы кода процедуры между `Sub` и `End Sub` инструкций.</span><span class="sxs-lookup"><span data-stu-id="fb876-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="fb876-111">Создание процедуры, возвращающей значение</span><span class="sxs-lookup"><span data-stu-id="fb876-111">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="fb876-112">Вне любых других процедур используйте `Function` , применив инструкцию `End Function` инструкции.</span><span class="sxs-lookup"><span data-stu-id="fb876-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="fb876-113">В `Function` инструкции, следуйте `Function` ключевое слово с именем процедуры, затем список параметров в скобки, а затем `As` предложение, указывающие тип данных возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="fb876-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3. <span data-ttu-id="fb876-114">Поместите операторы кода процедуры между `Function` и `End Function` инструкций.</span><span class="sxs-lookup"><span data-stu-id="fb876-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4. <span data-ttu-id="fb876-115">Используйте `Return` инструкция возвращает значение вызывающему коду.</span><span class="sxs-lookup"><span data-stu-id="fb876-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="fb876-116">Для подключения новой процедуры с помощью старого, повторяющихся блоков кода</span><span class="sxs-lookup"><span data-stu-id="fb876-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1. <span data-ttu-id="fb876-117">Убедитесь, что определение новой процедуры в том месте, где старый код имеет доступ к нему.</span><span class="sxs-lookup"><span data-stu-id="fb876-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2. <span data-ttu-id="fb876-118">В блок кода старые, повторяющихся, замените операторы, которые выполняют повторяющихся задач с помощью одного оператора, который вызывает `Sub` или `Function` процедуры.</span><span class="sxs-lookup"><span data-stu-id="fb876-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3. <span data-ttu-id="fb876-119">Если процедура является `Function` , возвращает значение, убедитесь, что вызывающий оператор выполняет действие с возвращаемым значением, например сохраняет его в переменной, в противном случае значение будет потеряно.</span><span class="sxs-lookup"><span data-stu-id="fb876-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb876-120">Пример</span><span class="sxs-lookup"><span data-stu-id="fb876-120">Example</span></span>  
 <span data-ttu-id="fb876-121">Следующие `Function` процедура вычисляет самая длинная сторона гипотенузы прямоугольного треугольника, значения для двух других сторон.</span><span class="sxs-lookup"><span data-stu-id="fb876-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fb876-122">См. также</span><span class="sxs-lookup"><span data-stu-id="fb876-122">See also</span></span>

- [<span data-ttu-id="fb876-123">Процедуры</span><span class="sxs-lookup"><span data-stu-id="fb876-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="fb876-124">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="fb876-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="fb876-125">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="fb876-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="fb876-126">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="fb876-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="fb876-127">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="fb876-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="fb876-128">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="fb876-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="fb876-129">Рекурсивные процедуры</span><span class="sxs-lookup"><span data-stu-id="fb876-129">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="fb876-130">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="fb876-130">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="fb876-131">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="fb876-131">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="fb876-132">Объектно ориентированного программирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb876-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
