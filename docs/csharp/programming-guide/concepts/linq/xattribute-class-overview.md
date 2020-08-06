---
title: Общие сведения о классе XAttribute (C#)
description: Атрибуты — это пары "имя-значение", ассоциированные с элементом. Класс XAttribute представляет XML-атрибуты. Сведения о работе с атрибутами в LINQ to XML при программировании на C#.
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 8a19de601041bbb20241c959e909483b97bcf797
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302234"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="31290-105">Общие сведения о классе XAttribute (C#)</span><span class="sxs-lookup"><span data-stu-id="31290-105">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="31290-106">Атрибуты - это пары «имя-значение», ассоциированные с элементом.</span><span class="sxs-lookup"><span data-stu-id="31290-106">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="31290-107">Класс <xref:System.Xml.Linq.XAttribute> представляет XML-атрибуты.</span><span class="sxs-lookup"><span data-stu-id="31290-107">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="31290-108">Обзор</span><span class="sxs-lookup"><span data-stu-id="31290-108">Overview</span></span>  
 <span data-ttu-id="31290-109">Работа с атрибутами [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] аналогична работе с элементами.</span><span class="sxs-lookup"><span data-stu-id="31290-109">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="31290-110">Они имеют аналогичные конструкторы.</span><span class="sxs-lookup"><span data-stu-id="31290-110">Their constructors are similar.</span></span> <span data-ttu-id="31290-111">Аналогичны и методы, используемые для получения их коллекций.</span><span class="sxs-lookup"><span data-stu-id="31290-111">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="31290-112">По своему виду выражение запроса LINQ для коллекции атрибутов очень напоминает выражение запроса LINQ для коллекции элементов.</span><span class="sxs-lookup"><span data-stu-id="31290-112">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="31290-113">Порядок, в котором атрибуты добавлялись к элементу, сохраняется.</span><span class="sxs-lookup"><span data-stu-id="31290-113">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="31290-114">Иначе говоря, при просмотре атрибутов они отображаются в том же порядке, в каком были добавлены.</span><span class="sxs-lookup"><span data-stu-id="31290-114">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="31290-115">Конструктор XAttribute</span><span class="sxs-lookup"><span data-stu-id="31290-115">The XAttribute Constructor</span></span>  
 <span data-ttu-id="31290-116">Чаще всего используется следующий конструктор класса <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="31290-116">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="31290-117">Конструктор</span><span class="sxs-lookup"><span data-stu-id="31290-117">Constructor</span></span>|<span data-ttu-id="31290-118">Описание</span><span class="sxs-lookup"><span data-stu-id="31290-118">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="31290-119">Создает объект <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="31290-119">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="31290-120">Аргумент `name` указывает имя атрибута; `content` указывает содержимое атрибута.</span><span class="sxs-lookup"><span data-stu-id="31290-120">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="31290-121">Создание элемента с атрибутом</span><span class="sxs-lookup"><span data-stu-id="31290-121">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="31290-122">Следующий код иллюстрирует типичную задачу создания элемента, содержащего атрибут:</span><span class="sxs-lookup"><span data-stu-id="31290-122">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="31290-123">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="31290-123">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="31290-124">Функциональное построение атрибутов</span><span class="sxs-lookup"><span data-stu-id="31290-124">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="31290-125">Объекты <xref:System.Xml.Linq.XAttribute> можно создавать в процессе создания объектов <xref:System.Xml.Linq.XElement> следующим образом:</span><span class="sxs-lookup"><span data-stu-id="31290-125">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 <span data-ttu-id="31290-126">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="31290-126">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="31290-127">Атрибуты не являются узлами</span><span class="sxs-lookup"><span data-stu-id="31290-127">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="31290-128">Между атрибутами и элементами имеются существенные различия.</span><span class="sxs-lookup"><span data-stu-id="31290-128">There are some differences between attributes and elements.</span></span> <span data-ttu-id="31290-129">Объекты <xref:System.Xml.Linq.XAttribute> не являются узлами в дереве XML.</span><span class="sxs-lookup"><span data-stu-id="31290-129"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="31290-130">Они представляют собой пары «имя-значение», ассоциированные с элементом XML.</span><span class="sxs-lookup"><span data-stu-id="31290-130">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="31290-131">В отличие от модели DOM, это более точно отражает структуру XML.</span><span class="sxs-lookup"><span data-stu-id="31290-131">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="31290-132">Хотя объекты <xref:System.Xml.Linq.XAttribute> фактически не являются узлами XML-дерева, работа с объектами <xref:System.Xml.Linq.XAttribute> весьма напоминает работу с объектами <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="31290-132">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="31290-133">Это различие имеет первостепенную важность только для разработчиков, создающих коды, которые взаимодействуют с XML-деревьями на уровне узлов.</span><span class="sxs-lookup"><span data-stu-id="31290-133">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="31290-134">Для многих разработчиков это различие не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="31290-134">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31290-135">См. также</span><span class="sxs-lookup"><span data-stu-id="31290-135">See also</span></span>

- [<span data-ttu-id="31290-136">Общие сведения о программировании LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="31290-136">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
