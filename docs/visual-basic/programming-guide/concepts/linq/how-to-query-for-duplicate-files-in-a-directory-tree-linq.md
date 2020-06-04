---
title: Практическое руководство. Запрос повторяющихся файлов в дереве папок (LINQ)
ms.date: 07/20/2015
ms.assetid: 387d7c97-95dd-4a50-9761-7e9cf8ae9e6a
ms.openlocfilehash: b37da0a26c8bb4abc885faa7bb0c467e2d7d2347
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396432"
---
# <a name="how-to-query-for-duplicate-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="870da-102">Как запросить дубликаты файлов в дереве каталогов (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="870da-102">How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="870da-103">Иногда файлы с одинаковыми именами могут находиться в нескольких папках.</span><span class="sxs-lookup"><span data-stu-id="870da-103">Sometimes files that have the same name may be located in more than one folder.</span></span> <span data-ttu-id="870da-104">Например, в папке установки Visual Studio несколько папок содержат файл readme.htm.</span><span class="sxs-lookup"><span data-stu-id="870da-104">For example, under the Visual Studio installation folder, several folders have a readme.htm file.</span></span> <span data-ttu-id="870da-105">В этом примере показано, как запросить такие повторяющиеся имена файлов в указанной корневой папке.</span><span class="sxs-lookup"><span data-stu-id="870da-105">This example shows how to query for such duplicate file names under a specified root folder.</span></span> <span data-ttu-id="870da-106">Во втором примере показано, как запросить файлы, размер и время создания которых также совпадают.</span><span class="sxs-lookup"><span data-stu-id="870da-106">The second example shows how to query for files whose size and creation times also match.</span></span>  
  
## <a name="example"></a><span data-ttu-id="870da-107">Пример</span><span class="sxs-lookup"><span data-stu-id="870da-107">Example</span></span>  
  
```vb  
Module QueryDuplicateFileNames  
  
    Public Sub Main()  
  
        Dim path As String = "C:\Program Files\Microsoft Visual Studio 9.0\Common7"  
        QueryDuplicates1(path)  
        ' Uncomment to run this query instead  
        ' QueryDuplicates2(path)  
  
    End Sub  
    Sub QueryDuplicates1(ByVal root As String)  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim duplicates = From aFile In dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories) _  
                                 Order By aFile.Name _  
                                 Group aFile By aFile.Name Into newGroup = Group _  
                                 Where newGroup.Count() >= 2 _  
                                 Select newGroup  
  
        ' Page the display so that the results can be read.  
        Dim trimLength = root.Length  
        PageOutput(duplicates, trimLength)  
  
    End Sub  
    Sub QueryDuplicates2(ByVal root As String)  
  
        ' This time a composite key is used. This sub finds all files  
        ' that have been copied into multiple subfolders.  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim duplicates = From aFile In Dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories) _  
                                 Order By aFile.Name _  
                                 Group aFile By aFile.Name, aFile.CreationTime, aFile.Length Into newGroup = Group _  
                                 Where newGroup.Count() >= 2 _  
                                 Select newGroup  
  
        ' Page the display so that the results can be read.  
        Dim trimLength = root.Length  
        PageOutput(duplicates, trimLength)  
  
    End Sub  
    ' Pages console display for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to display  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the paths in the output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="870da-108">В первом запросе используется простой ключ для определения соответствия; при этом выполняется поиск файлов, которые имеют то же имя, однако их содержимое может быть другим.</span><span class="sxs-lookup"><span data-stu-id="870da-108">The first query uses a simple key to determine a match; this finds files that have the same name but whose contents might be different.</span></span> <span data-ttu-id="870da-109">Второй запрос использует составной ключ для сравнения трех свойств объекта <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="870da-109">The second query uses a compound key to match against three properties of the <xref:System.IO.FileInfo> object.</span></span> <span data-ttu-id="870da-110">Этот запрос дает гораздо больше шансов найти файлы, имеющие одинаковые имена и схожее или идентичное содержимое.</span><span class="sxs-lookup"><span data-stu-id="870da-110">This query is much more likely to find files that have the same name and similar or identical content.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="870da-111">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="870da-111">Compile the code</span></span>  
<span data-ttu-id="870da-112">Создайте проект консольного приложения Visual Basic с `Imports` инструкцией для пространства имен System. LINQ.</span><span class="sxs-lookup"><span data-stu-id="870da-112">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="870da-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="870da-113">See also</span></span>

- [<span data-ttu-id="870da-114">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="870da-114">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="870da-115">LINQ и каталоги файлов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="870da-115">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
