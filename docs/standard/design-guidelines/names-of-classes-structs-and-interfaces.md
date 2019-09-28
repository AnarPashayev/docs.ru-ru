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
ms.openlocfilehash: 2ecd708ccb8eb91270e8ef9c174b8d7e599a2629
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353702"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="abbe3-102">Имена классов, структур и интерфейсов</span><span class="sxs-lookup"><span data-stu-id="abbe3-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="abbe3-103">Приведенные ниже рекомендации по именованию применяются к общему именованию типов.</span><span class="sxs-lookup"><span data-stu-id="abbe3-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="abbe3-104">**✓ DO** именах классов и структур с существительные и субстантивные словосочетания, с помощью PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="abbe3-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="abbe3-105">Это отличает имена типов от методов, названных с помощью фраз глагола.</span><span class="sxs-lookup"><span data-stu-id="abbe3-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="abbe3-106">**✓ DO** имя интерфейсы прилагательных фраз или время от времени с существительные и субстантивные словосочетания.</span><span class="sxs-lookup"><span data-stu-id="abbe3-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="abbe3-107">Существительные и фразы существительное следует использовать редко, и они могут указывать, что тип должен быть абстрактным классом, а не интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="abbe3-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="abbe3-108">**X DO NOT** использовать в именах префикс (например, «C»).</span><span class="sxs-lookup"><span data-stu-id="abbe3-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="abbe3-109">**✓ CONSIDER** конечное имя производных классов с именем базового класса.</span><span class="sxs-lookup"><span data-stu-id="abbe3-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="abbe3-110">Это очень понятное и понятное отношение.</span><span class="sxs-lookup"><span data-stu-id="abbe3-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="abbe3-111">Вот некоторые примеры кода: `ArgumentOutOfRangeException`, который является разновидностью `Exception`, и `SerializableAttribute`, который является разновидностью `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="abbe3-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="abbe3-112">Однако важно использовать разумные меры при применении этой рекомендации; Например, класс `Button` является разновидностью события `Control`, хотя `Control` не отображается в имени.</span><span class="sxs-lookup"><span data-stu-id="abbe3-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="abbe3-113">**✓ DO** префикса для имени интерфейса с буквы I, чтобы указать, что тип является интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="abbe3-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="abbe3-114">Например, `IComponent` (описательное существительное), `ICustomAttributeProvider` (субстантивные словосочетания), а `IPersistable` (прилагательные) — это соответствующие имена интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="abbe3-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="abbe3-115">Как и в случае с другими именами типов, следует избегать сокращений.</span><span class="sxs-lookup"><span data-stu-id="abbe3-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="abbe3-116">**✓ DO** убедитесь, что имена отличаются только по «I» префикс в имени интерфейса, при определении пары класс — интерфейс, где класс является стандартной реализации интерфейса.</span><span class="sxs-lookup"><span data-stu-id="abbe3-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="abbe3-117">Имена параметров универсального типа</span><span class="sxs-lookup"><span data-stu-id="abbe3-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="abbe3-118">Универсальные шаблоны были добавлены в .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="abbe3-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="abbe3-119">В этой функции появился новый тип идентификатора, называемый *параметром типа*.</span><span class="sxs-lookup"><span data-stu-id="abbe3-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="abbe3-120">**✓ DO** имя описательные имена параметров универсального типа, если имя не полностью интуитивно понятными и описательное имя могут быть.</span><span class="sxs-lookup"><span data-stu-id="abbe3-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="abbe3-121">**✓ CONSIDER** с помощью `T` как имя параметра типа для типов с одним параметром типа одной буквы.</span><span class="sxs-lookup"><span data-stu-id="abbe3-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```csharp  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="abbe3-122">**✓ DO** префикса описательным именам параметров типа с `T`.</span><span class="sxs-lookup"><span data-stu-id="abbe3-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```csharp  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="abbe3-123">**✓ CONSIDER** указывать ограничения накладываемые на параметр типа в имени параметра.</span><span class="sxs-lookup"><span data-stu-id="abbe3-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="abbe3-124">Например, параметр, ограниченный `ISession`, может называться `TSession`.</span><span class="sxs-lookup"><span data-stu-id="abbe3-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="abbe3-125">Имена общих типов</span><span class="sxs-lookup"><span data-stu-id="abbe3-125">Names of Common Types</span></span>  
 <span data-ttu-id="abbe3-126">**✓ DO** следуйте инструкциям, описанным в следующей таблице, при именовании типов, производных от или реализовывать некоторые типы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abbe3-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="abbe3-127">Базовый тип</span><span class="sxs-lookup"><span data-stu-id="abbe3-127">Base Type</span></span>|<span data-ttu-id="abbe3-128">Руководство по производному или реализующему типу</span><span class="sxs-lookup"><span data-stu-id="abbe3-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="abbe3-129">**✓ DO** добавляется суффикс «Attribute» к именам классов пользовательских атрибутов.</span><span class="sxs-lookup"><span data-stu-id="abbe3-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="abbe3-130">**✓ DO** добавляется суффикс «EventHandler» к именам делегатов, которые используются в событиях.</span><span class="sxs-lookup"><span data-stu-id="abbe3-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="abbe3-131">**✓ DO** добавляется суффикс «Callback» к именам делегатов, отличные от тех, которые используются в качестве обработчиков событий.</span><span class="sxs-lookup"><span data-stu-id="abbe3-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="abbe3-132">**X DO NOT** добавляется суффикс «Делегат» делегат.</span><span class="sxs-lookup"><span data-stu-id="abbe3-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="abbe3-133">**✓ DO** добавляется суффикс «EventArgs.»</span><span class="sxs-lookup"><span data-stu-id="abbe3-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="abbe3-134">**X DO NOT** наследовать от этого класса; используйте ключевое слово поддерживается в используемом языке вместо; например, в C#, используйте `enum` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="abbe3-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="abbe3-135">**X DO NOT** добавляется суффикс «Enum» или «Флаг».</span><span class="sxs-lookup"><span data-stu-id="abbe3-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="abbe3-136">**✓ DO** добавляется суффикс «Исключение».</span><span class="sxs-lookup"><span data-stu-id="abbe3-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="abbe3-137">**✓ DO** добавляется суффикс «Словарь».</span><span class="sxs-lookup"><span data-stu-id="abbe3-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="abbe3-138">Обратите внимание, что `IDictionary` — это конкретный тип коллекции, но это правило имеет приоритет над более общими коллекциями, приведенными ниже.</span><span class="sxs-lookup"><span data-stu-id="abbe3-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="abbe3-139">**✓ DO** добавляется суффикс «Коллекция».</span><span class="sxs-lookup"><span data-stu-id="abbe3-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="abbe3-140">**✓ DO** добавляется суффикс «Поток».</span><span class="sxs-lookup"><span data-stu-id="abbe3-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="abbe3-141">**✓ DO** добавляется суффикс «Разрешение».</span><span class="sxs-lookup"><span data-stu-id="abbe3-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="abbe3-142">Перечисления именования</span><span class="sxs-lookup"><span data-stu-id="abbe3-142">Naming Enumerations</span></span>  
 <span data-ttu-id="abbe3-143">Имена типов перечисления (также называемые перечислениями) в целом должны соответствовать стандартным правилам именования типов (Паскалкасинг и т. д.).</span><span class="sxs-lookup"><span data-stu-id="abbe3-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="abbe3-144">Однако существуют дополнительные рекомендации, которые применяются специально для перечислений.</span><span class="sxs-lookup"><span data-stu-id="abbe3-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="abbe3-145">**✓ DO** использовать имя типа единственного числа для перечисления, если его значения и битовые поля.</span><span class="sxs-lookup"><span data-stu-id="abbe3-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="abbe3-146">**✓ DO** использовать имя во множественном числе типа перечисления с битовыми полями в качестве значений, которые также называются перечисление флагов.</span><span class="sxs-lookup"><span data-stu-id="abbe3-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="abbe3-147">**X DO NOT** используйте суффикс «Enum» перечисление имен в типе.</span><span class="sxs-lookup"><span data-stu-id="abbe3-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="abbe3-148">**X DO NOT** использовать «Флаг» или имена типов в enum суффиксы «Флаги».</span><span class="sxs-lookup"><span data-stu-id="abbe3-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="abbe3-149">**X DO NOT** использовать префикс на имена значений перечисления (например, «ad» для перечислений ADO.), «rtf» для перечислений форматированного текста и т. д.</span><span class="sxs-lookup"><span data-stu-id="abbe3-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="abbe3-150">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="abbe3-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="abbe3-151">*Reprinted по разрешениям Пирсона для образовательных учреждений, Inc. из руководства по проектированию [Framework: Соглашения, идиомы и закономерности для многократно используемых библиотек .NET, 2-го выпуска @ no__t – 0 на Крзисзтоф Квалина и Михаил Abrams), опубликован 22 октября 2008 by Addison-Wesley Professional в рамках серии разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="abbe3-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abbe3-152">См. также</span><span class="sxs-lookup"><span data-stu-id="abbe3-152">See also</span></span>

- [<span data-ttu-id="abbe3-153">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="abbe3-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="abbe3-154">Правила именования</span><span class="sxs-lookup"><span data-stu-id="abbe3-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
