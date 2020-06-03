---
title: Руководство по программированию на C#. Универсальные шаблоны
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: a3ed3aa412c7d9c9d6b705dba80b527057c647fa
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241673"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="ddaef-102">Универсальные шаблоны (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="ddaef-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="ddaef-103">Универсальные шаблоны вводят на платформе .NET концепцию параметров универсального типа. Благодаря им вы можете создавать классы и методы с типами, спецификация которых отложена до момента объявления и создания экземпляров в клиентском коде.</span><span class="sxs-lookup"><span data-stu-id="ddaef-103">Generics introduce the concept of type parameters to .NET, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="ddaef-104">Как пример, ниже показан класс с параметром `T` универсального типа. Этот класс может использоваться в другом клиентском коде, не требуя ресурсов и не создавая рисков, связанных с операциями приведения и упаковки-преобразования в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="ddaef-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="ddaef-105">Универсальные классы и методы сочетают такие характеристики, как возможность многократного использования, типобезопасность и эффективность, которые не обеспечивают их неуниверсальные аналоги.</span><span class="sxs-lookup"><span data-stu-id="ddaef-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="ddaef-106">Универсальные типы наиболее часто используются с коллекциями и методами, которые выполняют с ними операции.</span><span class="sxs-lookup"><span data-stu-id="ddaef-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="ddaef-107">Пространство имен <xref:System.Collections.Generic> содержит несколько универсальных классов коллекций.</span><span class="sxs-lookup"><span data-stu-id="ddaef-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="ddaef-108">Неуниверсальные коллекции, например <xref:System.Collections.ArrayList>, не рекомендуются и поддерживаются только для обеспечения совместимости.</span><span class="sxs-lookup"><span data-stu-id="ddaef-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="ddaef-109">Дополнительные сведения см. в статье об [универсальных шаблонах в .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="ddaef-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="ddaef-110">Очевидно, вы можете создавать собственные универсальные типы и методы для предоставления собственных типобезопасных и эффективных обобщенных решений и шаблонов разработки.</span><span class="sxs-lookup"><span data-stu-id="ddaef-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="ddaef-111">В следующем примере кода показан простой универсальный класс связанного списка для демонстрационных целей.</span><span class="sxs-lookup"><span data-stu-id="ddaef-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="ddaef-112">(В большинстве случаев следует использовать класс <xref:System.Collections.Generic.List%601>, предоставляемый .NET, вместо создания собственного.) Параметр типа `T` используется в нескольких расположениях, где обычно используется конкретный тип для указания типа элемента, хранящегося в списке.</span><span class="sxs-lookup"><span data-stu-id="ddaef-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by .NET instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="ddaef-113">Он используется в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="ddaef-113">It is used in the following ways:</span></span>

- <span data-ttu-id="ddaef-114">в качестве типа параметра метода в методе `AddHead`;</span><span class="sxs-lookup"><span data-stu-id="ddaef-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="ddaef-115">в качестве типа возвращаемого значения свойства `Data` во вложенном классе `Node`;</span><span class="sxs-lookup"><span data-stu-id="ddaef-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="ddaef-116">в качестве типа закрытого члена `data` во вложенном классе.</span><span class="sxs-lookup"><span data-stu-id="ddaef-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="ddaef-117">Обратите внимание, что `T` доступен для вложенного класса `Node`.</span><span class="sxs-lookup"><span data-stu-id="ddaef-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="ddaef-118">Когда экземпляр `GenericList<T>` создается с конкретным типом, например `GenericList<int>`, каждое вхождение `T` будет заменено `int`.</span><span class="sxs-lookup"><span data-stu-id="ddaef-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="ddaef-119">В следующем примере кода показано, как клиентский код использует универсальный класс `GenericList<T>` для создания списка целых чисел.</span><span class="sxs-lookup"><span data-stu-id="ddaef-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="ddaef-120">Просто изменяя тип аргумента, следующий код можно легко изменить для создания списков строк или любого другого пользовательского типа:</span><span class="sxs-lookup"><span data-stu-id="ddaef-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="ddaef-121">Общие сведения об универсальных шаблонах</span><span class="sxs-lookup"><span data-stu-id="ddaef-121">Generics overview</span></span>

- <span data-ttu-id="ddaef-122">Используйте универсальные типы, чтобы получить максимально широкие возможности многократного использования кода, обеспечения безопасности типов и повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="ddaef-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="ddaef-123">Чаще всего универсальные шаблоны используются для создания классов коллекций.</span><span class="sxs-lookup"><span data-stu-id="ddaef-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="ddaef-124">Библиотека классов .NET содержит несколько универсальных классов коллекций в пространстве имен <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="ddaef-124">The .NET class library contains several generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="ddaef-125">Рекомендуется как можно чаще использовать их вместо таких классов, как <xref:System.Collections.ArrayList> в пространстве имен <xref:System.Collections>.</span><span class="sxs-lookup"><span data-stu-id="ddaef-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="ddaef-126">Вы можете создавать собственные универсальные интерфейсы, классы, методы, события и делегаты.</span><span class="sxs-lookup"><span data-stu-id="ddaef-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="ddaef-127">Универсальные классы можно ограничить, чтобы они разрешали доступ к методам только для определенных типов данных.</span><span class="sxs-lookup"><span data-stu-id="ddaef-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="ddaef-128">Сведения о типах, используемых в универсальном типе данных, можно получить во время выполнения с помощью отражения.</span><span class="sxs-lookup"><span data-stu-id="ddaef-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ddaef-129">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="ddaef-129">Related sections</span></span>

- [<span data-ttu-id="ddaef-130">Параметры универсального типа</span><span class="sxs-lookup"><span data-stu-id="ddaef-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="ddaef-131">Ограничения параметров типа</span><span class="sxs-lookup"><span data-stu-id="ddaef-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="ddaef-132">Универсальные классы</span><span class="sxs-lookup"><span data-stu-id="ddaef-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="ddaef-133">Универсальные интерфейсы</span><span class="sxs-lookup"><span data-stu-id="ddaef-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="ddaef-134">Универсальные методы</span><span class="sxs-lookup"><span data-stu-id="ddaef-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="ddaef-135">Универсальные делегаты</span><span class="sxs-lookup"><span data-stu-id="ddaef-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="ddaef-136">Различия между шаблонами языка C++ и универсальными шаблонами языка C#</span><span class="sxs-lookup"><span data-stu-id="ddaef-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="ddaef-137">Универсальные типы и отражение</span><span class="sxs-lookup"><span data-stu-id="ddaef-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="ddaef-138">Универсальные типы во время выполнения</span><span class="sxs-lookup"><span data-stu-id="ddaef-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="ddaef-139">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="ddaef-139">C# language specification</span></span>

<span data-ttu-id="ddaef-140">Дополнительные сведения см. в [спецификации языка C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="ddaef-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="ddaef-141">См. также</span><span class="sxs-lookup"><span data-stu-id="ddaef-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="ddaef-142">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="ddaef-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ddaef-143">Типы</span><span class="sxs-lookup"><span data-stu-id="ddaef-143">Types</span></span>](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="ddaef-144">Универсальные шаблоны в .NET</span><span class="sxs-lookup"><span data-stu-id="ddaef-144">Generics in .NET</span></span>](../../../standard/generics/index.md)
