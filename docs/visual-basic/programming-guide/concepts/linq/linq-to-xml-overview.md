---
title: Общие сведения о LINQ to XML
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: afdec54ac05bb4a631de7fdb599123ffe964c443
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368743"
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="cd923-102">Обзор LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd923-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="cd923-103">XML широко используется для форматирования данных в целом ряде контекстов.</span><span class="sxs-lookup"><span data-stu-id="cd923-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="cd923-104">Примеры XML можно обнаружить в веб-среде, в файлах конфигурации, в файлах Microsoft Office Word и в базах данных.</span><span class="sxs-lookup"><span data-stu-id="cd923-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 <span data-ttu-id="cd923-105">В [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] реализован современный пересмотренный подход к программированию средствами XML.</span><span class="sxs-lookup"><span data-stu-id="cd923-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="cd923-106">Она предоставляет возможности изменения документов в памяти в модель DOM (DOM) и поддерживает выражения запросов LINQ.</span><span class="sxs-lookup"><span data-stu-id="cd923-106">It provides the in-memory document-modification capabilities of the Document Object Model (DOM) and supports LINQ query expressions.</span></span> <span data-ttu-id="cd923-107">Хотя в синтаксическом отношении эти выражения запросов отличаются от XPath, они предоставляют аналогичные функциональные возможности.</span><span class="sxs-lookup"><span data-stu-id="cd923-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="cd923-108">Разработчики, использующие LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="cd923-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="cd923-109">предназначен для различных категорий разработчиков.</span><span class="sxs-lookup"><span data-stu-id="cd923-109">targets a variety of developers.</span></span> <span data-ttu-id="cd923-110">С точки зрения среднестатистического разработчика, заинтересованного в решении той или иной задачи, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] облегчает обработку XML, поскольку дает возможность получить опыт работы с запросами, аналогичный опыту работы с языком SQL.</span><span class="sxs-lookup"><span data-stu-id="cd923-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="cd923-111">Посвятив совсем немного времени изучению предмета, программисты могут научиться составлять сжатые и мощные запросы на предпочитаемом ими языке программирования.</span><span class="sxs-lookup"><span data-stu-id="cd923-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="cd923-112">Профессиональные разработчики могут с помощью [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] существенно повысить производительность своего труда.</span><span class="sxs-lookup"><span data-stu-id="cd923-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="cd923-113">Используя [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], они могут сократить объемы необходимого кода и сделать его более выразительным, более компактным и более мощным.</span><span class="sxs-lookup"><span data-stu-id="cd923-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="cd923-114">Они могут одновременно использовать выражения запросов из нескольких доменов данных.</span><span class="sxs-lookup"><span data-stu-id="cd923-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="cd923-115">Что такое LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="cd923-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="cd923-116">— это выполняющийся в памяти интерфейс программирования XML с поддержкой LINQ, который позволяет работать с XML из языков программирования .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cd923-116">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="cd923-117">подобен модели DOM в том отношении, что загружает XML-документ в память.</span><span class="sxs-lookup"><span data-stu-id="cd923-117">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="cd923-118">К такому документу можно направить запрос, его можно изменить, а после изменения его можно сохранить в файле или сериализовать и передать через Интернет.</span><span class="sxs-lookup"><span data-stu-id="cd923-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="cd923-119">Однако [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] отличается от модели DOM: она предоставляет новую объектную модель, которая более проста и удобна для работы с, и использует преимущества языковых функций в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cd923-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="cd923-120">Важнейшее достоинство [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] представлено интеграцией с LINQ.</span><span class="sxs-lookup"><span data-stu-id="cd923-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="cd923-121">Эта интеграция дает возможность создавать запросы к загруженному в память XML-документу с целью получения коллекций элементов и атрибутов.</span><span class="sxs-lookup"><span data-stu-id="cd923-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="cd923-122">По своей функциональности (но не по синтаксису) реализованные в [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] возможности формирования запросов сопоставимы с возможностями XPath и XQuery.</span><span class="sxs-lookup"><span data-stu-id="cd923-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="cd923-123">Интеграция LINQ в Visual Basic обеспечивает более надежную типизацию, проверку во время компиляции и улучшенную поддержку отладчика.</span><span class="sxs-lookup"><span data-stu-id="cd923-123">The integration of LINQ in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="cd923-124">Другим преимуществом [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] является то, что возможность использования результатов запросов в качестве параметров конструкторов объектов <xref:System.Xml.Linq.XElement> и <xref:System.Xml.Linq.XAttribute> позволяет применять мощный подход для создания XML-деревьев.</span><span class="sxs-lookup"><span data-stu-id="cd923-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="cd923-125">Этот подход, известный как *функциональное построение*, дает разработчикам возможность легко преобразовывать деревья XML из одной формы в другую.</span><span class="sxs-lookup"><span data-stu-id="cd923-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="cd923-126">Пусть имеется типичный заказ на покупку в формате XML, как это описано в разделе [Пример XML-файла. Стандартный заказ на покупку (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd923-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span> <span data-ttu-id="cd923-127">С помощью интерфейса [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] можно выполнить следующий запрос для получения значения атрибута артикула для каждого элемента в заказе на покупку:</span><span class="sxs-lookup"><span data-stu-id="cd923-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="cd923-128">Еще один пример. Пусть требуется сформировать отсортированный в соответствии с номерами деталей список продуктов стоимостью выше 100 долл.</span><span class="sxs-lookup"><span data-stu-id="cd923-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="cd923-129">Для получения этих сведений можно выполнить следующий запрос:</span><span class="sxs-lookup"><span data-stu-id="cd923-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="cd923-130">В дополнение к функциям, реализованным в LINQ, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] предоставляет усовершенствованный интерфейс программирования XML.</span><span class="sxs-lookup"><span data-stu-id="cd923-130">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="cd923-131">Благодаря [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] появляются следующие возможности:</span><span class="sxs-lookup"><span data-stu-id="cd923-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
- <span data-ttu-id="cd923-132">Загрузка XML из файлов или из потоков.</span><span class="sxs-lookup"><span data-stu-id="cd923-132">Load XML from files or streams.</span></span>  
  
- <span data-ttu-id="cd923-133">Сериализация XML в файлы или в потоки.</span><span class="sxs-lookup"><span data-stu-id="cd923-133">Serialize XML to files or streams.</span></span>  
  
- <span data-ttu-id="cd923-134">Создание XML-кодов «с чистого листа» с помощью функционального построения.</span><span class="sxs-lookup"><span data-stu-id="cd923-134">Create XML from scratch by using functional construction.</span></span>  
  
- <span data-ttu-id="cd923-135">Обращение с запросами к XML с помощью XPath-подобных осей.</span><span class="sxs-lookup"><span data-stu-id="cd923-135">Query XML using XPath-like axes.</span></span>  
  
- <span data-ttu-id="cd923-136">Манипулирование загруженным в память XML-деревом с помощью таких методов, как <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> и <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd923-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
- <span data-ttu-id="cd923-137">Проверка XML-деревьев с помощью XSD.</span><span class="sxs-lookup"><span data-stu-id="cd923-137">Validate XML trees using XSD.</span></span>  
  
- <span data-ttu-id="cd923-138">Использование сочетания этих функций для преобразования XML-деревьев из одной формы в другую.</span><span class="sxs-lookup"><span data-stu-id="cd923-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="cd923-139">Создание деревьев XML</span><span class="sxs-lookup"><span data-stu-id="cd923-139">Creating XML Trees</span></span>  
 <span data-ttu-id="cd923-140">Одним из наиболее важных преимуществ программирования с использованием [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] является простота создания XML-деревьев.</span><span class="sxs-lookup"><span data-stu-id="cd923-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="cd923-141">Например, чтобы создать небольшое XML-дерево, можно написать следующий код:</span><span class="sxs-lookup"><span data-stu-id="cd923-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 <span data-ttu-id="cd923-142">Компилятор Visual Basic преобразует литералы XML в [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] вызовы методов.</span><span class="sxs-lookup"><span data-stu-id="cd923-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="cd923-143">Дополнительные сведения см. в разделе [Создание деревьев XML (Visual Basic)](creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="cd923-143">For more information, see [Creating XML Trees (Visual Basic)](creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd923-144">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="cd923-144">See also</span></span>

- <xref:System.Xml.Linq>
- [<span data-ttu-id="cd923-145">Начало работы (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cd923-145">Getting Started (LINQ to XML)</span></span>](getting-started-linq-to-xml.md)
- <span data-ttu-id="cd923-146">[Overview of LINQ to XML in Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md) (Общие сведения о LINQ to XML в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd923-146">[Overview of LINQ to XML in Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md)</span></span>
- [<span data-ttu-id="cd923-147">XML</span><span class="sxs-lookup"><span data-stu-id="cd923-147">XML</span></span>](../../language-features/xml/index.md)
