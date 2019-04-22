---
title: Добавление элементов, атрибутов и узлов в дерево XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 35d3bdb27342dd7a871778ad4749db4d6849bd60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814322"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a><span data-ttu-id="7ea4a-102">Добавление элементов, атрибутов и узлов в дерево XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ea4a-102">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="7ea4a-103">Можно добавлять содержимое (элементы, атрибуты, комментарии, инструкции по обработке, текст и CDATA) к существующему XML-дереву.</span><span class="sxs-lookup"><span data-stu-id="7ea4a-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="7ea4a-104">Методы добавления содержимого</span><span class="sxs-lookup"><span data-stu-id="7ea4a-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="7ea4a-105">Следующие методы позволяют добавить дочернее содержимое к <xref:System.Xml.Linq.XElement> или <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="7ea4a-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="7ea4a-106">Метод</span><span class="sxs-lookup"><span data-stu-id="7ea4a-106">Method</span></span>|<span data-ttu-id="7ea4a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="7ea4a-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="7ea4a-108">Добавляет содержимое в конце дочернего содержимого <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="7ea4a-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="7ea4a-109">Добавляет содержимое в начале дочернего содержимого <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="7ea4a-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="7ea4a-110">Следующие методы позволяют добавлять содержимое как одноуровневые узлы для <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="7ea4a-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="7ea4a-111">Самым распространенным узлом, к которому можно добавлять содержимое как одноуровневые узлы, является <xref:System.Xml.Linq.XElement>, хотя можно добавлять содержимое в виде таких узлов и к другим типам узлов, например <xref:System.Xml.Linq.XText> или <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="7ea4a-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="7ea4a-112">Метод</span><span class="sxs-lookup"><span data-stu-id="7ea4a-112">Method</span></span>|<span data-ttu-id="7ea4a-113">Описание</span><span class="sxs-lookup"><span data-stu-id="7ea4a-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="7ea4a-114">Добавляет содержимое после <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="7ea4a-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="7ea4a-115">Добавляет содержимое перед <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="7ea4a-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7ea4a-116">Пример</span><span class="sxs-lookup"><span data-stu-id="7ea4a-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7ea4a-117">Описание</span><span class="sxs-lookup"><span data-stu-id="7ea4a-117">Description</span></span>  
 <span data-ttu-id="7ea4a-118">В следующем примере создаются два XML-дерева, затем выполняется изменение одного из них.</span><span class="sxs-lookup"><span data-stu-id="7ea4a-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7ea4a-119">Код</span><span class="sxs-lookup"><span data-stu-id="7ea4a-119">Code</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
```  
  
### <a name="comments"></a><span data-ttu-id="7ea4a-120">Комментарии</span><span class="sxs-lookup"><span data-stu-id="7ea4a-120">Comments</span></span>  
 <span data-ttu-id="7ea4a-121">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="7ea4a-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ea4a-122">См. также</span><span class="sxs-lookup"><span data-stu-id="7ea4a-122">See also</span></span>

- [<span data-ttu-id="7ea4a-123">Изменение деревьев XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ea4a-123">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
