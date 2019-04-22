---
title: Практическое руководство. Использование деревьев выражений для построения динамических запросов (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 2f91d95f888ab98902cc300afb61c41b62e64050
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827683"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="da83b-102">Практическое руководство. Использование деревьев выражений для построения динамических запросов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da83b-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="da83b-103">В LINQ деревья выражений используются для представления структурированных запросов к источникам данных, которые реализуют интерфейс <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="da83b-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="da83b-104">Например, поставщик LINQ реализует интерфейс <xref:System.Linq.IQueryable%601> для выполнения запросов к реляционным хранилищам данных.</span><span class="sxs-lookup"><span data-stu-id="da83b-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="da83b-105">Компилятор Visual Basic компилирует запросы к источникам данных в код, который строит дерево выражения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="da83b-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="da83b-106">Поставщик запросов может переходить по структуре данных дерева выражения и преобразовать ее в язык запросов, соответствующий источнику данных.</span><span class="sxs-lookup"><span data-stu-id="da83b-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="da83b-107">Деревья выражений также используются в LINQ для представления лямбда-выражений, которые присваиваются переменным типа <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="da83b-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="da83b-108">В этом разделе описывается использование деревьев выражений для создания динамических запросов LINQ.</span><span class="sxs-lookup"><span data-stu-id="da83b-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="da83b-109">Динамические запросы удобны в тех случаях, когда характеристики запроса неизвестны во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="da83b-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="da83b-110">Например, приложение может предоставлять пользовательский интерфейс, который позволяет конечному пользователю указать один или несколько предикатов для фильтрации данных.</span><span class="sxs-lookup"><span data-stu-id="da83b-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="da83b-111">Для использования LINQ для создания запросов такой тип приложения должен использовать деревья выражений для создания запроса LINQ во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="da83b-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da83b-112">Пример</span><span class="sxs-lookup"><span data-stu-id="da83b-112">Example</span></span>  
 <span data-ttu-id="da83b-113">В следующем примере показано использование деревьев выражений для создания запроса к источнику данных `IQueryable` и его выполнения.</span><span class="sxs-lookup"><span data-stu-id="da83b-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="da83b-114">В коде создается дерево выражения для представления следующего запроса:</span><span class="sxs-lookup"><span data-stu-id="da83b-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="da83b-115">Фабричные методы в пространстве имен <xref:System.Linq.Expressions> используются для создания деревьев выражений, представляющих общий запрос.</span><span class="sxs-lookup"><span data-stu-id="da83b-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="da83b-116">Выражения, которые представляют вызовы методов стандартных операторов запросов, ссылаются на реализации <xref:System.Linq.Queryable> этих методов.</span><span class="sxs-lookup"><span data-stu-id="da83b-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="da83b-117">Итоговое дерево выражения передается в реализацию <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> поставщика источника данных `IQueryable` для создания исполняемого запроса типа `IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="da83b-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="da83b-118">Результаты получаются путем перечисления переменной запроса.</span><span class="sxs-lookup"><span data-stu-id="da83b-118">The results are obtained by enumerating that query variable.</span></span>  
  
```vb  
' Add an Imports statement for System.Linq.Expressions.  
  
Dim companies =   
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",   
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",   
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",   
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",   
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}  
  
' The IQueryable data to query.  
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()  
  
' Compose the expression tree that represents the parameter to the predicate.  
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")  
  
' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****  
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".  
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))  
Dim right As Expression = Expression.Constant("coho winery")  
Dim e1 As Expression = Expression.Equal(left, right)  
  
' Create an expression tree that represents the expression: company.Length > 16.  
left = Expression.Property(pe, GetType(String).GetProperty("Length"))  
right = Expression.Constant(16, GetType(Integer))  
Dim e2 As Expression = Expression.GreaterThan(left, right)  
  
' Combine the expressions to create an expression tree that represents the  
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).  
Dim predicateBody As Expression = Expression.OrElse(e1, e2)  
  
' Create an expression tree that represents the expression:  
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)  
Dim whereCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "Where",   
        New Type() {queryableData.ElementType},   
        queryableData.Expression,   
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))  
' ***** End Where *****  
  
' ***** OrderBy(Function(company) company) *****  
' Create an expression tree that represents the expression:  
' whereCallExpression.OrderBy(Function(company) company)  
Dim orderByCallExpression As MethodCallExpression = Expression.Call(   
        GetType(Queryable),   
        "OrderBy",   
        New Type() {queryableData.ElementType, queryableData.ElementType},   
        whereCallExpression,   
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))  
' ***** End OrderBy *****  
  
' Create an executable query from the expression tree.  
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)  
  
' Enumerate the results.  
For Each company As String In results  
    Console.WriteLine(company)  
Next  
  
' This code produces the following output:  
'  
' Blue Yonder Airlines  
' City Power & Light  
' Coho Winery  
' Consolidated Messenger  
' Graphic Design Institute  
' Humongous Insurance  
' Lucerne Publishing  
' Northwind Traders  
' The Phone Company  
' Wide World Importers  
```  
  
 <span data-ttu-id="da83b-119">Этот код использует фиксированное число выражений в предикате, передаваемом в метод `Queryable.Where`.</span><span class="sxs-lookup"><span data-stu-id="da83b-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="da83b-120">Тем не менее можно написать приложение, которое будет сочетать переменное число выражений предиката, зависящих от вводимых пользователем данных.</span><span class="sxs-lookup"><span data-stu-id="da83b-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="da83b-121">Также можно изменять стандартные операторы запросов, которые вызываются в запросе, в зависимости от входных данных от пользователя.</span><span class="sxs-lookup"><span data-stu-id="da83b-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="da83b-122">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="da83b-122">Compiling the Code</span></span>  
  
-   <span data-ttu-id="da83b-123">Создайте новый проект **консольного приложения**.</span><span class="sxs-lookup"><span data-stu-id="da83b-123">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="da83b-124">Добавьте ссылку на библиотеку System.Core.dll, если такая ссылка отсутствует.</span><span class="sxs-lookup"><span data-stu-id="da83b-124">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="da83b-125">Включите пространство имен System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="da83b-125">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="da83b-126">Скопируйте код из примера и вставьте его в `Main` `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="da83b-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da83b-127">См. также</span><span class="sxs-lookup"><span data-stu-id="da83b-127">See also</span></span>

- <span data-ttu-id="da83b-128">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) (Деревья выражений (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="da83b-128">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)</span></span>
- [<span data-ttu-id="da83b-129">Практическое руководство. Выполнение деревьев выражений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da83b-129">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
