---
title: Вложенные типы
ms.date: 10/22/2008
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: bc0aee32b5cc1d40afdd9cce8260d5b5341a687d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706402"
---
# <a name="nested-types"></a><span data-ttu-id="66efa-102">Вложенные типы</span><span class="sxs-lookup"><span data-stu-id="66efa-102">Nested Types</span></span>

<span data-ttu-id="66efa-103">Вложенный тип — это тип, определенный в области другого типа, который называется включающим типом.</span><span class="sxs-lookup"><span data-stu-id="66efa-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="66efa-104">Вложенный тип имеет доступ ко всем элементам его включающего типа.</span><span class="sxs-lookup"><span data-stu-id="66efa-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="66efa-105">Например, он имеет доступ к закрытым полям, определенным во включающем типе, и к защищенным полям, определенным во всех предков включающего типа.</span><span class="sxs-lookup"><span data-stu-id="66efa-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>

 <span data-ttu-id="66efa-106">Как правило, вложенные типы следует использовать экономно.</span><span class="sxs-lookup"><span data-stu-id="66efa-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="66efa-107">Для этого есть несколько причин.</span><span class="sxs-lookup"><span data-stu-id="66efa-107">There are several reasons for this.</span></span> <span data-ttu-id="66efa-108">Некоторые разработчики не полностью знакомы с концепцией.</span><span class="sxs-lookup"><span data-stu-id="66efa-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="66efa-109">Эти разработчики могут, например, столкнуться с проблемами синтаксиса объявления переменных вложенных типов.</span><span class="sxs-lookup"><span data-stu-id="66efa-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="66efa-110">Вложенные типы также тесно связаны со своими включающими типами, поэтому они не подходят для универсальных типов.</span><span class="sxs-lookup"><span data-stu-id="66efa-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>

 <span data-ttu-id="66efa-111">Вложенные типы лучше всего подходят для моделирования сведений о реализации их включающих типов.</span><span class="sxs-lookup"><span data-stu-id="66efa-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="66efa-112">Конечному пользователю часто приходится объявлять переменные вложенного типа, и почти никогда не придется явно создавать экземпляры вложенных типов.</span><span class="sxs-lookup"><span data-stu-id="66efa-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="66efa-113">Например, перечислитель коллекции может быть вложенным типом этой коллекции.</span><span class="sxs-lookup"><span data-stu-id="66efa-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="66efa-114">Перечислители обычно создаются по включающему типу, а так как многие языки поддерживают оператор foreach, то переменные перечислителя редко должны быть объявлены конечным пользователем.</span><span class="sxs-lookup"><span data-stu-id="66efa-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>

 <span data-ttu-id="66efa-115">✔️ использовать вложенные типы, если связь между вложенным типом и его внешним типом является предпочтительной для семантики доступности членов.</span><span class="sxs-lookup"><span data-stu-id="66efa-115">✔️ DO use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>

 <span data-ttu-id="66efa-116">❌ НЕ используйте открытые вложенные типы в качестве логической конструкции группирования. для этого используйте пространства имен.</span><span class="sxs-lookup"><span data-stu-id="66efa-116">❌ DO NOT use public nested types as a logical grouping construct; use namespaces for this.</span></span>

 <span data-ttu-id="66efa-117">❌ Избегайте общедоступных вложенных типов.</span><span class="sxs-lookup"><span data-stu-id="66efa-117">❌ AVOID publicly exposed nested types.</span></span> <span data-ttu-id="66efa-118">Единственным исключением является ситуация, когда переменные вложенного типа должны быть объявлены только в редких сценариях, таких как подклассы или другие расширенные сценарии настройки.</span><span class="sxs-lookup"><span data-stu-id="66efa-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>

 <span data-ttu-id="66efa-119">❌ НЕ используйте вложенные типы, если на тип, вероятно, имеется ссылка за пределами содержащего его типа.</span><span class="sxs-lookup"><span data-stu-id="66efa-119">❌ DO NOT use nested types if the type is likely to be referenced outside of the containing type.</span></span>

 <span data-ttu-id="66efa-120">Например, перечисление, передаваемое методу, определенному в классе, не должно быть определено как вложенный тип в классе.</span><span class="sxs-lookup"><span data-stu-id="66efa-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>

 <span data-ttu-id="66efa-121">❌ НЕ используйте вложенные типы, если их необходимо создать с помощью клиентского кода.</span><span class="sxs-lookup"><span data-stu-id="66efa-121">❌ DO NOT use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="66efa-122">Если тип имеет открытый конструктор, возможно, он не является вложенным.</span><span class="sxs-lookup"><span data-stu-id="66efa-122">If a type has a public constructor, it should probably not be nested.</span></span>

 <span data-ttu-id="66efa-123">Если можно создать экземпляр типа, то, похоже, указывает, что тип имеет собственное место в структуре (его можно создать, работать с ним и уничтожить без использования внешнего типа), и поэтому он не должен быть вложенным.</span><span class="sxs-lookup"><span data-stu-id="66efa-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="66efa-124">Внутренние типы не должны широко использоваться за пределами внешнего типа, не имея никакой связи с внешним типом.</span><span class="sxs-lookup"><span data-stu-id="66efa-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>

 <span data-ttu-id="66efa-125">❌ НЕ определяйте вложенный тип как член интерфейса.</span><span class="sxs-lookup"><span data-stu-id="66efa-125">❌ DO NOT define a nested type as a member of an interface.</span></span> <span data-ttu-id="66efa-126">Многие языки не поддерживают такую конструкцию.</span><span class="sxs-lookup"><span data-stu-id="66efa-126">Many languages do not support such a construct.</span></span>

 <span data-ttu-id="66efa-127">*Части © 2005, 2009 Корпорация Майкрософт. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="66efa-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="66efa-128">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="66efa-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="66efa-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="66efa-129">See also</span></span>

- [<span data-ttu-id="66efa-130">Рекомендации по проектированию типов</span><span class="sxs-lookup"><span data-stu-id="66efa-130">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="66efa-131">Рекомендации по проектированию платформы</span><span class="sxs-lookup"><span data-stu-id="66efa-131">Framework Design Guidelines</span></span>](index.md)
