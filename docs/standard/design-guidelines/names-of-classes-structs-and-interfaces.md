---
title: Имена классов, структур и интерфейсов
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
author: KrzysztofCwalina
ms.openlocfilehash: c0790cd20daf859ec81e2252dc9bce46673daf90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945513"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="f4160-102">Имена классов, структур и интерфейсов</span><span class="sxs-lookup"><span data-stu-id="f4160-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="f4160-103">Рекомендации по именованию, следующие за применяются к именованию общий тип.</span><span class="sxs-lookup"><span data-stu-id="f4160-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="f4160-104">**✓ DO** именах классов и структур с существительные и субстантивные словосочетания, с помощью PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="f4160-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="f4160-105">Это отличает имена типов из методов, которые именуются с помощью команды фраз.</span><span class="sxs-lookup"><span data-stu-id="f4160-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="f4160-106">**✓ DO** имя интерфейсы прилагательных фраз или время от времени с существительные и субстантивные словосочетания.</span><span class="sxs-lookup"><span data-stu-id="f4160-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="f4160-107">Существительные и субстантивные словосочетания должен использоваться редко, и они могут указывать, что тип должен быть абстрактным классом и не интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="f4160-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="f4160-108">**X DO NOT** использовать в именах префикс (например, «C»).</span><span class="sxs-lookup"><span data-stu-id="f4160-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="f4160-109">**✓ CONSIDER** конечное имя производных классов с именем базового класса.</span><span class="sxs-lookup"><span data-stu-id="f4160-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="f4160-110">Это очень удобным для чтения и четко рассказывает о связи.</span><span class="sxs-lookup"><span data-stu-id="f4160-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="f4160-111">Примеры из этого кода —: `ArgumentOutOfRangeException`, которого представляет собой из `Exception`, и `SerializableAttribute`, который относится к типу из `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="f4160-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="f4160-112">Тем не менее очень важно использовать разумно этой рекомендации; например `Button` класс относится к типу из `Control` событий, несмотря на то что `Control` не отображается в его имени.</span><span class="sxs-lookup"><span data-stu-id="f4160-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="f4160-113">**✓ DO** префикса для имени интерфейса с буквы I, чтобы указать, что тип является интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="f4160-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="f4160-114">Например `IComponent` (описательное существительное), `ICustomAttributeProvider` (субстантивное словосочетание), и `IPersistable` (прилагательными) являются именами соответствующий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="f4160-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="f4160-115">Как и в случае с другими именами типов, избегайте сокращений.</span><span class="sxs-lookup"><span data-stu-id="f4160-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="f4160-116">**✓ DO** убедитесь, что имена отличаются только по «I» префикс в имени интерфейса, при определении пары класс — интерфейс, где класс является стандартной реализации интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f4160-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="f4160-117">Имена параметров универсального типа</span><span class="sxs-lookup"><span data-stu-id="f4160-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="f4160-118">Универсальные шаблоны были добавлены в .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="f4160-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="f4160-119">Компонент появился новый тип идентификатора называется *параметр типа*.</span><span class="sxs-lookup"><span data-stu-id="f4160-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="f4160-120">**✓ DO** имя описательные имена параметров универсального типа, если имя не полностью интуитивно понятными и описательное имя могут быть.</span><span class="sxs-lookup"><span data-stu-id="f4160-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="f4160-121">**✓ CONSIDER** с помощью `T` как имя параметра типа для типов с одним параметром типа одной буквы.</span><span class="sxs-lookup"><span data-stu-id="f4160-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="f4160-122">**✓ DO** префикса описательным именам параметров типа с `T`.</span><span class="sxs-lookup"><span data-stu-id="f4160-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="f4160-123">**✓ CONSIDER** указывать ограничения накладываемые на параметр типа в имени параметра.</span><span class="sxs-lookup"><span data-stu-id="f4160-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="f4160-124">Например, параметр с ограничением `ISession` может называться `TSession`.</span><span class="sxs-lookup"><span data-stu-id="f4160-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="f4160-125">Имена общих типов</span><span class="sxs-lookup"><span data-stu-id="f4160-125">Names of Common Types</span></span>  
 <span data-ttu-id="f4160-126">**✓ DO** следуйте инструкциям, описанным в следующей таблице, при именовании типов, производных от или реализовывать некоторые типы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4160-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="f4160-127">Базовый тип</span><span class="sxs-lookup"><span data-stu-id="f4160-127">Base Type</span></span>|<span data-ttu-id="f4160-128">Производные реализации рекомендации типа</span><span class="sxs-lookup"><span data-stu-id="f4160-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="f4160-129">**✓ DO** добавляется суффикс «Attribute» к именам классов пользовательских атрибутов.</span><span class="sxs-lookup"><span data-stu-id="f4160-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="f4160-130">**✓ DO** добавляется суффикс «EventHandler» к именам делегатов, которые используются в событиях.</span><span class="sxs-lookup"><span data-stu-id="f4160-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="f4160-131">**✓ DO** добавляется суффикс «Callback» к именам делегатов, отличные от тех, которые используются в качестве обработчиков событий.</span><span class="sxs-lookup"><span data-stu-id="f4160-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="f4160-132">**X DO NOT** добавляется суффикс «Делегат» делегат.</span><span class="sxs-lookup"><span data-stu-id="f4160-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="f4160-133">**✓ DO** добавляется суффикс «EventArgs.»</span><span class="sxs-lookup"><span data-stu-id="f4160-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="f4160-134">**X DO NOT** наследовать от этого класса; используйте ключевое слово поддерживается в используемом языке вместо; например, в C#, используйте `enum` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="f4160-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="f4160-135">**X DO NOT** добавляется суффикс «Enum» или «Флаг».</span><span class="sxs-lookup"><span data-stu-id="f4160-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="f4160-136">**✓ DO** добавляется суффикс «Исключение».</span><span class="sxs-lookup"><span data-stu-id="f4160-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="f4160-137">**✓ DO** добавляется суффикс «Словарь».</span><span class="sxs-lookup"><span data-stu-id="f4160-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="f4160-138">Обратите внимание, что `IDictionary` — это особый тип коллекции, но это правило имеет приоритет над в более общем случае рекомендуется коллекций, ниже.</span><span class="sxs-lookup"><span data-stu-id="f4160-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="f4160-139">**✓ DO** добавляется суффикс «Коллекция».</span><span class="sxs-lookup"><span data-stu-id="f4160-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="f4160-140">**✓ DO** добавляется суффикс «Поток».</span><span class="sxs-lookup"><span data-stu-id="f4160-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="f4160-141">**✓ DO** добавляется суффикс «Разрешение».</span><span class="sxs-lookup"><span data-stu-id="f4160-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="f4160-142">Именование перечислений</span><span class="sxs-lookup"><span data-stu-id="f4160-142">Naming Enumerations</span></span>  
 <span data-ttu-id="f4160-143">Имена типов перечисления (также называемый перечислений) в целом должны следовать стандартным правилам именования типа (PascalCasing и т. д.).</span><span class="sxs-lookup"><span data-stu-id="f4160-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="f4160-144">Тем не менее существуют дополнительные правила, применяемые к перечислений.</span><span class="sxs-lookup"><span data-stu-id="f4160-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="f4160-145">**✓ DO** использовать имя типа единственного числа для перечисления, если его значения и битовые поля.</span><span class="sxs-lookup"><span data-stu-id="f4160-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="f4160-146">**✓ DO** использовать имя во множественном числе типа перечисления с битовыми полями в качестве значений, которые также называются перечисление флагов.</span><span class="sxs-lookup"><span data-stu-id="f4160-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="f4160-147">**X DO NOT** используйте суффикс «Enum» перечисление имен в типе.</span><span class="sxs-lookup"><span data-stu-id="f4160-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="f4160-148">**X DO NOT** использовать «Флаг» или имена типов в enum суффиксы «Флаги».</span><span class="sxs-lookup"><span data-stu-id="f4160-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="f4160-149">**X DO NOT** использовать префикс на имена значений перечисления (например, «ad» для перечислений ADO.), «rtf» для перечислений форматированного текста и т. д.</span><span class="sxs-lookup"><span data-stu-id="f4160-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="f4160-150">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="f4160-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f4160-151">*Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="f4160-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4160-152">См. также</span><span class="sxs-lookup"><span data-stu-id="f4160-152">See also</span></span>

- [<span data-ttu-id="f4160-153">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="f4160-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="f4160-154">Правила именования</span><span class="sxs-lookup"><span data-stu-id="f4160-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
