---
title: Операции с элементами (C#)
ms.date: 10/03/2018
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
ms.openlocfilehash: b32066d13e700d95e4d2eef29e24e8b87690037d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594572"
---
# <a name="element-operations-c"></a>Операции с элементами (C#)

Операции с элементами возвращают один определенный элемент из последовательности.  
  
 В следующем разделе перечислены методы стандартных операторов запросов, которые выполняют операции с элементами.  
  
## <a name="methods"></a>Методы  
  
|Имя метода|ОПИСАНИЕ|Синтаксис выражения запроса C#|Дополнительные сведения|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Возвращает элемент коллекции с указанным индексом.|Неприменимо.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|Возвращает элемент коллекции с указанным индексом или значение по умолчанию, если индекс выходит за пределы допустимого диапазона.|Неприменимо.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|First|Возвращает первый элемент коллекции или первый элемент, удовлетворяющий условию.|Неприменимо.|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|Возвращает первый элемент коллекции или первый элемент, удовлетворяющий условию. Если такой элемент не существует, возвращает значение по умолчанию.|Неприменимо.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|Последняя|Возвращает последний элемент коллекции или последний элемент, удовлетворяющий условию.|Неприменимо.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|Возвращает последний элемент коллекции или последний элемент, удовлетворяющий условию. Если такой элемент не существует, возвращает значение по умолчанию.|Неприменимо.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|Возвращает единственный элемент коллекции или единственный элемент, удовлетворяющий условию. Создает исключение <xref:System.InvalidOperationException>, если нет ни одного элемента для возврата или таких элементов несколько. |Неприменимо.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|Возвращает единственный элемент коллекции или единственный элемент, удовлетворяющий условию. Возвращает значение по умолчанию, если нет элементов для возврата. Создает исключение <xref:System.InvalidOperationException>, если существует несколько элементов для возврата. |Неприменимо.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>См. также

- <xref:System.Linq>
- [Общие сведения о стандартных операторах запроса (C#)](./standard-query-operators-overview.md)
- [Практическое руководство. Запрос самого большого файла или файлов в дереве папок (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
