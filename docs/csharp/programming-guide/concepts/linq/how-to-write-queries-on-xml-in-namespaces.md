---
title: Создание запросов к XML в пространствах имен (C#)
description: Сведения о создании запросов к XML в пространствах имен. В таких запросах необходимо использовать объекты XName с правильно заданным пространством имен.
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 64eb9df1cde3b434a11e2e5410aab96993dc0fa1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303183"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="77d1e-104">Создание запросов к XML в пространствах имен (C#)</span><span class="sxs-lookup"><span data-stu-id="77d1e-104">How to write queries on XML in namespaces (C#)</span></span>
<span data-ttu-id="77d1e-105">Для записи XML-запросов в пространстве имен необходимо использовать объекты <xref:System.Xml.Linq.XName> с правильно заданным пространством имен.</span><span class="sxs-lookup"><span data-stu-id="77d1e-105">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="77d1e-106">Что касается языка C#, то наиболее распространенный подход состоит в инициализации <xref:System.Xml.Linq.XNamespace> с помощью строки, содержащей URI, а затем использовании перегруженного оператора сложения для объединения пространства имен с локальным именем.</span><span class="sxs-lookup"><span data-stu-id="77d1e-106">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="77d1e-107">Первый набор примеров в данном разделе показывает порядок создания XML-дерева в пространстве имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="77d1e-107">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="77d1e-108">Второй набор показывает порядок создания XML-дерева в пространстве имен с префиксом.</span><span class="sxs-lookup"><span data-stu-id="77d1e-108">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77d1e-109">Пример</span><span class="sxs-lookup"><span data-stu-id="77d1e-109">Example</span></span>  
 <span data-ttu-id="77d1e-110">В следующем примере создается XML-дерево, находящееся в пространстве имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="77d1e-110">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="77d1e-111">Затем извлекается коллекция элементов.</span><span class="sxs-lookup"><span data-stu-id="77d1e-111">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="77d1e-112">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="77d1e-112">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="77d1e-113">Пример</span><span class="sxs-lookup"><span data-stu-id="77d1e-113">Example</span></span>  
 <span data-ttu-id="77d1e-114">В C# порядок составления запросов одинаков как при выполнении запросов к XML-дереву, использующему пространство имен с префиксом, так и при выполнении запросов к XML-дереву, находящемуся в пространстве имен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="77d1e-114">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="77d1e-115">В следующем примере создается XML-дерево, находящееся в пространстве имен с префиксом.</span><span class="sxs-lookup"><span data-stu-id="77d1e-115">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="77d1e-116">Затем извлекается коллекция элементов.</span><span class="sxs-lookup"><span data-stu-id="77d1e-116">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="77d1e-117">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="77d1e-117">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="77d1e-118">См. также</span><span class="sxs-lookup"><span data-stu-id="77d1e-118">See also</span></span>

- [<span data-ttu-id="77d1e-119">Обзор пространств имен (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="77d1e-119">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
