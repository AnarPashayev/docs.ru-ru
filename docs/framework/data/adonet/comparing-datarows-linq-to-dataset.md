---
title: Сравнение объектов DataRow (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 2b45a4629474c394c8e49c41a7a98fc1181e124b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077177"
---
# <a name="comparing-datarows-linq-to-dataset"></a>Сравнение объектов DataRow (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Определяет различные операторы работы с наборами для сравнения исходных элементов, чтобы увидеть, что они равны. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] предоставляет следующие операторы наборов:  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 Эти операторы сравнивают элементы путем вызова методов <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> и <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> для каждой коллекции элементов. Для объектов <xref:System.Data.DataRow> эти операторы выполняют ссылочное сравнение, которое в общем случае не является идеальным для операторов наборов, выполняющихся над табличными данными. Для операторов наборов обычно требуется определить, являются ли равными значения элементов, а не ссылки на элементы. Поэтому в <xref:System.Data.DataRowComparer> был добавлен класс [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Этот класс можно использовать для сравнения значений в строках.  
  
 Класс <xref:System.Data.DataRowComparer> содержит реализацию сравнения значений для объектов <xref:System.Data.DataRow>, поэтому его можно использовать в операциях над наборами, таких как <xref:System.Linq.Enumerable.Distinct%2A>. Этот класс нельзя создать напрямую, вместо этого необходимо использовать свойство <xref:System.Data.DataRowComparer.Default%2A> для возврата экземпляра <xref:System.Data.DataRowComparer%601>. Затем вызывается метод <xref:System.Data.DataRowComparer%601.Equals%2A>, которому в качестве входных параметров передаются два сравниваемых объекта <xref:System.Data.DataRow>. Метод <xref:System.Data.DataRowComparer%601.Equals%2A> возвращает значение `true`, если упорядоченные наборы значений столбцов в обоих объектах <xref:System.Data.DataRow> равны, в противном случае значение `false`.  
  
## <a name="example"></a>Пример  
 В этом примере инструкция `Intersect` используется для возврата контактов, находящихся в обеих таблицах.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Пример  
 В следующем примере сравниваются две строки и возвращаются их хэш-коды.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>См. также

- <xref:System.Data.DataRowComparer>
- [Загрузка данных в набор данных](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [Примеры LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
