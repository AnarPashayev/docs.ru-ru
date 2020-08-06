---
title: Статически скомпилированные запросы (LINQ to XML) (C#)
description: Узнайте о статически скомпилированных запросах в LINQ to XML в C# и о том, чем они отличаются от запросов XPath, которые должны интерпретироваться в среде выполнения.
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: cd2e6a6507311d5fc17215a22c70bd0449292b6f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302312"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="d7bcb-103">Статически скомпилированные запросы (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d7bcb-103">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d7bcb-104">Одним из важнейших преимуществ LINQ to XML перед <xref:System.Xml.XmlDocument> с точки зрения производительности является то, что в LINQ to XML запросы компилируются статически, тогда как запросы XPath интерпретируются во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-104">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="d7bcb-105">Это встроенная функция LINQ to XML, поэтому вам не нужно будет принимать какие-либо подготовительные меры для ее использования, однако, чтобы сделать обоснованный выбор той или другой технологии, важно понимать их различие.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-105">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="d7bcb-106">Данное различие описано в текущем разделе.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-106">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="d7bcb-107">Сравнение статически скомпилированных запросов и языка XPath</span><span class="sxs-lookup"><span data-stu-id="d7bcb-107">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="d7bcb-108">В следующем примере показано, как получать элементы-потомки с указанным именем и атрибут с заданным значением.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-108">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="d7bcb-109">Далее представлено эквивалентное выражение XPath: `//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="d7bcb-109">The following is the equivalent XPath expression: `//Address[@Type='Shipping']`</span></span>
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d7bcb-110">Компилятор переписывает выражение запроса из этого примера с использованием синтаксиса запросов, основанных на методах.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-110">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="d7bcb-111">Код в следующем примере имеет синтаксис запросов, основанных на методах и приводит к получению таких же результатов, что и предыдущий код.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-111">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d7bcb-112">Метод <xref:System.Linq.Enumerable.Where%2A> является методом расширения.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-112">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="d7bcb-113">Дополнительные сведения см. в статье [Методы расширения](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d7bcb-113">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="d7bcb-114">Поскольку используется метод расширения <xref:System.Linq.Enumerable.Where%2A>, представленный выше запрос компилируется так, как показано далее.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-114">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="d7bcb-115">Этот пример приводит к получению в точности таких же результатов, что и два предыдущих примера.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-115">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="d7bcb-116">Таким образом, демонстрируется возможность эффективной компиляции запросов в вызовы методов со статическими ссылками.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-116">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="d7bcb-117">В сочетании с семантикой отложенного выполнения итераторов это позволяет повысить производительность.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-117">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="d7bcb-118">Дополнительные сведения о семантике отложенного выполнения итераторов см. в разделе [Отложенное выполнение и отложенное вычисление в LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d7bcb-118">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7bcb-119">В этих примерах показаны образцы кода, который может быть составлен компилятором.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-119">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="d7bcb-120">Действительная реализация может несколько отличаться от этих примеров, однако производительность останется такой же или приблизительно такой же.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-120">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="d7bcb-121">Выполнение выражений XPath с помощью XmlDocument</span><span class="sxs-lookup"><span data-stu-id="d7bcb-121">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="d7bcb-122">В следующем примере объект <xref:System.Xml.XmlDocument> используется для получения таких же результатов, что и в предыдущих примерах.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-122">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="d7bcb-123">Этот запрос возвращает такие же выходные данные, что и в примерах на основе LINQ to XML, за исключением того, что запрос LINQ to XML расставляет отступы в результирующем файле XML, а запрос <xref:System.Xml.XmlDocument> - нет.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-123">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="d7bcb-124">Однако производительность подхода на основе <xref:System.Xml.XmlDocument> в целом ниже, чем при использовании LINQ to XML, поскольку метод <xref:System.Xml.XmlNode.SelectNodes%2A> должен при каждом вызове выполнять следующие внутренние операции:</span><span class="sxs-lookup"><span data-stu-id="d7bcb-124">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="d7bcb-125">Анализирует строку, содержащую выражение XPath, и разбивает ее на лексемы.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-125">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="d7bcb-126">Проверяет лексемы, чтобы подтвердить правильность выражения XPath.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-126">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="d7bcb-127">Транслирует выражение во внутреннее дерево выражений.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-127">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="d7bcb-128">Проходит по узлам, выбирает соответствующие узлы на основании оценки выражения и добавляет их в набор результатов.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-128">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="d7bcb-129">При этом выполняется значительно больший объем работы, чем при использовании аналогичного запроса LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-129">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="d7bcb-130">Конкретный выигрыш по производительности зависит от типа запроса, однако в общем случае запросы LINQ to XML выполняют меньше работы и поэтому более эффективны, чем операции по оценке выражений XPath с помощью <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="d7bcb-130">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
