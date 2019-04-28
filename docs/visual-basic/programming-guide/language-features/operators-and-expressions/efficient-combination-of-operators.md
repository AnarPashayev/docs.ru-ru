---
title: Эффективное сочетание операторов (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8f5dd6c56b3e4576b9d798e0e5e10b2996f558dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864658"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="792ba-102">Эффективное сочетание операторов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="792ba-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="792ba-103">Сложные выражения могут содержать большое количество различных операторов.</span><span class="sxs-lookup"><span data-stu-id="792ba-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="792ba-104">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="792ba-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="792ba-105">Создание сложных выражений, подобное показанному в предыдущем примере требует глубокого понимания правил приоритета операторов.</span><span class="sxs-lookup"><span data-stu-id="792ba-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="792ba-106">Дополнительные сведения см. в разделе [порядок применения операторов в Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="792ba-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="792ba-107">Выражения в скобках</span><span class="sxs-lookup"><span data-stu-id="792ba-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="792ba-108">Часто возникает необходимость выполнения операций в порядке, отличающемся от определенного приоритетом операторов.</span><span class="sxs-lookup"><span data-stu-id="792ba-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="792ba-109">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="792ba-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="792ba-110">Предыдущий пример умножает `z` по `y`, затем результат прибавляется к `4`.</span><span class="sxs-lookup"><span data-stu-id="792ba-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="792ba-111">Но если вы хотите добавить `y` и `4` перед умножением на `z`, обычный порядок применения операторов можно переопределить с помощью скобок.</span><span class="sxs-lookup"><span data-stu-id="792ba-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="792ba-112">Выражение заключено в круглые скобки, принудительно это выражение, вычисляемое во-первых, вне зависимости от приоритета операторов.</span><span class="sxs-lookup"><span data-stu-id="792ba-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="792ba-113">Чтобы принудительно в предыдущем примере сначала выполнить сложение, нужно переписать его как в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="792ba-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="792ba-114">В предыдущем примере добавляется `y` и `4`, затем сумма умножается на `z`.</span><span class="sxs-lookup"><span data-stu-id="792ba-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="792ba-115">Вложенные выражения в скобках</span><span class="sxs-lookup"><span data-stu-id="792ba-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="792ba-116">Можно осуществлять вложение выражений в нескольких уровней круглых скобок для дальнейшего переопределения приоритетов.</span><span class="sxs-lookup"><span data-stu-id="792ba-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="792ba-117">Самую глубокую вложенную в скобках вычисляются во-первых, следуют следующей самую глубокую вложенную, и т. д бы глубоко вложенных и наконец выражения за пределами скобок.</span><span class="sxs-lookup"><span data-stu-id="792ba-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="792ba-118">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="792ba-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="792ba-119">В приведенном выше примере `z + 2` сначала вычисляется, то другие выражения в скобках.</span><span class="sxs-lookup"><span data-stu-id="792ba-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="792ba-120">Возведение в степень, который обычно имеет более высокий приоритет, чем сложение или умножение, вычисляется последним в этом примере, поскольку другие выражения заключены в круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="792ba-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792ba-121">См. также</span><span class="sxs-lookup"><span data-stu-id="792ba-121">See also</span></span>

- [<span data-ttu-id="792ba-122">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="792ba-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="792ba-123">Операторы сравнения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="792ba-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="792ba-124">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="792ba-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="792ba-125">Логические (побитовые) операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="792ba-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="792ba-126">Логические выражения</span><span class="sxs-lookup"><span data-stu-id="792ba-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="792ba-127">Сравнения значений</span><span class="sxs-lookup"><span data-stu-id="792ba-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="792ba-128">Практическое руководство. Вычисление числовых значений</span><span class="sxs-lookup"><span data-stu-id="792ba-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="792ba-129">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="792ba-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
