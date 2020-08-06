---
title: Преобразование формы дерева XML (C#)
description: Узнайте, как преобразовать форму дерева XML. Понятие "форма" применительно к дереву XML обозначает совокупность имен элементов, атрибутов и характеристик его иерархии.
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 4fa3cc18f235d061ae1778c177c4ac9b626f4b71
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302650"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="124ec-104">Преобразование формы дерева XML (C#)</span><span class="sxs-lookup"><span data-stu-id="124ec-104">How to transform the shape of an XML tree (C#)</span></span>
<span data-ttu-id="124ec-105">Понятие *форма* применительно к XML-документу обозначает совокупность имен элементов, атрибутов и характеристик его иерархии.</span><span class="sxs-lookup"><span data-stu-id="124ec-105">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="124ec-106">Иногда может потребоваться изменить форму XML-документа.</span><span class="sxs-lookup"><span data-stu-id="124ec-106">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="124ec-107">Например, может потребоваться передать существующий XML-документ в другую систему, которая использует другие названия элементов и атрибутов.</span><span class="sxs-lookup"><span data-stu-id="124ec-107">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="124ec-108">Можно пройти по документу, удаляя и переименовывая элементы согласно требованиям, однако использование результатов функциональных построений дает более читаемый код и просто код для обработки.</span><span class="sxs-lookup"><span data-stu-id="124ec-108">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="124ec-109">Дополнительные сведения о функциональном построении см. в разделе [Функциональное построение (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="124ec-109">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="124ec-110">В первом примере выполнится изменение организации всего XML-документа.</span><span class="sxs-lookup"><span data-stu-id="124ec-110">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="124ec-111">Происходит перемещение сложных элементов из одного места дерева в другое.</span><span class="sxs-lookup"><span data-stu-id="124ec-111">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="124ec-112">Во втором примере, приведенном в этом разделе, создается XML-документ, форма которого отлична от формы исходного документа.</span><span class="sxs-lookup"><span data-stu-id="124ec-112">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="124ec-113">Выполняется изменение тегов имен элементов, переименование некоторых элементов и опущение некоторых элементов, присутствующих в исходном дереве.</span><span class="sxs-lookup"><span data-stu-id="124ec-113">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="124ec-114">Пример</span><span class="sxs-lookup"><span data-stu-id="124ec-114">Example</span></span>  
 <span data-ttu-id="124ec-115">Следующий код позволяет изменить форму XML-файла при помощи внедренного выражения запроса.</span><span class="sxs-lookup"><span data-stu-id="124ec-115">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="124ec-116">Исходный XML-документ в этом примере содержит `Customers` элемент `Root`, в котором содержится список всех клиентов.</span><span class="sxs-lookup"><span data-stu-id="124ec-116">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="124ec-117">Он также содержит элемент `Orders` под элементом `Root`, который содержит все заказы.</span><span class="sxs-lookup"><span data-stu-id="124ec-117">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="124ec-118">В этом примере создается новое XML-дерево, в котором заказы каждого клиента содержатся в элементе `Orders`, который является дочерним по отношению к элементу `Customer`.</span><span class="sxs-lookup"><span data-stu-id="124ec-118">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="124ec-119">Оригинальный документ также содержит элемент `CustomerID` внутри элемента `Order`. Этот элемент будет удален из преобразованного документа.</span><span class="sxs-lookup"><span data-stu-id="124ec-119">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="124ec-120">В этом примере используется следующий XML-документ: [Пример XML-файла. Заказчики и заказы (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="124ec-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
XElement newCustOrd =  
    new XElement("Root",  
        from cust in co.Element("Customers").Elements("Customer")  
        select new XElement("Customer",  
            cust.Attributes(),  
            cust.Elements(),  
            new XElement("Orders",  
                from ord in co.Element("Orders").Elements("Order")  
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")  
                select new XElement("Order",  
                    ord.Attributes(),  
                    ord.Element("EmployeeID"),  
                    ord.Element("OrderDate"),  
                    ord.Element("RequiredDate"),  
                    ord.Element("ShipInfo")  
                )  
            )  
        )  
    );  
Console.WriteLine(newCustOrd);  
```  
  
 <span data-ttu-id="124ec-121">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="124ec-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <Fax>(503) 555-2376</Fax>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  . . .  
```  
  
## <a name="example"></a><span data-ttu-id="124ec-122">Пример</span><span class="sxs-lookup"><span data-stu-id="124ec-122">Example</span></span>  
 <span data-ttu-id="124ec-123">В этом примере выполняется переименование некоторых элементов и преобразование некоторых атрибутов в элементы.</span><span class="sxs-lookup"><span data-stu-id="124ec-123">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="124ec-124">Код вызывает `ConvertAddress`, который возвращает объекты <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="124ec-124">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="124ec-125">По отношению к методу аргументом является запрос, который определяет сложный элемент `Address`, в котором атрибут `Type` обладает значением `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="124ec-125">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="124ec-126">В этом примере используется следующий XML-документ: [Пример XML-файла. Типичный заказ на покупку (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="124ec-126">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
static IEnumerable<XElement> ConvertAddress(XElement add)  
{  
    List<XElement> fragment = new List<XElement>() {  
        new XElement("NAME", (string)add.Element("Name")),  
        new XElement("STREET", (string)add.Element("Street")),  
        new XElement("CITY", (string)add.Element("City")),  
        new XElement("ST", (string)add.Element("State")),  
        new XElement("POSTALCODE", (string)add.Element("Zip")),  
        new XElement("COUNTRY", (string)add.Element("Country"))  
    };  
    return fragment;  
}  
  
static void Main(string[] args)  
{  
    XElement po = XElement.Load("PurchaseOrder.xml");  
    XElement newPo = new XElement("PO",  
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),  
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),  
        ConvertAddress(  
            (from el in po.Elements("Address")  
            where (string)el.Attribute("Type") == "Shipping"  
            select el)  
            .First()  
        )  
    );  
    Console.WriteLine(newPo);  
}  
```  
  
 <span data-ttu-id="124ec-127">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="124ec-127">This code produces the following output:</span></span>  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
