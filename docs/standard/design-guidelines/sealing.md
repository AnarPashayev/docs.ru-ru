---
title: Запечатывание
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: KrzysztofCwalina
ms.openlocfilehash: f25573c0fef29ef54dc04c5287757903429d89d4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615204"
---
# <a name="sealing"></a><span data-ttu-id="fb299-102">Запечатывание</span><span class="sxs-lookup"><span data-stu-id="fb299-102">Sealing</span></span>
<span data-ttu-id="fb299-103">Одной из особенностей платформ объектно ориентированного — что разработчики могут расширять и настраивать их способами, непредвиденным, проектировщики этой инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="fb299-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="fb299-104">Это power и опасность расширяемой архитектуры.</span><span class="sxs-lookup"><span data-stu-id="fb299-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="fb299-105">При создании вашей платформы, это так, поэтому очень важно тщательно разрабатывать приложения для расширения его при необходимости, а также ограничить расширяемости, когда это представляет опасность.</span><span class="sxs-lookup"><span data-stu-id="fb299-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="fb299-106">Мощный механизм, который запрещает расширяемости запечатывания.</span><span class="sxs-lookup"><span data-stu-id="fb299-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="fb299-107">Можно запечатать класс или отдельные члены.</span><span class="sxs-lookup"><span data-stu-id="fb299-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="fb299-108">Запечатывание класс запрещает наследование класса.</span><span class="sxs-lookup"><span data-stu-id="fb299-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="fb299-109">Запечатывание член запрещает пользователям переопределять конкретного элемента.</span><span class="sxs-lookup"><span data-stu-id="fb299-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="fb299-110">**X DO NOT** запечатывайте классы без необходимости веская причина для этого.</span><span class="sxs-lookup"><span data-stu-id="fb299-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="fb299-111">Запечатывание класса, так как вы не могу представить сценарий расширяемости не веских причин.</span><span class="sxs-lookup"><span data-stu-id="fb299-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="fb299-112">Пользователям, платформы и наследование от классов по различным причинам nonobvious, таких как добавление членов удобства.</span><span class="sxs-lookup"><span data-stu-id="fb299-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="fb299-113">См. в разделе [незапечатанные классы](../../../docs/standard/design-guidelines/unsealed-classes.md) примеры nonobvious причинам требуется наследовать от типа.</span><span class="sxs-lookup"><span data-stu-id="fb299-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="fb299-114">Следующие веские причины для запечатывания класса:</span><span class="sxs-lookup"><span data-stu-id="fb299-114">Good reasons for sealing a class include the following:</span></span>  
  
- <span data-ttu-id="fb299-115">Этот класс является статическим классом.</span><span class="sxs-lookup"><span data-stu-id="fb299-115">The class is a static class.</span></span> <span data-ttu-id="fb299-116">См. в разделе [разработка статичных классов](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="fb299-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
- <span data-ttu-id="fb299-117">Класс сохраняет конфиденциальные секреты в наследуемые защищенные члены.</span><span class="sxs-lookup"><span data-stu-id="fb299-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
- <span data-ttu-id="fb299-118">Этот класс наследует многие виртуальные члены и затраты на их по отдельности запечатывание бы перевешивают преимущества выходя из незапечатанного класса.</span><span class="sxs-lookup"><span data-stu-id="fb299-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
- <span data-ttu-id="fb299-119">Класс является атрибут, который требуется очень быстро среды выполнения поиска.</span><span class="sxs-lookup"><span data-stu-id="fb299-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="fb299-120">Запечатанный атрибуты имеют немного более высоких уровней производительности, чем незапечатанный из них.</span><span class="sxs-lookup"><span data-stu-id="fb299-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="fb299-121">см. в разделе [атрибуты](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="fb299-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="fb299-122">**X DO NOT** объявлять защищенные или виртуальные члены в запечатанных типах.</span><span class="sxs-lookup"><span data-stu-id="fb299-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="fb299-123">По определению не может наследоваться от запечатанные типы.</span><span class="sxs-lookup"><span data-stu-id="fb299-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="fb299-124">Это означает, что не может быть вызвана защищенные члены в запечатанных типах и виртуальных методов для запечатанных типов не могут быть переопределены.</span><span class="sxs-lookup"><span data-stu-id="fb299-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="fb299-125">**✓ CONSIDER** запечатывание члены, которые можно переопределить.</span><span class="sxs-lookup"><span data-stu-id="fb299-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="fb299-126">Проблемы, которые могут быть результатом Общие сведения о виртуальных членах (подробно [виртуальные члены](../../../docs/standard/design-guidelines/virtual-members.md)) применить переопределения, несмотря на то что для немного в меньшей степени.</span><span class="sxs-lookup"><span data-stu-id="fb299-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="fb299-127">Запечатывание переопределение скрывает от вас этих проблем, начиная с этого момента в иерархии наследования.</span><span class="sxs-lookup"><span data-stu-id="fb299-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="fb299-128">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="fb299-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fb299-129">*Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="fb299-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb299-130">См. также</span><span class="sxs-lookup"><span data-stu-id="fb299-130">See also</span></span>

- [<span data-ttu-id="fb299-131">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="fb299-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="fb299-132">Разработка с обеспечением расширяемости</span><span class="sxs-lookup"><span data-stu-id="fb299-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="fb299-133">Незапечатанные классы</span><span class="sxs-lookup"><span data-stu-id="fb299-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
