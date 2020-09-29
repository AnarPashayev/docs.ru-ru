---
title: Разделение файла на несколько файлов с помощью групп (LINQ) (C#)
description: Узнайте, как разделить файл на несколько файлов с помощью групп. Изучите пример кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 07/20/2015
ms.assetid: 8179b91c-d778-4e57-884f-77fe5a8e4e40
ms.openlocfilehash: b7be01be0f1539eb6ed4f4857af2625672319493
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203934"
---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-c"></a>Разделение файла на несколько файлов с помощью групп (LINQ) (C#)

В этом примере показан один из способов объединения содержимого двух файлов и последующего создания набора новых файлов, данные в котором будут организованы иначе.  
  
### <a name="to-create-the-data-files"></a>Создание файлов данных  
  
1. Скопируйте эти имена в текстовый файл с именем names1.txt и сохраните его в папке проекта:  
  
    ```text  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2. Скопируйте эти имена в текстовый файл с именем names2.txt и сохраните его в папке проекта. Обратите внимание на то, что имена этих двух файлов похожи.  
  
    ```text  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a>Пример  
  
```csharp  
class SplitWithGroups  
{  
    static void Main()  
    {  
        string[] fileA = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] fileB = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Concatenate and remove duplicate names based on  
        // default string comparer  
        var mergeQuery = fileA.Union(fileB);  
  
        // Group the names by the first letter in the last name.  
        var groupQuery = from name in mergeQuery  
                         let n = name.Split(',')  
                         group name by n[0][0] into g  
                         orderby g.Key  
                         select g;  
  
        // Create a new file for each group that was created  
        // Note that nested foreach loops are required to access  
        // individual items with each group.  
        foreach (var g in groupQuery)  
        {  
            // Create the new file name.  
            string fileName = @"../../../testFile_" + g.Key + ".txt";  
  
            // Output to display.  
            Console.WriteLine(g.Key);  
  
            // Write file.  
            using (System.IO.StreamWriter sw = new System.IO.StreamWriter(fileName))  
            {  
                foreach (var item in g)  
                {  
                    sw.WriteLine(item);  
                    // Output to console for example purposes.  
                    Console.WriteLine("   {0}", item);  
                }  
            }  
        }  
        // Keep console window open in debug mode.  
        Console.WriteLine("Files have been written. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:
    A  
       Aw, Kam Foo  
    B  
       Bankov, Peter  
       Beebe, Ann  
    E  
       El Yassir, Mehdi  
    G  
       Garcia, Hugo  
       Guy, Wey Yuan  
       Garcia, Debra  
       Gilchrist, Beth  
       Giakoumakis, Leo  
    H  
       Holm, Michael  
    L  
       Liu, Jinghao  
    M  
       Myrcha, Jacek  
       McLin, Nkenge  
    N  
       Noriega, Fabricio  
    P  
       Potra, Cristina  
    T  
       Toyoshima, Tim  
 */  
```  
  
 Программа записывает отдельный файл для каждой группы в ту же папку, где находятся файлы данных.  
  
## <a name="compiling-the-code"></a>Компиляция кода

Создайте проект консольного приложения C# с директивами `using` для пространств имен System.Linq и System.IO.
  
## <a name="see-also"></a>См. также

- [LINQ и строки (C#)](./linq-and-strings.md)
- [LINQ и каталоги файлов (C#)](./linq-and-file-directories.md)
