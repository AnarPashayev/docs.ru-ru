---
title: Навигация в наборе узлов с помощью XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
ms.openlocfilehash: 132154afdfd3e5bd6769bfcce338e598136e7515
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288762"
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="0dd10-102">Навигация в наборе узлов с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0dd10-102">Node Set Navigation Using XPathNavigator</span></span>
<span data-ttu-id="0dd10-103">Навигацию по узлам в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> обеспечивают методы просмотра набора узлов класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0dd10-103">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="0dd10-104">Возможен просмотр всех узлов или набора выбранных узлов, возвращаемого одним из методов выбора класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0dd10-104">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="0dd10-105">Навигация в наборе узлов элементов</span><span class="sxs-lookup"><span data-stu-id="0dd10-105">Element Node Set Navigation</span></span>  
 <span data-ttu-id="0dd10-106">В классе <xref:System.Xml.XPath.XPathNavigator> предусмотрено несколько методов, используемых для навигации по узлам элементов.</span><span class="sxs-lookup"><span data-stu-id="0dd10-106">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="0dd10-107">В следующей таблице показаны доступные методы навигации и описания способов перемещения. В таблицу не включены методы, применяемые для навигации по узлам атрибутов и пространств имен.</span><span class="sxs-lookup"><span data-stu-id="0dd10-107">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="0dd10-108">Дополнительные сведения о выборе узлов объекта <xref:System.Xml.XPath.XPathNavigator> см. в руководстве по [выбору, вычислению и отбору данных XML с помощью XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="0dd10-108">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="0dd10-109">Дополнительные сведения о навигации по узлам атрибутов и пространств имен см. в руководстве по [навигации в узлах атрибутов и пространств имен с помощью XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="0dd10-109">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="0dd10-110">Метод</span><span class="sxs-lookup"><span data-stu-id="0dd10-110">Method</span></span>|<span data-ttu-id="0dd10-111">Описание</span><span class="sxs-lookup"><span data-stu-id="0dd10-111">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="0dd10-112">Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в положение указанного объекта <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0dd10-112">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="0dd10-113">Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в дочерний узел текущего узла.</span><span class="sxs-lookup"><span data-stu-id="0dd10-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="0dd10-114">Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в первый узел одного уровня с текущим узлом.</span><span class="sxs-lookup"><span data-stu-id="0dd10-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="0dd10-115">Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в первый дочерний узел текущего узла.</span><span class="sxs-lookup"><span data-stu-id="0dd10-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="0dd10-116">Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в указанный элемент в порядке следования документов.</span><span class="sxs-lookup"><span data-stu-id="0dd10-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="0dd10-117">Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в узел, имеющий атрибут типа `ID` со значением, которое совпадает с данным значением <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0dd10-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="0dd10-118">Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в следующий узел одного уровня с текущим узлом.</span><span class="sxs-lookup"><span data-stu-id="0dd10-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="0dd10-119">Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в родительский узел текущего узла.</span><span class="sxs-lookup"><span data-stu-id="0dd10-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="0dd10-120">Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в предыдущий узел одного уровня с текущим узлом.</span><span class="sxs-lookup"><span data-stu-id="0dd10-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="0dd10-121">Перемещает объект <xref:System.Xml.XPath.XPathNavigator> в корневой узел XML-документа.</span><span class="sxs-lookup"><span data-stu-id="0dd10-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="0dd10-122">Навигация по узлам комментариев и инструкций по обработке</span><span class="sxs-lookup"><span data-stu-id="0dd10-122">Comments and Processing Instruction Node Navigation</span></span>  
 <span data-ttu-id="0dd10-123">Следующие методы класса <xref:System.Xml.XPath.XPathNavigator> допустимы для перемещения комментариев и инструкций по обработке из других узлов в XML-документ.</span><span class="sxs-lookup"><span data-stu-id="0dd10-123">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="0dd10-124">См. также</span><span class="sxs-lookup"><span data-stu-id="0dd10-124">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="0dd10-125">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="0dd10-125">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="0dd10-126">Навигация по узлам атрибутов и пространств имен с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0dd10-126">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="0dd10-127">Извлечение XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0dd10-127">Extract XML Data Using XPathNavigator</span></span>](extract-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="0dd10-128">Доступ к XML-данным со строгой типизацией с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0dd10-128">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
