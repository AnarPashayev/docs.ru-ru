---
title: Примеры синтаксиса выражений запросов. Проекция (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: 3bd7934cef03df391c1871b8499f911a023d7d3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097594"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="1363c-102">Примеры синтаксиса выражений запросов. Проекция (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="1363c-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="1363c-103">Примеры в данном разделе демонстрируют, как использовать методы <xref:System.Linq.Enumerable.Select%2A> и <xref:System.Linq.Enumerable.SelectMany%2A> для запроса к <xref:System.Data.DataSet> с использованием синтаксиса выражений запросов.</span><span class="sxs-lookup"><span data-stu-id="1363c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="1363c-104">`FillDataSet` Метод, используемый в этих примерах указывается в [загрузка данных в DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="1363c-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="1363c-105">В примерах данного раздела используются таблицы Contact, Address, Product, SalesOrderHeader и SalesOrderDetail из образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1363c-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1363c-106">В примерах в этом разделе используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="1363c-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="1363c-107">Дополнительные сведения см. в разделе [Как Создание проектов LINQ to DataSet в Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1363c-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="1363c-108">Выбрать</span><span class="sxs-lookup"><span data-stu-id="1363c-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="1363c-109">Пример</span><span class="sxs-lookup"><span data-stu-id="1363c-109">Example</span></span>  
 <span data-ttu-id="1363c-110">В этом примере метод <xref:System.Linq.Enumerable.Select%2A> используется, чтобы вернуть все строки из таблицы `Product` и отобразить названия продуктов.</span><span class="sxs-lookup"><span data-stu-id="1363c-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="1363c-111">Пример</span><span class="sxs-lookup"><span data-stu-id="1363c-111">Example</span></span>  
 <span data-ttu-id="1363c-112">В этом примере метод <xref:System.Linq.Enumerable.Select%2A> используется для возврата последовательности, состоящей только из названий продуктов.</span><span class="sxs-lookup"><span data-stu-id="1363c-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="1363c-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="1363c-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="1363c-114">Пример</span><span class="sxs-lookup"><span data-stu-id="1363c-114">Example</span></span>  
 <span data-ttu-id="1363c-115">В этом примере инструкция `From …, …` (эквивалент метода <xref:System.Linq.Enumerable.SelectMany%2A>) используется для выбора всех заказов, в которых `TotalDue` составляет менее 500,00.</span><span class="sxs-lookup"><span data-stu-id="1363c-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="1363c-116">Пример</span><span class="sxs-lookup"><span data-stu-id="1363c-116">Example</span></span>  
 <span data-ttu-id="1363c-117">В этом примере инструкция `From …, …` (эквивалент метода <xref:System.Linq.Enumerable.SelectMany%2A>) используется для выбора всех заказов, сделанных 1 октября 2002 года или позднее.</span><span class="sxs-lookup"><span data-stu-id="1363c-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="1363c-118">Пример</span><span class="sxs-lookup"><span data-stu-id="1363c-118">Example</span></span>  
 <span data-ttu-id="1363c-119">В этом примере инструкция `From …, …` (эквивалент метода <xref:System.Linq.Enumerable.SelectMany%2A>) используется для выбора всех заказов, в которых общий объем продаж составляет более 10 000,00, а ключевое слово `From` применяется, чтобы исключить повторный запрос общего объема.</span><span class="sxs-lookup"><span data-stu-id="1363c-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="1363c-120">См. также</span><span class="sxs-lookup"><span data-stu-id="1363c-120">See also</span></span>

- [<span data-ttu-id="1363c-121">Загрузка данных в DataSet</span><span class="sxs-lookup"><span data-stu-id="1363c-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="1363c-122">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1363c-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="1363c-123">Общие сведения о стандартных операторах запроса (C#)</span><span class="sxs-lookup"><span data-stu-id="1363c-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="1363c-124">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1363c-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
