---
title: Имена членов типа
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
author: KrzysztofCwalina
ms.openlocfilehash: b4da14575d29582814d32a3050087b7acc0da802
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353701"
---
# <a name="names-of-type-members"></a><span data-ttu-id="07f3b-102">Имена членов типа</span><span class="sxs-lookup"><span data-stu-id="07f3b-102">Names of Type Members</span></span>
<span data-ttu-id="07f3b-103">Типы состоят из элементов: методов, свойств, событий, конструкторов и полей.</span><span class="sxs-lookup"><span data-stu-id="07f3b-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="07f3b-104">В следующих разделах приведены рекомендации по именованию элементов типа.</span><span class="sxs-lookup"><span data-stu-id="07f3b-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="07f3b-105">Имена методов</span><span class="sxs-lookup"><span data-stu-id="07f3b-105">Names of Methods</span></span>  
 <span data-ttu-id="07f3b-106">Так как методы служат для выполнения действий, при разработке рекомендуется задавать их имена глаголами или глагольными фразами.</span><span class="sxs-lookup"><span data-stu-id="07f3b-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="07f3b-107">Следование этой рекомендации также помогает отличать имена методов от имен типов и свойств, использующих фразы, где главное слово — существительное или прилагательное.</span><span class="sxs-lookup"><span data-stu-id="07f3b-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="07f3b-108">**✓ DO**: давайте методам имена на основе глаголов или глагольных фраз.</span><span class="sxs-lookup"><span data-stu-id="07f3b-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```csharp  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="07f3b-109">Имена свойств</span><span class="sxs-lookup"><span data-stu-id="07f3b-109">Names of Properties</span></span>  
 <span data-ttu-id="07f3b-110">В отличие от других элементов, свойства должны иметь имена в виде фраз на основе существительного или прилагательных.</span><span class="sxs-lookup"><span data-stu-id="07f3b-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="07f3b-111">Причина в том, что свойство ссылается на данные, и это должно быть отражено в его имени.</span><span class="sxs-lookup"><span data-stu-id="07f3b-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="07f3b-112">В именах свойств всегда используется PascalCase.</span><span class="sxs-lookup"><span data-stu-id="07f3b-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="07f3b-113">**✓ DO**: называйте свойства существительными, прилагательными или субстантивной фразой.</span><span class="sxs-lookup"><span data-stu-id="07f3b-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="07f3b-114">**X DO NOT**: не создавайте свойства с именами, совпадающими с именами методов "Get", как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="07f3b-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="07f3b-115">Обычно это означает, что свойство целесообразно сделать методом.</span><span class="sxs-lookup"><span data-stu-id="07f3b-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="07f3b-116">**✓ DO**: называйте свойства коллекции, используя фразу во множественном числе, описывающую ее элементы. Не используйте фразу в единственном числе, добавляя к ней "List" или "Collection".</span><span class="sxs-lookup"><span data-stu-id="07f3b-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="07f3b-117">**✓ DO**: называйте логические свойства без отрицаний (`CanSeek`, а не `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="07f3b-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="07f3b-118">При необходимости вы можете добавить префикс "Is", "Can" или "Has", но только если это действительно имеет смысл.</span><span class="sxs-lookup"><span data-stu-id="07f3b-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="07f3b-119">**✓ CONSIDER**: вы можете назвать свойство так же, как и его тип.</span><span class="sxs-lookup"><span data-stu-id="07f3b-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="07f3b-120">Например, следующее свойство должным образом получает и задает значение перечисления с именем `Color`, поэтому свойство имеет имя `Color`:</span><span class="sxs-lookup"><span data-stu-id="07f3b-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```csharp  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="07f3b-121">Имена событий</span><span class="sxs-lookup"><span data-stu-id="07f3b-121">Names of Events</span></span>  
 <span data-ttu-id="07f3b-122">События всегда ссылаются на какое-то действие, которое происходит или уже произошло.</span><span class="sxs-lookup"><span data-stu-id="07f3b-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="07f3b-123">Следовательно, события, как и методы, следует называть с помощью глаголов, а время глагола (настоящее или прошедшее) будет указывать на время возникновения события.</span><span class="sxs-lookup"><span data-stu-id="07f3b-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="07f3b-124">**✓ DO**: называйте события с помощью глаголов или глагольных фраз.</span><span class="sxs-lookup"><span data-stu-id="07f3b-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="07f3b-125">Примеры: `Clicked`, `Painting`, `DroppedDown` и т. д.</span><span class="sxs-lookup"><span data-stu-id="07f3b-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="07f3b-126">**✓ DO**: давайте событиям имена с использованием настоящего и прошедшего времени.</span><span class="sxs-lookup"><span data-stu-id="07f3b-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="07f3b-127">Например, событие закрытия, которое происходит перед закрытием окна, может называться `Closing`, а которое после — `Closed`.</span><span class="sxs-lookup"><span data-stu-id="07f3b-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="07f3b-128">**X DO NOT**: не используйте префиксы "Before" и "After" или постфиксы, чтобы указать время возникновения события.</span><span class="sxs-lookup"><span data-stu-id="07f3b-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="07f3b-129">Используйте настоящее и прошедшее время, как описано выше.</span><span class="sxs-lookup"><span data-stu-id="07f3b-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="07f3b-130">**✓ DO**: добавляйте к именам обработчиков событий (или делегатов, используемых как типы событий), суффикс "EventHandler", как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="07f3b-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="07f3b-131">**✓ DO**: используйте в обработчиках событий два параметра: `sender` и `e`.</span><span class="sxs-lookup"><span data-stu-id="07f3b-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="07f3b-132">Параметр sender обозначает объект, который вызвал событие.</span><span class="sxs-lookup"><span data-stu-id="07f3b-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="07f3b-133">Этот параметр обычно имеет тип `object`, даже если можно использовать более конкретный тип.</span><span class="sxs-lookup"><span data-stu-id="07f3b-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="07f3b-134">**✓ DO**: добавляйте к именам классов аргументов событий суффикс "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="07f3b-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="07f3b-135">Имена полей</span><span class="sxs-lookup"><span data-stu-id="07f3b-135">Names of Fields</span></span>  
 <span data-ttu-id="07f3b-136">Рекомендации по именованию полей относятся к статическим открытым и защищенным полям.</span><span class="sxs-lookup"><span data-stu-id="07f3b-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="07f3b-137">Рекомендации не охватывают внутренние и закрытые поля, а использование открытых полей или полей защищенных экземпляров запрещено [правилами разработки элементов](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="07f3b-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="07f3b-138">**✓ DO**: используйте PascalCase в именах полей.</span><span class="sxs-lookup"><span data-stu-id="07f3b-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="07f3b-139">**✓ DO**: называйте поля с помощью существительных, прилагательных или субстантивных фраз.</span><span class="sxs-lookup"><span data-stu-id="07f3b-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="07f3b-140">**X DO NOT**: не используйте префикс в именах полей.</span><span class="sxs-lookup"><span data-stu-id="07f3b-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="07f3b-141">Например, не используйте "g_" или "s_" для указания, что поле является статическим.</span><span class="sxs-lookup"><span data-stu-id="07f3b-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="07f3b-142">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="07f3b-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="07f3b-143">*Reprinted по разрешениям Пирсона для образовательных учреждений, Inc. из руководства по проектированию [Framework: Соглашения, идиомы и закономерности для многократно используемых библиотек .NET, 2-го выпуска @ no__t – 0 на Крзисзтоф Квалина и Михаил Abrams), опубликован 22 октября 2008 by Addison-Wesley Professional в рамках серии разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="07f3b-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f3b-144">См. также</span><span class="sxs-lookup"><span data-stu-id="07f3b-144">See also</span></span>

- [<span data-ttu-id="07f3b-145">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="07f3b-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="07f3b-146">Правила именования</span><span class="sxs-lookup"><span data-stu-id="07f3b-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
