---
title: Практическое руководство. Группировать файлы по расширению (LINQ) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: f36be784641d45aaae447097ae2bebb5fd650034
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593479"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="c3844-102">Практическое руководство. Группировать файлы по расширению (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3844-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="c3844-103">В этом примере показано, как можно использовать LINQ для выполнения расширенного группирования и сортировки списков файлов или папок.</span><span class="sxs-lookup"><span data-stu-id="c3844-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="c3844-104">Кроме того, здесь показывается, как разбить на страницы выходные данные в окне консоли с помощью методов <xref:System.Linq.Enumerable.Skip%2A> и <xref:System.Linq.Enumerable.Take%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3844-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3844-105">Пример</span><span class="sxs-lookup"><span data-stu-id="c3844-105">Example</span></span>  
 <span data-ttu-id="c3844-106">Следующий запрос демонстрирует группирование содержимого указанного дерева каталогов по расширению файла.</span><span class="sxs-lookup"><span data-stu-id="c3844-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of   
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
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
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
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
  
 <span data-ttu-id="c3844-107">Вывод этой программы может быть длинным в зависимости от объема данных локальной файловой системы и значения `startFolder`.</span><span class="sxs-lookup"><span data-stu-id="c3844-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="c3844-108">В этом примере демонстрируется постраничный просмотр, который позволяет просматривать все результаты.</span><span class="sxs-lookup"><span data-stu-id="c3844-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="c3844-109">Те же методы могут применяться для приложений Windows и веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="c3844-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="c3844-110">Обратите внимание, что поскольку код разбивает элементы в группе на страницы, требуется вложенный цикл `For Each`.</span><span class="sxs-lookup"><span data-stu-id="c3844-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="c3844-111">Также существует некоторая дополнительная логика для вычисления текущей позиции в списке и предоставления пользователю возможности остановить разбиение по страницам и выйти из программы.</span><span class="sxs-lookup"><span data-stu-id="c3844-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="c3844-112">В данном конкретном случае запрос разбиения на страницы выполняется для кэшированных результатов исходного запроса.</span><span class="sxs-lookup"><span data-stu-id="c3844-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="c3844-113">В других контекстах, например LINQ to SQL, подобное кэширование не требуется.</span><span class="sxs-lookup"><span data-stu-id="c3844-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c3844-114">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="c3844-114">Compiling the Code</span></span>  
<span data-ttu-id="c3844-115">Создайте проект консольного приложения VB.NET, с помощью `Imports` оператор для пространства имен System.Linq.</span><span class="sxs-lookup"><span data-stu-id="c3844-115">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c3844-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c3844-116">See also</span></span>

- [<span data-ttu-id="c3844-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3844-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="c3844-118">LINQ и каталоги файлов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3844-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
