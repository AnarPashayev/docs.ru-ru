---
title: Перегрузки операторов
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: KrzysztofCwalina
ms.openlocfilehash: 441dc2777cd8d221300c526b6b31a647af60ca71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756862"
---
# <a name="operator-overloads"></a><span data-ttu-id="6d656-102">Перегрузки операторов</span><span class="sxs-lookup"><span data-stu-id="6d656-102">Operator Overloads</span></span>
<span data-ttu-id="6d656-103">Перегрузки операторов позволяют типы framework отображаться так, как если бы они были примитивы встроенный язык.</span><span class="sxs-lookup"><span data-stu-id="6d656-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>  
  
 <span data-ttu-id="6d656-104">Несмотря на то, что разрешенных и полезен в некоторых ситуациях, перегрузки операторов следует использовать осторожно.</span><span class="sxs-lookup"><span data-stu-id="6d656-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="6d656-105">Есть много таких ситуаций, в которых оператор перегрузка были злонамеренное использование, например при запуске конструкторах framework использование операторов для операций, которые должны быть простые методы.</span><span class="sxs-lookup"><span data-stu-id="6d656-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="6d656-106">Следующие рекомендации помогут вам решить, когда и как использовать перегрузку операторов.</span><span class="sxs-lookup"><span data-stu-id="6d656-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>  
  
 <span data-ttu-id="6d656-107">**X AVOID** определения перегрузки оператора, за исключением того, в типах, которые следует воспринимается как типы-примитивы (встроенные).</span><span class="sxs-lookup"><span data-stu-id="6d656-107">**X AVOID** defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>  
  
 <span data-ttu-id="6d656-108">**✓ CONSIDER** определения перегрузки оператора в типе, который следует кажется типом-примитивом.</span><span class="sxs-lookup"><span data-stu-id="6d656-108">**✓ CONSIDER** defining operator overloads in a type that should feel like a primitive type.</span></span>  
  
 <span data-ttu-id="6d656-109">Например <xref:System.String?displayProperty=nameWithType> имеет `operator==` и `operator!=` определен.</span><span class="sxs-lookup"><span data-stu-id="6d656-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>  
  
 <span data-ttu-id="6d656-110">**✓ DO** определения перегрузки операторов в структур, которые представляют собой числа (например, <xref:System.Decimal?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="6d656-110">**✓ DO** define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="6d656-111">**X DO NOT** быть забавны при определении перегрузки операторов.</span><span class="sxs-lookup"><span data-stu-id="6d656-111">**X DO NOT** be cute when defining operator overloads.</span></span>  
  
 <span data-ttu-id="6d656-112">Перегрузка операторов полезно в случаях, в которых совершенно очевидно, каким будет результат операции.</span><span class="sxs-lookup"><span data-stu-id="6d656-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="6d656-113">Например, имеет смысл иметь возможность вычесть единицу <xref:System.DateTime> из другого `DateTime` и получите <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="6d656-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="6d656-114">Тем не менее он не подходит для использования оператора логического объединения объединения двух запросов к базе данных, или оператор сдвига для записи в поток.</span><span class="sxs-lookup"><span data-stu-id="6d656-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>  
  
 <span data-ttu-id="6d656-115">**X DO NOT** предоставляют перегрузки оператор, если по крайней мере один из операндов имеет тип, определив перегрузку.</span><span class="sxs-lookup"><span data-stu-id="6d656-115">**X DO NOT** provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>  
  
 <span data-ttu-id="6d656-116">**✓ DO** перегружать операторы симметричную.</span><span class="sxs-lookup"><span data-stu-id="6d656-116">**✓ DO** overload operators in a symmetric fashion.</span></span>  
  
 <span data-ttu-id="6d656-117">Например, при перегрузке `operator==`, следует также перегрузить `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="6d656-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="6d656-118">Аналогично при перегрузке `operator<`, следует также перегрузить `operator>`, и т. д.</span><span class="sxs-lookup"><span data-stu-id="6d656-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>  
  
 <span data-ttu-id="6d656-119">**✓ CONSIDER** предоставлять методы с понятными именами, которые соответствуют каждой перегруженный оператор.</span><span class="sxs-lookup"><span data-stu-id="6d656-119">**✓ CONSIDER** providing methods with friendly names that correspond to each overloaded operator.</span></span>  
  
 <span data-ttu-id="6d656-120">Многие языки не поддерживают перегрузку операторов.</span><span class="sxs-lookup"><span data-stu-id="6d656-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="6d656-121">По этой причине рекомендуется Включение дополнительного метода с соответствующим именем домена, обеспечивающее эквивалентную функциональность типы с перегруженными операторами.</span><span class="sxs-lookup"><span data-stu-id="6d656-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>  
  
 <span data-ttu-id="6d656-122">Следующая таблица содержит список операторов и имена соответствующих методов понятное.</span><span class="sxs-lookup"><span data-stu-id="6d656-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>  
  
|<span data-ttu-id="6d656-123">Символ оператора C#</span><span class="sxs-lookup"><span data-stu-id="6d656-123">C# Operator Symbol</span></span>|<span data-ttu-id="6d656-124">Имя метаданных</span><span class="sxs-lookup"><span data-stu-id="6d656-124">Metadata Name</span></span>|<span data-ttu-id="6d656-125">Понятное имя</span><span class="sxs-lookup"><span data-stu-id="6d656-125">Friendly Name</span></span>|  
|-------------------------|-------------------|-------------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|  
|`=`|`op_Assign`|`Assign`|  
|`<<`|`op_LeftShift`|`LeftShift`|  
|`>>`|`op_RightShift`|`RightShift`|  
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|  
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|  
|`==`|`op_Equality`|`Equals`|  
|`!=`|`op_Inequality`|`Equals`|  
|`>`|`op_GreaterThan`|`CompareTo`|  
|`<`|`op_LessThan`|`CompareTo`|  
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|  
|`<=`|`op_LessThanOrEqual`|`CompareTo`|  
|`*=`|`op_MultiplicationAssignment`|`Multiply`|  
|`-=`|`op_SubtractionAssignment`|`Subtract`|  
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|  
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|  
|`%=`|`op_ModulusAssignment`|`Mod`|  
|`+=`|`op_AdditionAssignment`|`Add`|  
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|  
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### <a name="overloading-operator-"></a><span data-ttu-id="6d656-126">Перегрузка оператора ==</span><span class="sxs-lookup"><span data-stu-id="6d656-126">Overloading Operator ==</span></span>  
 <span data-ttu-id="6d656-127">Перегрузка `operator ==` довольно сложен.</span><span class="sxs-lookup"><span data-stu-id="6d656-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="6d656-128">Семантика оператора должны быть совместим с несколько других элементов, таких как <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d656-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="conversion-operators"></a><span data-ttu-id="6d656-129">Операторы преобразования</span><span class="sxs-lookup"><span data-stu-id="6d656-129">Conversion Operators</span></span>  
 <span data-ttu-id="6d656-130">Операторы преобразования являются унарными операторами, которые позволяют преобразовывать из одного типа в другой.</span><span class="sxs-lookup"><span data-stu-id="6d656-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="6d656-131">Операторы должны определяться как статические члены на операнд или тип возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="6d656-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="6d656-132">Существует два типа операторов преобразования: явные и неявные.</span><span class="sxs-lookup"><span data-stu-id="6d656-132">There are two types of conversion operators: implicit and explicit.</span></span>  
  
 <span data-ttu-id="6d656-133">**X DO NOT** предоставить оператор преобразования, если такое преобразование не ожидается конечными пользователями.</span><span class="sxs-lookup"><span data-stu-id="6d656-133">**X DO NOT** provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>  
  
 <span data-ttu-id="6d656-134">**X DO NOT** определить операторы преобразования за пределами области типа.</span><span class="sxs-lookup"><span data-stu-id="6d656-134">**X DO NOT** define conversion operators outside of a type’s domain.</span></span>  
  
 <span data-ttu-id="6d656-135">Например <xref:System.Int32>, <xref:System.Double>, и <xref:System.Decimal> являются все числовые типы, тогда как <xref:System.DateTime> не является.</span><span class="sxs-lookup"><span data-stu-id="6d656-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="6d656-136">Таким образом, должно быть не оператор преобразования `Double(long)` для `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="6d656-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="6d656-137">В этом случае рекомендуется использовать конструктор.</span><span class="sxs-lookup"><span data-stu-id="6d656-137">A constructor is preferred in such a case.</span></span>  
  
 <span data-ttu-id="6d656-138">**X DO NOT** предоставить неявный оператор преобразования, если преобразование является потенциально с потерями.</span><span class="sxs-lookup"><span data-stu-id="6d656-138">**X DO NOT** provide an implicit conversion operator if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="6d656-139">Например, не должно быть неявное преобразование из `Double` для `Int32` поскольку `Double` имеет широкий диапазон, чем `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6d656-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="6d656-140">Могут быть предоставлены явный оператор преобразования, даже если преобразование является потенциально с потерями.</span><span class="sxs-lookup"><span data-stu-id="6d656-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="6d656-141">**X DO NOT** вызывайте исключения из неявных приведений типов.</span><span class="sxs-lookup"><span data-stu-id="6d656-141">**X DO NOT** throw exceptions from implicit casts.</span></span>  
  
 <span data-ttu-id="6d656-142">Очень трудно для конечных пользователей понять, что происходит, так как они могут быть виду, что преобразование выполняется.</span><span class="sxs-lookup"><span data-stu-id="6d656-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>  
  
 <span data-ttu-id="6d656-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> случае вызов оператора приведения преобразование с потерями и контракт оператора не допускает преобразования с потерей данных.</span><span class="sxs-lookup"><span data-stu-id="6d656-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>  
  
 <span data-ttu-id="6d656-144">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="6d656-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6d656-145">*Перепечатано разрешением Пирсона для образовательных учреждений, Inc. из [рекомендации по разработке Framework: Условные обозначения, стили и шаблоны для библиотеки .NET для повторного использования, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Кшиштов Квалина и Брэд Абрамс, опубликованных 22 октября 2008 г., издательство Addison-Wesley Professional как части цикла разработки Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6d656-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d656-146">См. также</span><span class="sxs-lookup"><span data-stu-id="6d656-146">See also</span></span>

- [<span data-ttu-id="6d656-147">Правила разработки членов</span><span class="sxs-lookup"><span data-stu-id="6d656-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="6d656-148">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="6d656-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
