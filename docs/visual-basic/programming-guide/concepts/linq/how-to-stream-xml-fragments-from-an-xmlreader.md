---
title: Практическое руководство. Потоковая передача фрагментов XML из XmlReader
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: ff22625767c4e0752ca19d5a315395934b566230
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397704"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>Последующее: потоковая передача фрагментов XML из XmlReader (Visual Basic)
При необходимости обработать большой XML-файл загрузка в память полного XML-дерева, возможно, будет неосуществима. В этом разделе показано, как обрабатывать фрагменты в потоке с помощью <xref:System.Xml.XmlReader>.  
  
 Одним из самых эффективных способов использования <xref:System.Xml.XmlReader> для чтения объектов <xref:System.Xml.Linq.XElement> является написание собственного метода оси. Метод оси, как правило, возвращает коллекцию, например <xref:System.Collections.Generic.IEnumerable%601> элементов <xref:System.Xml.Linq.XElement>, как показано в примере этого раздела. В пользовательском методе оси после создания XML-фрагмента с помощью вызова метода <xref:System.Xml.Linq.XNode.ReadFrom%2A> возвратите коллекцию, используя `yield return`. Тем самым в пользовательском методе оси обеспечивается семантика отложенного выполнения.  
  
 При создании XML-дерева из объекта <xref:System.Xml.XmlReader> модулю чтения <xref:System.Xml.XmlReader> должен быть указан обрабатываемый элемент. Метод <xref:System.Xml.Linq.XNode.ReadFrom%2A> не выполняет возврат до тех пор, пока не считает закрывающий тег элемента.  
  
 Если нужно создать частичное дерево, можно создать экземпляр <xref:System.Xml.XmlReader>, указать для модуля чтения узел, который должен быть преобразован в дерево <xref:System.Xml.Linq.XElement>, и создать объект <xref:System.Xml.Linq.XElement>.  
  
 В разделе [как выполнять потоковую передачу XML-фрагментов с доступом к сведениям заголовка (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md) содержатся сведения и пример потоковой передачи более сложного документа.  
  
 В статье [как выполнить потоковое преобразование больших XML-документов (Visual Basic)](how-to-perform-streaming-transform-of-large-xml-documents.md) содержится пример использования LINQ to XML для преобразования чрезвычайно больших XML-документов с сохранением небольшого объема памяти.  
  
## <a name="example"></a>Пример  
 В следующем примере создается пользовательский метод оси. Его можно запросить с помощью запроса LINQ. Пользовательский метод оси `StreamRootChildDoc` специально разработан для чтения документа с повторяющимся элементом `Child`.  
  
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
  
 В этом примере выводятся следующие данные:  
  
```console  
bbb  
ccc  
```  
  
 В этом примере документ-источник весьма невелик. Тем не менее, даже если бы он содержал миллионы элементов `Child`, для этого примера потребовался бы очень небольшой объем памяти.  
  
## <a name="see-also"></a>См. также раздел

- [Пошаговое руководство. Реализация IEnumerable(Of T) в Visual Basic](../../language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [Синтаксический анализ XML (Visual Basic)](parsing-xml.md)
