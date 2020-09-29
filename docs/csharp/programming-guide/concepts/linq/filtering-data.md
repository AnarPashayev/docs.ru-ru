---
title: Фильтрация данных (C#)
description: Фильтрация, также известная как выборка, позволяет ограничивать результаты на основе условия. Узнайте о методах стандартных операторов запросов в LINQ в C#, которые выполняют фильтрацию.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 51bf9f930ba67ba07c7c0f357910d5e36014138d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186046"
---
# <a name="filtering-data-c"></a>Фильтрация данных (C#)

Фильтрация — это операция по ограничению значений в результирующем наборе только элементами, соответствующими указанному условию. Это также называется выборкой.  
  
 На следующем рисунке показаны результаты операции фильтрации последовательности символов. Предикат для операции фильтрации указывает, что символ должен быть "A".  
  
 ![Схема, иллюстрирующая операцию фильтрации LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 Методы стандартных операторов запросов, которые выполняют выборку, перечислены в следующем разделе.  
  
## <a name="methods"></a>Методы  
  
|Имя метода|Описание|Синтаксис выражения запроса C#|Дополнительные сведения|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|Выбирает значения в зависимости от возможности приведения их к указанному типу.|Не применяется|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|Where|Выбирает значения, основанные на функции предиката.|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Пример синтаксиса выражения запроса  

 В следующем примере для выбора из массива строк, имеющих определенную длину, используется предложение `where`.  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Linq>
- [Общие сведения о стандартных операторах запроса (C#)](./standard-query-operators-overview.md)
- [предложение where](../../../language-reference/keywords/where-clause.md)
- [Динамическое определение фильтров предикатов во время выполнения](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Практическое руководство. Выполнение запроса к метаданным сборки при помощи отражения (LINQ) (C#)](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [Практическое руководство. Запрос файлов с указанными атрибутами или именем (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [Практическое руководство. Сортировка или фильтрация текстовых данных по любому слову или полю (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
