---
title: Запечатывание
ms.date: 10/22/2008
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: bf8aad5d79e659ad9a767c2b0992eb9ee05fd531
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730946"
---
# <a name="sealing"></a><span data-ttu-id="ef757-102">Запечатывание</span><span class="sxs-lookup"><span data-stu-id="ef757-102">Sealing</span></span>

<span data-ttu-id="ef757-103">Одной из функций объектно-ориентированных платформ является то, что разработчики могут расширять и настраивать их способами, не предусмотренными конструкторами инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="ef757-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="ef757-104">Это как мощность, так и опасность расширяемого проектирования.</span><span class="sxs-lookup"><span data-stu-id="ef757-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="ef757-105">При проектировании платформы, следовательно, очень важно тщательно спроектировать расширяемость при необходимости и ограничить расширяемость, когда она опасно.</span><span class="sxs-lookup"><span data-stu-id="ef757-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="ef757-106">Мощный механизм, который предотвращает запечатывание расширяемости.</span><span class="sxs-lookup"><span data-stu-id="ef757-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="ef757-107">Можно запечатывать либо класс, либо отдельные члены.</span><span class="sxs-lookup"><span data-stu-id="ef757-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="ef757-108">Запечатывание класса не позволяет пользователям наследовать от класса.</span><span class="sxs-lookup"><span data-stu-id="ef757-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="ef757-109">Запечатывание элемента не позволяет пользователям переопределять конкретный элемент.</span><span class="sxs-lookup"><span data-stu-id="ef757-109">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="ef757-110">❌ Не запечатывать классы без хорошей причины.</span><span class="sxs-lookup"><span data-stu-id="ef757-110">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="ef757-111">Запечатывание класса, так как вы не можете подумать о сценарии расширяемости, не является хорошей причиной.</span><span class="sxs-lookup"><span data-stu-id="ef757-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="ef757-112">Пользователи платформы могут наследовать от классов по различным неочевидным причинам, например к добавлению удобных членов.</span><span class="sxs-lookup"><span data-stu-id="ef757-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="ef757-113">Примеры неочевидных причин, по которым пользователям необходимо наследовать от типа, см. в разделе [незапечатанные классы](unsealed-classes.md) .</span><span class="sxs-lookup"><span data-stu-id="ef757-113">See [Unsealed Classes](unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="ef757-114">Ниже приведены веские причины для запечатывания класса.</span><span class="sxs-lookup"><span data-stu-id="ef757-114">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="ef757-115">Класс является статическим классом.</span><span class="sxs-lookup"><span data-stu-id="ef757-115">The class is a static class.</span></span> <span data-ttu-id="ef757-116">См. раздел [Разработка статических классов](static-class.md).</span><span class="sxs-lookup"><span data-stu-id="ef757-116">See [Static Class Design](static-class.md).</span></span>

- <span data-ttu-id="ef757-117">Класс хранит секреты с учетом уровня безопасности в наследуемых защищенных членах.</span><span class="sxs-lookup"><span data-stu-id="ef757-117">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="ef757-118">Класс наследует многие виртуальные члены, и стоимость их запечатывания по отдельности может перевесить преимущества незапечатанного класса.</span><span class="sxs-lookup"><span data-stu-id="ef757-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="ef757-119">Класс является атрибутом, который требует очень быстрого поиска в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="ef757-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="ef757-120">Запечатанные атрибуты имеют несколько более высокие уровни производительности, чем незапечатанные.</span><span class="sxs-lookup"><span data-stu-id="ef757-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="ef757-121">См. раздел [атрибуты](attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ef757-121">See [Attributes](attributes.md).</span></span>

 <span data-ttu-id="ef757-122">❌ НЕ объявляйте защищенные или виртуальные члены в запечатанных типах.</span><span class="sxs-lookup"><span data-stu-id="ef757-122">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="ef757-123">По определению Запечатанные типы не могут наследоваться от.</span><span class="sxs-lookup"><span data-stu-id="ef757-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="ef757-124">Это означает, что нельзя вызывать защищенные члены в запечатанных типах, а виртуальные методы в запечатанных типах не могут быть переопределены.</span><span class="sxs-lookup"><span data-stu-id="ef757-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="ef757-125">✔️ Рассмотрите возможность запечатывания переопределяемых элементов.</span><span class="sxs-lookup"><span data-stu-id="ef757-125">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="ef757-126">Проблемы, которые могут возникнуть в результате введения виртуальных членов (обсуждаются в [виртуальных членах](virtual-members.md)), применяются и к переопределениям, хотя и немного меньше.</span><span class="sxs-lookup"><span data-stu-id="ef757-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="ef757-127">Запечатывание экранирования от этих проблем, начиная с этой точки в иерархии наследования.</span><span class="sxs-lookup"><span data-stu-id="ef757-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="ef757-128">*Части © 2005, 2009 Корпорация Майкрософт. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="ef757-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ef757-129">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ef757-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ef757-130">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ef757-130">See also</span></span>

- [<span data-ttu-id="ef757-131">Рекомендации по проектированию платформы</span><span class="sxs-lookup"><span data-stu-id="ef757-131">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="ef757-132">Разработка с обеспечением расширяемости</span><span class="sxs-lookup"><span data-stu-id="ef757-132">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="ef757-133">Незапечатанные классы</span><span class="sxs-lookup"><span data-stu-id="ef757-133">Unsealed Classes</span></span>](unsealed-classes.md)
