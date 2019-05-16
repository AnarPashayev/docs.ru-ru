---
title: Конструкторы
description: Узнайте, как определить и использовать конструкторы в F# для создания и инициализации объектов классов и структур.
ms.date: 05/16/2016
ms.openlocfilehash: 47fb6e77ce369d7aa4fce3aa2c97ecf7df280c03
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645232"
---
# <a name="constructors"></a><span data-ttu-id="ebb14-103">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="ebb14-103">Constructors</span></span>

<span data-ttu-id="ebb14-104">В этом разделе описывается определение и использование конструкторов для создания и инициализации объектов классов и структур.</span><span class="sxs-lookup"><span data-stu-id="ebb14-104">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="ebb14-105">Создание объектов классов</span><span class="sxs-lookup"><span data-stu-id="ebb14-105">Construction of Class Objects</span></span>

<span data-ttu-id="ebb14-106">Объекты типов классов имеют конструкторы.</span><span class="sxs-lookup"><span data-stu-id="ebb14-106">Objects of class types have constructors.</span></span> <span data-ttu-id="ebb14-107">Существует два типа конструкторов.</span><span class="sxs-lookup"><span data-stu-id="ebb14-107">There are two kinds of constructors.</span></span> <span data-ttu-id="ebb14-108">Одним является первичный конструктор, параметры которого отображаются в скобках сразу после имени типа.</span><span class="sxs-lookup"><span data-stu-id="ebb14-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="ebb14-109">Второй — необязательные дополнительные конструкторы, которые задаются с помощью `new` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="ebb14-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="ebb14-110">Такие дополнительные конструкторы необходимо вызвать первичного конструктора.</span><span class="sxs-lookup"><span data-stu-id="ebb14-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="ebb14-111">Содержит первичный конструктор `let` и `do` привязок, которые отображаются в начале определения класса.</span><span class="sxs-lookup"><span data-stu-id="ebb14-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="ebb14-112">Объект `let` привязка объявляет, закрытые поля и методы класса; `do` привязки выполняет код.</span><span class="sxs-lookup"><span data-stu-id="ebb14-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="ebb14-113">Дополнительные сведения о `let` привязок в конструкторах классов см. в разделе [ `let` привязок в классах](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="ebb14-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="ebb14-114">Дополнительные сведения о `do` привязок в конструкторах, см. в разделе [ `do` привязок в классах](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="ebb14-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="ebb14-115">Независимо от типа необходимо вызвать конструктор первичного конструктора или дополнительный конструктор, можно создать объекты с помощью `new` выражение, с или без дополнительного `new` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="ebb14-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="ebb14-116">Инициализации объектов вместе с аргументами конструктора либо, перечисляя аргументы по порядку и разделены запятыми и заключены в круглые скобки, или с помощью именованных аргументов, а также значения в скобках.</span><span class="sxs-lookup"><span data-stu-id="ebb14-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="ebb14-117">Вы можно также задать свойства объекта во время создания объекта, используя имена свойств и присвоение значений, так же, как именованные аргументы конструктора.</span><span class="sxs-lookup"><span data-stu-id="ebb14-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="ebb14-118">Следующий код иллюстрирует классом, имеющим конструктор и различные способы создания объектов.</span><span class="sxs-lookup"><span data-stu-id="ebb14-118">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="ebb14-119">Выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ebb14-119">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="ebb14-120">Создание структур</span><span class="sxs-lookup"><span data-stu-id="ebb14-120">Construction of Structures</span></span>

<span data-ttu-id="ebb14-121">Структуры следовать всем правилам классов.</span><span class="sxs-lookup"><span data-stu-id="ebb14-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="ebb14-122">Таким образом, может иметь первичный конструктор, и можно задать дополнительные конструкторы с помощью `new`.</span><span class="sxs-lookup"><span data-stu-id="ebb14-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="ebb14-123">Однако есть одно важное отличие между структурами и классами: структуры могут иметь конструктор по умолчанию (то есть без аргументов), даже если определен без первичного конструктора.</span><span class="sxs-lookup"><span data-stu-id="ebb14-123">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="ebb14-124">Конструктор по умолчанию инициализирует все поля, значение по умолчанию для этого типа, обычно ноль или его эквивалент.</span><span class="sxs-lookup"><span data-stu-id="ebb14-124">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="ebb14-125">Никакие конструкторы, которые задаются для структуры должны иметь по крайней мере один аргумент, таким образом, чтобы они не конфликтовали с помощью конструктора по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ebb14-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="ebb14-126">Кроме того, структуры часто имеют поля, которые создаются с помощью `val` ключевое слово; классы также могут иметь эти поля.</span><span class="sxs-lookup"><span data-stu-id="ebb14-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="ebb14-127">Структуры и классы, имеющие поля, определенные с помощью `val` ключевого слова могут также инициализироваться в дополнительных конструкторов с помощью выражений записей, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="ebb14-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="ebb14-128">Дополнительные сведения см. в разделе [явные поля: `val` Ключевое слово](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="ebb14-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="ebb14-129">Выполнение побочных эффектов в конструкторах</span><span class="sxs-lookup"><span data-stu-id="ebb14-129">Executing Side Effects in Constructors</span></span>

<span data-ttu-id="ebb14-130">Первичный конструктор в классе может выполнять код в `do` привязки.</span><span class="sxs-lookup"><span data-stu-id="ebb14-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="ebb14-131">Однако что делать, если у вас есть без выполнения кода в дополнительном конструкторе `do` привязки?</span><span class="sxs-lookup"><span data-stu-id="ebb14-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="ebb14-132">Чтобы сделать это, используйте `then` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="ebb14-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="ebb14-133">Побочные эффекты главного конструктора по-прежнему выполняются.</span><span class="sxs-lookup"><span data-stu-id="ebb14-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="ebb14-134">Таким образом выходные данные выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ebb14-134">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="ebb14-135">Собственные идентификаторы в конструкторах</span><span class="sxs-lookup"><span data-stu-id="ebb14-135">Self Identifiers in Constructors</span></span>

<span data-ttu-id="ebb14-136">В других членах укажите имя для текущего объекта в определении каждого члена.</span><span class="sxs-lookup"><span data-stu-id="ebb14-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="ebb14-137">Можно также включить собственный идентификатор первая часть определения класса с помощью `as` ключевое слово сразу после параметров конструктора.</span><span class="sxs-lookup"><span data-stu-id="ebb14-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="ebb14-138">Следующий пример иллюстрирует этот синтаксис.</span><span class="sxs-lookup"><span data-stu-id="ebb14-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="ebb14-139">В дополнительных конструкторов также можно определить собственный идентификатор, поместив `as` предложение сразу же после параметров конструктора.</span><span class="sxs-lookup"><span data-stu-id="ebb14-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="ebb14-140">Следующий пример иллюстрирует этот синтаксис.</span><span class="sxs-lookup"><span data-stu-id="ebb14-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="ebb14-141">Проблемы могут возникать при попытке использовать объект, пока она полностью определена.</span><span class="sxs-lookup"><span data-stu-id="ebb14-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="ebb14-142">Таким образом использует собственный идентификатор может привести к компилятору выдавать предупреждение, а также вставлять дополнительные проверки, чтобы убедиться, что членам объекта не осуществляется до инициализации объекта.</span><span class="sxs-lookup"><span data-stu-id="ebb14-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="ebb14-143">Следует использовать только собственный идентификатор в `do` привязки первичного конструктора или после `then` ключевое слово в дополнительных конструкторов.</span><span class="sxs-lookup"><span data-stu-id="ebb14-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="ebb14-144">Имя данного идентификатора не обязательно должны `this`.</span><span class="sxs-lookup"><span data-stu-id="ebb14-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="ebb14-145">Это может быть любой допустимый идентификатор.</span><span class="sxs-lookup"><span data-stu-id="ebb14-145">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="ebb14-146">Присвоение значений свойствам при инициализации</span><span class="sxs-lookup"><span data-stu-id="ebb14-146">Assigning Values to Properties at Initialization</span></span>

<span data-ttu-id="ebb14-147">Можно назначить значения свойствам объекта класса в коде инициализации, добавив список назначений формы `property = value` в список аргументов для конструктора.</span><span class="sxs-lookup"><span data-stu-id="ebb14-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="ebb14-148">Это показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="ebb14-148">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="ebb14-149">Следующая версия предыдущего примера кода показано сочетание обычные аргументы, необязательные аргументы и параметры свойств в одном вызове конструктора.</span><span class="sxs-lookup"><span data-stu-id="ebb14-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="ebb14-150">Конструкторы в унаследованного класса</span><span class="sxs-lookup"><span data-stu-id="ebb14-150">Constructors in inherited class</span></span>

<span data-ttu-id="ebb14-151">При наследовании от базового класса, который имеет конструктор, необходимо указать аргументы в предложении наследовать.</span><span class="sxs-lookup"><span data-stu-id="ebb14-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="ebb14-152">Дополнительные сведения см. в разделе [конструкторы и наследование](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="ebb14-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="ebb14-153">Статические конструкторы или конструкторы типов</span><span class="sxs-lookup"><span data-stu-id="ebb14-153">Static Constructors or Type Constructors</span></span>

<span data-ttu-id="ebb14-154">Помимо указания кода для создания объектов, статические `let` и `do` привязки могут разрабатываться в типах классов, которые выполняются до первого использования типа для инициализации на уровне типа.</span><span class="sxs-lookup"><span data-stu-id="ebb14-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="ebb14-155">Дополнительные сведения см. в разделе [ `let` привязок в классах](let-bindings-in-classes.md) и [ `do` привязок в классах](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="ebb14-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ebb14-156">См. также</span><span class="sxs-lookup"><span data-stu-id="ebb14-156">See also</span></span>

- [<span data-ttu-id="ebb14-157">Члены</span><span class="sxs-lookup"><span data-stu-id="ebb14-157">Members</span></span>](index.md)
