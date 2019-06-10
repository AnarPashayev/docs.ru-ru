---
title: Возможности C#, поддерживающие LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: bf9af90c9695ad9428a887a901a95282672a4f75
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722537"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="49697-102">Возможности C#, поддерживающие LINQ</span><span class="sxs-lookup"><span data-stu-id="49697-102">C# Features That Support LINQ</span></span>

<span data-ttu-id="49697-103">В следующем разделе приведены новые конструкции языка, представленные в C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="49697-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="49697-104">Несмотря на то, что эти новые возможности в некоторой степени используются с запросами [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], они не ограничиваются [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] и могут использоваться в любом контексте, где они будут целесообразны.</span><span class="sxs-lookup"><span data-stu-id="49697-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="49697-105">Выражения запросов</span><span class="sxs-lookup"><span data-stu-id="49697-105">Query Expressions</span></span>

<span data-ttu-id="49697-106">Выражения запросов используют декларативный синтаксис, аналогичный SQL или XQuery, для выполнения запросов к коллекциям IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="49697-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="49697-107">Во время компиляции синтаксис запроса преобразуется в вызовы методов к реализации поставщика [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] методов расширения стандартных операторов запросов.</span><span class="sxs-lookup"><span data-stu-id="49697-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="49697-108">Приложения управляют стандартными операторами запросов в области, указывая соответствующее пространство имен с помощью директивы `using`.</span><span class="sxs-lookup"><span data-stu-id="49697-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="49697-109">Следующее выражение запроса принимает массив строк, группирует их в соответствии с первым символом в строке и упорядочивает группы.</span><span class="sxs-lookup"><span data-stu-id="49697-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="49697-110">Дополнительные сведения см. в разделе [Выражения запросов LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span><span class="sxs-lookup"><span data-stu-id="49697-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="49697-111">Неявно типизированные переменные (var)</span><span class="sxs-lookup"><span data-stu-id="49697-111">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="49697-112">Вместо явного задания типа при объявлении и инициализации переменной можно использовать модификатор [var](../../../../csharp/language-reference/keywords/var.md), чтобы сообщить компилятору о необходимости определить и присвоить тип, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="49697-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="49697-113">Переменные, объявленные как `var`, настолько же строго типизированы, как и переменные, тип которых вы задаете явно.</span><span class="sxs-lookup"><span data-stu-id="49697-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="49697-114">Использование `var` делает возможным создание анонимных типов, однако его можно использовать только для локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="49697-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="49697-115">Массивы также могут быть объявлены путем неявной типизации.</span><span class="sxs-lookup"><span data-stu-id="49697-115">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="49697-116">Дополнительные сведения см. в статье [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) (Неявно типизированные локальные переменные).</span><span class="sxs-lookup"><span data-stu-id="49697-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="49697-117">Инициализаторы объектов и коллекций</span><span class="sxs-lookup"><span data-stu-id="49697-117">Object and Collection Initializers</span></span>

<span data-ttu-id="49697-118">Инициализаторы объектов и коллекций позволяют инициализировать объекты без явного вызова конструктора для объекта.</span><span class="sxs-lookup"><span data-stu-id="49697-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="49697-119">Инициализаторы обычно используются в выражениях запросов при проецировании исходных данных в новый тип данных.</span><span class="sxs-lookup"><span data-stu-id="49697-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="49697-120">При наличии, например, класса с именем `Customer` с общедоступными свойствами `Name` и `Phone` инициализатор объектов можно использовать как в следующем примере кода:</span><span class="sxs-lookup"><span data-stu-id="49697-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="49697-121">Продолжим рассматривать класс `Customer`. Предположим, что есть источник данных с именем `IncomingOrders` и что для каждого заказа с большим значением `OrderSize` нужно создавать класс `Customer` на основе этого заказа.</span><span class="sxs-lookup"><span data-stu-id="49697-121">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="49697-122">Можно выполнить запрос LINQ для этого источника данных и использовать инициализацию объекта, чтобы заполнить коллекцию:</span><span class="sxs-lookup"><span data-stu-id="49697-122">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="49697-123">У источника данных может быть больше скрытых свойств, чем у класса `Customer`, такого как `OrderSize`. Но инициализация объекта позволяет преобразовать данные, возвращаемые по запросу, в требуемый тип. Мы выберем данные, соответствующие нашему классу.</span><span class="sxs-lookup"><span data-stu-id="49697-123">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="49697-124">В результате мы заполнили `IEnumerable` новыми классами `Customer`, как и требовалось.</span><span class="sxs-lookup"><span data-stu-id="49697-124">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="49697-125">Приведенный выше код также можно представить в синтаксисе метода LINQ:</span><span class="sxs-lookup"><span data-stu-id="49697-125">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="49697-126">Дополнительные сведения:</span><span class="sxs-lookup"><span data-stu-id="49697-126">For more information, see:</span></span>

- [<span data-ttu-id="49697-127">Инициализаторы объектов и коллекций</span><span class="sxs-lookup"><span data-stu-id="49697-127">Object and Collection Initializers</span></span>](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="49697-128">Синтаксис выражений запроса для стандартных операторов запроса</span><span class="sxs-lookup"><span data-stu-id="49697-128">Query Expression Syntax for Standard Query Operators</span></span>](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="49697-129">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="49697-129">Anonymous Types</span></span>

<span data-ttu-id="49697-130">Анонимный тип создается компилятором, и имя типа доступно только компилятору.</span><span class="sxs-lookup"><span data-stu-id="49697-130">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="49697-131">Анонимные типы обеспечивают удобный способ временной группировки набора свойств в результатах запроса без необходимости определения отдельного именованного типа.</span><span class="sxs-lookup"><span data-stu-id="49697-131">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="49697-132">Анонимные типы инициализируются с помощью нового выражения и инициализатора объектов, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="49697-132">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="49697-133">Дополнительные сведения см. в статье [Анонимные типы](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="49697-133">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="49697-134">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="49697-134">Extension Methods</span></span>

<span data-ttu-id="49697-135">Метод расширения представляет собой статический метод, который может быть связан с типом, чтобы его можно было вызывать, как если бы он являлся методом экземпляра типа.</span><span class="sxs-lookup"><span data-stu-id="49697-135">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="49697-136">Эта возможность позволяет, по сути, "добавлять" новые методы в существующие типы, фактически не изменяя их.</span><span class="sxs-lookup"><span data-stu-id="49697-136">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="49697-137">Стандартные операторы запросов представляют собой набор методов расширения, предоставляющих функции запросов [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] для любого типа, реализующего интерфейс <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="49697-137">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="49697-138">Дополнительные сведения см. в разделе [Методы расширения](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="49697-138">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="49697-139">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="49697-139">Lambda Expressions</span></span>

<span data-ttu-id="49697-140">Лямбда-выражение — это встроенная функция, которая использует оператор => для отделения входных параметров от тела функции и может быть преобразована во время компиляции в делегат или дерево выражения.</span><span class="sxs-lookup"><span data-stu-id="49697-140">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="49697-141">В программировании [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] вы сталкиваетесь с лямбда-выражениями при выполнении прямых вызовов к стандартным операторам запросов.</span><span class="sxs-lookup"><span data-stu-id="49697-141">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="49697-142">Дополнительные сведения:</span><span class="sxs-lookup"><span data-stu-id="49697-142">For more information, see:</span></span>

- [<span data-ttu-id="49697-143">Анонимные функции</span><span class="sxs-lookup"><span data-stu-id="49697-143">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="49697-144">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="49697-144">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)

- <span data-ttu-id="49697-145">[Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) (Деревья выражений (C#))</span><span class="sxs-lookup"><span data-stu-id="49697-145">[Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="49697-146">См. также</span><span class="sxs-lookup"><span data-stu-id="49697-146">See also</span></span>

- [<span data-ttu-id="49697-147">LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="49697-147">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
