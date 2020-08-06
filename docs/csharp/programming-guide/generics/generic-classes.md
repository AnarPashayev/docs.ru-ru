---
title: Руководство по программированию на C#. Универсальные классы
description: Сведения об универсальных классах, используемых в коллекциях, например в связанных списках, хэш-таблицах, стеках, очередях и деревьях.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: 308f4328540e1001018942738d931be3d8be53ed
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301922"
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="2cc1b-103">Универсальные классы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="2cc1b-103">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="2cc1b-104">Универсальные классы инкапсулируют операции, которые не относятся к конкретному типу данных.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-104">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="2cc1b-105">Универсальные классы чаще всего используются для работы с коллекциями, такими как связанные списки, хэш-таблицы, стеки, очереди, деревья и т. д.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-105">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="2cc1b-106">Такие операции, как добавление и удаление элементов коллекции, по существу выполняются одинаково, независимо от типа хранимых данных.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-106">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="2cc1b-107">В большинстве случаев для этого используются классы коллекций. Рекомендуется выбирать те из них, которые представлены в библиотеке классов платформы .NET.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-107">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET class library.</span></span> <span data-ttu-id="2cc1b-108">Дополнительные сведения об использовании этих классов см. в разделе [Универсальные коллекции в .NET](../../../standard/generics/collections.md).</span><span class="sxs-lookup"><span data-stu-id="2cc1b-108">For more information about using these classes, see [Generic Collections in .NET](../../../standard/generics/collections.md).</span></span>  
  
 <span data-ttu-id="2cc1b-109">Как правило, при создании универсального класса сначала определяется конкретный класс, после чего его типы поочередно заменяются параметрами типов до тех пор, пока не будет достигнут необходимый баланс между степенью обобщения и удобством работы.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-109">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="2cc1b-110">При создании собственных универсальных классов необходимо учитывать следующие важные моменты:</span><span class="sxs-lookup"><span data-stu-id="2cc1b-110">When creating your own generic classes, important considerations include the following:</span></span>  
  
- <span data-ttu-id="2cc1b-111">Типы, которые требуется обобщить с использованием параметров типа.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-111">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="2cc1b-112">Как правило, чем больше типов параметризовано, тем более гибким и универсальным становится ваш код.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-112">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="2cc1b-113">Тем не менее слишком высокая степень обобщения может отрицательно сказаться на понятности создаваемого вами кода для других разработчиков.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-113">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
- <span data-ttu-id="2cc1b-114">Ограничения (если требуются), которые будут применяться к параметрам типа (см. раздел [Ограничения параметров типа](./constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="2cc1b-114">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](./constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="2cc1b-115">Рекомендуется применять максимально возможный объем ограничений, при котором вы по-прежнему сможете работать с необходимыми типами.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-115">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="2cc1b-116">Например, если универсальный класс будет использоваться только для работы со ссылочными типами, примените ограничение класса.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-116">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="2cc1b-117">Это позволит исключить случайное использование класса с типами значений и позволит использовать оператор `as` в отношении `T`, а также проверять наличие значений null.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-117">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
- <span data-ttu-id="2cc1b-118">Требуется ли разбивать универсальные функции между базовыми классами и подклассами.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-118">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="2cc1b-119">Поскольку универсальные классы могут выступать в качестве базовых классов, здесь необходимо учитывать те же принципы разработки, что и для классов, не являющихся универсальными.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-119">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="2cc1b-120">См. описание правил наследования от универсальных базовых классов далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-120">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
- <span data-ttu-id="2cc1b-121">Требуется ли реализовывать один или несколько универсальных интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-121">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="2cc1b-122">Например, при разработке класса, который будет использоваться для создания элементов коллекции на основе универсальных шаблонов, может потребоваться реализовать интерфейс <xref:System.IComparable%601>, где `T` — это тип вашего класса.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-122">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="2cc1b-123">Пример простого универсального класса можно найти в разделе [Введение в универсальные шаблоны](./index.md).</span><span class="sxs-lookup"><span data-stu-id="2cc1b-123">For an example of a simple generic class, see [Introduction to Generics](./index.md).</span></span>  
  
 <span data-ttu-id="2cc1b-124">Правила в отношении параметров типа и ограничений влияют на поведение универсального класса, особенно в контексте наследования и доступа к элементам.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-124">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="2cc1b-125">Прежде чем продолжить, необходимо ознакомиться с некоторыми терминами и понятиями.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-125">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="2cc1b-126">Ссылка на универсальный класс `Node<T>,` в клиентском коде может задаваться с использованием аргумента типа или путем создания закрытого сконструированного типа (`Node<int>`).</span><span class="sxs-lookup"><span data-stu-id="2cc1b-126">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="2cc1b-127">Кроме того, можно не задавать параметр типа (например, при указании универсального базового класса), чтобы определить открытый сконструированный тип (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="2cc1b-127">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="2cc1b-128">Универсальные классы могут наследоваться от конкретных, а также закрытых или открытых сконструированных базовых классов:</span><span class="sxs-lookup"><span data-stu-id="2cc1b-128">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 <span data-ttu-id="2cc1b-129">Классы, не являющиеся универсальными, то есть конкретные классы, могут наследоваться от закрытых сконструированных базовых классов. Наследование от аналогичных открытых классов или от параметров типа невозможно, поскольку во время выполнения клиентский код не может предоставить аргумент типа, необходимый для создания экземпляра базового класса.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-129">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 <span data-ttu-id="2cc1b-130">Универсальные классы, наследуемые от открытых сконструированных типов, должны предоставлять аргументы типа для любых параметров типа базового класса, которые не используются совместно с наследующим классом. Это продемонстрировано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="2cc1b-130">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 <span data-ttu-id="2cc1b-131">Универсальные классы, наследуемые от открытых сконструированных типов, должны задавать множество ограничений, которые явно или косвенно включают в себя все ограничения базового типа:</span><span class="sxs-lookup"><span data-stu-id="2cc1b-131">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 <span data-ttu-id="2cc1b-132">Универсальные типы могут использовать несколько параметров типа и ограничений, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="2cc1b-132">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 <span data-ttu-id="2cc1b-133">Открытые и закрытые сконструированные типы можно использовать в качестве параметров метода:</span><span class="sxs-lookup"><span data-stu-id="2cc1b-133">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 <span data-ttu-id="2cc1b-134">Если универсальный класс реализует интерфейс, все экземпляры такого класса можно привести к этому интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-134">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="2cc1b-135">Универсальные классы инвариантны.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-135">Generic classes are invariant.</span></span> <span data-ttu-id="2cc1b-136">Другими словами, если входной параметр задает `List<BaseClass>`, при попытке предоставить `List<DerivedClass>` возникает ошибка времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="2cc1b-136">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc1b-137">См. также</span><span class="sxs-lookup"><span data-stu-id="2cc1b-137">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="2cc1b-138">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="2cc1b-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2cc1b-139">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="2cc1b-139">Generics</span></span>](./index.md)
- [<span data-ttu-id="2cc1b-140">Сохранение состояния перечислителей</span><span class="sxs-lookup"><span data-stu-id="2cc1b-140">Saving the State of Enumerators</span></span>](https://docs.microsoft.com/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [<span data-ttu-id="2cc1b-141">Загадка по наследованию, часть 1</span><span class="sxs-lookup"><span data-stu-id="2cc1b-141">An Inheritance Puzzle, Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)
