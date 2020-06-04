---
title: Общие сведения о классе XElement
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: a0e50c8a5a14150ee09a328f4dcdd5bc88363621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413223"
---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="18cb9-102">Общие сведения о классе XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18cb9-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="18cb9-103">Класс <xref:System.Xml.Linq.XElement> - это один из фундаментальных классов в [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="18cb9-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="18cb9-104">Он обозначает элемент XML.</span><span class="sxs-lookup"><span data-stu-id="18cb9-104">It represents an XML element.</span></span> <span data-ttu-id="18cb9-105">Этот класс можно использовать для создания элементов, изменения содержимого элемента, добавления, изменения или удаления дочерних элементов, добавления к элементам атрибутов или сериализации содержимого элемента в текстовой форме.</span><span class="sxs-lookup"><span data-stu-id="18cb9-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="18cb9-106">Можно также настроить взаимодействие с другими классами в <xref:System.Xml?displayProperty=nameWithType>, например <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> и <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="18cb9-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="18cb9-107">Функциональные особенности класса XElement</span><span class="sxs-lookup"><span data-stu-id="18cb9-107">XElement Functionality</span></span>  
 <span data-ttu-id="18cb9-108">В этом разделе рассматриваются функциональные особенности класса <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="18cb9-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="18cb9-109">Создание XML-деревьев</span><span class="sxs-lookup"><span data-stu-id="18cb9-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="18cb9-110">Можно создавать XML-деревья несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="18cb9-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="18cb9-111">Можно создать XML-дерево при помощи кода.</span><span class="sxs-lookup"><span data-stu-id="18cb9-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="18cb9-112">Дополнительные сведения см. в разделе [Создание деревьев XML (Visual Basic)](creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="18cb9-112">For more information, see [Creating XML Trees (Visual Basic)](creating-xml-trees.md).</span></span>  
  
- <span data-ttu-id="18cb9-113">Можно выполнить синтаксический анализ XML из нескольких источников, в том числе из <xref:System.IO.TextReader>, текстовых файлов или веб-адреса (URL-адреса).</span><span class="sxs-lookup"><span data-stu-id="18cb9-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="18cb9-114">Дополнительные сведения см. в разделе [анализ XML (Visual Basic)](parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="18cb9-114">For more information, see [Parsing XML (Visual Basic)](parsing-xml.md).</span></span>  
  
- <span data-ttu-id="18cb9-115">Для распределения контента по дереву можно использовать <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="18cb9-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="18cb9-116">Дополнительные сведения см. в разделе <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="18cb9-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="18cb9-117">Если установлен модуль, позволяющий заносить содержимое в средство <xref:System.Xml.XmlWriter>, то можно использовать метод <xref:System.Xml.Linq.XContainer.CreateWriter%2A>, чтобы создать модуль записи, передать его этому модулю, после чего использовать контент, записанный в систему <xref:System.Xml.XmlWriter>, чтобы заполнить XML-дерево.</span><span class="sxs-lookup"><span data-stu-id="18cb9-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="18cb9-118">Однако наиболее распространенным является такой метод создания XML-дерева:</span><span class="sxs-lookup"><span data-stu-id="18cb9-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 <span data-ttu-id="18cb9-119">Другим распространенным способом создания дерева XML является использование результатов запроса LINQ для заполнения дерева XML, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="18cb9-119">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="18cb9-120">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="18cb9-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="18cb9-121">Сериализация деревьев XML</span><span class="sxs-lookup"><span data-stu-id="18cb9-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="18cb9-122">Можно сериализовать XML-дерево в <xref:System.IO.File>, <xref:System.IO.TextWriter> или в <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="18cb9-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="18cb9-123">Дополнительные сведения см. в разделе [сериализация XML-деревьев (Visual Basic)](serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="18cb9-123">For more information, see [Serializing XML Trees (Visual Basic)](serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="18cb9-124">Получение XML-данных через методы оси</span><span class="sxs-lookup"><span data-stu-id="18cb9-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="18cb9-125">Можно воспользоваться методами оси для получения свойств, дочерних элементов, элементов-потомков и элементов-предков.</span><span class="sxs-lookup"><span data-stu-id="18cb9-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="18cb9-126">При выполнении запросов LINQ используются методы оси и обеспечиваются гибкие и эффективные способы навигации по XML-дереву, а также его обработки.</span><span class="sxs-lookup"><span data-stu-id="18cb9-126">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="18cb9-127">Дополнительные сведения см. в разделе [оси LINQ to XML (Visual Basic)](linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="18cb9-127">For more information, see [LINQ to XML Axes (Visual Basic)](linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="18cb9-128">Выполнение запросов деревьям XML</span><span class="sxs-lookup"><span data-stu-id="18cb9-128">Querying XML Trees</span></span>  
 <span data-ttu-id="18cb9-129">Вы можете создавать запросы LINQ, которые извлекают данные из дерева XML.</span><span class="sxs-lookup"><span data-stu-id="18cb9-129">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="18cb9-130">Дополнительные сведения см. в разделе [запросы к деревьям XML (Visual Basic)](querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="18cb9-130">For more information, see [Querying XML Trees (Visual Basic)](querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="18cb9-131">Изменение деревьев XML</span><span class="sxs-lookup"><span data-stu-id="18cb9-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="18cb9-132">Один и тот же элемент можно изменить несколькими способами, в том числе изменив содержимое или атрибуты.</span><span class="sxs-lookup"><span data-stu-id="18cb9-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="18cb9-133">Можно также удалить элемент из родительской структуры.</span><span class="sxs-lookup"><span data-stu-id="18cb9-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="18cb9-134">Дополнительные сведения см. в разделе [изменение деревьев XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="18cb9-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18cb9-135">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="18cb9-135">See also</span></span>

- [<span data-ttu-id="18cb9-136">Общие сведения о программировании LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18cb9-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
