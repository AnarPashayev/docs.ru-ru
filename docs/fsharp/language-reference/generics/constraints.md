---
title: Ограничения
description: Сведения об F# ограничениях, применяемых к параметрам универсального типа для указания требований для аргумента типа в универсальном типе или функции.
ms.date: 05/16/2016
ms.openlocfilehash: 9912ba63138d893a7c616661dd2b1cbdbe51916c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736792"
---
# <a name="constraints"></a><span data-ttu-id="cb3e2-103">Ограничения</span><span class="sxs-lookup"><span data-stu-id="cb3e2-103">Constraints</span></span>

<span data-ttu-id="cb3e2-104">В этом разделе описываются ограничения, которые можно применять к параметрам универсального типа для указания требований для аргумента типа в универсальном типе или функции.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb3e2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb3e2-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="cb3e2-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="cb3e2-106">Remarks</span></span>

<span data-ttu-id="cb3e2-107">Существует несколько различных ограничений, которые можно применить для ограничения типов, которые могут использоваться в универсальном типе.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="cb3e2-108">В следующей таблице перечислены и описаны эти ограничения.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="cb3e2-109">Ограничение</span><span class="sxs-lookup"><span data-stu-id="cb3e2-109">Constraint</span></span>|<span data-ttu-id="cb3e2-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb3e2-110">Syntax</span></span>|<span data-ttu-id="cb3e2-111">Описание</span><span class="sxs-lookup"><span data-stu-id="cb3e2-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="cb3e2-112">Ограничение типа</span><span class="sxs-lookup"><span data-stu-id="cb3e2-112">Type Constraint</span></span>|<span data-ttu-id="cb3e2-113">*тип-параметр* : &gt; *тип*</span><span class="sxs-lookup"><span data-stu-id="cb3e2-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="cb3e2-114">Указанный тип должен быть равен или производному от указанного типа, или, если тип является интерфейсом, предоставленный тип должен реализовывать интерфейс.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="cb3e2-115">Ограничение null</span><span class="sxs-lookup"><span data-stu-id="cb3e2-115">Null Constraint</span></span>|<span data-ttu-id="cb3e2-116">*тип-параметр* : NULL</span><span class="sxs-lookup"><span data-stu-id="cb3e2-116">*type-parameter* : null</span></span>|<span data-ttu-id="cb3e2-117">Указанный тип должен поддерживать литерал null.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-117">The provided type must support the null literal.</span></span> <span data-ttu-id="cb3e2-118">Сюда входят все типы объектов .NET, но F# не типы списка, кортежа, функции, класса, записи или объединения.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="cb3e2-119">Ограничение явного члена</span><span class="sxs-lookup"><span data-stu-id="cb3e2-119">Explicit Member Constraint</span></span>|<span data-ttu-id="cb3e2-120">[(]*параметр типа* [или... или *параметр типа*)]: (*сигнатура члена*)</span><span class="sxs-lookup"><span data-stu-id="cb3e2-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="cb3e2-121">По крайней мере один из указанных аргументов типа должен иметь член с указанной сигнатурой. не предназначено для общего использования.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="cb3e2-122">Члены должны быть либо явно определены в типе, либо частью расширения неявного типа, чтобы быть допустимыми целевыми объектами для ограничения явного члена.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="cb3e2-123">Ограничение конструктора</span><span class="sxs-lookup"><span data-stu-id="cb3e2-123">Constructor Constraint</span></span>|<span data-ttu-id="cb3e2-124">*тип — параметр* : (New: unit-&gt; "a)</span><span class="sxs-lookup"><span data-stu-id="cb3e2-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="cb3e2-125">Указанный тип должен иметь конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-125">The provided type must have a parameterless constructor.</span></span>|
|<span data-ttu-id="cb3e2-126">Ограничение типа значения</span><span class="sxs-lookup"><span data-stu-id="cb3e2-126">Value Type Constraint</span></span>|<span data-ttu-id="cb3e2-127">: структура</span><span class="sxs-lookup"><span data-stu-id="cb3e2-127">: struct</span></span>|<span data-ttu-id="cb3e2-128">Указанный тип должен быть типом значения .NET.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="cb3e2-129">Ограничение ссылочного типа</span><span class="sxs-lookup"><span data-stu-id="cb3e2-129">Reference Type Constraint</span></span>|<span data-ttu-id="cb3e2-130">: не структура</span><span class="sxs-lookup"><span data-stu-id="cb3e2-130">: not struct</span></span>|<span data-ttu-id="cb3e2-131">Указанный тип должен быть ссылочным типом .NET.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="cb3e2-132">Ограничение типа перечисления</span><span class="sxs-lookup"><span data-stu-id="cb3e2-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="cb3e2-133">: Enum @ no__t-0*базовый тип*&gt;</span><span class="sxs-lookup"><span data-stu-id="cb3e2-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="cb3e2-134">Указанный тип должен быть перечислимым типом с указанным базовым типом. не предназначено для общего использования.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="cb3e2-135">Ограничение делегата</span><span class="sxs-lookup"><span data-stu-id="cb3e2-135">Delegate Constraint</span></span>|<span data-ttu-id="cb3e2-136">: Delegate @ no__t-0*кортеж — параметр-Type*, *return-Type*&gt;</span><span class="sxs-lookup"><span data-stu-id="cb3e2-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="cb3e2-137">Указанный тип должен быть типом делегата с указанными аргументами и возвращаемым значением. не предназначено для общего использования.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="cb3e2-138">Ограничение сравнения</span><span class="sxs-lookup"><span data-stu-id="cb3e2-138">Comparison Constraint</span></span>|<span data-ttu-id="cb3e2-139">: сравнение</span><span class="sxs-lookup"><span data-stu-id="cb3e2-139">: comparison</span></span>|<span data-ttu-id="cb3e2-140">Указанный тип должен поддерживать сравнение.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="cb3e2-141">Ограничение на равенство</span><span class="sxs-lookup"><span data-stu-id="cb3e2-141">Equality Constraint</span></span>|<span data-ttu-id="cb3e2-142">: равенство</span><span class="sxs-lookup"><span data-stu-id="cb3e2-142">: equality</span></span>|<span data-ttu-id="cb3e2-143">Указанный тип должен поддерживать равенство.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="cb3e2-144">Неуправляемое ограничение</span><span class="sxs-lookup"><span data-stu-id="cb3e2-144">Unmanaged Constraint</span></span>|<span data-ttu-id="cb3e2-145">: неуправляемый</span><span class="sxs-lookup"><span data-stu-id="cb3e2-145">: unmanaged</span></span>|<span data-ttu-id="cb3e2-146">Указанный тип должен иметь неуправляемый тип.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="cb3e2-147">Неуправляемые типы являются определенными примитивными типами (`sbyte`, `byte`, `char` `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, 0, 1, 2 или 3), типы перечисления, 4 или не универсальный структура, поля которой являются неуправляемыми типами.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="cb3e2-148">Необходимо добавить ограничение, если в коде должна использоваться функция, доступная в типе ограничения, но не для типов в целом.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="cb3e2-149">Например, если для указания типа класса используется ограничение типа, можно использовать любой из методов этого класса в универсальной функции или типе.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="cb3e2-150">Указание ограничений иногда требуется при явном написании параметров типа, поскольку без ограничения компилятор не может проверить, что используемые функции будут доступны для любого типа, который может быть предоставлен во время выполнения для типа. параметр.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="cb3e2-151">Наиболее распространенные ограничения, используемые в F# коде, — это ограничения типов, задающих базовые классы или интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="cb3e2-152">Другие ограничения используются F# библиотекой для реализации определенных функций, таких как ограничение явного члена, которое используется для реализации перегрузки операторов для арифметических операторов или предоставляется в основном из-за того, что F# поддерживает полный набор ограничений, поддерживаемых средой CLR.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="cb3e2-153">Во время процесса определения типа некоторые ограничения выводятся автоматически компилятором.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="cb3e2-154">Например, если в функции используется оператор `+`, компилятор выводит явное ограничение на члены типов переменных, используемых в выражении.</span><span class="sxs-lookup"><span data-stu-id="cb3e2-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="cb3e2-155">В следующем коде показаны некоторые объявления ограничений:</span><span class="sxs-lookup"><span data-stu-id="cb3e2-155">The following code illustrates some constraint declarations:</span></span>

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a><span data-ttu-id="cb3e2-156">См. также</span><span class="sxs-lookup"><span data-stu-id="cb3e2-156">See also</span></span>

- [<span data-ttu-id="cb3e2-157">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="cb3e2-157">Generics</span></span>](index.md)
- [<span data-ttu-id="cb3e2-158">Ограничения</span><span class="sxs-lookup"><span data-stu-id="cb3e2-158">Constraints</span></span>](constraints.md)
