---
title: Как запросить предложения с указанным набором слов (LINQ) (C#)
description: Узнайте, как использовать LINQ в C# для поиска в текстовом файле предложений, содержащих совпадения для каждого набора слов, который может быть заполнен во время выполнения.
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: c334c7948f19fb857709ff04a83e1dae56fc69da
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104521"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="3d0fd-103">Как запросить предложения с указанным набором слов (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3d0fd-103">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>
<span data-ttu-id="3d0fd-104">В этом примере показан поиск предложений, содержащих совпадения для каждого из указанного набора слов в текстовом файле.</span><span class="sxs-lookup"><span data-stu-id="3d0fd-104">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="3d0fd-105">Хотя массив терминов для поиска в этом примере жестко закодирован, его можно заполнять динамически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="3d0fd-105">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="3d0fd-106">В этом примере запрос возвращает предложения, которые содержат слова "Historically", "data" и "integrated".</span><span class="sxs-lookup"><span data-stu-id="3d0fd-106">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d0fd-107">Пример</span><span class="sxs-lookup"><span data-stu-id="3d0fd-107">Example</span></span>  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET Framework APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 <span data-ttu-id="3d0fd-108">Запрос сначала разделяет текст на предложения, а затем разделяет предложения на массив строк, содержащих слова.</span><span class="sxs-lookup"><span data-stu-id="3d0fd-108">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="3d0fd-109">Для каждого из этих массивов метод <xref:System.Linq.Enumerable.Distinct%2A> удаляет все повторяющиеся слова, после чего выполняет операцию <xref:System.Linq.Enumerable.Intersect%2A> в отношении массива слов и массива `wordsToMatch`.</span><span class="sxs-lookup"><span data-stu-id="3d0fd-109">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="3d0fd-110">Если число пересечений совпадает с размером массива `wordsToMatch`, все слова были найдены и возвращается исходное предложение.</span><span class="sxs-lookup"><span data-stu-id="3d0fd-110">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="3d0fd-111">В вызове <xref:System.String.Split%2A> знаки пунктуации используются как разделители для того, чтобы удалить их из строки.</span><span class="sxs-lookup"><span data-stu-id="3d0fd-111">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="3d0fd-112">Если этого не сделать, то, например, можно получить строку "Historically," которая не будет совпадать с "Historically" в массиве `wordsToMatch`.</span><span class="sxs-lookup"><span data-stu-id="3d0fd-112">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="3d0fd-113">В зависимости от знаков препинания в исходном тексте может потребоваться использовать дополнительные разделители.</span><span class="sxs-lookup"><span data-stu-id="3d0fd-113">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3d0fd-114">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="3d0fd-114">Compiling the Code</span></span>  
<span data-ttu-id="3d0fd-115">Создайте проект консольного приложения C# с директивами `using` для пространств имен System.Linq и System.IO.</span><span class="sxs-lookup"><span data-stu-id="3d0fd-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d0fd-116">См. также</span><span class="sxs-lookup"><span data-stu-id="3d0fd-116">See also</span></span>

- [<span data-ttu-id="3d0fd-117">LINQ и строки (C#)</span><span class="sxs-lookup"><span data-stu-id="3d0fd-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
