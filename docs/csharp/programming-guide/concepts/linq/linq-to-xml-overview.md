---
title: Общие сведения о LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 0ae7b226f4fef0aeec895b0b908711a6edb13728
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612840"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="fb2dc-102">Общие сведения о LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fb2dc-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="fb2dc-103">XML широко используется для форматирования данных в целом ряде контекстов.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="fb2dc-104">Примеры XML можно обнаружить в веб-среде, в файлах конфигурации, в файлах Microsoft Office Word и в базах данных.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

<span data-ttu-id="fb2dc-105">В [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] реализован современный пересмотренный подход к программированию средствами XML.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="fb2dc-106">Кроме того, реализованы встроенные в память возможности модификации документов модели DOM, поддерживаются выражения запросов [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fb2dc-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="fb2dc-107">Хотя в синтаксическом отношении эти выражения запросов отличаются от XPath, они предоставляют аналогичные функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="fb2dc-108">Разработчики, использующие LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="fb2dc-108">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="fb2dc-109">предназначен для различных категорий разработчиков.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-109">targets a variety of developers.</span></span> <span data-ttu-id="fb2dc-110">С точки зрения среднестатистического разработчика, заинтересованного в решении той или иной задачи, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] облегчает обработку XML, поскольку дает возможность получить опыт работы с запросами, аналогичный опыту работы с языком SQL.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="fb2dc-111">Посвятив совсем немного времени изучению предмета, программисты могут научиться составлять сжатые и мощные запросы на предпочитаемом ими языке программирования.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="fb2dc-112">Профессиональные разработчики могут с помощью [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] существенно повысить производительность своего труда.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="fb2dc-113">Используя [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], они могут сократить объемы необходимого кода и сделать его более выразительным, более компактным и более мощным.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="fb2dc-114">Они могут одновременно использовать выражения запросов из нескольких доменов данных.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-114">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="fb2dc-115">Что такое LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="fb2dc-115">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="fb2dc-116">- это оснащенный средствами LINQ и встроенный в память программный интерфейс XML, позволяющий работать с XML-файлами внутри языков программирования [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fb2dc-116">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="fb2dc-117">подобен модели DOM в том отношении, что загружает XML-документ в память.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-117">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="fb2dc-118">К такому документу можно направить запрос, его можно изменить, а после изменения его можно сохранить в файле или сериализовать и передать через Интернет.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="fb2dc-119">Но между [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] и моделью DOM существуют отличия: Интерфейс реализует облегченную и более простую в работе модель объектов; кроме того, в нем используются преимущества языковых возможностей, реализованные в C#.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="fb2dc-120">Важнейшее достоинство [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] состоит в его интеграции с [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fb2dc-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="fb2dc-121">Эта интеграция дает возможность создавать запросы к загруженному в память XML-документу с целью получения коллекций элементов и атрибутов.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="fb2dc-122">По своей функциональности (но не по синтаксису) реализованные в [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] возможности формирования запросов сопоставимы с возможностями XPath и XQuery.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="fb2dc-123">Благодаря интеграции [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] в C# обеспечивается более строгая типизация, проверка во время компиляции и улучшенная поддержка отладчика.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="fb2dc-124">Другим преимуществом [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] является то, что возможность использования результатов запросов в качестве параметров конструкторов объектов <xref:System.Xml.Linq.XElement> и <xref:System.Xml.Linq.XAttribute> позволяет применять мощный подход для создания XML-деревьев.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="fb2dc-125">Этот подход, известный как *функциональное построение*, дает разработчикам возможность легко преобразовывать деревья XML из одной формы в другую.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="fb2dc-126">Пусть имеется типичный заказ на покупку в формате XML, как это описано в статье [Пример XML-файла. Типичный заказ на покупку (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="fb2dc-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="fb2dc-127">С помощью интерфейса [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] можно выполнить следующий запрос для получения значения атрибута артикула для каждого элемента в заказе на покупку:</span><span class="sxs-lookup"><span data-stu-id="fb2dc-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="fb2dc-128">Это можно переписать в форме синтаксиса метода:</span><span class="sxs-lookup"><span data-stu-id="fb2dc-128">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="fb2dc-129">Еще один пример. Пусть требуется сформировать отсортированный в соответствии с номерами деталей список продуктов стоимостью выше 100 долл.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-129">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="fb2dc-130">Для получения этих сведений можно выполнить следующий запрос:</span><span class="sxs-lookup"><span data-stu-id="fb2dc-130">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

<span data-ttu-id="fb2dc-131">Опять же, это можно переписать в форме синтаксиса метода:</span><span class="sxs-lookup"><span data-stu-id="fb2dc-131">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="fb2dc-132">В дополнение к функциям, реализованным в [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] предоставляет усовершенствованный интерфейс программирования XML.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-132">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="fb2dc-133">Благодаря [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] появляются следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="fb2dc-133">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="fb2dc-134">Загрузка XML из [файлов](how-to-load-xml-from-a-file.md) или из [потоков](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="fb2dc-134">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="fb2dc-135">Сериализация XML в файлы или в потоки.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-135">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="fb2dc-136">Создание XML-кодов «с чистого листа» с помощью функционального построения.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-136">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="fb2dc-137">Обращение с запросами к XML с помощью XPath-подобных осей.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-137">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="fb2dc-138">Манипулирование загруженным в память XML-деревом с помощью таких методов, как <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> и <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-138">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="fb2dc-139">Проверка XML-деревьев с помощью XSD.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-139">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="fb2dc-140">Использование сочетания этих функций для преобразования XML-деревьев из одной формы в другую.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-140">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="fb2dc-141">Создание деревьев XML</span><span class="sxs-lookup"><span data-stu-id="fb2dc-141">Creating XML Trees</span></span>

<span data-ttu-id="fb2dc-142">Одним из наиболее важных преимуществ программирования с использованием [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] является простота создания XML-деревьев.</span><span class="sxs-lookup"><span data-stu-id="fb2dc-142">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="fb2dc-143">Так, для создания небольшого дерева XML можно написать следующий код:</span><span class="sxs-lookup"><span data-stu-id="fb2dc-143">For example, to create a small XML tree, you can write code as follows:</span></span>

```csharp
XElement contacts =
new XElement("Contacts",
    new XElement("Contact",
        new XElement("Name", "Patrick Hines"),
        new XElement("Phone", "206-555-0144",
            new XAttribute("Type", "Home")),
        new XElement("phone", "425-555-0145",
            new XAttribute("Type", "Work")),
        new XElement("Address",
            new XElement("Street1", "123 Main St"),
            new XElement("City", "Mercer Island"),
            new XElement("State", "WA"),
            new XElement("Postal", "68042")
        )
    )
);
```

<span data-ttu-id="fb2dc-144">Дополнительные сведения см. в разделе [Создание деревьев XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="fb2dc-144">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb2dc-145">См. также</span><span class="sxs-lookup"><span data-stu-id="fb2dc-145">See also</span></span>

- <xref:System.Xml.Linq>
- [<span data-ttu-id="fb2dc-146">Начало работы (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="fb2dc-146">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
