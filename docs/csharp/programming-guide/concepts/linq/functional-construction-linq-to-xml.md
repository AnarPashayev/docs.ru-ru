---
title: Функциональное построение (LINQ to XML) (C#)
description: Узнайте, как в C# программный интерфейс LINQ to XML обеспечивает функциональное построение — возможность создания XML-дерева одной инструкцией.
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: f209a7ef2a4597ec8eeccb3083b77223a27e7a65
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103772"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="b640a-103">Функциональное построение (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b640a-103">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="b640a-104">предоставляет эффективный способ создания XML-элементов, который называется *функциональным построением*.</span><span class="sxs-lookup"><span data-stu-id="b640a-104">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="b640a-105">Функциональное построение — это возможность создать XML-дерево одной инструкцией.</span><span class="sxs-lookup"><span data-stu-id="b640a-105">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="b640a-106">Существует несколько основных функций интерфейса программирования [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], обеспечивающих функциональное построение.</span><span class="sxs-lookup"><span data-stu-id="b640a-106">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="b640a-107">Конструктор <xref:System.Xml.Linq.XElement> принимает различные типы аргументов для содержимого.</span><span class="sxs-lookup"><span data-stu-id="b640a-107">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="b640a-108">Например, можно передать еще один объект <xref:System.Xml.Linq.XElement>, который станет дочерним элементом.</span><span class="sxs-lookup"><span data-stu-id="b640a-108">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="b640a-109">Можно передать объект <xref:System.Xml.Linq.XAttribute>, который станет атрибутом элемента.</span><span class="sxs-lookup"><span data-stu-id="b640a-109">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="b640a-110">Можно также передать любой другой тип объекта, который будет преобразован в строку и станет текстовым содержимым элемента.</span><span class="sxs-lookup"><span data-stu-id="b640a-110">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="b640a-111">Конструктор <xref:System.Xml.Linq.XElement> принимает массив `params` типа <xref:System.Object>, так что этому конструктору можно передать любое количество объектов.</span><span class="sxs-lookup"><span data-stu-id="b640a-111">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="b640a-112">Это позволяет создавать элементы со сложным содержимым.</span><span class="sxs-lookup"><span data-stu-id="b640a-112">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="b640a-113">Если объект реализует интерфейс <xref:System.Collections.Generic.IEnumerable%601>, коллекция в этом объекте перечисляется и добавляются все элементы коллекции.</span><span class="sxs-lookup"><span data-stu-id="b640a-113">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="b640a-114">Если коллекция содержит объекты <xref:System.Xml.Linq.XElement> или <xref:System.Xml.Linq.XAttribute>, каждый ее элемент добавляется отдельно.</span><span class="sxs-lookup"><span data-stu-id="b640a-114">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="b640a-115">Это важно, так как позволяет передавать результаты запроса LINQ конструктору.</span><span class="sxs-lookup"><span data-stu-id="b640a-115">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="b640a-116">Эти возможности позволяют использовать код для создания XML-деревьев.</span><span class="sxs-lookup"><span data-stu-id="b640a-116">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="b640a-117">Ниже представлен пример такого кода.</span><span class="sxs-lookup"><span data-stu-id="b640a-117">The following is an example:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="b640a-118">Эти возможности позволяют также написать код, в котором используются результаты запросов LINQ при создании дерева XML, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="b640a-118">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="b640a-119">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="b640a-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  