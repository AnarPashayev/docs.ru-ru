---
title: События LINQ to XML
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: d00f6f1b2a14ac73c1bcd4a1f74b9714ca304da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368820"
---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="4531b-102">События LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4531b-102">LINQ to XML Events (Visual Basic)</span></span>
<span data-ttu-id="4531b-103">События [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] позволяют получать уведомления, когда изменяется дерево XML.</span><span class="sxs-lookup"><span data-stu-id="4531b-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="4531b-104">Можно добавить события в экземпляр любого объекта <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="4531b-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="4531b-105">Обработчик события будет получать уведомления об изменениях объекта <xref:System.Xml.Linq.XObject> и всех его потомков.</span><span class="sxs-lookup"><span data-stu-id="4531b-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="4531b-106">Например, можно добавить обработчик события в корень дерева и обрабатывать все изменения дерева в этом обработчике события.</span><span class="sxs-lookup"><span data-stu-id="4531b-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="4531b-107">Примеры таких событий [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] см. в разделах <xref:System.Xml.Linq.XObject.Changing> и <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="4531b-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="4531b-108">Типы и события</span><span class="sxs-lookup"><span data-stu-id="4531b-108">Types and Events</span></span>  
 <span data-ttu-id="4531b-109">Используйте следующие типы при работе с событиями.</span><span class="sxs-lookup"><span data-stu-id="4531b-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="4531b-110">Type</span><span class="sxs-lookup"><span data-stu-id="4531b-110">Type</span></span>|<span data-ttu-id="4531b-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="4531b-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="4531b-112">Задает тип события, когда событие вызывается объектом <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="4531b-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="4531b-113">Предоставляет данные для событий <xref:System.Xml.Linq.XObject.Changing> и <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="4531b-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="4531b-114">При изменении дерева XML возникают следующие события.</span><span class="sxs-lookup"><span data-stu-id="4531b-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="4531b-115">Событие</span><span class="sxs-lookup"><span data-stu-id="4531b-115">Event</span></span>|<span data-ttu-id="4531b-116">Описание:</span><span class="sxs-lookup"><span data-stu-id="4531b-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="4531b-117">Возникает непосредственно перед тем, как объект <xref:System.Xml.Linq.XObject> или какой-либо его потомок изменяется.</span><span class="sxs-lookup"><span data-stu-id="4531b-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="4531b-118">Возникает, когда изменился объект <xref:System.Xml.Linq.XObject> или один из его потомков.</span><span class="sxs-lookup"><span data-stu-id="4531b-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4531b-119">Пример</span><span class="sxs-lookup"><span data-stu-id="4531b-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4531b-120">Описание:</span><span class="sxs-lookup"><span data-stu-id="4531b-120">Description</span></span>  
 <span data-ttu-id="4531b-121">События полезны, когда нужно поддержать какие-либо статистические данные в дереве XML.</span><span class="sxs-lookup"><span data-stu-id="4531b-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="4531b-122">Например, нужно рассчитать сумму элементов строки.</span><span class="sxs-lookup"><span data-stu-id="4531b-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="4531b-123">Следующий пример использует события для подсчета суммы всех дочерних элементов сложного элемента `Items`.</span><span class="sxs-lookup"><span data-stu-id="4531b-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4531b-124">Код</span><span class="sxs-lookup"><span data-stu-id="4531b-124">Code</span></span>  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="4531b-125">Комментарии</span><span class="sxs-lookup"><span data-stu-id="4531b-125">Comments</span></span>  
 <span data-ttu-id="4531b-126">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="4531b-126">This code produces the following output:</span></span>  
  
```console  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4531b-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4531b-127">See also</span></span>

- [<span data-ttu-id="4531b-128">Расширенное программирование LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4531b-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
