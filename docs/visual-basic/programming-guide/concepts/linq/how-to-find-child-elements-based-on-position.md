---
title: Практическое руководство. Поиск дочерних элементов по положению (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: d6dd1150ae3e4ad586e476b777b1f7d47d60c261
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405265"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="8e834-102">Пошаговое руководство. Поиск дочерних элементов по положению (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e834-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8e834-103">Иногда требуется найти элементы на основании их позиции.</span><span class="sxs-lookup"><span data-stu-id="8e834-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="8e834-104">Может понадобиться найти второй элемент или найти третий элемент через пятый.</span><span class="sxs-lookup"><span data-stu-id="8e834-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="8e834-105">Выражение XPath:</span><span class="sxs-lookup"><span data-stu-id="8e834-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="8e834-106">Существует два простых подхода к написанию этого запроса [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e834-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="8e834-107">Можно использовать операторы <xref:System.Linq.Enumerable.Skip%2A> и <xref:System.Linq.Enumerable.Take%2A> или перегруженный оператор <xref:System.Linq.Enumerable.Where%2A>, который потребляет индекс.</span><span class="sxs-lookup"><span data-stu-id="8e834-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="8e834-108">При использовании перегрузки оператора <xref:System.Linq.Enumerable.Where%2A> необходимо использовать лямбда-выражение, которое имеет два аргумента.</span><span class="sxs-lookup"><span data-stu-id="8e834-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="8e834-109">Следующий пример показывает обе возможности выбора на основе позиции.</span><span class="sxs-lookup"><span data-stu-id="8e834-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e834-110">Пример</span><span class="sxs-lookup"><span data-stu-id="8e834-110">Example</span></span>  
 <span data-ttu-id="8e834-111">В данном примере производится поиск второго элемента через четвертый элемент `Test`.</span><span class="sxs-lookup"><span data-stu-id="8e834-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="8e834-112">Результатом является коллекция элементов.</span><span class="sxs-lookup"><span data-stu-id="8e834-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="8e834-113">В этом примере используется следующий XML-документ: [Пример XML-файла. Конфигурация тестирования (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8e834-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim testCfg As XElement = XElement.Load("TestConfig.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test").Skip(1).Take(3)  
  
'LINQ to XML query  
Dim list2 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test"). _  
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)  
  
' XPath expression  
Dim list3 As IEnumerable(Of XElement) = _  
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")  
  
If list1.Count() = list2.Count() And _  
       list1.Count() = list3.Count() And _  
       list1.Intersect(list2).Count() = list1.Count() And _  
       list1.Intersect(list3).Count() = list1.Count() Then  
  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="8e834-114">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="8e834-114">This example produces the following output:</span></span>  
  
```console  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e834-115">См. также</span><span class="sxs-lookup"><span data-stu-id="8e834-115">See also</span></span>

- [<span data-ttu-id="8e834-116">LINQ to XML для пользователей XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e834-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
