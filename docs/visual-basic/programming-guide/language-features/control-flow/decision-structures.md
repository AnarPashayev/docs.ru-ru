---
title: Структуры решений
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 79c4949cd4d5b07d1b1d666b21467bf8db41ab3d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095620"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="8c48f-102">Структуры решений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c48f-102">Decision Structures (Visual Basic)</span></span>

<span data-ttu-id="8c48f-103">Visual Basic позволяет тестировать условия и выполнять различные операции в зависимости от результатов этого теста.</span><span class="sxs-lookup"><span data-stu-id="8c48f-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="8c48f-104">Можно проверить наличие условия, которое имеет значение true или false, для различных значений выражения или для различных исключений, создаваемых при выполнении последовательности инструкций.</span><span class="sxs-lookup"><span data-stu-id="8c48f-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="8c48f-105">На следующем рисунке показана структура принятия решений, которая проверяет истинность условия и принимает различные действия в зависимости от того, имеет ли оно значение true или false.</span><span class="sxs-lookup"><span data-stu-id="8c48f-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Блок-схема if... Затем... Else.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="8c48f-107">Если... Затем... Else, конструкция</span><span class="sxs-lookup"><span data-stu-id="8c48f-107">If...Then...Else Construction</span></span>  

 <span data-ttu-id="8c48f-108">`If...Then...Else` операторы позволяют проверить одно или несколько условий и выполнить одну или несколько инструкций в зависимости от каждого условия.</span><span class="sxs-lookup"><span data-stu-id="8c48f-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="8c48f-109">Проверить условия и выполнить действия можно следующими способами.</span><span class="sxs-lookup"><span data-stu-id="8c48f-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="8c48f-110">Выполнить одну или несколько инструкций, если условие `True`</span><span class="sxs-lookup"><span data-stu-id="8c48f-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="8c48f-111">Выполнить одну или несколько инструкций, если условие `False`</span><span class="sxs-lookup"><span data-stu-id="8c48f-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="8c48f-112">Запускать некоторые инструкции, если условие имеет значение `True` , а другие — `False`</span><span class="sxs-lookup"><span data-stu-id="8c48f-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="8c48f-113">Проверить дополнительное условие, если предыдущие условия `False`</span><span class="sxs-lookup"><span data-stu-id="8c48f-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="8c48f-114">Структура элемента управления, которая предоставляет все эти возможности, — это [If... Затем... Else, инструкция](../../../language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8c48f-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="8c48f-115">Можно использовать однострочную версию, если имеется только один тест и один оператор для выполнения.</span><span class="sxs-lookup"><span data-stu-id="8c48f-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="8c48f-116">При наличии более сложного набора условий и действий можно использовать версию из нескольких строк.</span><span class="sxs-lookup"><span data-stu-id="8c48f-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="8c48f-117">Выберите... Конструкция CASE</span><span class="sxs-lookup"><span data-stu-id="8c48f-117">Select...Case Construction</span></span>  

 <span data-ttu-id="8c48f-118">`Select...Case`Конструкция позволяет оценивать выражение один раз и выполнять разные наборы инструкций на основе различных возможных значений.</span><span class="sxs-lookup"><span data-stu-id="8c48f-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="8c48f-119">Дополнительные сведения см. в разделе [SELECT... Case, инструкция](../../../language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8c48f-119">For more information, see [Select...Case Statement](../../../language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="8c48f-120">Попробуйте... Перехватить... Finally, создание</span><span class="sxs-lookup"><span data-stu-id="8c48f-120">Try...Catch...Finally Construction</span></span>  

 <span data-ttu-id="8c48f-121">`Try...Catch...Finally` операторы позволяют запускать набор инструкций в среде, сохраняющей управление, если какая-либо из инструкций вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="8c48f-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="8c48f-122">Для разных исключений можно выполнять различные действия.</span><span class="sxs-lookup"><span data-stu-id="8c48f-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="8c48f-123">При необходимости можно указать блок кода, который будет выполняться перед выходом из всей `Try...Catch...Finally` конструкции, независимо от того, что происходит.</span><span class="sxs-lookup"><span data-stu-id="8c48f-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="8c48f-124">Дополнительные сведения см. в разделе [Оператор Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8c48f-124">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c48f-125">Для многих структур управления при щелчке ключевого слова все ключевые слова в структуре выделяются.</span><span class="sxs-lookup"><span data-stu-id="8c48f-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="8c48f-126">Например, если щелкнуть `If` `If...Then...Else` конструкцию, `If` будут выделены все экземпляры,,, `Then` `ElseIf` `Else` и `End If` в конструкции.</span><span class="sxs-lookup"><span data-stu-id="8c48f-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="8c48f-127">Чтобы перейти к следующему или предыдущему выделенному ключевому слову, нажмите клавиши CTRL + SHIFT + стрелка вниз или CTRL + SHIFT + стрелка вверх.</span><span class="sxs-lookup"><span data-stu-id="8c48f-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c48f-128">См. также</span><span class="sxs-lookup"><span data-stu-id="8c48f-128">See also</span></span>

- [<span data-ttu-id="8c48f-129">Поток управления</span><span class="sxs-lookup"><span data-stu-id="8c48f-129">Control Flow</span></span>](index.md)
- [<span data-ttu-id="8c48f-130">Циклические структуры</span><span class="sxs-lookup"><span data-stu-id="8c48f-130">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="8c48f-131">Другие структуры управления</span><span class="sxs-lookup"><span data-stu-id="8c48f-131">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="8c48f-132">Вложенные структуры управления</span><span class="sxs-lookup"><span data-stu-id="8c48f-132">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="8c48f-133">Оператор If</span><span class="sxs-lookup"><span data-stu-id="8c48f-133">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
