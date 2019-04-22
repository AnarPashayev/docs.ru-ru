---
title: Общие сведения о стандартных операторах (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 9bfdf2163be52d9016a800d65006bbc4fbf560a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841476"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="4c88f-102">Общие сведения о стандартных операторах (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-102">Standard Query Operators Overview (Visual Basic)</span></span>
<span data-ttu-id="4c88f-103">*Стандартные операторы запросов* — это методы, формирующие шаблон LINQ.</span><span class="sxs-lookup"><span data-stu-id="4c88f-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="4c88f-104">Большинство этих методов работают с последовательностями. В данном контексте последовательность — это объект, тип которого реализует интерфейс <xref:System.Collections.Generic.IEnumerable%601> или <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="4c88f-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="4c88f-105">Функциональные возможности стандартных операторов запросов включают фильтрацию, проекцию, статистическую обработку, сортировку и многие другие.</span><span class="sxs-lookup"><span data-stu-id="4c88f-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="4c88f-106">Существует два набора стандартных операторов запросов LINQ, один из них работает с объектами типа <xref:System.Collections.Generic.IEnumerable%601>, а другой — с объектами типа <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="4c88f-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="4c88f-107">Методы, входящие в каждый из наборов, являются статическими членами классов <xref:System.Linq.Enumerable> и <xref:System.Linq.Queryable> соответственно.</span><span class="sxs-lookup"><span data-stu-id="4c88f-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="4c88f-108">Они определяются как *методы расширения* типа, к которому применяются.</span><span class="sxs-lookup"><span data-stu-id="4c88f-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="4c88f-109">Это означает, что их можно вызывать, используя либо синтаксис статического метода, либо синтаксис метода экземпляра.</span><span class="sxs-lookup"><span data-stu-id="4c88f-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="4c88f-110">Кроме того, несколько стандартных методов операторов запроса работают с типами, отличными от основанных на <xref:System.Collections.Generic.IEnumerable%601> или <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="4c88f-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="4c88f-111">Тип <xref:System.Linq.Enumerable> определяет два таких метода, которые работают с объектами типа <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="4c88f-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="4c88f-112">Эти методы (<xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> и <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>) позволяют выполнять запрос к непараметризованным или не являющимся универсальными коллекциям с использованием шаблона LINQ.</span><span class="sxs-lookup"><span data-stu-id="4c88f-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="4c88f-113">Для этого создается строго типизированная коллекция объектов.</span><span class="sxs-lookup"><span data-stu-id="4c88f-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="4c88f-114">Класс <xref:System.Linq.Queryable> определяет два схожих метода (<xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> и <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>), которые работают с объектами типа <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="4c88f-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="4c88f-115">Стандартные операторы запросов имеют различное время выполнения, которое зависит от того, возвращают они одноэлементное значение или последовательность значений.</span><span class="sxs-lookup"><span data-stu-id="4c88f-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="4c88f-116">Методы, возвращающие одноэлементное значение (например, <xref:System.Linq.Enumerable.Average%2A> и <xref:System.Linq.Enumerable.Sum%2A>), выполняются одновременно.</span><span class="sxs-lookup"><span data-stu-id="4c88f-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="4c88f-117">Методы, которые возвращают последовательность, откладывают выполнение запроса и возвращают перечисляемый объект.</span><span class="sxs-lookup"><span data-stu-id="4c88f-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="4c88f-118">При использовании методов, которые применяются к коллекциям, т. е. методов, которые расширяют <xref:System.Collections.Generic.IEnumerable%601>, возвращаемый перечисляемый объект захватывает переданные в этот метод аргументы.</span><span class="sxs-lookup"><span data-stu-id="4c88f-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="4c88f-119">При перечислении этого объекта задействуется логика оператора запросов и возвращаются результаты запросов.</span><span class="sxs-lookup"><span data-stu-id="4c88f-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="4c88f-120">При этом методы, расширяющие <xref:System.Linq.IQueryable%601>, не реализуют поведение запросов, но формируют дерево выражения, представляющее выполняемый запрос.</span><span class="sxs-lookup"><span data-stu-id="4c88f-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="4c88f-121">Запрос обрабатывается объектом <xref:System.Linq.IQueryable%601> источника.</span><span class="sxs-lookup"><span data-stu-id="4c88f-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="4c88f-122">Вызовы методов запросов можно объединять в один запрос, в результате чего запросы могут становиться довольно сложными.</span><span class="sxs-lookup"><span data-stu-id="4c88f-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="4c88f-123">В следующем примере кода показано, как использовать стандартные операторы запросов для получения сведений о последовательности.</span><span class="sxs-lookup"><span data-stu-id="4c88f-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="4c88f-124">Синтаксис выражений запросов</span><span class="sxs-lookup"><span data-stu-id="4c88f-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="4c88f-125">Некоторые из наиболее часто используемых стандартных операторов запросов имеют представление в виде ключевых слов в синтаксисе языка C# и Visual Basic, что позволяет вызывать их как часть *выражения* *запроса*.</span><span class="sxs-lookup"><span data-stu-id="4c88f-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="4c88f-126">Дополнительные сведения о стандартных операторах запросов с выделенными ключевыми словами и их синтаксисе см. в разделе [синтаксис выражений запроса для стандартных операторов запросов (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="4c88f-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="4c88f-127">Расширение стандартных операторов запросов</span><span class="sxs-lookup"><span data-stu-id="4c88f-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="4c88f-128">Набор стандартных операторов запросов можно дополнить, создав специальные методы, соответствующие вашему целевому домену или технологии.</span><span class="sxs-lookup"><span data-stu-id="4c88f-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="4c88f-129">Кроме того, можно заменить стандартные операторы запросов на собственные реализации, предоставляющие дополнительные услуги, такие как удаленное вычисление, перевод запросов и оптимизация.</span><span class="sxs-lookup"><span data-stu-id="4c88f-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="4c88f-130">Пример см. в разделе <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c88f-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4c88f-131">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="4c88f-131">Related Sections</span></span>  
 <span data-ttu-id="4c88f-132">Следующие ссылки адресуют к разделам, содержащим дополнительные сведения о различных стандартных операторах запросов в зависимости от их функциональности.</span><span class="sxs-lookup"><span data-stu-id="4c88f-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="4c88f-133">Сортировка данных</span><span class="sxs-lookup"><span data-stu-id="4c88f-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="4c88f-134">Операции с множествами (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="4c88f-135">Фильтрация данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="4c88f-136">Операции, использующие квантификаторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="4c88f-137">Операции проекции (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="4c88f-138">Секционирование данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="4c88f-139">Объединение (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="4c88f-140">Группирование данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="4c88f-141">Операции создания (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="4c88f-142">Операции равенства (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="4c88f-143">Операции с элементами (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="4c88f-144">Преобразование типов данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="4c88f-145">Операции объединения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="4c88f-146">Операции агрегирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="4c88f-147">См. также</span><span class="sxs-lookup"><span data-stu-id="4c88f-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="4c88f-148">Знакомство с LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-148">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="4c88f-149">Синтаксис выражений запроса для стандартных операторов запросов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="4c88f-150">Классификация стандартных операторов запросов по способу выполнения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c88f-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="4c88f-151">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="4c88f-151">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
