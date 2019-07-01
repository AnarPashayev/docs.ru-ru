---
title: Справочник по C#. Типы значений
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 9907811a43f408020e2ee76621d4975a53945570
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424034"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="4054a-102">Типы значений (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="4054a-102">Value types (C# Reference)</span></span>

<span data-ttu-id="4054a-103">Существует два типа значений:</span><span class="sxs-lookup"><span data-stu-id="4054a-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="4054a-104">Структуры</span><span class="sxs-lookup"><span data-stu-id="4054a-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="4054a-105">Перечисления</span><span class="sxs-lookup"><span data-stu-id="4054a-105">Enumerations</span></span>](enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="4054a-106">Основные возможности типов значений</span><span class="sxs-lookup"><span data-stu-id="4054a-106">Main features of value types</span></span>

<span data-ttu-id="4054a-107">Переменная типа значения содержит значение типа.</span><span class="sxs-lookup"><span data-stu-id="4054a-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="4054a-108">Например, переменная типа `int` может содержать значение `42`.</span><span class="sxs-lookup"><span data-stu-id="4054a-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="4054a-109">Это отличается от переменной ссылочного типа, которая содержит ссылку на экземпляр типа, также известный как объект.</span><span class="sxs-lookup"><span data-stu-id="4054a-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="4054a-110">Когда вы присваиваете новое значение переменной типа значения, это значение копируется.</span><span class="sxs-lookup"><span data-stu-id="4054a-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="4054a-111">Когда вы присваиваете новое значение переменной ссылочного типа, копируется не сам объект, а ссылка на него.</span><span class="sxs-lookup"><span data-stu-id="4054a-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="4054a-112">Все типы значения являются неявными производными от <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4054a-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="4054a-113">В отличие от ссылочных типов, создать новый производный от типа значения тип нельзя.</span><span class="sxs-lookup"><span data-stu-id="4054a-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="4054a-114">Тем не менее, как и ссылочные типы, структуры могут реализовывать интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="4054a-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="4054a-115">Переменные типа значения не могут иметь значение `null` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4054a-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="4054a-116">Однако переменные соответствующих [типов, допускающих значение null](../../../csharp/programming-guide/nullable-types/index.md), могут иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="4054a-116">However, variables of the corresponding [nullable types](../../../csharp/programming-guide/nullable-types/index.md) can be `null`.</span></span>

<span data-ttu-id="4054a-117">Каждый тип значения имеет неявный конструктор без параметров, который инициализирует значение по умолчанию этого типа.</span><span class="sxs-lookup"><span data-stu-id="4054a-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="4054a-118">Дополнительные сведения о значениях по умолчанию для типов значений см. в разделе [Таблица значений по умолчанию (справочник по C#)](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="4054a-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="4054a-119">Простые типы</span><span class="sxs-lookup"><span data-stu-id="4054a-119">Simple types</span></span>

<span data-ttu-id="4054a-120">*Простые типы* — это набор предопределенных типов структур, предоставленных C#, который содержит следующие типы:</span><span class="sxs-lookup"><span data-stu-id="4054a-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="4054a-121">[Целочисленные типы](../builtin-types/integral-numeric-types.md): типы целого числа и тип [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="4054a-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](char.md) type</span></span>
- [<span data-ttu-id="4054a-122">Типы с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="4054a-122">Floating-point types</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="4054a-123">bool</span><span class="sxs-lookup"><span data-stu-id="4054a-123">bool</span></span>](bool.md)

<span data-ttu-id="4054a-124">Простые типы определяются с помощью ключевых слов, но эти ключевые слова являются просто псевдонимами для предопределенных типов структур в пространстве имен <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="4054a-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="4054a-125">Например, [int](../builtin-types/integral-numeric-types.md) является псевдонимом типа <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4054a-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4054a-126">Полный список псевдонимов см. в разделе [Таблица встроенных типов (Справочник по C#)](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="4054a-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="4054a-127">Простые типы отличаются от других типов структур тем, что они разрешают некоторые дополнительные операции:</span><span class="sxs-lookup"><span data-stu-id="4054a-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="4054a-128">Простые типы можно инициализировать с помощью литералов.</span><span class="sxs-lookup"><span data-stu-id="4054a-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="4054a-129">Например, `'A'` — это литерал типа `char`, а `2001` — литерал типа `int`.</span><span class="sxs-lookup"><span data-stu-id="4054a-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="4054a-130">Константы простых типов можно объявить с помощью ключевого слова [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="4054a-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="4054a-131">Невозможно иметь константы других типов структур.</span><span class="sxs-lookup"><span data-stu-id="4054a-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="4054a-132">Константные выражения, операнды которых являются константами простого типа, вычисляются во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="4054a-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="4054a-133">Дополнительные сведения см. в разделе [Простые типы](~/_csharplang/spec/types.md#simple-types) статьи [Предварительная спецификация C# 6.0](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4054a-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="4054a-134">Инициализация типов значений</span><span class="sxs-lookup"><span data-stu-id="4054a-134">Initializing value types</span></span>

<span data-ttu-id="4054a-135">В языке C# локальные переменные необходимо инициализировать перед использованием.</span><span class="sxs-lookup"><span data-stu-id="4054a-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="4054a-136">Например, можно объявить локальную переменную без инициализации, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="4054a-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="4054a-137">Тем не менее использовать ее до инициализации нельзя.</span><span class="sxs-lookup"><span data-stu-id="4054a-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="4054a-138">Для инициализации локальной переменной можно использовать следующую инструкцию:</span><span class="sxs-lookup"><span data-stu-id="4054a-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="4054a-139">Эта инструкция эквивалентна следующей:</span><span class="sxs-lookup"><span data-stu-id="4054a-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="4054a-140">При необходимости объявление и инициализация могут быть выполнены в одной инструкции, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="4054a-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="4054a-141">– или –</span><span class="sxs-lookup"><span data-stu-id="4054a-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="4054a-142">Оператор [new](../operators/new-operator.md) вызывает конструктор без параметров конкретного типа и присваивает переменной значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4054a-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="4054a-143">В приведенном выше примере конструктору без параметров присвоено значение `0` для `myInt`.</span><span class="sxs-lookup"><span data-stu-id="4054a-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="4054a-144">Дополнительные сведения о значениях, присваиваемых путем вызова конструктора по умолчанию, см. в разделе [Таблица значений по умолчанию (справочник по C#)](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="4054a-144">For more information about values assigned by calling default constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="4054a-145">С определяемыми пользователем типами используйте [new](../operators/new-operator.md) для вызова конструктора без параметров.</span><span class="sxs-lookup"><span data-stu-id="4054a-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="4054a-146">Например, следующая инструкция вызывает конструктор без параметров структуры `Point`:</span><span class="sxs-lookup"><span data-stu-id="4054a-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
Point p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="4054a-147">После этого вызова структура считается определенно присвоенной, то есть все ее элементы будут инициализированы и получат значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4054a-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="4054a-148">Дополнительные сведения об операторе `new` см. в разделе [new (справочник по C#)](../operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4054a-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span></span>

<span data-ttu-id="4054a-149">Дополнительные сведения о форматировании выходных данных числовых типов см. в разделе [Таблица форматирования числовых результатов (справочник по C#)](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="4054a-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4054a-150">См. также</span><span class="sxs-lookup"><span data-stu-id="4054a-150">See also</span></span>

- [<span data-ttu-id="4054a-151">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="4054a-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4054a-152">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="4054a-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4054a-153">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="4054a-153">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4054a-154">Типы</span><span class="sxs-lookup"><span data-stu-id="4054a-154">Types</span></span>](types.md)
- [<span data-ttu-id="4054a-155">Ссылочные типы</span><span class="sxs-lookup"><span data-stu-id="4054a-155">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="4054a-156">Типы, допускающие значения NULL</span><span class="sxs-lookup"><span data-stu-id="4054a-156">Nullable types</span></span>](../../programming-guide/nullable-types/index.md)
