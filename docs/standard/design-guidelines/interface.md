---
title: Разработка интерфейса
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: KrzysztofCwalina
ms.openlocfilehash: 1f982aa37f92b7270725574d949989ca120297d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026371"
---
# <a name="interface-design"></a><span data-ttu-id="df688-102">Разработка интерфейса</span><span class="sxs-lookup"><span data-stu-id="df688-102">Interface Design</span></span>
<span data-ttu-id="df688-103">Несмотря на то, что большинство интерфейсов API лучше всего моделируются с помощью классов и структур, бывают случаи, в которых интерфейсы больше подходят и являются единственным вариантом.</span><span class="sxs-lookup"><span data-stu-id="df688-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>  
  
 <span data-ttu-id="df688-104">Среда CLR не поддерживает множественное наследование (т. е. классы CLR, не могут наследоваться от более чем одного базового класса), но разрешает типы для реализации одного или нескольких интерфейсов, помимо наследования от базового класса.</span><span class="sxs-lookup"><span data-stu-id="df688-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="df688-105">Таким образом интерфейсы часто используются для получения эффекта множественного наследования.</span><span class="sxs-lookup"><span data-stu-id="df688-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="df688-106">Например <xref:System.IDisposable> — это интерфейс, позволяющий типы для поддержки disposability независимо от других иерархии наследования, в котором хочу участвовать.</span><span class="sxs-lookup"><span data-stu-id="df688-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>  
  
 <span data-ttu-id="df688-107">Другие ситуации, в какие определение интерфейса соответствующий пример — создание общий интерфейс, который может поддерживаться несколько типов, включая некоторые типы значений.</span><span class="sxs-lookup"><span data-stu-id="df688-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="df688-108">Типы значений не может наследовать от типов, отличных от <xref:System.ValueType>, но они могут реализовывать интерфейсы, с помощью интерфейса доступна только для предоставления общего базового типа.</span><span class="sxs-lookup"><span data-stu-id="df688-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>  
  
 <span data-ttu-id="df688-109">**✓ DO** Определите интерфейс, если требуется, чтобы некоторые общий API, которые должны поддерживаться набор типов, который включает типы значений.</span><span class="sxs-lookup"><span data-stu-id="df688-109">**✓ DO** define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>  
  
 <span data-ttu-id="df688-110">**✓ CONSIDER** определять интерфейс, если необходима поддержка его функциональные возможности для типов, являющихся производными от другого типа.</span><span class="sxs-lookup"><span data-stu-id="df688-110">**✓ CONSIDER** defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>  
  
 <span data-ttu-id="df688-111">**X AVOID** с помощью маркера интерфейсов (интерфейсы без членов).</span><span class="sxs-lookup"><span data-stu-id="df688-111">**X AVOID** using marker interfaces (interfaces with no members).</span></span>  
  
 <span data-ttu-id="df688-112">Если требуется пометить класс как имеющий определенных характеристик (маркер), как правило, используйте настраиваемый атрибут, а не интерфейс.</span><span class="sxs-lookup"><span data-stu-id="df688-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>  
  
 <span data-ttu-id="df688-113">**✓ DO** укажите по крайней мере один тип, который является реализацией интерфейса.</span><span class="sxs-lookup"><span data-stu-id="df688-113">**✓ DO** provide at least one type that is an implementation of an interface.</span></span>  
  
 <span data-ttu-id="df688-114">Это помогает проверить архитектуру интерфейса.</span><span class="sxs-lookup"><span data-stu-id="df688-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="df688-115">Например <xref:System.Collections.Generic.List%601> представляет собой реализацию <xref:System.Collections.Generic.IList%601> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="df688-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>  
  
 <span data-ttu-id="df688-116">**✓ DO** предоставляют по крайней мере один API, использующий каждый из определенных интерфейсов (метод, принимающий интерфейс как параметр или свойство с типом интерфейса).</span><span class="sxs-lookup"><span data-stu-id="df688-116">**✓ DO** provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>  
  
 <span data-ttu-id="df688-117">Это помогает проверить архитектуру интерфейс.</span><span class="sxs-lookup"><span data-stu-id="df688-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="df688-118">Например <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> потребляет <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="df688-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>  
  
 <span data-ttu-id="df688-119">**X DO NOT** добавление членов в интерфейс, который был доставлен.</span><span class="sxs-lookup"><span data-stu-id="df688-119">**X DO NOT** add members to an interface that has previously shipped.</span></span>  
  
 <span data-ttu-id="df688-120">Это нарушит реализаций интерфейса.</span><span class="sxs-lookup"><span data-stu-id="df688-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="df688-121">Чтобы избежать проблем управления версиями следует создать новый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="df688-121">You should create a new interface in order to avoid versioning problems.</span></span>  
  
 <span data-ttu-id="df688-122">За исключением ситуации, описанные в следующих рекомендаций как правило, выберите классы, а не интерфейсов в разработке повторно используемых библиотек управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="df688-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>  
  
 <span data-ttu-id="df688-123">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="df688-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="df688-124">*Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="df688-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df688-125">См. также</span><span class="sxs-lookup"><span data-stu-id="df688-125">See also</span></span>

- [<span data-ttu-id="df688-126">Рекомендации по разработке типов</span><span class="sxs-lookup"><span data-stu-id="df688-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="df688-127">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="df688-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
