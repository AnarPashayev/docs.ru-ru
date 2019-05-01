---
title: Рекомендации по разработке платформы
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: KrzysztofCwalina
ms.openlocfilehash: c20430f9cdcd71cc2e178d38aeed48f9fa4e75c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026384"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="c68cb-102">Рекомендации по разработке платформы</span><span class="sxs-lookup"><span data-stu-id="c68cb-102">Framework Design Guidelines</span></span>
<span data-ttu-id="c68cb-103">Этот раздел содержит рекомендации по проектированию библиотек, которые расширяют и взаимодействовать с .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c68cb-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="c68cb-104">Цель — помочь разработчикам библиотек обеспечить API согласованности и удобства использования, предоставляя унифицированную модель программирования, не зависящий от языка программирования, используемая для разработки.</span><span class="sxs-lookup"><span data-stu-id="c68cb-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="c68cb-105">Рекомендуется следовать этим рекомендациям по проектированию при разработке классов и компонентов, расширяющих возможности .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c68cb-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="c68cb-106">Несогласованные библиотеки конструктора отрицательно влияет на производительность и не рекомендует внедрения.</span><span class="sxs-lookup"><span data-stu-id="c68cb-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="c68cb-107">Инструкции составлены как простые рекомендации, которые начинаются с условиями `Do`, `Consider`, `Avoid`, и `Do not`.</span><span class="sxs-lookup"><span data-stu-id="c68cb-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="c68cb-108">Эти рекомендации предназначены для облегчения проектировщикам библиотек классов понимания необходимости компромиссов между разными решениями.</span><span class="sxs-lookup"><span data-stu-id="c68cb-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="c68cb-109">Могут возникнуть ситуации, где хорошо спроектированной библиотеки требуется нарушение этим рекомендациям по проектированию.</span><span class="sxs-lookup"><span data-stu-id="c68cb-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="c68cb-110">Таких случаях должна возникать редко, и важно, что у вас есть понятное и привлекательное причину вашего решения.</span><span class="sxs-lookup"><span data-stu-id="c68cb-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="c68cb-111">Эти рекомендации являются выдержки из книги книги *рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки многократного использования .NET, второе издание*, Кшиштов Квалина, Брэд Абрамс.</span><span class="sxs-lookup"><span data-stu-id="c68cb-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c68cb-112">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="c68cb-112">In This Section</span></span>  
 [<span data-ttu-id="c68cb-113">Правила именования</span><span class="sxs-lookup"><span data-stu-id="c68cb-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="c68cb-114">Рекомендации по именованию сборок, пространств имен, типов и членов в библиотеках классов.</span><span class="sxs-lookup"><span data-stu-id="c68cb-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="c68cb-115">Рекомендации по разработке типов</span><span class="sxs-lookup"><span data-stu-id="c68cb-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="c68cb-116">Рекомендации по использованию статических и абстрактных классов, интерфейсов, перечислений, структур и других типов.</span><span class="sxs-lookup"><span data-stu-id="c68cb-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="c68cb-117">Правила разработки членов</span><span class="sxs-lookup"><span data-stu-id="c68cb-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="c68cb-118">Рекомендации по разработке и использовании свойства, методы, конструкторы, поля, события, операторы и параметры.</span><span class="sxs-lookup"><span data-stu-id="c68cb-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="c68cb-119">Разработка с обеспечением расширяемости</span><span class="sxs-lookup"><span data-stu-id="c68cb-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="c68cb-120">Рассматриваются механизмы расширяемости, таких как создание подклассов, с помощью событий, виртуальные члены и обратные вызовы и объясняется, как выбрать механизмы, которые лучше всего соответствует требованиям вашей платформы.</span><span class="sxs-lookup"><span data-stu-id="c68cb-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="c68cb-121">Правила разработки исключений</span><span class="sxs-lookup"><span data-stu-id="c68cb-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="c68cb-122">Описывает рекомендации по проектированию для проектирования, создания и перехвата исключений.</span><span class="sxs-lookup"><span data-stu-id="c68cb-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="c68cb-123">Правила использования</span><span class="sxs-lookup"><span data-stu-id="c68cb-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="c68cb-124">Описывает правила с помощью распространенных типов, таких как массивы, атрибуты и коллекции, поддержка сериализации и перегрузка операторов равенства.</span><span class="sxs-lookup"><span data-stu-id="c68cb-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="c68cb-125">Обычные шаблоны разработки</span><span class="sxs-lookup"><span data-stu-id="c68cb-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="c68cb-126">Рекомендации по выбору и реализация свойства зависимостей.</span><span class="sxs-lookup"><span data-stu-id="c68cb-126">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="c68cb-127">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="c68cb-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c68cb-128">*Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c68cb-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c68cb-129">См. также</span><span class="sxs-lookup"><span data-stu-id="c68cb-129">See also</span></span>

- [<span data-ttu-id="c68cb-130">Обзор</span><span class="sxs-lookup"><span data-stu-id="c68cb-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)
- [<span data-ttu-id="c68cb-131">Руководство по разработке</span><span class="sxs-lookup"><span data-stu-id="c68cb-131">Development Guide</span></span>](../../../docs/framework/development-guide.md)
