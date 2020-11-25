---
title: Атрибуты
ms.date: 10/22/2008
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: c02c41244fa74b686277c2f3c3940405fe2d95ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701371"
---
# <a name="attributes"></a><span data-ttu-id="ca02e-102">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ca02e-102">Attributes</span></span>

<span data-ttu-id="ca02e-103"><xref:System.Attribute?displayProperty=nameWithType> является базовым классом, используемым для определения пользовательских атрибутов.</span><span class="sxs-lookup"><span data-stu-id="ca02e-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="ca02e-104">Атрибуты — это заметки, которые могут быть добавлены к элементам программирования, таким как сборки, типы, члены и параметры.</span><span class="sxs-lookup"><span data-stu-id="ca02e-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="ca02e-105">Они хранятся в метаданных сборки и доступны во время выполнения с помощью API-интерфейсов отражения.</span><span class="sxs-lookup"><span data-stu-id="ca02e-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="ca02e-106">Например, платформа определяет объект <xref:System.ObsoleteAttribute> , который можно применить к типу или члену, чтобы указать, что тип или член является устаревшим.</span><span class="sxs-lookup"><span data-stu-id="ca02e-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="ca02e-107">Атрибуты могут иметь одно или несколько свойств, которые содержат дополнительные данные, связанные с атрибутом.</span><span class="sxs-lookup"><span data-stu-id="ca02e-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="ca02e-108">Например, `ObsoleteAttribute` может содержать дополнительные сведения о выпуске, в котором тип или член устарел, а также описание новых интерфейсов API, заменяющих устаревший API.</span><span class="sxs-lookup"><span data-stu-id="ca02e-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>

 <span data-ttu-id="ca02e-109">При применении атрибута необходимо указать некоторые свойства атрибута.</span><span class="sxs-lookup"><span data-stu-id="ca02e-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="ca02e-110">Они называются обязательными свойствами или требуемыми аргументами, так как они представлены как параметры позиционированного конструктора.</span><span class="sxs-lookup"><span data-stu-id="ca02e-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="ca02e-111">Например, <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> свойство объекта <xref:System.Diagnostics.ConditionalAttribute> является обязательным свойством.</span><span class="sxs-lookup"><span data-stu-id="ca02e-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="ca02e-112">Свойства, которые не обязательно должны указываться при применении атрибута, называются необязательными свойствами (или необязательными аргументами).</span><span class="sxs-lookup"><span data-stu-id="ca02e-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="ca02e-113">Они представлены настраиваемыми свойствами.</span><span class="sxs-lookup"><span data-stu-id="ca02e-113">They are represented by settable properties.</span></span> <span data-ttu-id="ca02e-114">Компиляторы предоставляют специальный синтаксис для установки этих свойств при применении атрибута.</span><span class="sxs-lookup"><span data-stu-id="ca02e-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="ca02e-115">Например, <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> свойство представляет необязательный аргумент.</span><span class="sxs-lookup"><span data-stu-id="ca02e-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="ca02e-116">✔️ имена классов настраиваемых атрибутов с суффиксом "Attribute".</span><span class="sxs-lookup"><span data-stu-id="ca02e-116">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="ca02e-117">✔️ применить <xref:System.AttributeUsageAttribute> к настраиваемым атрибутам.</span><span class="sxs-lookup"><span data-stu-id="ca02e-117">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="ca02e-118">✔️ предоставлять настраиваемые свойства для необязательных аргументов.</span><span class="sxs-lookup"><span data-stu-id="ca02e-118">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="ca02e-119">✔️ предоставить свойства только для получения обязательных аргументов.</span><span class="sxs-lookup"><span data-stu-id="ca02e-119">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="ca02e-120">✔️ предоставить параметры конструктора для инициализации свойств, соответствующих обязательным аргументам.</span><span class="sxs-lookup"><span data-stu-id="ca02e-120">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="ca02e-121">Каждый параметр должен иметь одно и то же имя (хотя с другим регистром) в качестве соответствующего свойства.</span><span class="sxs-lookup"><span data-stu-id="ca02e-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="ca02e-122">❌ Не рекомендуется предоставлять параметры конструктора для инициализации свойств, соответствующих необязательным аргументам.</span><span class="sxs-lookup"><span data-stu-id="ca02e-122">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="ca02e-123">Иными словами, не имеют свойств, которые могут быть заданы с помощью конструктора и метода задания.</span><span class="sxs-lookup"><span data-stu-id="ca02e-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="ca02e-124">В этой рекомендации явно указаны аргументы, которые являются необязательными и являются обязательными, и в них не предусмотрены два способа выполнения одного и того же действия.</span><span class="sxs-lookup"><span data-stu-id="ca02e-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="ca02e-125">❌ Избегайте перегрузки конструкторов настраиваемых атрибутов.</span><span class="sxs-lookup"><span data-stu-id="ca02e-125">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="ca02e-126">Наличие только одного конструктора явно взаимодействует с пользователем, какие аргументы являются обязательными, а какие — необязательными.</span><span class="sxs-lookup"><span data-stu-id="ca02e-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="ca02e-127">✔️ запечатывать классы настраиваемых атрибутов, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="ca02e-127">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="ca02e-128">Это позволяет ускорить поиск атрибута.</span><span class="sxs-lookup"><span data-stu-id="ca02e-128">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="ca02e-129">*Части &copy; 2005, 2009 Корпорация Майкрософт. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="ca02e-129">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ca02e-130">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="ca02e-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ca02e-131">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ca02e-131">See also</span></span>

- [<span data-ttu-id="ca02e-132">Рекомендации по проектированию платформы</span><span class="sxs-lookup"><span data-stu-id="ca02e-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="ca02e-133">Рекомендации по использованию</span><span class="sxs-lookup"><span data-stu-id="ca02e-133">Usage Guidelines</span></span>](usage-guidelines.md)
