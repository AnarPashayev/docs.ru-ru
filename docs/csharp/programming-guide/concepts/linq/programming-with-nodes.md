---
title: Программирование с узлами (C#)
description: Узнайте о программировании с использованием узлов. Это позволяет разработчикам создавать программы, работающие на более высоком уровне, чем элементы и атрибуты.
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8a31d6459ab644a682d480239cabc3d88fd7dc14
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301688"
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="10012-104">Программирование с узлами (C#)</span><span class="sxs-lookup"><span data-stu-id="10012-104">Programming with Nodes (C#)</span></span>
<span data-ttu-id="10012-105">Разработчикам [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], которым требуется написать такие программы, как XML-редактор, система преобразования или модуль формирования отчетов, часто приходится писать программы, которые работают на более высоком уровне гранулярности по сравнению с элементами и атрибутами.</span><span class="sxs-lookup"><span data-stu-id="10012-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="10012-106">Им часто приходится работать на уровне узлов, обрабатывая текстовые узлы, инструкции по обработке и комментарии.</span><span class="sxs-lookup"><span data-stu-id="10012-106">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="10012-107">В этом разделе приводятся некоторые сведения о программировании на уровне узлов.</span><span class="sxs-lookup"><span data-stu-id="10012-107">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="10012-108">Сведения об узле</span><span class="sxs-lookup"><span data-stu-id="10012-108">Node Details</span></span>  
 <span data-ttu-id="10012-109">Программист, работающий на уровне узлов, должен учитывать целый ряд нюансов программирования.</span><span class="sxs-lookup"><span data-stu-id="10012-109">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="10012-110">Родительскому свойству дочерних узлов XDocument задано значение Null</span><span class="sxs-lookup"><span data-stu-id="10012-110">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="10012-111">Свойство <xref:System.Xml.Linq.XObject.Parent%2A> содержит родительский объект <xref:System.Xml.Linq.XElement>, а не родительский узел.</span><span class="sxs-lookup"><span data-stu-id="10012-111">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="10012-112">Дочерние узлы объекта <xref:System.Xml.Linq.XDocument> не имеют родительского объекта <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="10012-112">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="10012-113">Их родителем является документ, поэтому свойству <xref:System.Xml.Linq.XObject.Parent%2A> этих узлов задается значение NULL.</span><span class="sxs-lookup"><span data-stu-id="10012-113">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="10012-114">Следующий пример демонстрирует это:</span><span class="sxs-lookup"><span data-stu-id="10012-114">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="10012-115">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="10012-115">This example produces the following output:</span></span>  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="10012-116">Соседние текстовые узлы возможны</span><span class="sxs-lookup"><span data-stu-id="10012-116">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="10012-117">В нескольких моделях программирования XML соседние текстовые узлы всегда объединяются.</span><span class="sxs-lookup"><span data-stu-id="10012-117">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="10012-118">Иногда такую операцию называют нормализацией текстовых узлов.</span><span class="sxs-lookup"><span data-stu-id="10012-118">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="10012-119">не нормализует текстовые узлы.</span><span class="sxs-lookup"><span data-stu-id="10012-119">does not normalize text nodes.</span></span> <span data-ttu-id="10012-120">Если добавить два текстовых узла в один элемент, то они будут соседними.</span><span class="sxs-lookup"><span data-stu-id="10012-120">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="10012-121">Однако если добавить содержимое, определенное как строка, а не как узел <xref:System.Xml.Linq.XText>, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] может объединить строку с соседним текстовым узлом.</span><span class="sxs-lookup"><span data-stu-id="10012-121">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="10012-122">Следующий пример демонстрирует это:</span><span class="sxs-lookup"><span data-stu-id="10012-122">The following example demonstrates this:</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does not add a new text node  
xmlTree.Add("new content");  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does add a new, adjacent text node  
xmlTree.Add(new XText("more text"));  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
```  
  
 <span data-ttu-id="10012-123">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="10012-123">This example produces the following output:</span></span>  
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="10012-124">Пустые текстовые узлы возможны</span><span class="sxs-lookup"><span data-stu-id="10012-124">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="10012-125">В некоторых моделях программирования XML гарантируется, что текстовые узлы не будут содержать пустые строки.</span><span class="sxs-lookup"><span data-stu-id="10012-125">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="10012-126">Обоснованием является то, что такой текстовый узел не будет влиять на сериализацию XML.</span><span class="sxs-lookup"><span data-stu-id="10012-126">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="10012-127">Однако по этой же причине, по которой возможны соседние текстовые узлы, удаление текста из текстового узла путем присваивания ему в качестве значения пустой строки не приводит к удалению самого текстового узла.</span><span class="sxs-lookup"><span data-stu-id="10012-127">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);
```  
  
 <span data-ttu-id="10012-128">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="10012-128">This example produces the following output:</span></span>  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="10012-129">Пустые текстовые узлы влияют на сериализацию</span><span class="sxs-lookup"><span data-stu-id="10012-129">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="10012-130">Если элемент содержит только дочерний текстовый узел, который является пустым, то он сериализуется с использованием синтаксиса длинных тегов: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="10012-130">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="10012-131">Если элемент не содержит ни одного дочернего узла, то он сериализуется c использованием синтаксиса коротких тегов: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="10012-131">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);
