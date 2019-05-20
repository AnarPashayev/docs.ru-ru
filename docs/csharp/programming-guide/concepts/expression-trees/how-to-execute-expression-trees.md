---
title: Практическое руководство. Выполнение деревьев выражений (C#)
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: acf841194ef0990d2eb00481454c89088f4616c8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586139"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="ffb12-102">Практическое руководство. Выполнение деревьев выражений (C#)</span><span class="sxs-lookup"><span data-stu-id="ffb12-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="ffb12-103">В этом разделе показано, как выполнить дерево выражения.</span><span class="sxs-lookup"><span data-stu-id="ffb12-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="ffb12-104">В результате выполнения дерева выражения может возвращаться значение или просто выполняться действие, такое как вызов метода.</span><span class="sxs-lookup"><span data-stu-id="ffb12-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="ffb12-105">Можно выполнять только деревья выражений, представляющие лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="ffb12-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="ffb12-106">Деревья выражений, представляющие лямбда-выражения, имеют тип <xref:System.Linq.Expressions.LambdaExpression> или <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="ffb12-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="ffb12-107">Для выполнения таких деревьев выражений вызовите метод <xref:System.Linq.Expressions.LambdaExpression.Compile%2A>, чтобы создать исполняемый делегат, а затем вызовите делегат.</span><span class="sxs-lookup"><span data-stu-id="ffb12-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffb12-108">Если тип делегата неизвестен, то есть лямбда-выражение имеет тип <xref:System.Linq.Expressions.LambdaExpression>, а не тип <xref:System.Linq.Expressions.Expression%601>, необходимо вызвать метод <xref:System.Delegate.DynamicInvoke%2A> для делегата, а не напрямую.</span><span class="sxs-lookup"><span data-stu-id="ffb12-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="ffb12-109">Если дерево выражения не представляет лямбда-выражение, можно создать новое лямбда-выражение, в качестве тела которого будет использоваться исходное дерево выражения. Для этого следует вызвать метод <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>.</span><span class="sxs-lookup"><span data-stu-id="ffb12-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="ffb12-110">Затем можно выполнить лямбда-выражение, как описано ранее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="ffb12-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffb12-111">Пример</span><span class="sxs-lookup"><span data-stu-id="ffb12-111">Example</span></span>  
 <span data-ttu-id="ffb12-112">В приведенном ниже примере кода показано, как путем создания и выполнения лямбда-выражения выполнить дерево выражения, которое представляет возведение числа в степень.</span><span class="sxs-lookup"><span data-stu-id="ffb12-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="ffb12-113">Выводится результат, представляющий число, возведенное в степень.</span><span class="sxs-lookup"><span data-stu-id="ffb12-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ffb12-114">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="ffb12-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="ffb12-115">Включите пространство имен System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="ffb12-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffb12-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ffb12-116">See also</span></span>

- <span data-ttu-id="ffb12-117">[Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) (Деревья выражений (C#))</span><span class="sxs-lookup"><span data-stu-id="ffb12-117">[Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)</span></span>
- [<span data-ttu-id="ffb12-118">Практическое руководство. Изменение деревьев выражений (C#)</span><span class="sxs-lookup"><span data-stu-id="ffb12-118">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
