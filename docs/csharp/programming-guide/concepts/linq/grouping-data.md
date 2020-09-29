---
title: Группирование данных (C#)
description: При группировании данные объединяются в группы элементов, имеющие общий атрибут. Узнайте о методах стандартных операторов запросов в LINQ в C#, которые группируют элементы данных.
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 584d50fc15dd8b4ce1cfdf4766f3bc8b8383eb12
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202569"
---
# <a name="grouping-data-c"></a>Группирование данных (C#)

Группированием называют операцию объединения данных в группы таким образом, чтобы у элементов в каждой группе был общий атрибут.  
  
 На следующем рисунке показаны результаты операции группирования последовательности символов. Ключ для каждой группы — это символ.  
  
 ![Схема, показывающая операцию группирования LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 Далее перечислены методы стандартных операторов запроса, которые группируют элементы данных.  
  
## <a name="methods"></a>Методы  
  
|Имя метода|Описание|Синтаксис выражения запроса C#|Дополнительные сведения|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|Группирует элементы с общим атрибутом. Каждая группа представлена объектом <xref:System.Linq.IGrouping%602>.|`group … by`<br /><br /> -или-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Вставляет элементы в <xref:System.Linq.Lookup%602> (словарь "один ко многим") в зависимости от функции выбора ключа.|Не применяется|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Пример синтаксиса выражения запроса  

 В следующем примере кода предложение `group by` используется для группирования целых чисел в списке на основании четности.  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a>См. также

- <xref:System.Linq>
- [Общие сведения о стандартных операторах запроса (C#)](./standard-query-operators-overview.md)
- [предложение group](../../../language-reference/keywords/group-clause.md)
- [Создание вложенной группы](../../../linq/create-a-nested-group.md)
- [Группировка файлов по расширению (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)
- [Группировка результатов запросов](../../../linq/group-query-results.md)
- [Вложенный запрос в операции группирования](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [Разделение файла на несколько файлов с помощью групп (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
