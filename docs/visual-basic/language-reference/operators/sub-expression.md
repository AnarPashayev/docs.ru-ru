---
title: Часть выражения (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 2330b410f54b54d8f6cb7d8ad6f9b39a3f4d31bc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701339"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="5b224-102">Часть выражения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b224-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="5b224-103">Объявляет параметры и код, определяющие лямбда-выражение подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="5b224-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b224-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5b224-104">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="5b224-105">Части</span><span class="sxs-lookup"><span data-stu-id="5b224-105">Parts</span></span>  
  
|<span data-ttu-id="5b224-106">Термин</span><span class="sxs-lookup"><span data-stu-id="5b224-106">Term</span></span>|<span data-ttu-id="5b224-107">Определение</span><span class="sxs-lookup"><span data-stu-id="5b224-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="5b224-108">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="5b224-108">Optional.</span></span> <span data-ttu-id="5b224-109">Список имен локальных переменных, представляющих параметры процедуры.</span><span class="sxs-lookup"><span data-stu-id="5b224-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="5b224-110">Круглые скобки должны присутствовать, даже если список пуст.</span><span class="sxs-lookup"><span data-stu-id="5b224-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="5b224-111">Дополнительные сведения см. в разделе [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="5b224-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="5b224-112">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="5b224-112">Required.</span></span> <span data-ttu-id="5b224-113">Один оператор.</span><span class="sxs-lookup"><span data-stu-id="5b224-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="5b224-114">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="5b224-114">Required.</span></span> <span data-ttu-id="5b224-115">Список инструкций.</span><span class="sxs-lookup"><span data-stu-id="5b224-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b224-116">Примечания</span><span class="sxs-lookup"><span data-stu-id="5b224-116">Remarks</span></span>  
 <span data-ttu-id="5b224-117">*Лямбда-выражение* — это подпрограммы без имени и выполняющая одну или несколько инструкций.</span><span class="sxs-lookup"><span data-stu-id="5b224-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="5b224-118">Лямбда-выражение можно использовать в любом месте, где можно использовать тип делегата, за исключением того, что в качестве аргумента для `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="5b224-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="5b224-119">Дополнительные сведения о делегатах и использовании лямбда-выражений с делегатами см. в разделе [оператор Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) и [Преобразование неявного делегата](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="5b224-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="5b224-120">Синтаксис лямбда-выражений</span><span class="sxs-lookup"><span data-stu-id="5b224-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="5b224-121">Синтаксис лямбда-выражения напоминает стандартную подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="5b224-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="5b224-122">Ниже приведены различия.</span><span class="sxs-lookup"><span data-stu-id="5b224-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="5b224-123">Лямбда-выражение не имеет имени.</span><span class="sxs-lookup"><span data-stu-id="5b224-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="5b224-124">Лямбда-выражение не может иметь модификатор, например `Overloads` или `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="5b224-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="5b224-125">Тело однострочного лямбда-выражения должно быть оператором, а не выражением.</span><span class="sxs-lookup"><span data-stu-id="5b224-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="5b224-126">Тело может состоять из вызова подпроцедуры, но не вызова процедуры функции.</span><span class="sxs-lookup"><span data-stu-id="5b224-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="5b224-127">В лямбда-выражении либо все параметры должны иметь указанные типы данных, либо все параметры должны быть выведены.</span><span class="sxs-lookup"><span data-stu-id="5b224-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="5b224-128">Необязательные параметры и `ParamArray` не допускаются в лямбда-выражениях.</span><span class="sxs-lookup"><span data-stu-id="5b224-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="5b224-129">Универсальные параметры не допускаются в лямбда-выражениях.</span><span class="sxs-lookup"><span data-stu-id="5b224-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b224-130">Пример</span><span class="sxs-lookup"><span data-stu-id="5b224-130">Example</span></span>  
 <span data-ttu-id="5b224-131">Ниже приведен пример лямбда-выражения, записывающего значение в консоль.</span><span class="sxs-lookup"><span data-stu-id="5b224-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="5b224-132">В примере показан синтаксис однострочного и многострочного лямбда-выражения для подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="5b224-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="5b224-133">Дополнительные примеры см. в разделе [лямбда-выражения](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5b224-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="5b224-134">См. также</span><span class="sxs-lookup"><span data-stu-id="5b224-134">See also</span></span>

- [<span data-ttu-id="5b224-135">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="5b224-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="5b224-136">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="5b224-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="5b224-137">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="5b224-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="5b224-138">Операторы</span><span class="sxs-lookup"><span data-stu-id="5b224-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="5b224-139">Неявное преобразование делегата</span><span class="sxs-lookup"><span data-stu-id="5b224-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
