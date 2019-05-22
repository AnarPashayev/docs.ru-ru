---
title: Практическое руководство. Руководство по программированию на C#. Возвращение подмножества свойств элементов в запросе
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: acff804d87d67bf8758b97ad04805359bb3f2e32
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586076"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="b7e94-102">Практическое руководство. Руководство по программированию на C#. Возвращение подмножества свойств элементов в запросе</span><span class="sxs-lookup"><span data-stu-id="b7e94-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="b7e94-103">Используйте анонимный тип в выражении запроса, если выполняются оба следующих условия:</span><span class="sxs-lookup"><span data-stu-id="b7e94-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="b7e94-104">требуется возвращать только некоторые свойства каждого исходного элемента;</span><span class="sxs-lookup"><span data-stu-id="b7e94-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="b7e94-105">не требуется хранить результаты запроса за пределами области метода, в котором выполняется запрос.</span><span class="sxs-lookup"><span data-stu-id="b7e94-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="b7e94-106">Если требуется возвращать только одно свойство или поле из каждого исходного элемента, вы можете использовать оператор "точка" в предложении `select`.</span><span class="sxs-lookup"><span data-stu-id="b7e94-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="b7e94-107">Например, чтобы вернуть только `ID` для каждого элемента `student`, напишите предложение `select` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b7e94-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="b7e94-108">Пример</span><span class="sxs-lookup"><span data-stu-id="b7e94-108">Example</span></span>  
 <span data-ttu-id="b7e94-109">В следующем примере показано, как использовать анонимный тип для возвращения только конкретного набора свойств каждого исходного элемента, соответствующего указанному условию.</span><span class="sxs-lookup"><span data-stu-id="b7e94-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="b7e94-110">Обратите внимание, что анонимный тип использует имена исходных элементов для соответствующих свойств, если имена не заданы.</span><span class="sxs-lookup"><span data-stu-id="b7e94-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="b7e94-111">Чтобы присваивать новые имена свойствам в анонимном типе, напишите инструкцию `select` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b7e94-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="b7e94-112">Если вы попробуете сделать это в предыдущем примере, также необходимо изменить инструкцию `Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="b7e94-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b7e94-113">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="b7e94-113">Compiling the Code</span></span>  
  
<span data-ttu-id="b7e94-114">Чтобы выполнить этот код, скопируйте и вставьте класс в консольное приложение C# с директивой `using` для пространства имен System.Linq.</span><span class="sxs-lookup"><span data-stu-id="b7e94-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b7e94-115">См. также</span><span class="sxs-lookup"><span data-stu-id="b7e94-115">See also</span></span>

- [<span data-ttu-id="b7e94-116">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="b7e94-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b7e94-117">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="b7e94-117">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="b7e94-118">Выражения запросов LINQ</span><span class="sxs-lookup"><span data-stu-id="b7e94-118">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
