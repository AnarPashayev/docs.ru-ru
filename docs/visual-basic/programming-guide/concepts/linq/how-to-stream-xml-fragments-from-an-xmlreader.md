---
title: Практическое руководство. Stream XML-фрагментов из XmlReader (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: 8c5aa1afff983f3763bbf7c74268eba622df7751
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614900"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="681e6-102">Практическое руководство. Stream XML-фрагментов из XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="681e6-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="681e6-103">При необходимости обработать большой XML-файл загрузка в память полного XML-дерева, возможно, будет неосуществима.</span><span class="sxs-lookup"><span data-stu-id="681e6-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="681e6-104">В этом разделе показано, как обрабатывать фрагменты в потоке с помощью <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="681e6-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="681e6-105">Одним из самых эффективных способов использования <xref:System.Xml.XmlReader> для чтения объектов <xref:System.Xml.Linq.XElement> является написание собственного метода оси.</span><span class="sxs-lookup"><span data-stu-id="681e6-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="681e6-106">Метод оси, как правило, возвращает коллекцию, например <xref:System.Collections.Generic.IEnumerable%601> элементов <xref:System.Xml.Linq.XElement>, как показано в примере этого раздела.</span><span class="sxs-lookup"><span data-stu-id="681e6-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="681e6-107">В пользовательском методе оси после создания XML-фрагмента с помощью вызова метода <xref:System.Xml.Linq.XNode.ReadFrom%2A> возвратите коллекцию, используя `yield return`.</span><span class="sxs-lookup"><span data-stu-id="681e6-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="681e6-108">Тем самым в пользовательском методе оси обеспечивается семантика отложенного выполнения.</span><span class="sxs-lookup"><span data-stu-id="681e6-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="681e6-109">При создании XML-дерева из объекта <xref:System.Xml.XmlReader> модулю чтения <xref:System.Xml.XmlReader> должен быть указан обрабатываемый элемент.</span><span class="sxs-lookup"><span data-stu-id="681e6-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="681e6-110">Метод <xref:System.Xml.Linq.XNode.ReadFrom%2A> не выполняет возврат до тех пор, пока не считает закрывающий тег элемента.</span><span class="sxs-lookup"><span data-stu-id="681e6-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="681e6-111">Если нужно создать частичное дерево, можно создать экземпляр <xref:System.Xml.XmlReader>, указать для модуля чтения узел, который должен быть преобразован в дерево <xref:System.Xml.Linq.XElement>, и создать объект <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="681e6-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="681e6-112">В разделе [Практическое руководство. Stream XML-фрагментов с доступом к сведениям заголовка (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) содержит сведения и пример потоковой передачи более сложного документа.</span><span class="sxs-lookup"><span data-stu-id="681e6-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="681e6-113">В разделе [Практическое руководство. Выполнение потокового преобразования крупных XML-документов (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) содержит пример использования LINQ to XML для преобразования чрезвычайно больших XML-документов при сохранении небольшой потребности в памяти.</span><span class="sxs-lookup"><span data-stu-id="681e6-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="681e6-114">Пример</span><span class="sxs-lookup"><span data-stu-id="681e6-114">Example</span></span>  
 <span data-ttu-id="681e6-115">В следующем примере создается пользовательский метод оси.</span><span class="sxs-lookup"><span data-stu-id="681e6-115">This example creates a custom axis method.</span></span> <span data-ttu-id="681e6-116">Его можно запросить с помощью запроса [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="681e6-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="681e6-117">Пользовательский метод оси `StreamRootChildDoc` специально разработан для чтения документа с повторяющимся элементом `Child`.</span><span class="sxs-lookup"><span data-stu-id="681e6-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim markup = "<Root>" &  
                     "  <Child Key=""01"">" &  
                     "    <GrandChild>aaa</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""02"">" &  
                     "    <GrandChild>bbb</GrandChild>" &  
                     "  </Child>" &  
                     "  <Child Key=""03"">" &  
                     "    <GrandChild>ccc</GrandChild>" &  
                     "  </Child>" &  
                     "</Root>"  
  
        Dim grandChildData =  
             From el In New StreamRootChildDoc(New IO.StringReader(markup))  
             Where CInt(el.@Key) > 1  
             Select el.<GrandChild>.Value  
  
        For Each s In grandChildData  
            Console.WriteLine(s)  
        Next  
    End Sub  
End Module  
  
Public Class StreamRootChildDoc  
    Implements IEnumerable(Of XElement)  
  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
    End Sub  
  
    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator  
        Return New StreamChildEnumerator(_stringReader)  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator  
        Return Me.GetEnumerator()  
    End Function  
End Class  
  
Public Class StreamChildEnumerator  
    Implements IEnumerator(Of XElement)  
  
    Private _current As XElement  
    Private _reader As Xml.XmlReader  
    Private _stringReader As IO.StringReader  
  
    Public Sub New(ByVal stringReader As IO.StringReader)  
        _stringReader = stringReader  
        _reader = Xml.XmlReader.Create(_stringReader)  
        _reader.MoveToContent()  
    End Sub  
  
    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current  
        Get  
            Return _current  
        End Get  
    End Property  
  
    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current  
        Get  
            Return Me.Current  
        End Get  
    End Property  
  
    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext  
        While _reader.Read()  
            Select Case _reader.NodeType  
                Case Xml.XmlNodeType.Element  
                    Dim el = TryCast(XElement.ReadFrom(_reader), XElement)  
                    If el IsNot Nothing Then  
                        _current = el  
                        Return True  
                    End If  
            End Select  
        End While  
  
        Return False  
    End Function  
  
    Public Sub Reset() Implements IEnumerator.Reset  
        _reader = Xml.XmlReader.Create(_stringReader)  
        _reader.MoveToContent()  
    End Sub  
  
#Region "IDisposable Support"  
    Private disposedValue As Boolean ' To detect redundant calls  
  
    ' IDisposable  
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)  
        If Not Me.disposedValue Then  
            If disposing Then  
                _reader.Close()  
            End If  
        End If  
        Me.disposedValue = True  
    End Sub  
  
    Public Sub Dispose() Implements IDisposable.Dispose  
        Dispose(True)  
        GC.SuppressFinalize(Me)  
    End Sub  
#End Region  
  
End Class  
```  
  
 <span data-ttu-id="681e6-118">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="681e6-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="681e6-119">В этом примере документ-источник весьма невелик.</span><span class="sxs-lookup"><span data-stu-id="681e6-119">In this example, the source document is very small.</span></span> <span data-ttu-id="681e6-120">Тем не менее, даже если бы он содержал миллионы элементов `Child`, для этого примера потребовался бы очень небольшой объем памяти.</span><span class="sxs-lookup"><span data-stu-id="681e6-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681e6-121">См. также</span><span class="sxs-lookup"><span data-stu-id="681e6-121">See also</span></span>

- [<span data-ttu-id="681e6-122">Пошаговое руководство: Реализация IEnumerable(Of T) в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="681e6-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [<span data-ttu-id="681e6-123">Синтаксический анализ XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="681e6-123">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