```  
  
 <span data-ttu-id="10012-132">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="10012-132">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="10012-133">Пространства имен являются атрибутами в дереве LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="10012-133">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="10012-134">Несмотря на то что синтаксис деклараций пространств имен похож на синтаксис атрибутов, в некоторых программных интерфейсах, например XSLT и XPath, декларации пространств имен не считаются атрибутами.</span><span class="sxs-lookup"><span data-stu-id="10012-134">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="10012-135">Однако в [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] пространства имен хранятся в XML-дереве как объекты <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="10012-135">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="10012-136">Если просмотреть атрибуты элемента, который содержит декларацию пространства имен, то можно увидеть, что декларация пространства имен является одним из элементов возвращенной коллекции.</span><span class="sxs-lookup"><span data-stu-id="10012-136">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="10012-137">Свойство <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> указывает, является ли атрибут декларацией пространства имен.</span><span class="sxs-lookup"><span data-stu-id="10012-137">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="10012-138">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="10012-138">This example produces the following output:</span></span>  
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="10012-139">Методы оси XPath не возвращают дочерние пробелы XDocument</span><span class="sxs-lookup"><span data-stu-id="10012-139">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="10012-140">допускает дочерние текстовые узлы объекта <xref:System.Xml.Linq.XDocument>, если эти текстовые узлы содержат только пробелы.</span><span class="sxs-lookup"><span data-stu-id="10012-140">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="10012-141">Однако модель объектов XPath не включает пробелы как дочерние узлы документа, поэтому при прохождении по дочерним узлам объекта <xref:System.Xml.Linq.XDocument> при помощи оси <xref:System.Xml.Linq.XContainer.Nodes%2A> возвращаются текстовые узлы с пробелами.</span><span class="sxs-lookup"><span data-stu-id="10012-141">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="10012-142">Однако при прохождении по дочерним узлам объекта <xref:System.Xml.Linq.XDocument> при помощи методов оси XPath текстовые узлы с пробелами возвращены не будут.</span><span class="sxs-lookup"><span data-stu-id="10012-142">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
```csharp  
// Create a document with some white-space child nodes of the document.  
XDocument root = XDocument.Parse(  
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
  
<Root/>  
  
<!--a comment-->  
", LoadOptions.PreserveWhitespace);  
  
// count the white-space child nodes using LINQ to XML  
Console.WriteLine(root.Nodes().OfType<XText>().Count());  
  
// count the white-space child nodes using XPathEvaluate  
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());
```  
  
 <span data-ttu-id="10012-143">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="10012-143">This example produces the following output:</span></span>  
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="10012-144">Объекты XDeclaration не являются узлами</span><span class="sxs-lookup"><span data-stu-id="10012-144">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="10012-145">При прохождении по дочерним узлам объекта <xref:System.Xml.Linq.XDocument> нельзя увидеть объект XML-декларации.</span><span class="sxs-lookup"><span data-stu-id="10012-145">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="10012-146">Это свойство документа, а не его дочерний узел.</span><span class="sxs-lookup"><span data-stu-id="10012-146">It is a property of the document, not a child node of it.</span></span>  
  
```csharp  
XDocument doc = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root")  
);  
doc.Save("Temp.xml");  
Console.WriteLine(File.ReadAllText("Temp.xml"));  
  
// this shows that there is only one child node of the document  
Console.WriteLine(doc.Nodes().Count());  
```  
  
 <span data-ttu-id="10012-147">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="10012-147">This example produces the following output:</span></span>  
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  