---
title: Практическое руководство. Сортировка или фильтрация текстовых данных по любому слову или полю (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: 305733ccf249f1a2c2608a5bd01d74ba2b1e1b86
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585787"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="5e3af-102">Практическое руководство. Сортировка или фильтрация текстовых данных по любому слову или полю (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5e3af-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>
<span data-ttu-id="5e3af-103">В следующем примере демонстрируется сортировка строк структурированного текста, таких как значения, разделенные запятыми, по любому полю в строке.</span><span class="sxs-lookup"><span data-stu-id="5e3af-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="5e3af-104">Поле можно указывать в среде выполнения динамически.</span><span class="sxs-lookup"><span data-stu-id="5e3af-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="5e3af-105">Допустим, поля в файле scores.csv содержат идентификационные номера учащихся и баллы, которые они набрали в результате четырех тестов.</span><span class="sxs-lookup"><span data-stu-id="5e3af-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="5e3af-106">Создание файла с данными</span><span class="sxs-lookup"><span data-stu-id="5e3af-106">To create a file that contains data</span></span>  
  
1. <span data-ttu-id="5e3af-107">Скопируйте данные из файла scores.csv (см. раздел [Практическое руководство. Объединение содержимого из файлов разных форматов (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)) в папку решения.</span><span class="sxs-lookup"><span data-stu-id="5e3af-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e3af-108">Пример</span><span class="sxs-lookup"><span data-stu-id="5e3af-108">Example</span></span>  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 <span data-ttu-id="5e3af-109">Это пример показывает также, как вернуть переменную запроса из метода.</span><span class="sxs-lookup"><span data-stu-id="5e3af-109">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e3af-110">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="5e3af-110">Compiling the Code</span></span>  

<span data-ttu-id="5e3af-111">Создайте проект консольного приложения C# с директивами `using` для пространств имен System.Linq и System.IO.</span><span class="sxs-lookup"><span data-stu-id="5e3af-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5e3af-112">См. также</span><span class="sxs-lookup"><span data-stu-id="5e3af-112">See also</span></span>

- [<span data-ttu-id="5e3af-113">LINQ и строки (C#)</span><span class="sxs-lookup"><span data-stu-id="5e3af-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
