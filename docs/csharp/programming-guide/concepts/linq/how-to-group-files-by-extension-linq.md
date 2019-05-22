---
title: Практическое руководство. Группировка файлов по расширению (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: 0b8cb30396a93f5f878c091c4aad3cab9db3f2d4
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584297"
---
# <a name="how-to-group-files-by-extension-linq-c"></a><span data-ttu-id="7c6f5-102">Практическое руководство. Группировка файлов по расширению (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7c6f5-102">How to: Group Files by Extension (LINQ) (C#)</span></span>
<span data-ttu-id="7c6f5-103">В этом примере показано, как можно использовать LINQ для выполнения расширенного группирования и сортировки списков файлов или папок.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="7c6f5-104">Кроме того, здесь показывается, как разбить на страницы выходные данные в окне консоли с помощью методов <xref:System.Linq.Enumerable.Skip%2A> и <xref:System.Linq.Enumerable.Take%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c6f5-105">Пример</span><span class="sxs-lookup"><span data-stu-id="7c6f5-105">Example</span></span>  
 <span data-ttu-id="7c6f5-106">Следующий запрос демонстрирует группирование содержимого указанного дерева каталогов по расширению файла.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of   
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="7c6f5-107">Вывод этой программы может быть длинным в зависимости от объема данных локальной файловой системы и значения `startFolder`.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="7c6f5-108">В этом примере демонстрируется постраничный просмотр, который позволяет просматривать все результаты.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="7c6f5-109">Те же методы могут применяться для приложений Windows и веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="7c6f5-110">Обратите внимание, что поскольку код разбивает элементы в группе на страницы, требуется вложенный цикл `foreach`.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-110">Notice that because the code pages the items in a group, a nested `foreach` loop is required.</span></span> <span data-ttu-id="7c6f5-111">Также существует некоторая дополнительная логика для вычисления текущей позиции в списке и предоставления пользователю возможности остановить разбиение по страницам и выйти из программы.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="7c6f5-112">В данном конкретном случае запрос разбиения на страницы выполняется для кэшированных результатов исходного запроса.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="7c6f5-113">В других контекстах, например LINQ to SQL, подобное кэширование не требуется.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c6f5-114">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="7c6f5-114">Compiling the Code</span></span>  
 <span data-ttu-id="7c6f5-115">Создайте проект консольного приложения C# с директивами `using` для пространств имен System.Linq и System.IO.</span><span class="sxs-lookup"><span data-stu-id="7c6f5-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c6f5-116">См. также</span><span class="sxs-lookup"><span data-stu-id="7c6f5-116">See also</span></span>

- [<span data-ttu-id="7c6f5-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="7c6f5-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="7c6f5-118">LINQ и каталоги файлов (C#)</span><span class="sxs-lookup"><span data-stu-id="7c6f5-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
