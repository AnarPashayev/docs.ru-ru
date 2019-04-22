---
title: Практическое руководство. Число вхождений слова в строке (LINQ) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: b3d34503e87aff1180dca4cb8233d668d35b0255
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820325"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="9462b-102">Практическое руководство. Число вхождений слова в строке (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9462b-102">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="9462b-103">В этом примере показано, как с помощью запроса LINQ определить, сколько раз то или иное слово встречается в строке.</span><span class="sxs-lookup"><span data-stu-id="9462b-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="9462b-104">Обратите внимание на то, что для этого сначала вызывается метод <xref:System.String.Split%2A>, который создает массив слов.</span><span class="sxs-lookup"><span data-stu-id="9462b-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="9462b-105">Использование метода <xref:System.String.Split%2A> связано с определенным снижением производительности.</span><span class="sxs-lookup"><span data-stu-id="9462b-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="9462b-106">Если для строки выполняется только подсчет слов, рекомендуется вместо него использовать метод <xref:System.Text.RegularExpressions.Regex.Matches%2A> или <xref:System.String.IndexOf%2A>.</span><span class="sxs-lookup"><span data-stu-id="9462b-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="9462b-107">Если же производительность не критична или вы уже разбили предложение, чтобы выполнить с ним другие типы запросов, имеет смысл подсчитать слова или фразы с помощью LINQ.</span><span class="sxs-lookup"><span data-stu-id="9462b-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9462b-108">Пример</span><span class="sxs-lookup"><span data-stu-id="9462b-108">Example</span></span>  
  
```vb  
Class CountWords  
  
    Shared Sub Main()  
  
        Dim text As String = "Historically, the world of data and the world of objects" &   
                  " have not been well integrated. Programmers work in C# or Visual Basic" &   
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &   
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &   
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &   
                  " them. Data types often require translation between the two worlds; there are" &   
                  " different standard functions. Because the object world has no notion of query, a" &   
                  " query can only be represented as a string without compile-time type checking or" &   
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &   
                  " objects in memory is often tedious and error-prone."  
  
        Dim searchTerm As String = "data"  
  
        ' Convert the string into an array of words.  
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                 StringSplitOptions.RemoveEmptyEntries)  
  
        ' Create and execute the query. It executes immediately   
        ' because a singleton value is produced.  
        ' Use ToLower to match "data" and "Data"   
        Dim matchQuery = From word In dataSource   
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()   
                      Select word  
  
        ' Count the matches.  
        Dim count As Integer = matchQuery.Count()  
        Console.WriteLine(count & " occurrence(s) of the search term """ &   
                          searchTerm & """ were found.")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 3 occurrence(s) of the search term "data" were found.  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9462b-109">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="9462b-109">Compiling the Code</span></span>  
 <span data-ttu-id="9462b-110">Создайте проект, предназначенный для .NET Framework 3.5 или более поздней версии, со ссылкой на библиотеку System.Core.dll и директивой `Imports` для пространства имен System.Linq.</span><span class="sxs-lookup"><span data-stu-id="9462b-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9462b-111">См. также</span><span class="sxs-lookup"><span data-stu-id="9462b-111">See also</span></span>

- [<span data-ttu-id="9462b-112">LINQ и строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9462b-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
