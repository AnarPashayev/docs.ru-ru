---
title: Сравнение запросов к XML-документам Запросы к XElement (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
ms.openlocfilehash: 500b1e58663ef6aca052850ad7994687e2cc36f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817725"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a><span data-ttu-id="082fa-102">Сравнение запросов к XML-документам Запросы к XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="082fa-102">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>
<span data-ttu-id="082fa-103">При загрузке документа через <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> обратите внимание на то, что запросы придется составлять не так, как при загрузке через <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="082fa-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="082fa-104">Сравнение XDocument.Load и XElement.Load</span><span class="sxs-lookup"><span data-stu-id="082fa-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="082fa-105">При загрузке XML-документа в <xref:System.Xml.Linq.XElement> через <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XElement> в корне XML-дерева содержит корневой элемент загруженного документа.</span><span class="sxs-lookup"><span data-stu-id="082fa-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="082fa-106">Однако при загрузке этого же XML-документа в <xref:System.Xml.Linq.XDocument> через <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> корень дерева - это узел <xref:System.Xml.Linq.XDocument>, а элемент корня загруженного документа - это один разрешенный дочерний узел <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="082fa-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="082fa-107">Оси [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] работают в зависимости от корневого узла.</span><span class="sxs-lookup"><span data-stu-id="082fa-107">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="082fa-108">В этом первом примере выполняется загрузка XML-дерева при помощи <xref:System.Xml.Linq.XElement.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="082fa-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="082fa-109">Затем выполняется запрос по дочерним элементам корня дерева.</span><span class="sxs-lookup"><span data-stu-id="082fa-109">It then queries for the child elements of the root of the tree.</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="082fa-110">Как и ожидается, выполняется вывод следующих данных:</span><span class="sxs-lookup"><span data-stu-id="082fa-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="082fa-111">Следующий пример такой же, как и пример выше, за исключением того, что XML-дерево загружается в <xref:System.Xml.Linq.XDocument>, а не в <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="082fa-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="082fa-112">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="082fa-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="082fa-113">Обратите внимание, что при таком же запросе выводится только узел `Root`, а не три дочерних узла.</span><span class="sxs-lookup"><span data-stu-id="082fa-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="082fa-114">Одним из подходов при этом может быть использование свойства <xref:System.Xml.Linq.XDocument.Root%2A> перед доступом к методам оси:</span><span class="sxs-lookup"><span data-stu-id="082fa-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="082fa-115">Теперь на этот запрос выводятся те же результаты, что и при запросе по дереву, корень которого размещен в <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="082fa-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="082fa-116">Пример выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="082fa-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="082fa-117">См. также</span><span class="sxs-lookup"><span data-stu-id="082fa-117">See also</span></span>

- [<span data-ttu-id="082fa-118">Базовые запросы (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="082fa-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
