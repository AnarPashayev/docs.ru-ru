---
title: Ошибки смешанного декларативного и императивного кода (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 30760999a264c81e16104c0c9b112d442ce66121
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591623"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="35bcb-102">Ошибки смешанного декларативного и императивного кода (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="35bcb-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="35bcb-103">содержит различные методы, которые позволяют прямо модифицировать XML-дерево.</span><span class="sxs-lookup"><span data-stu-id="35bcb-103">contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="35bcb-104">Можно добавить элементы, удалить элементы, изменить содержимое элемента, добавить атрибуты и т. п.</span><span class="sxs-lookup"><span data-stu-id="35bcb-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="35bcb-105">Интерфейс программирования описывается в разделе [Изменение деревьев XML (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="35bcb-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span> <span data-ttu-id="35bcb-106">Если выполняется переход в пределах одной оси, например <xref:System.Xml.Linq.XContainer.Elements%2A>, и при этом выполняется изменение XML-дерева, можно в итоге обнаружить некоторые неожиданные ошибки.</span><span class="sxs-lookup"><span data-stu-id="35bcb-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="35bcb-107">Этот вид ошибки иногда называется Halloween Problem.</span><span class="sxs-lookup"><span data-stu-id="35bcb-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="35bcb-108">Определение этой ошибки</span><span class="sxs-lookup"><span data-stu-id="35bcb-108">Definition of the Problem</span></span>  
 <span data-ttu-id="35bcb-109">При создании некоего кода с использованием LINQ, при котором выполняется последовательное прохождение по элементам коллекции, код пишется в декларативном стиле.</span><span class="sxs-lookup"><span data-stu-id="35bcb-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="35bcb-110">Это больше похоже на описание того, *что* именно требуется получить, а не *как* именно требуется выполнить задачу.</span><span class="sxs-lookup"><span data-stu-id="35bcb-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="35bcb-111">Если написать код, при котором 1) извлекается первый элемент, 2) выполняется его проверка согласно определенному условию, 3) выполняется его изменение и 4) выполняется его помещение назад в список элементов, то это означает, что это был бы императивный код.</span><span class="sxs-lookup"><span data-stu-id="35bcb-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="35bcb-112">При этом вы описываете, *как именно* следует выполнить задачу.</span><span class="sxs-lookup"><span data-stu-id="35bcb-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="35bcb-113">Смешение этих стилей кода в одной операции является источником неполадок.</span><span class="sxs-lookup"><span data-stu-id="35bcb-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="35bcb-114">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="35bcb-114">Consider the following:</span></span>  
  
 <span data-ttu-id="35bcb-115">Предположим, дан список из трех элементов (a, b и c):</span><span class="sxs-lookup"><span data-stu-id="35bcb-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="35bcb-116">Теперь предположим, что необходимо пройти по связанному списку, добавив три новых пункта (a', b' и c').</span><span class="sxs-lookup"><span data-stu-id="35bcb-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="35bcb-117">При этом необходимо, чтобы результирующий список выглядел так:</span><span class="sxs-lookup"><span data-stu-id="35bcb-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="35bcb-118">Пишется код, который последовательно обращается к элементам списка и для каждого пункта добавляет новый пункт после него.</span><span class="sxs-lookup"><span data-stu-id="35bcb-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="35bcb-119">При этом код распознает элемент `a` и вставит элемент `a'` после него.</span><span class="sxs-lookup"><span data-stu-id="35bcb-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="35bcb-120">Теперь код перейдет к следующему узлу списка, которым является `a'`!</span><span class="sxs-lookup"><span data-stu-id="35bcb-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="35bcb-121">После чего он добавляет новый элемент списка - `a''`.</span><span class="sxs-lookup"><span data-stu-id="35bcb-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="35bcb-122">Как это следовало бы решить в реальной ситуации?</span><span class="sxs-lookup"><span data-stu-id="35bcb-122">How would you solve this in the real world?</span></span> <span data-ttu-id="35bcb-123">Можно сделать копию оригинального списка, после чего создать полностью новый список.</span><span class="sxs-lookup"><span data-stu-id="35bcb-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="35bcb-124">Или, если вы пишете чисто императивный код, можно найти первый пункт, добавить новый пункт и перейти на два шага вперед по списку, чтобы перескочить элемент, который был только что добавлен.</span><span class="sxs-lookup"><span data-stu-id="35bcb-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="35bcb-125">Добавление при последовательном переходе</span><span class="sxs-lookup"><span data-stu-id="35bcb-125">Adding While Iterating</span></span>  
 <span data-ttu-id="35bcb-126">Например, требуется написать некоторый код, при помощи которого для каждого элемента дерева создается его дубликат:</span><span class="sxs-lookup"><span data-stu-id="35bcb-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="35bcb-127">Этот код представляет собой бесконечный цикл.</span><span class="sxs-lookup"><span data-stu-id="35bcb-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="35bcb-128">Инструкция `foreach` последовательно применяется ко всей оси `Elements()`, при этом добавляются новые элементы к элементу `doc`.</span><span class="sxs-lookup"><span data-stu-id="35bcb-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="35bcb-129">После этого она переходит на только что добавленные элементы.</span><span class="sxs-lookup"><span data-stu-id="35bcb-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="35bcb-130">И поскольку она выделяет память для новых объектов на каждом шаге, она захватит всю доступную память.</span><span class="sxs-lookup"><span data-stu-id="35bcb-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="35bcb-131">Эту неполадку можно устранить за счет переноса массива в память, используя стандартный оператор запросов <xref:System.Linq.Enumerable.ToList%2A> следующим образом.</span><span class="sxs-lookup"><span data-stu-id="35bcb-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="35bcb-132">Теперь код работает, как и положено.</span><span class="sxs-lookup"><span data-stu-id="35bcb-132">Now the code works.</span></span> <span data-ttu-id="35bcb-133">В итоге получается следующее XML-дерево:</span><span class="sxs-lookup"><span data-stu-id="35bcb-133">The resulting XML tree is the following:</span></span>  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="35bcb-134">Удаление элементов при последовательном переходе</span><span class="sxs-lookup"><span data-stu-id="35bcb-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="35bcb-135">Если требуется удалить все узлы, размещенные на определенном уровне, может возникнуть искушение попробовать реализовать это так:</span><span class="sxs-lookup"><span data-stu-id="35bcb-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="35bcb-136">Однако этот код не выполнит поставленной задачи.</span><span class="sxs-lookup"><span data-stu-id="35bcb-136">However, this does not do what you want.</span></span> <span data-ttu-id="35bcb-137">В такой ситуации после удаления первого элемента A он удаляется из XML-дерева, которое содержится в корне, при этом коду метода элементов (Elements method), который выполняет последовательный переход, не удастся найти следующий элемент.</span><span class="sxs-lookup"><span data-stu-id="35bcb-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="35bcb-138">Предыдущий код представит следующий вывод.</span><span class="sxs-lookup"><span data-stu-id="35bcb-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="35bcb-139">Решение снова заключается в вызове <xref:System.Linq.Enumerable.ToList%2A>, чтобы материализовать коллекцию следующим образом.</span><span class="sxs-lookup"><span data-stu-id="35bcb-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="35bcb-140">Выводятся следующие результаты.</span><span class="sxs-lookup"><span data-stu-id="35bcb-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="35bcb-141">Кроме того, можно совсем исключить итерацию за счет вызова <xref:System.Xml.Linq.XElement.RemoveAll%2A> на родительском элементе.</span><span class="sxs-lookup"><span data-stu-id="35bcb-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="35bcb-142">Почему LINQ не может автоматически обрабатывать такие ошибки?</span><span class="sxs-lookup"><span data-stu-id="35bcb-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="35bcb-143">Одним из подходов может быть вызов всех элементов в память, вместо того чтобы проводить неспешное вычисление каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="35bcb-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="35bcb-144">Однако это может негативно отразиться на производительности и загрузить память.</span><span class="sxs-lookup"><span data-stu-id="35bcb-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="35bcb-145">Фактически, если бы LINQ и (LINQ to XML) использовали этот подход, он бы оказался неудачным в реальных ситуациях.</span><span class="sxs-lookup"><span data-stu-id="35bcb-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="35bcb-146">Другой возможный подход мог бы реализоваться путем введения некоего синтаксиса транзакций в LINQ и использования компилятора для попытки анализа кода и определения того, необходимо ли материализовать какую-то конкретную коллекцию.</span><span class="sxs-lookup"><span data-stu-id="35bcb-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="35bcb-147">Однако попытка определения всего кода с побочными эффектами чрезвычайно сложна.</span><span class="sxs-lookup"><span data-stu-id="35bcb-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="35bcb-148">Рассмотрим следующий код.</span><span class="sxs-lookup"><span data-stu-id="35bcb-148">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="35bcb-149">Такому коду для проведения анализа потребуется анализировать методы TestSomeCondition и DoMyProjection, а также все методы, которые вызывают их, чтобы определить, есть ли у кода какие-либо побочные эффекты.</span><span class="sxs-lookup"><span data-stu-id="35bcb-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="35bcb-150">Однако коду анализа не удавалось просто искать код, в котором есть побочные эффекты.</span><span class="sxs-lookup"><span data-stu-id="35bcb-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="35bcb-151">Для этого потребовалось бы выбрать только тот код, у которого есть побочные эффекты на дочерних элементах `root`.</span><span class="sxs-lookup"><span data-stu-id="35bcb-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="35bcb-152">LINQ to XML не пытается выполнить такой анализ.</span><span class="sxs-lookup"><span data-stu-id="35bcb-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="35bcb-153">Поэтому задача избежания таких проблем лежит на вас.</span><span class="sxs-lookup"><span data-stu-id="35bcb-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="35bcb-154">Руководство</span><span class="sxs-lookup"><span data-stu-id="35bcb-154">Guidance</span></span>  
 <span data-ttu-id="35bcb-155">Во-первых, не стоит смешивать декларативный и императивный код.</span><span class="sxs-lookup"><span data-stu-id="35bcb-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="35bcb-156">Даже если вам точно известна семантика ваших коллекций и методов, которые применяются для изменения XML-дерева, если удастся создать некий код, в котором такие категории проблем невозможны, код все равно потребуется поддерживать другим разработчикам в будущем, а для них это не всегда может быть так же ясно, как для вас.</span><span class="sxs-lookup"><span data-stu-id="35bcb-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="35bcb-157">Если смешать декларативный и императивный стили, то код значительно усложнится.</span><span class="sxs-lookup"><span data-stu-id="35bcb-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="35bcb-158">Если удастся написать код, который материализует коллекцию таким образом, что эти проблемы удастся избежать, отметьте это в комментариях кода, чтобы другие программисты понимали, как это сделано.</span><span class="sxs-lookup"><span data-stu-id="35bcb-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="35bcb-159">Во-вторых, если требования производительности и другие условия позволяют, используйте только декларативный код.</span><span class="sxs-lookup"><span data-stu-id="35bcb-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="35bcb-160">Не следует изменять существующее XML-дерево.</span><span class="sxs-lookup"><span data-stu-id="35bcb-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="35bcb-161">Лучше создать новое.</span><span class="sxs-lookup"><span data-stu-id="35bcb-161">Generate a new one.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
 