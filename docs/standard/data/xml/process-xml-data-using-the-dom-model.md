---
title: Обработка XML-данных с использованием модели DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
ms.openlocfilehash: 01ef4bef57b8a2e3e13f28a98adb21b111f3f4ed
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710457"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="ef4a3-102">Обработка XML-данных с использованием модели DOM</span><span class="sxs-lookup"><span data-stu-id="ef4a3-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="ef4a3-103">Модель DOM рассматривает XML-данные как стандартный набор объектов и используется для обработки XML-данных в памяти.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="ef4a3-104">Пространство имен `System.Xml` обеспечивает программное представление XML-документов, фрагментов, узлов и наборов узлов.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="ef4a3-105">Оно основывается на рекомендациях базовой модели DOM уровня 1 и модели DOM уровня 2 консорциума W3C.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="ef4a3-106">Класс <xref:System.Xml.XmlDocument> представляет XML-документ.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="ef4a3-107">Он включает элементы для получения и создания всех других XML-объектов.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="ef4a3-108">С помощью класса <xref:System.Xml.XmlDocument> и связанных с ним классов можно конструировать XML-документы, загружать и обращаться к данным, изменять данные и сохранять изменения.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef4a3-109">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="ef4a3-109">In This Section</span></span>  
  
- [<span data-ttu-id="ef4a3-110">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="ef4a3-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="ef4a3-111">Типы XML-узлов</span><span class="sxs-lookup"><span data-stu-id="ef4a3-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
- [<span data-ttu-id="ef4a3-112">Иерархия модели объектов (DOM) документов XML</span><span class="sxs-lookup"><span data-stu-id="ef4a3-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="ef4a3-113">Сопоставление объектной иерархии с XML-данными</span><span class="sxs-lookup"><span data-stu-id="ef4a3-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="ef4a3-114">Создание XML-документа</span><span class="sxs-lookup"><span data-stu-id="ef4a3-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
- [<span data-ttu-id="ef4a3-115">Считывание XML-документа в модели DOM</span><span class="sxs-lookup"><span data-stu-id="ef4a3-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="ef4a3-116">Вставка узлов в XML-документ</span><span class="sxs-lookup"><span data-stu-id="ef4a3-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="ef4a3-117">Удаление узлов, содержимого и значений из XML-документа</span><span class="sxs-lookup"><span data-stu-id="ef4a3-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="ef4a3-118">Изменение узлов, содержимого и значений в XML-документе</span><span class="sxs-lookup"><span data-stu-id="ef4a3-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="ef4a3-119">Проверка XML-документа в модели DOM</span><span class="sxs-lookup"><span data-stu-id="ef4a3-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="ef4a3-120">Сохранение и запись документа</span><span class="sxs-lookup"><span data-stu-id="ef4a3-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="ef4a3-121">Выбор узлов с помощью XPath-навигации</span><span class="sxs-lookup"><span data-stu-id="ef4a3-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="ef4a3-122">Разрешение внешних ресурсов</span><span class="sxs-lookup"><span data-stu-id="ef4a3-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
- [<span data-ttu-id="ef4a3-123">Сравнение объектов с помощью XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="ef4a3-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="ef4a3-124">Коллекции узлов в NamedNodeMap и NodeList</span><span class="sxs-lookup"><span data-stu-id="ef4a3-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="ef4a3-125">Динамические обновления объектов NodeList и NamedNodeMap</span><span class="sxs-lookup"><span data-stu-id="ef4a3-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="ef4a3-126">Поддержка пространств имен в модели DOM</span><span class="sxs-lookup"><span data-stu-id="ef4a3-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="ef4a3-127">Обработка событий в XML-документе с помощью XmlNodeChangedEventArgs</span><span class="sxs-lookup"><span data-stu-id="ef4a3-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="ef4a3-128">Расширение модели DOM</span><span class="sxs-lookup"><span data-stu-id="ef4a3-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="ef4a3-129">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="ef4a3-129">Related Sections</span></span>  
 [<span data-ttu-id="ef4a3-130">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="ef4a3-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="ef4a3-131">Описывает обработку XML с использованием класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
