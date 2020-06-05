---
title: Оператор IsTrue
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: bc129d3a3aec76285d5ea8fb727fc72c3064c9cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370652"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="0045e-102">Оператор IsTrue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0045e-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="0045e-103">Определяет, является ли выражение `True` .</span><span class="sxs-lookup"><span data-stu-id="0045e-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="0045e-104">`IsTrue`В коде нельзя вызывать явным образом, но компилятор Visual Basic может использовать его для создания кода из `OrElse` предложений.</span><span class="sxs-lookup"><span data-stu-id="0045e-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="0045e-105">Если вы определяете класс или структуру, а затем используете переменную этого типа в `OrElse` предложении, необходимо определить `IsTrue` для этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="0045e-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="0045e-106">Компилятор рассматривает `IsTrue` операторы и `IsFalse` как *парную пару*.</span><span class="sxs-lookup"><span data-stu-id="0045e-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="0045e-107">Это означает, что при определении одного из них необходимо также определить другой.</span><span class="sxs-lookup"><span data-stu-id="0045e-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="0045e-108">Использование IsTrue компилятором</span><span class="sxs-lookup"><span data-stu-id="0045e-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="0045e-109">После определения класса или структуры можно использовать переменную этого типа в `For` `If` `Else If` операторе,, или `While` , или в `When` предложении.</span><span class="sxs-lookup"><span data-stu-id="0045e-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="0045e-110">В этом случае компилятору требуется оператор, который преобразует тип в `Boolean` значение, чтобы можно было проверить условие.</span><span class="sxs-lookup"><span data-stu-id="0045e-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="0045e-111">Он выполняет поиск подходящего оператора в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="0045e-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="0045e-112">Оператор расширяющего преобразования из класса или структуры в `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0045e-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="0045e-113">Оператор расширяющего преобразования из класса или структуры в `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="0045e-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="0045e-114">`IsTrue`Оператор для класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="0045e-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="0045e-115">Суженное преобразование в `Boolean?` , не охватывающее преобразование из `Boolean` в `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="0045e-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="0045e-116">Оператор сужения преобразования из класса или структуры в `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0045e-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="0045e-117">Если не было определено преобразование в `Boolean` `IsTrue` оператор или, компилятор сообщает об ошибке.</span><span class="sxs-lookup"><span data-stu-id="0045e-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0045e-118">`IsTrue`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, если его операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="0045e-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="0045e-119">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="0045e-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0045e-120">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0045e-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0045e-121">Пример</span><span class="sxs-lookup"><span data-stu-id="0045e-121">Example</span></span>  
 <span data-ttu-id="0045e-122">В следующем примере кода определяется структура структуры, включающей определения для `IsFalse` `IsTrue` операторов и.</span><span class="sxs-lookup"><span data-stu-id="0045e-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="0045e-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0045e-123">See also</span></span>

- [<span data-ttu-id="0045e-124">Оператор IsFalse</span><span class="sxs-lookup"><span data-stu-id="0045e-124">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="0045e-125">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="0045e-125">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="0045e-126">Оператор OrElse</span><span class="sxs-lookup"><span data-stu-id="0045e-126">OrElse Operator</span></span>](orelse-operator.md)
