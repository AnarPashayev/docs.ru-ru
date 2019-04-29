---
title: Практическое руководство. Использование деревьев выражений для построения динамических запросов (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 2f91d95f888ab98902cc300afb61c41b62e64050
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966222"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Практическое руководство. Использование деревьев выражений для построения динамических запросов (Visual Basic)
В LINQ деревья выражений используются для представления структурированных запросов к источникам данных, которые реализуют интерфейс <xref:System.Linq.IQueryable%601>. Например, поставщик LINQ реализует интерфейс <xref:System.Linq.IQueryable%601> для выполнения запросов к реляционным хранилищам данных. Компилятор Visual Basic компилирует запросы к источникам данных в код, который строит дерево выражения во время выполнения. Поставщик запросов может переходить по структуре данных дерева выражения и преобразовать ее в язык запросов, соответствующий источнику данных.  
  
 Деревья выражений также используются в LINQ для представления лямбда-выражений, которые присваиваются переменным типа <xref:System.Linq.Expressions.Expression%601>.  
  
 В этом разделе описывается использование деревьев выражений для создания динамических запросов LINQ. Динамические запросы удобны в тех случаях, когда характеристики запроса неизвестны во время компиляции. Например, приложение может предоставлять пользовательский интерфейс, который позволяет конечному пользователю указать один или несколько предикатов для фильтрации данных. Для использования LINQ для создания запросов такой тип приложения должен использовать деревья выражений для создания запроса LINQ во время выполнения.  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование деревьев выражений для создания запроса к источнику данных `IQueryable` и его выполнения. В коде создается дерево выражения для представления следующего запроса:  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 Фабричные методы в пространстве имен <xref:System.Linq.Expressions> используются для создания деревьев выражений, представляющих общий запрос. Выражения, которые представляют вызовы методов стандартных операторов запросов, ссылаются на реализации <xref:System.Linq.Queryable> этих методов. Итоговое дерево выражения передается в реализацию <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> поставщика источника данных `IQueryable` для создания исполняемого запроса типа `IQueryable`. Результаты получаются путем перечисления переменной запроса.  
  
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
  
 Этот код использует фиксированное число выражений в предикате, передаваемом в метод `Queryable.Where`. Тем не менее можно написать приложение, которое будет сочетать переменное число выражений предиката, зависящих от вводимых пользователем данных. Также можно изменять стандартные операторы запросов, которые вызываются в запросе, в зависимости от входных данных от пользователя.  
  
## <a name="compiling-the-code"></a>Компиляция кода  
  
- Создайте новый проект **консольного приложения**.  
  
- Добавьте ссылку на библиотеку System.Core.dll, если такая ссылка отсутствует.  
  
- Включите пространство имен System.Linq.Expressions.  
  
- Скопируйте код из примера и вставьте его в `Main` `Sub` процедуры.  
  
## <a name="see-also"></a>См. также

- [Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) (Деревья выражений (Visual Basic))
- [Практическое руководство. Выполнение деревьев выражений (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
