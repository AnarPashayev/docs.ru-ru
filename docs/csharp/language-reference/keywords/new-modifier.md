---
description: Справочник по C#. Модификатор new
title: Справочник по C#. Модификатор new
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 2da0a360868250169fb16380c80bf32c4b335d7a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139415"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="5fa53-103">Модификатор new (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="5fa53-103">new modifier (C# Reference)</span></span>

<span data-ttu-id="5fa53-104">При использовании в качестве модификатора объявления ключевое слово `new` явным образом скрывает члены, унаследованные от базового класса.</span><span class="sxs-lookup"><span data-stu-id="5fa53-104">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="5fa53-105">При скрытии унаследованного члена его производная версия заменяет версию базового класса.</span><span class="sxs-lookup"><span data-stu-id="5fa53-105">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="5fa53-106">Хотя члены можно скрывать без использования модификатора `new`, в этом случае появляется предупреждение компилятора.</span><span class="sxs-lookup"><span data-stu-id="5fa53-106">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="5fa53-107">При использовании `new` для явного скрытия члена, предупреждение не появляется.</span><span class="sxs-lookup"><span data-stu-id="5fa53-107">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="5fa53-108">Ключевое слово `new` можно также использовать для [создания экземпляра типа](../operators/new-operator.md) или как [ограничение универсального типа](./new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="5fa53-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="5fa53-109">Чтобы скрыть унаследованный член, объявите его в производном классе с использованием такого же имени члена и измените с помощью ключевого слова `new`.</span><span class="sxs-lookup"><span data-stu-id="5fa53-109">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="5fa53-110">Пример:</span><span class="sxs-lookup"><span data-stu-id="5fa53-110">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="5fa53-111">В этом примере `BaseC.Invoke` скрывается с помощью `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="5fa53-111">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="5fa53-112">Поле `x` не затрагивается, поскольку оно не скрыто таким же именем.</span><span class="sxs-lookup"><span data-stu-id="5fa53-112">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="5fa53-113">Скрытие имен через наследование принимает одну из следующих форм.</span><span class="sxs-lookup"><span data-stu-id="5fa53-113">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="5fa53-114">Как правило, константы, поля, свойства и типы, которые вводятся в классе или структуре, скрывают все члены базового класса с таким же именем.</span><span class="sxs-lookup"><span data-stu-id="5fa53-114">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="5fa53-115">Однако существуют особые случаи.</span><span class="sxs-lookup"><span data-stu-id="5fa53-115">There are special cases.</span></span> <span data-ttu-id="5fa53-116">Например, если объявить новое поле с именем `N`, чтобы сделать тип невызываемым, в то время как в базовом типе был объявлен метод `N`, новое поле не скрывает базовое объявление в синтаксисе вызова.</span><span class="sxs-lookup"><span data-stu-id="5fa53-116">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="5fa53-117">Дополнительные сведения см. в разделе [Поиск членов](~/_csharplang/spec/expressions.md#member-lookup) в [спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5fa53-117">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="5fa53-118">Метод, введенный в классе или структуре, скрывает свойства, поля и типы с тем же именем в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="5fa53-118">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="5fa53-119">Кроме того, он также скрывает все методы базового класса, имеющие такую же сигнатуру.</span><span class="sxs-lookup"><span data-stu-id="5fa53-119">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="5fa53-120">Индексатор, представленный в классе или структуре, скрывает все индексаторы базового класса, имеющие одинаковую сигнатуру.</span><span class="sxs-lookup"><span data-stu-id="5fa53-120">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="5fa53-121">Совместное использование модификаторов `new` и [override](override.md) в одном члене является недопустимым, так как эти два модификатора имеют взаимоисключающие значения.</span><span class="sxs-lookup"><span data-stu-id="5fa53-121">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="5fa53-122">Модификатор `new` создает новый член с таким же именем и приводит к скрытию исходного члена.</span><span class="sxs-lookup"><span data-stu-id="5fa53-122">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="5fa53-123">Модификатор `override` расширяет реализацию для наследуемого члена.</span><span class="sxs-lookup"><span data-stu-id="5fa53-123">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="5fa53-124">При использовании модификатора `new` в объявлении, которое не скрывает наследуемый член, возникает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="5fa53-124">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="5fa53-125">Пример</span><span class="sxs-lookup"><span data-stu-id="5fa53-125">Example</span></span>

<span data-ttu-id="5fa53-126">В этом примере базовый класс `BaseC` и производный класс `DerivedC` используют одно и то же имя поля `x`, которое скрывает значение унаследованного поля.</span><span class="sxs-lookup"><span data-stu-id="5fa53-126">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="5fa53-127">В примере показано использование модификатора `new`.</span><span class="sxs-lookup"><span data-stu-id="5fa53-127">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="5fa53-128">Здесь также показано обращение к скрытым членам базового класса с помощью их полных имен.</span><span class="sxs-lookup"><span data-stu-id="5fa53-128">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="5fa53-129">Пример</span><span class="sxs-lookup"><span data-stu-id="5fa53-129">Example</span></span>

<span data-ttu-id="5fa53-130">В этом примере вложенный класс скрывает класс, имеющий такое же имя в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="5fa53-130">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="5fa53-131">Здесь показано использование модификатора `new` для исключения предупреждений, а также обращение к членам скрытого класса с помощью их полных имен.</span><span class="sxs-lookup"><span data-stu-id="5fa53-131">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="5fa53-132">В случае удаления модификатора `new` программа продолжит компиляцию и выполнение, однако появится следующее предупреждение.</span><span class="sxs-lookup"><span data-stu-id="5fa53-132">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="5fa53-133">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="5fa53-133">C# language specification</span></span>

<span data-ttu-id="5fa53-134">Дополнительные сведения см. в разделе [Модификатор new](~/_csharplang/spec/classes.md#the-new-modifier) в [спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5fa53-134">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5fa53-135">См. также</span><span class="sxs-lookup"><span data-stu-id="5fa53-135">See also</span></span>

- [<span data-ttu-id="5fa53-136">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="5fa53-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5fa53-137">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="5fa53-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5fa53-138">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="5fa53-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5fa53-139">Модификаторы</span><span class="sxs-lookup"><span data-stu-id="5fa53-139">Modifiers</span></span>](index.md)
- [<span data-ttu-id="5fa53-140">Управление версиями с помощью ключевых слов Override и New</span><span class="sxs-lookup"><span data-stu-id="5fa53-140">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="5fa53-141">Использование ключевых слов Override и New</span><span class="sxs-lookup"><span data-stu-id="5fa53-141">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
