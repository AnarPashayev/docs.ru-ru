---
title: Операции агрегирования (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 72268e27fdf6d573279e98438fd884a076e0c8a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669035"
---
# <a name="aggregation-operations-visual-basic"></a>Операции агрегирования (Visual Basic)
Статистическая операция вычисляет одно значение по коллекции значений. Например, статистической обработкой является вычисление средней дневной температуры с использованием значений дневной температуры за месяц.  
  
 На приведенном ниже рисунке показаны результаты двух различных операций агрегирования с последовательностью чисел. Первая операция суммирует числа. Вторая операция возвращает максимальное значение в последовательности.  
  
 ![Рисунок, показывающий операции агрегирования LINQ.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 В следующем разделе перечислены методы стандартных операторов запросов, которые выполняют операции агрегирования.  
  
## <a name="methods"></a>Методы  
  
|Имя метода|Описание|Синтаксис выражений запросов Visual Basic|Дополнительные сведения|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Статистическое выражение|Выполняет пользовательскую операцию агрегирования со значениями коллекции.|Неприменимо.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Метод Average|Вычисляет среднее значение коллекции значений.|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Количество|Подсчитывает число элементов в коллекции (при необходимости только те элементы, которые удовлетворяют функции предиката).|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Подсчитывает число элементов в большой коллекции (при необходимости только те элементы, которые удовлетворяют функции предиката).|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Максимум|Определяет максимальное значение в коллекции.|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Минимум|Определяет минимальное значение в коллекции.|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Sum|Вычисляет сумму значений в коллекции.|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Примеры синтаксиса выражений запросов  
  
### <a name="average"></a>Метод Average  
 В следующем примере кода используется `Aggregate Into Average` предложение в Visual Basic для вычисления средней температуры в массиве чисел, представляющих температуру.  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a>Количество  
 В следующем примере кода используется `Aggregate Into Count` предложение в Visual Basic для подсчета числа значений в массиве, не меньше 80.  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a>LongCount  
 В следующем примере кода используется `Aggregate Into LongCount` предложение для подсчета числа значений в массиве.  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a>Максимум  
 В следующем примере кода используется `Aggregate Into Max` предложение, для которого требуется вычислить высокой температуры в массиве чисел, представляющих температуру.  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a>Минимум  
 В следующем примере кода используется `Aggregate Into Min` предложение для вычисления минимального температуры в массиве чисел, представляющих температуру.  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a>Sum  
 В следующем примере кода используется `Aggregate Into Sum` предложение для вычисления общего расхода из массива значений, представляющих расходы.  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a>См. также

- <xref:System.Linq>
- [Общие сведения о стандартных операторах запроса (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Предложение Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Практическое руководство. Вычисление значений столбцов в текстовом CSV-файле (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Практическое руководство. Число, суммы или среднего значения данных](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [Практическое руководство. Поиск минимального или максимального значения в результатах запроса](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [Практическое руководство. Запрос для большого файла или файлов в дереве папок (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [Практическое руководство. Запрос общего числа байтов в наборе папок (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
