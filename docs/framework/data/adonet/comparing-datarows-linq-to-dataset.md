---
title: Сравнение объектов DataRow (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 0903aac366426e8b4d271ae4bfaa54c79a198e5c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583750"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="2ab43-102">Сравнение объектов DataRow (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="2ab43-102">Comparing DataRows (LINQ to DataSet)</span></span>
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] <span data-ttu-id="2ab43-103">определяет различные операторы для работы с наборами, позволяющие сравнивать элементы и определять их равенство.</span><span class="sxs-lookup"><span data-stu-id="2ab43-103">defines various set operators to compare source elements to see if they are equal.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] <span data-ttu-id="2ab43-104">предоставляет следующие операторы для работы с наборами:</span><span class="sxs-lookup"><span data-stu-id="2ab43-104">provides the following set operators:</span></span>  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="2ab43-105">Эти операторы сравнивают элементы путем вызова методов <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> и <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> для каждой коллекции элементов.</span><span class="sxs-lookup"><span data-stu-id="2ab43-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="2ab43-106">Для объектов <xref:System.Data.DataRow> эти операторы выполняют ссылочное сравнение, которое в общем случае не является идеальным для операторов наборов, выполняющихся над табличными данными.</span><span class="sxs-lookup"><span data-stu-id="2ab43-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="2ab43-107">Для операторов наборов обычно требуется определить, являются ли равными значения элементов, а не ссылки на элементы.</span><span class="sxs-lookup"><span data-stu-id="2ab43-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="2ab43-108">Поэтому в <xref:System.Data.DataRowComparer> был добавлен класс [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2ab43-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="2ab43-109">Этот класс можно использовать для сравнения значений в строках.</span><span class="sxs-lookup"><span data-stu-id="2ab43-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="2ab43-110">Класс <xref:System.Data.DataRowComparer> содержит реализацию сравнения значений для объектов <xref:System.Data.DataRow>, поэтому его можно использовать в операциях над наборами, таких как <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="2ab43-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="2ab43-111">Этот класс нельзя создать напрямую, вместо этого необходимо использовать свойство <xref:System.Data.DataRowComparer.Default%2A> для возврата экземпляра <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="2ab43-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="2ab43-112">Затем вызывается метод <xref:System.Data.DataRowComparer%601.Equals%2A>, которому в качестве входных параметров передаются два сравниваемых объекта <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="2ab43-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="2ab43-113">Метод <xref:System.Data.DataRowComparer%601.Equals%2A> возвращает значение `true`, если упорядоченные наборы значений столбцов в обоих объектах <xref:System.Data.DataRow> равны, в противном случае значение `false`.</span><span class="sxs-lookup"><span data-stu-id="2ab43-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ab43-114">Пример</span><span class="sxs-lookup"><span data-stu-id="2ab43-114">Example</span></span>  
 <span data-ttu-id="2ab43-115">В этом примере инструкция `Intersect` используется для возврата контактов, находящихся в обеих таблицах.</span><span class="sxs-lookup"><span data-stu-id="2ab43-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="2ab43-116">Пример</span><span class="sxs-lookup"><span data-stu-id="2ab43-116">Example</span></span>  
 <span data-ttu-id="2ab43-117">В следующем примере сравниваются две строки и возвращаются их хэш-коды.</span><span class="sxs-lookup"><span data-stu-id="2ab43-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="2ab43-118">См. также</span><span class="sxs-lookup"><span data-stu-id="2ab43-118">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="2ab43-119">Загрузка данных в DataSet</span><span class="sxs-lookup"><span data-stu-id="2ab43-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="2ab43-120">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="2ab43-120">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
