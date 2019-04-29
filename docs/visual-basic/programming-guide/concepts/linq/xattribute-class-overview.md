---
title: Сведения о классе XAttribute (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 6b24f429a69067f6af1a61efe4102a5638db3031
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907456"
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="841dc-102">Сведения о классе XAttribute (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="841dc-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="841dc-103">Атрибуты - это пары «имя-значение», ассоциированные с элементом.</span><span class="sxs-lookup"><span data-stu-id="841dc-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="841dc-104">Класс <xref:System.Xml.Linq.XAttribute> представляет XML-атрибуты.</span><span class="sxs-lookup"><span data-stu-id="841dc-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="841dc-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="841dc-105">Overview</span></span>  
 <span data-ttu-id="841dc-106">Работа с атрибутами [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] аналогична работе с элементами.</span><span class="sxs-lookup"><span data-stu-id="841dc-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="841dc-107">Они имеют аналогичные конструкторы.</span><span class="sxs-lookup"><span data-stu-id="841dc-107">Their constructors are similar.</span></span> <span data-ttu-id="841dc-108">Аналогичны и методы, используемые для получения их коллекций.</span><span class="sxs-lookup"><span data-stu-id="841dc-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="841dc-109">По своему виду выражение запроса [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] для коллекции атрибутов весьма напоминает выражение запроса [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] для коллекции элементов.</span><span class="sxs-lookup"><span data-stu-id="841dc-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="841dc-110">Порядок, в котором атрибуты добавлялись к элементу, сохраняется.</span><span class="sxs-lookup"><span data-stu-id="841dc-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="841dc-111">Иначе говоря, при просмотре атрибутов они отображаются в том же порядке, в каком были добавлены.</span><span class="sxs-lookup"><span data-stu-id="841dc-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="841dc-112">Конструктор XAttribute</span><span class="sxs-lookup"><span data-stu-id="841dc-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="841dc-113">Чаще всего используется следующий конструктор класса <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="841dc-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="841dc-114">Конструктор</span><span class="sxs-lookup"><span data-stu-id="841dc-114">Constructor</span></span>|<span data-ttu-id="841dc-115">Описание</span><span class="sxs-lookup"><span data-stu-id="841dc-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="841dc-116">Создает объект <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="841dc-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="841dc-117">Аргумент `name` указывает имя атрибута; `content` указывает содержимое атрибута.</span><span class="sxs-lookup"><span data-stu-id="841dc-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="841dc-118">Создание элемента с атрибутом</span><span class="sxs-lookup"><span data-stu-id="841dc-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="841dc-119">В следующем коде показано элемента, который содержит атрибут с помощью XML-литералов в Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="841dc-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="841dc-120">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="841dc-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="841dc-121">Функциональное построение атрибутов</span><span class="sxs-lookup"><span data-stu-id="841dc-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="841dc-122">Объекты <xref:System.Xml.Linq.XAttribute> можно создавать в процессе создания объектов <xref:System.Xml.Linq.XElement> следующим образом:</span><span class="sxs-lookup"><span data-stu-id="841dc-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 <span data-ttu-id="841dc-123">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="841dc-123">This example produces the following output:</span></span>  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="841dc-124">Атрибуты не являются узлами</span><span class="sxs-lookup"><span data-stu-id="841dc-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="841dc-125">Между атрибутами и элементами имеются существенные различия.</span><span class="sxs-lookup"><span data-stu-id="841dc-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="841dc-126">Объекты <xref:System.Xml.Linq.XAttribute> не являются узлами в дереве XML.</span><span class="sxs-lookup"><span data-stu-id="841dc-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="841dc-127">Они представляют собой пары «имя-значение», ассоциированные с элементом XML.</span><span class="sxs-lookup"><span data-stu-id="841dc-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="841dc-128">В отличие от модели DOM, это более точно отражает структуру XML.</span><span class="sxs-lookup"><span data-stu-id="841dc-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="841dc-129">Хотя объекты <xref:System.Xml.Linq.XAttribute> фактически не являются узлами XML-дерева, работа с объектами <xref:System.Xml.Linq.XAttribute> весьма напоминает работу с объектами <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="841dc-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="841dc-130">Это различие имеет первостепенную важность только для разработчиков, создающих коды, которые взаимодействуют с XML-деревьями на уровне узлов.</span><span class="sxs-lookup"><span data-stu-id="841dc-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="841dc-131">Для многих разработчиков это различие не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="841dc-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="841dc-132">См. также</span><span class="sxs-lookup"><span data-stu-id="841dc-132">See also</span></span>

- [<span data-ttu-id="841dc-133">Обзор LINQ to XML программирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="841dc-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
