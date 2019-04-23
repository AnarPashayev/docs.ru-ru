---
title: Практическое руководство. Изменение порядка полей файла с разделителями (LINQ) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: 6f41a8e38812cf9d3c652fa605febf2511f07a27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339090"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a><span data-ttu-id="3c31d-102">Практическое руководство. Изменение порядка полей файла с разделителями (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c31d-102">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="3c31d-103">CSV-файл — это текстовый файл, который часто используется для хранения данных электронных таблиц или других табличных данных, представленных строками и столбцами.</span><span class="sxs-lookup"><span data-stu-id="3c31d-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="3c31d-104">Использование метода <xref:System.String.Split%2A> для разделения полей упрощает создание запросов к CSV-файлам и управление ими с помощью LINQ.</span><span class="sxs-lookup"><span data-stu-id="3c31d-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="3c31d-105">Фактически та же технология может использоваться для изменения порядка частей любой структурированной строки текста, а не только CSV-файлов.</span><span class="sxs-lookup"><span data-stu-id="3c31d-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="3c31d-106">В следующем примере предполагается, что три столбца представляют "фамилию", "имя" и "идентификатор" учащихся.</span><span class="sxs-lookup"><span data-stu-id="3c31d-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="3c31d-107">Поля группируются в алфавитном порядке по фамилии учащихся.</span><span class="sxs-lookup"><span data-stu-id="3c31d-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="3c31d-108">Запрос создает новую последовательность, в которой столбец идентификатора отображается первым, за ним следует второй столбец, который объединяет имя и фамилию учащегося.</span><span class="sxs-lookup"><span data-stu-id="3c31d-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="3c31d-109">Порядок строк изменен в соответствии с полем идентификатора.</span><span class="sxs-lookup"><span data-stu-id="3c31d-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="3c31d-110">Результаты сохраняются в новый файл, и исходные данные не изменяются.</span><span class="sxs-lookup"><span data-stu-id="3c31d-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="3c31d-111">Создание файла данных</span><span class="sxs-lookup"><span data-stu-id="3c31d-111">To create the data file</span></span>  
  
1. <span data-ttu-id="3c31d-112">Скопируйте следующие строки в обычный текстовый файл с именем spreadsheet1.csv.</span><span class="sxs-lookup"><span data-stu-id="3c31d-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="3c31d-113">Сохраните файл в папке проекта.</span><span class="sxs-lookup"><span data-stu-id="3c31d-113">Save the file in your project folder.</span></span>  
  
    ```  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a><span data-ttu-id="3c31d-114">Пример</span><span class="sxs-lookup"><span data-stu-id="3c31d-114">Example</span></span>  
  
```vb  
Class CSVFiles  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data source.  
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")  
  
        ' Execute the query. Put field 2 first, then  
        ' reverse and combine fields 0 and 1 from the old field  
        Dim lineQuery = From line In lines   
                        Let x = line.Split(New Char() {","})   
                        Order By x(2)   
                        Select x(2) & ", " & (x(1) & " " & x(0))  
  
        ' Execute the query and write out the new file. Note that WriteAllLines  
        ' takes a string array, so ToArray is called on the query.  
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output to spreadsheet2.csv:  
' 111, Svetlana Omelchenko  
' 112, Claire O'Donnell  
' 113, Sven Mortensen  
' 114, Cesar Garcia  
' 115, Debra Garcia  
' 116, Fadi Fakhouri  
' 117, Hanying Feng  
' 118, Hugo Garcia  
' 119, Lance Tucker  
' 120, Terry Adams  
' 121, Eugene Zabokritski  
' 122, Michael Tucker  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3c31d-115">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="3c31d-115">Compiling the Code</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c31d-116">См. также</span><span class="sxs-lookup"><span data-stu-id="3c31d-116">See also</span></span>

- [<span data-ttu-id="3c31d-117">LINQ и строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c31d-117">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="3c31d-118">LINQ и каталоги файлов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c31d-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
- [<span data-ttu-id="3c31d-119">Практическое руководство. Создание XML из CSV-файлов</span><span class="sxs-lookup"><span data-stu-id="3c31d-119">How to: Generate XML from CSV Files</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)
