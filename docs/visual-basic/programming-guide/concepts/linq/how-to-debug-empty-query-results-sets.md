---
title: Практическое руководство. Отладка пустых наборов результатов запроса (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 076e7109dc89294ba0c1706bf9a66120e6a0b85d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630978"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="8acb7-102">Практическое руководство. Отладка пустых наборов результатов запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8acb7-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>

<span data-ttu-id="8acb7-103">Одной из наиболее типичных проблем при запросах к XML-деревьям является то, что, если XML-дерево содержит пространство имен по умолчанию, разработчик иногда пишет запрос так, как если бы XML-код не располагался в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="8acb7-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="8acb7-104">Первый набор примеров в данном разделе показывает типичный способ загрузки XML в пространстве имен по умолчанию и неправильного запроса к нему.</span><span class="sxs-lookup"><span data-stu-id="8acb7-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>

<span data-ttu-id="8acb7-105">Второй набор примеров показывает необходимые исправления для запроса XML в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="8acb7-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="8acb7-106">Дополнительные сведения см. в разделе [Работа с пространствами имен XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="8acb7-106">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>

## <a name="example"></a><span data-ttu-id="8acb7-107">Пример</span><span class="sxs-lookup"><span data-stu-id="8acb7-107">Example</span></span>

<span data-ttu-id="8acb7-108">Этот пример показывает создание XML в пространстве имен, а также запрос, возвращающий пустой результирующий набор.</span><span class="sxs-lookup"><span data-stu-id="8acb7-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

<span data-ttu-id="8acb7-109">Этот пример выдает следующий результат:</span><span class="sxs-lookup"><span data-stu-id="8acb7-109">This example produces the following result:</span></span>

```
Result set follows:
End of result set
```

## <a name="example"></a><span data-ttu-id="8acb7-110">Пример</span><span class="sxs-lookup"><span data-stu-id="8acb7-110">Example</span></span>

<span data-ttu-id="8acb7-111">Этот пример показывает создание XML в пространстве имен, а также запрос, код которого написан правильно.</span><span class="sxs-lookup"><span data-stu-id="8acb7-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>

<span data-ttu-id="8acb7-112">Решением является объявление и инициализация глобального пространства имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8acb7-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="8acb7-113">При этом все свойства XML помещаются в пространство имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8acb7-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="8acb7-114">Для последующей правильной работы примера не требуется больше никаких изменений.</span><span class="sxs-lookup"><span data-stu-id="8acb7-114">No other modifications are required to the example to make it work properly.</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="8acb7-115">Этот пример выдает следующий результат:</span><span class="sxs-lookup"><span data-stu-id="8acb7-115">This example produces the following result:</span></span>

```
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="8acb7-116">См. также</span><span class="sxs-lookup"><span data-stu-id="8acb7-116">See also</span></span>

- [<span data-ttu-id="8acb7-117">Основные запросы (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8acb7-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
