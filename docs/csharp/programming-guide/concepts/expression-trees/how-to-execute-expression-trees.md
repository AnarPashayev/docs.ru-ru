---
title: Практическое руководство. Выполнение деревьев выражений (C#)
description: Узнайте, как выполнить дерево выражения, чтобы вернуть значение или выполнить действие, например вызов метода.
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 19c3e639d64a44d180c75964261569dc0d6c2d89
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91154019"
---
# <a name="how-to-execute-expression-trees-c"></a>Практическое руководство. Выполнение деревьев выражений (C#)

В этом разделе показано, как выполнить дерево выражения. В результате выполнения дерева выражения может возвращаться значение или просто выполняться действие, такое как вызов метода.  
  
 Можно выполнять только деревья выражений, представляющие лямбда-выражения. Деревья выражений, представляющие лямбда-выражения, имеют тип <xref:System.Linq.Expressions.LambdaExpression> или <xref:System.Linq.Expressions.Expression%601>. Для выполнения таких деревьев выражений вызовите метод <xref:System.Linq.Expressions.LambdaExpression.Compile%2A>, чтобы создать исполняемый делегат, а затем вызовите делегат.  
  
> [!NOTE]
> Если тип делегата неизвестен, то есть лямбда-выражение имеет тип <xref:System.Linq.Expressions.LambdaExpression>, а не тип <xref:System.Linq.Expressions.Expression%601>, необходимо вызвать метод <xref:System.Delegate.DynamicInvoke%2A> для делегата, а не напрямую.  
  
 Если дерево выражения не представляет лямбда-выражение, можно создать новое лямбда-выражение, в качестве тела которого будет использоваться исходное дерево выражения. Для этого следует вызвать метод <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>. Затем можно выполнить лямбда-выражение, как описано ранее в этом разделе.  
  
## <a name="example"></a>Пример  

 В приведенном ниже примере кода показано, как путем создания и выполнения лямбда-выражения выполнить дерево выражения, которое представляет возведение числа в степень. Выводится результат, представляющий число, возведенное в степень.  
  
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
  
## <a name="compiling-the-code"></a>Компиляция кода  
  
- Включите пространство имен System.Linq.Expressions.  
  
## <a name="see-also"></a>См. также

- [Деревья выражений (C#)](./index.md)
- [Изменение деревьев выражений (C#)](./how-to-modify-expression-trees.md)
