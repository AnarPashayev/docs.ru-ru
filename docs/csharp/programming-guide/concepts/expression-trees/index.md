---
title: Деревья выражений (C#)
description: Сведения о деревьях выражений. Узнайте, как компилировать и запускать код, представляемый этими структурами данных, в которых каждый узел является выражением.
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 04b5486b6d3c54f0dfd3914eacbda5cffe15890a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167643"
---
# <a name="expression-trees-c"></a><span data-ttu-id="a3add-104">Деревья выражений (C#)</span><span class="sxs-lookup"><span data-stu-id="a3add-104">Expression Trees (C#)</span></span>

<span data-ttu-id="a3add-105">Деревья выражений представляют код в виде древовидной структуры, где каждый узел является выражением, например, вызовом метода или двоичной операцией, такой как `x < y`.</span><span class="sxs-lookup"><span data-stu-id="a3add-105">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="a3add-106">Вы можете компилировать и выполнять код, представленный деревьями выражений.</span><span class="sxs-lookup"><span data-stu-id="a3add-106">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="a3add-107">Это позволяет динамически изменять выполняемый код, выполнять запросы LINQ в различных базах данных и создавать динамические запросы.</span><span class="sxs-lookup"><span data-stu-id="a3add-107">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="a3add-108">См. дополнительные сведения об [использовании деревьев выражений в LINQ для создания динамических запросов (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="a3add-108">For more information about expression trees in LINQ, see [How to use expression trees to build dynamic queries (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>
  
 <span data-ttu-id="a3add-109">Кроме того, деревья выражений используются в среде выполнения динамического языка (DLR) для обеспечения взаимодействия между динамическими языками и платформой .NET, а также предоставления разработчикам компиляторов возможности выдавать деревья выражений вместо промежуточного языка MSIL.</span><span class="sxs-lookup"><span data-stu-id="a3add-109">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and .NET and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="a3add-110">Дополнительные сведения о DLR см. в разделе [Общие сведения о среде DLR](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a3add-110">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="a3add-111">Вы можете использовать компилятор C# или Visual Basic для создания дерева выражений на основе анонимного лямбда-выражения или создания деревьев выражений вручную с помощью пространства имен <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="a3add-111">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="a3add-112">Создание деревьев выражений на основе лямбда-выражений</span><span class="sxs-lookup"><span data-stu-id="a3add-112">Creating Expression Trees from Lambda Expressions</span></span>  

 <span data-ttu-id="a3add-113">Когда лямбда-выражение назначается переменной с типом <xref:System.Linq.Expressions.Expression%601>, компилятор выдает код для создания дерева выражений, представляющего лямбда-выражение.</span><span class="sxs-lookup"><span data-stu-id="a3add-113">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="a3add-114">Компилятор C# может создавать деревья выражений только на основе лямбда-выражений (или однострочных лямбда-функций).</span><span class="sxs-lookup"><span data-stu-id="a3add-114">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="a3add-115">Они не могут анализировать лямбды операторов (или многострочные лямбды).</span><span class="sxs-lookup"><span data-stu-id="a3add-115">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="a3add-116">Дополнительные сведения о лямбда-выражениях на C# см. в разделе [Лямбда-выражения](../../../language-reference/operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a3add-116">For more information about lambda expressions in C#, see [Lambda Expressions](../../../language-reference/operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="a3add-117">В следующем примере кода демонстрируется способ применения компилятора C# для создания дерева выражений, представляющего лямбда-выражение `num => num < 5`.</span><span class="sxs-lookup"><span data-stu-id="a3add-117">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="a3add-118">Создание деревьев выражений с помощью API-интерфейса</span><span class="sxs-lookup"><span data-stu-id="a3add-118">Creating Expression Trees by Using the API</span></span>  

 <span data-ttu-id="a3add-119">Для создания деревьев выражений с помощью API-интерфейса используйте класс <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="a3add-119">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="a3add-120">Этот класс содержит статические методы фабрики, позволяющие создать узлы дерева выражения конкретного типа, например, <xref:System.Linq.Expressions.ParameterExpression>, который представляет переменную или параметр, или <xref:System.Linq.Expressions.MethodCallExpression>, который представляет вызов метода.</span><span class="sxs-lookup"><span data-stu-id="a3add-120">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="a3add-121"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> и другие зависящие от выражения типы также определяются в пространстве имен <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="a3add-121"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="a3add-122">Эти типы являются производными от абстрактного типа <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="a3add-122">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="a3add-123">В следующем примере кода демонстрируется способ создания дерева выражений, представляющего лямбда-выражение `num => num < 5`, с помощью API.</span><span class="sxs-lookup"><span data-stu-id="a3add-123">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Manually build the expression tree for
// the lambda expression num => num < 5.  
ParameterExpression numParam = Expression.Parameter(typeof(int), "num");  
ConstantExpression five = Expression.Constant(5, typeof(int));  
BinaryExpression numLessThanFive = Expression.LessThan(numParam, five);  
Expression<Func<int, bool>> lambda1 =  
    Expression.Lambda<Func<int, bool>>(  
        numLessThanFive,  
        new ParameterExpression[] { numParam });  
```  
  
 <span data-ttu-id="a3add-124">На платформе .NET Framework 4 или более поздней версии API деревьев выражений также поддерживает присваивание и выражения потока управления, такие как циклы, условные блоки и блоки `try-catch`.</span><span class="sxs-lookup"><span data-stu-id="a3add-124">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="a3add-125">С помощью API-интерфейса можно создавать деревья выражений, более сложные, чем деревья, создаваемые компилятором C# из лямбда-выражений.</span><span class="sxs-lookup"><span data-stu-id="a3add-125">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="a3add-126">В следующем примере показан способ создания дерева выражений, которое вычисляет факториал числа.</span><span class="sxs-lookup"><span data-stu-id="a3add-126">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```csharp  
// Creating a parameter expression.  
ParameterExpression value = Expression.Parameter(typeof(int), "value");  
  
// Creating an expression to hold a local variable.
ParameterExpression result = Expression.Parameter(typeof(int), "result");  
  
// Creating a label to jump to from a loop.  
LabelTarget label = Expression.Label(typeof(int));  
  
// Creating a method body.  
BlockExpression block = Expression.Block(  
    // Adding a local variable.  
    new[] { result },  
    // Assigning a constant to a local variable: result = 1  
    Expression.Assign(result, Expression.Constant(1)),  
    // Adding a loop.  
        Expression.Loop(  
    // Adding a conditional block into the loop.  
           Expression.IfThenElse(  
    // Condition: value > 1  
               Expression.GreaterThan(value, Expression.Constant(1)),  
    // If true: result *= value --  
               Expression.MultiplyAssign(result,  
                   Expression.PostDecrementAssign(value)),  
    // If false, exit the loop and go to the label.  
               Expression.Break(label, result)  
           ),  
    // Label to jump to.  
       label  
    )  
);  
  
// Compile and execute an expression tree.  
int factorial = Expression.Lambda<Func<int, int>>(block, value).Compile()(5);  
  
Console.WriteLine(factorial);  
// Prints 120.  
```

<span data-ttu-id="a3add-127">Дополнительные сведения см. в записи блога [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/) (Создание динамических методов с использованием деревьев выражений в Visual Studio 2010), которая также применима к более поздним версиям Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3add-127">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="a3add-128">Синтаксический анализ деревьев выражений</span><span class="sxs-lookup"><span data-stu-id="a3add-128">Parsing Expression Trees</span></span>  

 <span data-ttu-id="a3add-129">В следующем примере кода показано, как дерево выражений, представляющее лямбда-выражение `num => num < 5`, может быть разложено на части.</span><span class="sxs-lookup"><span data-stu-id="a3add-129">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Create an expression tree.  
Expression<Func<int, bool>> exprTree = num => num < 5;  
  
// Decompose the expression tree.  
ParameterExpression param = (ParameterExpression)exprTree.Parameters[0];  
BinaryExpression operation = (BinaryExpression)exprTree.Body;  
ParameterExpression left = (ParameterExpression)operation.Left;  
ConstantExpression right = (ConstantExpression)operation.Right;  
  
Console.WriteLine("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value);  
  
// This code produces the following output:  
  
// Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="a3add-130">Неизменность деревьев выражений</span><span class="sxs-lookup"><span data-stu-id="a3add-130">Immutability of Expression Trees</span></span>  

 <span data-ttu-id="a3add-131">Деревья выражений должны быть неизменными.</span><span class="sxs-lookup"><span data-stu-id="a3add-131">Expression trees should be immutable.</span></span> <span data-ttu-id="a3add-132">Это означает, что если требуется изменить дерево выражений, следует создать новое дерево выражений путем копирования существующего и заменить узлы в нем.</span><span class="sxs-lookup"><span data-stu-id="a3add-132">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="a3add-133">Для прохода по существующему дереву выражений можно использовать другое дерево выражений (посетитель).</span><span class="sxs-lookup"><span data-stu-id="a3add-133">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="a3add-134">См. дополнительные сведения об [изменении деревьев выражений (C#)](./how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="a3add-134">For more information, see [How to modify expression trees (C#)](./how-to-modify-expression-trees.md).</span></span>
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="a3add-135">Компиляция деревьев выражений</span><span class="sxs-lookup"><span data-stu-id="a3add-135">Compiling Expression Trees</span></span>  

 <span data-ttu-id="a3add-136">Тип <xref:System.Linq.Expressions.Expression%601> предоставляет метод  <xref:System.Linq.Expressions.Expression%601.Compile%2A>, который компилирует код, представляемый деревом выражений, в исполняемый делегат.</span><span class="sxs-lookup"><span data-stu-id="a3add-136">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="a3add-137">В следующем примере кода показан способ компиляции дерева выражений и выполнения результирующего кода.</span><span class="sxs-lookup"><span data-stu-id="a3add-137">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```csharp  
// Creating an expression tree.  
Expression<Func<int, bool>> expr = num => num < 5;  
  
// Compiling the expression tree into a delegate.  
Func<int, bool> result = expr.Compile();  
  
// Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4));  
  
// Prints True.  
  
// You can also use simplified syntax  
// to compile and run an expression tree.  
// The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4));  
  
// Also prints True.  
```  
  
 <span data-ttu-id="a3add-138">См. дополнительные сведения о [выполнении деревьев выражений (C#)](./how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="a3add-138">For more information, see [How to execute expression trees (C#)](./how-to-execute-expression-trees.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a3add-139">См. также</span><span class="sxs-lookup"><span data-stu-id="a3add-139">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="a3add-140">Выполнение деревьев выражений (C#)</span><span class="sxs-lookup"><span data-stu-id="a3add-140">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="a3add-141">Изменение деревьев выражений (C#)</span><span class="sxs-lookup"><span data-stu-id="a3add-141">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
- [<span data-ttu-id="a3add-142">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="a3add-142">Lambda Expressions</span></span>](../../../language-reference/operators/lambda-expressions.md)
- [<span data-ttu-id="a3add-143">Общие сведения о среде DLR</span><span class="sxs-lookup"><span data-stu-id="a3add-143">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="a3add-144">Основные понятия программирования (C#)</span><span class="sxs-lookup"><span data-stu-id="a3add-144">Programming Concepts (C#)</span></span>](../index.md)
