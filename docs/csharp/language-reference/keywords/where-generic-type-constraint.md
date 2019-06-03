---
title: Справочник по C#. Предложение where (ограничение универсального типа)
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 3982c97bc56b42237700343b2572d1bba930bbbd
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422772"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="bef22-102">where (ограничение универсального типа) (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="bef22-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="bef22-103">Предложение `where` в универсальном определении задает ограничения на типы, которые используются в качестве аргументов для параметров типа в универсальном типе, методе, делегате или локальной функции.</span><span class="sxs-lookup"><span data-stu-id="bef22-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="bef22-104">Ограничения могут задавать интерфейсы, базовые классы или требовать, чтобы универсальный тип был ссылочным типом, типом значения или неуправляемым типом.</span><span class="sxs-lookup"><span data-stu-id="bef22-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value or unmanaged type.</span></span> <span data-ttu-id="bef22-105">Они объявляют характеристики, которыми должен обладать аргумент типа.</span><span class="sxs-lookup"><span data-stu-id="bef22-105">They declare capabilities that the type argument must possess.</span></span>

<span data-ttu-id="bef22-106">Например, можно объявить универсальный класс `MyGenericClass` так, чтобы параметр типа `T` реализовывал интерфейс <xref:System.IComparable%601>:</span><span class="sxs-lookup"><span data-stu-id="bef22-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="bef22-107">Дополнительные сведения о предложении where в выражении запроса см. в разделе [Предложение where](where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="bef22-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="bef22-108">Предложение `where` также может включать ограничение базового класса.</span><span class="sxs-lookup"><span data-stu-id="bef22-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="bef22-109">Ограничение базового класса указывает, что тип, который должен использоваться как аргумент типа для этого универсального типа, имеет заданный класс в качестве базового класса (или является этим базовым классом), который должен использоваться как аргумент типа для этого универсального типа.</span><span class="sxs-lookup"><span data-stu-id="bef22-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class (or is that base class) to be used as a type argument for that generic type.</span></span> <span data-ttu-id="bef22-110">Если ограничение базового класса используется, оно должно быть указано перед любыми другими ограничениями данного параметра типа.</span><span class="sxs-lookup"><span data-stu-id="bef22-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="bef22-111">Некоторые типы не могут использоваться как ограничение базового класса: <xref:System.Object>, <xref:System.Array> и <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="bef22-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="bef22-112">До C# 7.3 <xref:System.Enum>, <xref:System.Delegate> и <xref:System.MulticastDelegate> также не могли использоваться в качестве ограничений базового класса.</span><span class="sxs-lookup"><span data-stu-id="bef22-112">Prior to C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="bef22-113">Ниже приведен пример типов, которые теперь можно указать как базовый класс:</span><span class="sxs-lookup"><span data-stu-id="bef22-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

<span data-ttu-id="bef22-114">Предложение `where` может указывать, что тип является `class` или `struct`.</span><span class="sxs-lookup"><span data-stu-id="bef22-114">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="bef22-115">Ограничение `struct` избавляет от необходимости указывать ограничение базового класса `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="bef22-115">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="bef22-116">Тип `System.ValueType` не может использоваться как ограничение базового класса.</span><span class="sxs-lookup"><span data-stu-id="bef22-116">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="bef22-117">Ограничения `class` и `struct` показаны в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="bef22-117">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

<span data-ttu-id="bef22-118">Предложение `where` также может включать ограничение `unmanaged`.</span><span class="sxs-lookup"><span data-stu-id="bef22-118">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="bef22-119">Ограничение `unmanaged` позволяет использовать в качестве параметра типа только типы, называемые **неуправляемыми типами**.</span><span class="sxs-lookup"><span data-stu-id="bef22-119">The `unmanaged` constraint limits the type parameter to types known as **unmanaged types**.</span></span> <span data-ttu-id="bef22-120">**Неуправляемый тип** — это тип, который не является ссылочным и не содержит поля ссылочного типа на любом уровне вложения.</span><span class="sxs-lookup"><span data-stu-id="bef22-120">An **unmanaged type** is a type that isn't a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="bef22-121">Ограничение `unmanaged` упрощает написание кода взаимодействия низкого уровня на языке C#.</span><span class="sxs-lookup"><span data-stu-id="bef22-121">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="bef22-122">Это ограничение включает подпрограммы с возможностью повторного использования для всех неуправляемых типов.</span><span class="sxs-lookup"><span data-stu-id="bef22-122">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="bef22-123">Ограничение `unmanaged` нельзя использовать с ограничением `class` или `struct`.</span><span class="sxs-lookup"><span data-stu-id="bef22-123">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="bef22-124">Ограничение `unmanaged` требует тип `struct`:</span><span class="sxs-lookup"><span data-stu-id="bef22-124">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

<span data-ttu-id="bef22-125">Предложение `where` также может включать ограничение конструктора, `new()`.</span><span class="sxs-lookup"><span data-stu-id="bef22-125">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="bef22-126">Это ограничение позволяет создать экземпляр параметра типа с помощью оператора `new`.</span><span class="sxs-lookup"><span data-stu-id="bef22-126">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="bef22-127">[Ограничение new()](new-constraint.md) сообщает компилятору о том, что все предоставленные аргументы типа должны иметь доступный конструктор без параметров (или конструктор по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="bef22-127">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="bef22-128">Например:</span><span class="sxs-lookup"><span data-stu-id="bef22-128">For example:</span></span>

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

<span data-ttu-id="bef22-129">Ограничение `new()` отображается в предложении `where` последним.</span><span class="sxs-lookup"><span data-stu-id="bef22-129">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="bef22-130">Ограничение `new()` не может использоваться с ограничениями `struct` или `unmanaged`.</span><span class="sxs-lookup"><span data-stu-id="bef22-130">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="bef22-131">Все типы, удовлетворяющие этим ограничениям, должны иметь доступ к конструктору без параметров, поэтому ограничение `new()` будет избыточным.</span><span class="sxs-lookup"><span data-stu-id="bef22-131">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="bef22-132">Если параметров типа несколько, для каждого из них необходимо использовать по одному предложению `where`, например:</span><span class="sxs-lookup"><span data-stu-id="bef22-132">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

<span data-ttu-id="bef22-133">Кроме того, ограничения можно присоединять к параметрам типа универсальных методов следующим образом:</span><span class="sxs-lookup"><span data-stu-id="bef22-133">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

<span data-ttu-id="bef22-134">Обратите внимание на то, что ограничения параметров типа для делегатов имеют такой же синтаксис, как и методы:</span><span class="sxs-lookup"><span data-stu-id="bef22-134">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

<span data-ttu-id="bef22-135">Дополнительные сведения об универсальных делегатах см. в разделе [Универсальные делегаты](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="bef22-135">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="bef22-136">Дополнительные сведения о синтаксисе и применении ограничений см. в разделе [Ограничения параметров типа](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="bef22-136">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bef22-137">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="bef22-137">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bef22-138">См. также</span><span class="sxs-lookup"><span data-stu-id="bef22-138">See also</span></span>

- [<span data-ttu-id="bef22-139">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="bef22-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="bef22-140">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="bef22-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="bef22-141">Введение в универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="bef22-141">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="bef22-142">Ограничение new</span><span class="sxs-lookup"><span data-stu-id="bef22-142">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)
- [<span data-ttu-id="bef22-143">Ограничения параметров типа</span><span class="sxs-lookup"><span data-stu-id="bef22-143">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
