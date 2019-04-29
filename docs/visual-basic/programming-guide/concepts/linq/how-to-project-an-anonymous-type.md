---
title: Практическое руководство. Проецирование анонимного типа (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
ms.openlocfilehash: cc8e59ac1037fc173cb44d8c8ff344374c5766ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644329"
---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="94bb8-102">Практическое руководство. Проецирование анонимного типа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94bb8-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="94bb8-103">В некоторых случаях может потребоваться проецировать запрос на новый тип, даже если известно, что этот тип будет использоваться недолго.</span><span class="sxs-lookup"><span data-stu-id="94bb8-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="94bb8-104">Создание нового типа для использования в проекции требует много дополнительной работы.</span><span class="sxs-lookup"><span data-stu-id="94bb8-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="94bb8-105">Гораздо более эффективный подход заключается в проецировании на анонимный тип.</span><span class="sxs-lookup"><span data-stu-id="94bb8-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="94bb8-106">Анонимные типы позволяют определять класс и инициализировать его объект, не присваивая имя этому классу.</span><span class="sxs-lookup"><span data-stu-id="94bb8-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="94bb8-107">Анонимные типы являются реализацией в языке C# математического понятия *кортежа*.</span><span class="sxs-lookup"><span data-stu-id="94bb8-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="94bb8-108">Математический термин «кортеж» обозначает одноэлементные, двухэлементные, трехэлементные, четырехэлементные, пятиэлементные и n-элементные последовательности.</span><span class="sxs-lookup"><span data-stu-id="94bb8-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="94bb8-109">Он относится к конечной последовательности объектов, каждый из которых имеет конкретный тип.</span><span class="sxs-lookup"><span data-stu-id="94bb8-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="94bb8-110">Иногда такую последовательность называют списком пар «имя/значение».</span><span class="sxs-lookup"><span data-stu-id="94bb8-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="94bb8-111">Например, содержимое адреса в XML-документе [Пример XML-файла. Типичный заказ на покупку (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) можно представить следующим образом:</span><span class="sxs-lookup"><span data-stu-id="94bb8-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="94bb8-112">Создание экземпляра анонимного типа удобно трактовать как создание n-элементного кортежа.</span><span class="sxs-lookup"><span data-stu-id="94bb8-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="94bb8-113">При написании запроса, создающего кортеж в предложении `Select`, запрос возвращает объект `IEnumerable` кортежа.</span><span class="sxs-lookup"><span data-stu-id="94bb8-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94bb8-114">Пример</span><span class="sxs-lookup"><span data-stu-id="94bb8-114">Example</span></span>  
 <span data-ttu-id="94bb8-115">В этом примере предложение `Select` проецирует анонимный тип.</span><span class="sxs-lookup"><span data-stu-id="94bb8-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="94bb8-116">Затем в этом примере используется тип `Dim` для создания объекта `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="94bb8-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="94bb8-117">В цикле `For Each` переменная итерации становится экземпляром анонимного типа, созданного в выражении запроса.</span><span class="sxs-lookup"><span data-stu-id="94bb8-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="94bb8-118">В этом примере используется следующий XML-документ: [Пример XML-файла. Заказчики и заказы (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="94bb8-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 <span data-ttu-id="94bb8-119">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="94bb8-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="94bb8-120">См. также</span><span class="sxs-lookup"><span data-stu-id="94bb8-120">See also</span></span>

- [<span data-ttu-id="94bb8-121">Проекции и преобразования (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94bb8-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
