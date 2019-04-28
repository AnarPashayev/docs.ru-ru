---
title: Практическое руководство. Объединение двух коллекций (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 85689fa756ab20a4dcd054b70eb3003c767936ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778057"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="1da35-102">Практическое руководство. Объединение двух коллекций (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1da35-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="1da35-103">Элемент или атрибут в XML-документе может иногда относиться к другому элементу или атрибуту.</span><span class="sxs-lookup"><span data-stu-id="1da35-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="1da35-104">Например, XML-документ из раздела [Пример XML-файла. Заказчики и заказы (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) содержит список заказчиков и список заказов.</span><span class="sxs-lookup"><span data-stu-id="1da35-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="1da35-105">Каждый элемент `Customer` содержит атрибут `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="1da35-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="1da35-106">Каждый элемент `Order` содержит элемент `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="1da35-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="1da35-107">Элемент `CustomerID` для каждого заказа ссылается на атрибут `CustomerID`, присвоенный также и клиенту.</span><span class="sxs-lookup"><span data-stu-id="1da35-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="1da35-108">Раздел [Пример XSD-файла. Заказчики и заказы](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) содержит XSD-файл, с помощью которого можно проверить этот документ.</span><span class="sxs-lookup"><span data-stu-id="1da35-108">The topic [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="1da35-109">Здесь используются функции XSD `xs:key` и `xs:keyref` для установления того, что атрибут `CustomerID` элемента `Customer` является ключом, а также для установления связи между элементом `CustomerID` каждого из элементов `Order` и атрибутом `CustomerID` каждого из элементов `Customer`.</span><span class="sxs-lookup"><span data-stu-id="1da35-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="1da35-110">В [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] можно воспользоваться преимуществами таких связей элементов и атрибутов при помощи предложения `Join`.</span><span class="sxs-lookup"><span data-stu-id="1da35-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="1da35-111">Обратите внимание, что, поскольку индекс недоступен, такое соединение будет сильно загружать среду.</span><span class="sxs-lookup"><span data-stu-id="1da35-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="1da35-112">Более подробные сведения о `Join`, см. в разделе [операции соединения (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="1da35-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1da35-113">Пример</span><span class="sxs-lookup"><span data-stu-id="1da35-113">Example</span></span>  
 <span data-ttu-id="1da35-114">В следующем примере выполняется соединение элементов `Customer` с элементами `Order` и создается новый XML-документ, который включает элемент `CompanyName` в заказы.</span><span class="sxs-lookup"><span data-stu-id="1da35-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="1da35-115">Перед выполнением запроса в примере выполняется проверка созданного документа по схеме, приведенной в разделе [Пример XSD-файла. Заказчики и заказы](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="1da35-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="1da35-116">Это позволяет обеспечить бесперебойную работу предложения соединения.</span><span class="sxs-lookup"><span data-stu-id="1da35-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="1da35-117">В этом запросе сначала выполняется получение всех элементов `Customer`, а затем присоединение их к элементам `Order`.</span><span class="sxs-lookup"><span data-stu-id="1da35-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="1da35-118">Он отбирает только заказы от клиентов со значением `CustomerID` больше «K».</span><span class="sxs-lookup"><span data-stu-id="1da35-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="1da35-119">После этого выполняется проецирование нового элемента `Order`, который содержит сведения о клиентах внутри каждого заказа.</span><span class="sxs-lookup"><span data-stu-id="1da35-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="1da35-120">В этом примере используется следующий XML-документ: [Пример XML-файла. Заказчики и заказы (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1da35-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="1da35-121">В этом примере используется следующая XSD-схема: [Пример XSD-файла. Заказчики и заказы](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="1da35-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="1da35-122">Обратите внимание, что такое соединение не будет работать оптимально.</span><span class="sxs-lookup"><span data-stu-id="1da35-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="1da35-123">Соединение осуществляется путем линейного поиска.</span><span class="sxs-lookup"><span data-stu-id="1da35-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="1da35-124">Не используются хэш-таблицы и индексы, которые могли бы помочь оптимизировать производительность.</span><span class="sxs-lookup"><span data-stu-id="1da35-124">There are no hash tables or indexes to help with performance.</span></span>  
  
```vb  
Public Class Program  
    Public Shared errors As Boolean = False  
  
    Public Shared Function LamValidEvent(ByVal o As Object, _  
                 ByVal e As ValidationEventArgs) As Boolean  
        Console.WriteLine("{0}", e.Message)  
        errors = True  
    End Function  
  
    Shared Sub Main()  
        Dim schemas As New XmlSchemaSet()  
        schemas.Add("", "CustomersOrders.xsd")  
  
        Console.Write("Attempting to validate, ")  
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
  
        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))  
        If errors Then  
            Console.WriteLine("custOrdDoc did not validate")  
        Else  
            Console.WriteLine("custOrdDoc validated")  
        End If  
  
        If Not errors Then  
            'Join customers and orders, and create a new XML document with  
            ' a different shape.  
            'The new document contains orders only for customers with a  
            ' CustomerID > 'K'.  
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault  
            Dim newCustOrd As XElement = _  
                <Root>  
                    <%= From c In custOrd.<Customers>.<Customer> _  
                        Join o In custOrd.<Orders>.<Order> _  
                        On c.@CustomerID Equals o.<CustomerID>.Value _  
                        Where c.@CustomerID.CompareTo("K") > 0 _  
                        Select _  
                        <Order>  
                            <CustomerID><%= c.@CustomerID %></CustomerID>  
                            <%= c.<CompanyName> %>  
                            <%= c.<ContactName> %>  
                            <%= o.<EmployeeID> %>  
                            <%= o.<OrderDate> %>  
                        </Order> _  
                    %>  
                </Root>  
            Console.WriteLine(newCustOrd)  
        End If  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="1da35-125">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="1da35-125">This code produces the following output:</span></span>  
  
```  
Attempting to validate, custOrdDoc validated  
<Root>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-03-21T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-05-22T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-06-25T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-10-27T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>6</EmployeeID>  
    <OrderDate>1997-11-10T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>4</EmployeeID>  
    <OrderDate>1998-02-12T00:00:00</OrderDate>  
  </Order>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1da35-126">См. также</span><span class="sxs-lookup"><span data-stu-id="1da35-126">See also</span></span>

- [<span data-ttu-id="1da35-127">Дополнительные способы создания запросов (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1da35-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
