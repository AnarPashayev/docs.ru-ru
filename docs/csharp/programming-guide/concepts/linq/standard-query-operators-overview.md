---
title: Общие сведения о стандартных операторах запроса (C#)
description: Функциональные возможности стандартных операторов запросов LINQ включают фильтрацию, проекцию, статистическую обработку, сортировку при программировании на C#.
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 1ff98e47641dbe7a884b7d6c7758c1fe61b95091
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178779"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="88c05-103">Общие сведения о стандартных операторах запроса (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-103">Standard Query Operators Overview (C#)</span></span>

<span data-ttu-id="88c05-104">*Стандартные операторы запросов* — это методы, формирующие шаблон LINQ.</span><span class="sxs-lookup"><span data-stu-id="88c05-104">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="88c05-105">Большинство этих методов работают с последовательностями. В данном контексте последовательность — это объект, тип которого реализует интерфейс <xref:System.Collections.Generic.IEnumerable%601> или <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="88c05-105">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="88c05-106">Функциональные возможности стандартных операторов запросов включают фильтрацию, проекцию, статистическую обработку, сортировку и многие другие.</span><span class="sxs-lookup"><span data-stu-id="88c05-106">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="88c05-107">Существует два набора стандартных операторов запросов LINQ, один из них работает с объектами типа <xref:System.Collections.Generic.IEnumerable%601>, а другой — с объектами типа <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="88c05-107">There are two sets of LINQ standard query operators: one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601>, another that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="88c05-108">Методы, входящие в каждый из наборов, являются статическими членами классов <xref:System.Linq.Enumerable> и <xref:System.Linq.Queryable> соответственно.</span><span class="sxs-lookup"><span data-stu-id="88c05-108">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="88c05-109">Они определяются как *методы расширения* типа, к которому применяются.</span><span class="sxs-lookup"><span data-stu-id="88c05-109">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="88c05-110">Методы расширения можно вызывать, используя либо синтаксис статического метода, либо синтаксис метода экземпляра.</span><span class="sxs-lookup"><span data-stu-id="88c05-110">Extension methods can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="88c05-111">Кроме того, несколько стандартных методов операторов запроса работают с типами, отличными от основанных на <xref:System.Collections.Generic.IEnumerable%601> или <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="88c05-111">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="88c05-112">Тип <xref:System.Linq.Enumerable> определяет два таких метода, которые работают с объектами типа <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="88c05-112">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="88c05-113">Эти методы (<xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> и <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>) позволяют выполнять запрос к непараметризованным или не являющимся универсальными коллекциям с использованием шаблона LINQ.</span><span class="sxs-lookup"><span data-stu-id="88c05-113">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="88c05-114">Для этого создается строго типизированная коллекция объектов.</span><span class="sxs-lookup"><span data-stu-id="88c05-114">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="88c05-115">Класс <xref:System.Linq.Queryable> определяет два схожих метода (<xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> и <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>), которые работают с объектами типа <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="88c05-115">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="88c05-116">Стандартные операторы запросов имеют различное время выполнения, которое зависит от того, возвращают они одноэлементное значение или последовательность значений.</span><span class="sxs-lookup"><span data-stu-id="88c05-116">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="88c05-117">Методы, возвращающие одноэлементное значение (например, <xref:System.Linq.Enumerable.Average%2A> и <xref:System.Linq.Enumerable.Sum%2A>), выполняются одновременно.</span><span class="sxs-lookup"><span data-stu-id="88c05-117">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="88c05-118">Методы, которые возвращают последовательность, откладывают выполнение запроса и возвращают перечисляемый объект.</span><span class="sxs-lookup"><span data-stu-id="88c05-118">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="88c05-119">При использовании методов, которые применяются к коллекциям, т. е. методов, которые расширяют <xref:System.Collections.Generic.IEnumerable%601>, возвращаемый перечисляемый объект захватывает переданные в этот метод аргументы.</span><span class="sxs-lookup"><span data-stu-id="88c05-119">For methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="88c05-120">При перечислении этого объекта задействуется логика оператора запросов и возвращаются результаты запросов.</span><span class="sxs-lookup"><span data-stu-id="88c05-120">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="88c05-121">Напротив, методы, расширяющие <xref:System.Linq.IQueryable%601>, не реализуют никаких поведений запросов.</span><span class="sxs-lookup"><span data-stu-id="88c05-121">In contrast, methods that extend <xref:System.Linq.IQueryable%601> don't implement any querying behavior.</span></span> <span data-ttu-id="88c05-122">Они создают дерево выражений, представляющее выполняемый запрос.</span><span class="sxs-lookup"><span data-stu-id="88c05-122">They build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="88c05-123">Запрос обрабатывается объектом <xref:System.Linq.IQueryable%601> источника.</span><span class="sxs-lookup"><span data-stu-id="88c05-123">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="88c05-124">Вызовы методов запросов можно объединять в один запрос, в результате чего запросы могут становиться довольно сложными.</span><span class="sxs-lookup"><span data-stu-id="88c05-124">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="88c05-125">В следующем примере кода показано, как использовать стандартные операторы запросов для получения сведений о последовательности.</span><span class="sxs-lookup"><span data-stu-id="88c05-125">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="88c05-126">Синтаксис выражений запросов</span><span class="sxs-lookup"><span data-stu-id="88c05-126">Query Expression Syntax</span></span>  

 <span data-ttu-id="88c05-127">Некоторые из наиболее часто используемых стандартных операторов запросов имеют представление в виде ключевых слов в синтаксисе языка C# и Visual Basic, что позволяет вызывать их как часть *выражения* *запроса*.</span><span class="sxs-lookup"><span data-stu-id="88c05-127">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="88c05-128">Дополнительные сведения о стандартных операторах запросов с выделенными ключевыми словами и соответствующим синтаксисом см. в разделе [Синтаксис выражений запросов для стандартных операторов запросов (C#)](./query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="88c05-128">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="88c05-129">Расширение стандартных операторов запросов</span><span class="sxs-lookup"><span data-stu-id="88c05-129">Extending the Standard Query Operators</span></span>  

 <span data-ttu-id="88c05-130">Набор стандартных операторов запросов можно дополнить, создав специальные методы, соответствующие вашему целевому домену или технологии.</span><span class="sxs-lookup"><span data-stu-id="88c05-130">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="88c05-131">Кроме того, можно заменить стандартные операторы запросов на собственные реализации, предоставляющие дополнительные услуги, такие как удаленное вычисление, перевод запросов и оптимизация.</span><span class="sxs-lookup"><span data-stu-id="88c05-131">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="88c05-132">Пример см. в разделе <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="88c05-132">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="88c05-133">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="88c05-133">Related Sections</span></span>  

 <span data-ttu-id="88c05-134">Следующие ссылки адресуют к статьям, содержащим дополнительные сведения о различных стандартных операторах запросов в зависимости от их функциональности.</span><span class="sxs-lookup"><span data-stu-id="88c05-134">The following links take you to articles that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="88c05-135">Сортировка данных (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-135">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="88c05-136">Операции над множествами (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-136">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="88c05-137">Фильтрация данных (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-137">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="88c05-138">Операции, использующие квантификаторы (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-138">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="88c05-139">Операции проекции (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-139">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="88c05-140">Секционирование данных (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-140">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="88c05-141">Операции соединения (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-141">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="88c05-142">Группирование данных (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-142">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="88c05-143">Операции создания (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-143">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="88c05-144">Операции сравнения (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-144">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="88c05-145">Операции с элементами (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-145">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="88c05-146">Преобразование типов данных (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-146">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="88c05-147">Операции объединения (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-147">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="88c05-148">Операции агрегирования (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-148">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="88c05-149">См. также</span><span class="sxs-lookup"><span data-stu-id="88c05-149">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="88c05-150">Введение в запросы LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-150">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="88c05-151">Синтаксис выражений запроса для стандартных операторов запроса (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-151">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="88c05-152">Классификация стандартных операторов запросов по способу выполнения (C#)</span><span class="sxs-lookup"><span data-stu-id="88c05-152">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="88c05-153">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="88c05-153">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
