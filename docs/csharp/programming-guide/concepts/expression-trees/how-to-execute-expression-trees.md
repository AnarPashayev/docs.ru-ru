---
title: Практическое руководство. Выполнение деревьев выражений (C#)
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 4a73201d06d21964a40fbbe57fa952da35c5942c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924362"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="344d6-102">Практическое руководство. Выполнение деревьев выражений (C#)</span><span class="sxs-lookup"><span data-stu-id="344d6-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="344d6-103">В этом разделе показано, как выполнить дерево выражения.</span><span class="sxs-lookup"><span data-stu-id="344d6-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="344d6-104">В результате выполнения дерева выражения может возвращаться значение или просто выполняться действие, такое как вызов метода.</span><span class="sxs-lookup"><span data-stu-id="344d6-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="344d6-105">Можно выполнять только деревья выражений, представляющие лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="344d6-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="344d6-106">Деревья выражений, представляющие лямбда-выражения, имеют тип <xref:System.Linq.Expressions.LambdaExpression> или <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="344d6-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="344d6-107">Для выполнения таких деревьев выражений вызовите метод <xref:System.Linq.Expressions.LambdaExpression.Compile%2A>, чтобы создать исполняемый делегат, а затем вызовите делегат.</span><span class="sxs-lookup"><span data-stu-id="344d6-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="344d6-108">Если тип делегата неизвестен, то есть лямбда-выражение имеет тип <xref:System.Linq.Expressions.LambdaExpression>, а не тип <xref:System.Linq.Expressions.Expression%601>, необходимо вызвать метод <xref:System.Delegate.DynamicInvoke%2A> для делегата, а не напрямую.</span><span class="sxs-lookup"><span data-stu-id="344d6-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="344d6-109">Если дерево выражения не представляет лямбда-выражение, можно создать новое лямбда-выражение, в качестве тела которого будет использоваться исходное дерево выражения. Для этого следует вызвать метод <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>.</span><span class="sxs-lookup"><span data-stu-id="344d6-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="344d6-110">Затем можно выполнить лямбда-выражение, как описано ранее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="344d6-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="344d6-111">Пример</span><span class="sxs-lookup"><span data-stu-id="344d6-111">Example</span></span>  
 <span data-ttu-id="344d6-112">В приведенном ниже примере кода показано, как путем создания и выполнения лямбда-выражения выполнить дерево выражения, которое представляет возведение числа в степень.</span><span class="sxs-lookup"><span data-stu-id="344d6-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="344d6-113">Выводится результат, представляющий число, возведенное в степень.</span><span class="sxs-lookup"><span data-stu-id="344d6-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="344d6-114">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="344d6-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="344d6-115">Включите пространство имен System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="344d6-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="344d6-116">См. также</span><span class="sxs-lookup"><span data-stu-id="344d6-116">See also</span></span>

- <span data-ttu-id="344d6-117">[Expression Trees (C#)](./index.md) (Деревья выражений (C#))</span><span class="sxs-lookup"><span data-stu-id="344d6-117">[Expression Trees (C#)](./index.md)</span></span>
- [<span data-ttu-id="344d6-118">Практическое руководство. Изменение деревьев выражений (C#)</span><span class="sxs-lookup"><span data-stu-id="344d6-118">How to: Modify Expression Trees (C#)</span></span>](./how-to-modify-expression-trees.md)
