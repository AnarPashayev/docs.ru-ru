---
title: Проверка с использованием XSD (LINQ to XML) (C#)
description: Узнайте, как проверить XML-дерево по XSD-файлу. Изучите примеры кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 3b4d2137d511efbe20e4d31ad27e4975d5444ec9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302637"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="9d7a3-104">Проверка с использованием XSD (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9d7a3-104">How to validate using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9d7a3-105">Пространство имен <xref:System.Xml.Schema> содержит методы расширения, облегчающие проверку правильности XML-дерева по XSD-файлу.</span><span class="sxs-lookup"><span data-stu-id="9d7a3-105">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="9d7a3-106">Дополнительные сведения см. в документации метода <xref:System.Xml.Schema.Extensions.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d7a3-106">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d7a3-107">Пример</span><span class="sxs-lookup"><span data-stu-id="9d7a3-107">Example</span></span>  
 <span data-ttu-id="9d7a3-108">В следующем примере создается набор схем <xref:System.Xml.Schema.XmlSchemaSet>, затем с его помощью проводится проверка правильности двух объектов <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="9d7a3-108">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="9d7a3-109">Правильность одного документа подтверждается, а второго - нет.</span><span class="sxs-lookup"><span data-stu-id="9d7a3-109">One of the documents is valid, the other is not.</span></span>  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="9d7a3-110">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="9d7a3-110">This example produces the following output:</span></span>  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="9d7a3-111">Пример</span><span class="sxs-lookup"><span data-stu-id="9d7a3-111">Example</span></span>  
 <span data-ttu-id="9d7a3-112">Код в приведенном ниже примере проверяет действительность XML-документа из раздела [Пример XML-файла. Клиенты и заказы (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) по схеме из раздела [Пример XSD-файла. Клиенты и заказы](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="9d7a3-112">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="9d7a3-113">Затем в исходный XML-документ вносятся изменения.</span><span class="sxs-lookup"><span data-stu-id="9d7a3-113">It then modifies the source XML document.</span></span> <span data-ttu-id="9d7a3-114">Изменяется атрибут `CustomerID` первого клиента.</span><span class="sxs-lookup"><span data-stu-id="9d7a3-114">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="9d7a3-115">После этого изменения заказы ссылаются на несуществующего клиента, поэтому XML-документ больше не должен пройти проверку правильности.</span><span class="sxs-lookup"><span data-stu-id="9d7a3-115">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="9d7a3-116">В этом примере используется следующий XML-документ: [Пример XML-файла. Заказчики и заказы (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="9d7a3-116">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="9d7a3-117">В этом примере используется следующая XSD-схема: [Пример XSD-файла. Заказчики и заказы](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="9d7a3-117">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="9d7a3-118">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="9d7a3-118">This example produces the following output:</span></span>  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d7a3-119">См. также</span><span class="sxs-lookup"><span data-stu-id="9d7a3-119">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="9d7a3-120">Создание деревьев XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9d7a3-120">Creating XML Trees (C#)</span></span>](creating-xml-trees-linq-to-xml-2.md)
