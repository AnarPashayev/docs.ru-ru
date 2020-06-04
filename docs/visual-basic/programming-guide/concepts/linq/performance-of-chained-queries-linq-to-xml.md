---
title: Производительность связанных запросов (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 6b87f2744f663ebd45dceb036dcaac71b80765fc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396393"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="44b3f-102">Производительность цепочек запросов (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44b3f-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="44b3f-103">Одним из наиболее важных преимуществ LINQ (и LINQ to XML) является возможность эффективного выполнения цепочек запросов наряду с одиночными большими и более сложными запросами.</span><span class="sxs-lookup"><span data-stu-id="44b3f-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>

<span data-ttu-id="44b3f-104">Цепочкой запросов называется запрос, использующий в качестве источника другой запрос.</span><span class="sxs-lookup"><span data-stu-id="44b3f-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="44b3f-105">Например, в следующем простом коде запрос `query2` в качестве источника включает в себя запрос `query1`.</span><span class="sxs-lookup"><span data-stu-id="44b3f-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

<span data-ttu-id="44b3f-106">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="44b3f-106">This example produces the following output:</span></span>

```console
4
```

<span data-ttu-id="44b3f-107">Эта цепочка запросов по своим показателям производительности аналогична выполнению итераций по связанному списку.</span><span class="sxs-lookup"><span data-stu-id="44b3f-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>

- <span data-ttu-id="44b3f-108">Производительность оси <xref:System.Xml.Linq.XContainer.Elements%2A> и выполнения итераций по связанному списку практически одинакова.</span><span class="sxs-lookup"><span data-stu-id="44b3f-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="44b3f-109">Ось <xref:System.Xml.Linq.XContainer.Elements%2A> реализована в виде итератора с отложенным выполнением.</span><span class="sxs-lookup"><span data-stu-id="44b3f-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="44b3f-110">Это означает, что помимо итераций по связанному списку выполняется и другая работа, например, выделяется память для объекта итератора и отслеживается состояние выполнения.</span><span class="sxs-lookup"><span data-stu-id="44b3f-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="44b3f-111">Эта работа делится на две категории: работа, выполняемая при настройке итератора, и работа, выполняемая при каждой итерации.</span><span class="sxs-lookup"><span data-stu-id="44b3f-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="44b3f-112">Настройка требует небольшого фиксированного объема работы, тогда как объем работы, выполняемой при каждой итерации, пропорционален количеству элементов в исходной коллекции.</span><span class="sxs-lookup"><span data-stu-id="44b3f-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>

- <span data-ttu-id="44b3f-113">В запросе `query1` предложение `Where` вызывает метод <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="44b3f-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="44b3f-114">Этот метод так же реализован в виде итератора.</span><span class="sxs-lookup"><span data-stu-id="44b3f-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="44b3f-115">Работа по настройке состоит в создании экземпляра выражения-делегата, которое будет ссылаться на лямбда-выражение, и в выполнении обычной настройки итератора.</span><span class="sxs-lookup"><span data-stu-id="44b3f-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="44b3f-116">Выражение-делегат вызывается в каждой итерации для выполнения предиката.</span><span class="sxs-lookup"><span data-stu-id="44b3f-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="44b3f-117">Работа по настройке и работа, выполняемая при каждой итерации, аналогична работе, выполняемой при итерациях по оси.</span><span class="sxs-lookup"><span data-stu-id="44b3f-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>

- <span data-ttu-id="44b3f-118">В запросе `query1` предложение select вызывает метод <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="44b3f-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="44b3f-119">Этот метод имеет такие же показатели производительности, что и метод <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="44b3f-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>

- <span data-ttu-id="44b3f-120">В запросе `query2` предложения `Where` и `Select` имеют такие же показатели производительности, как и в запросе `query1`.</span><span class="sxs-lookup"><span data-stu-id="44b3f-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>

 <span data-ttu-id="44b3f-121">Таким образом, работа итерации по запросу `query2` прямо пропорциональна количеству элементов в источнике первого запроса, то есть имеет линейную зависимость.</span><span class="sxs-lookup"><span data-stu-id="44b3f-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>

## <a name="see-also"></a><span data-ttu-id="44b3f-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="44b3f-122">See also</span></span>

- [<span data-ttu-id="44b3f-123">Производительность (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44b3f-123">Performance (LINQ to XML) (Visual Basic)</span></span>](performance-linq-to-xml.md)
