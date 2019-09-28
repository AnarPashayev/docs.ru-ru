---
title: Функция CType (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 4a0391b0a5d76f36803b433369d4832c02b05e09
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592099"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="bc680-102">Функция CType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc680-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="bc680-103">Возвращает результат явного преобразования выражения в указанный тип данных, объект, структуру, класс или интерфейс.</span><span class="sxs-lookup"><span data-stu-id="bc680-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc680-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bc680-104">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="bc680-105">Части</span><span class="sxs-lookup"><span data-stu-id="bc680-105">Parts</span></span>

<span data-ttu-id="bc680-106">`expression` любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="bc680-106">`expression` Any valid expression.</span></span> <span data-ttu-id="bc680-107">Если значение `expression` находится вне диапазона, допустимого `typename`, Visual Basic создает исключение.</span><span class="sxs-lookup"><span data-stu-id="bc680-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="bc680-108">`typename` любое выражение, которое является допустимым в предложении `As` в инструкции `Dim`, то есть имя любого типа данных, объекта, структуры, класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="bc680-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc680-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="bc680-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="bc680-110">Для преобразования типов также можно использовать следующие функции.</span><span class="sxs-lookup"><span data-stu-id="bc680-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="bc680-111">Функции преобразования типов, такие как `CByte`, `CDbl` и `CInt`, которые выполняют преобразование в конкретный тип данных.</span><span class="sxs-lookup"><span data-stu-id="bc680-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="bc680-112">Дополнительные сведения см. в разделе [функции преобразования типов](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="bc680-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>
> - <span data-ttu-id="bc680-113">Оператор [DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) или [Оператор TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bc680-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="bc680-114">Для этих операторов требуется, чтобы один тип наследовал или реализовывал другой тип.</span><span class="sxs-lookup"><span data-stu-id="bc680-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="bc680-115">Они могут обеспечить более высокую производительность, чем `CType` при преобразовании в тип данных `Object` и из него.</span><span class="sxs-lookup"><span data-stu-id="bc680-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="bc680-116">`CType` компилируется встроенным образом. Это означает, что код преобразования является частью кода, который вычисляет выражение.</span><span class="sxs-lookup"><span data-stu-id="bc680-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="bc680-117">В некоторых случаях код выполняется быстрее, так как для выполнения преобразования не вызываются никакие процедуры.</span><span class="sxs-lookup"><span data-stu-id="bc680-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="bc680-118">Если преобразование не определено с `expression` на `typename` (например, с `Integer` до `Date`), Visual Basic выводит сообщение об ошибке времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="bc680-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="bc680-119">Если во время выполнения происходит сбой преобразования, выдается соответствующее исключение.</span><span class="sxs-lookup"><span data-stu-id="bc680-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="bc680-120">Если сужение преобразования завершается неудачно, то наиболее распространенным результатом является <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="bc680-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="bc680-121">Если преобразование не определено, в выбрасывается <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="bc680-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="bc680-122">Например, это может произойти, если `expression` относится к типу `Object`, а тип времени выполнения не преобразуется в `typename`.</span><span class="sxs-lookup"><span data-stu-id="bc680-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="bc680-123">Если тип данных `expression` или `typename` является определенным классом или структурой, можно определить `CType` в этом классе или структуре как оператор преобразования.</span><span class="sxs-lookup"><span data-stu-id="bc680-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="bc680-124">Это делает `CType` выступающим в качестве *перегруженного оператора*.</span><span class="sxs-lookup"><span data-stu-id="bc680-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="bc680-125">В этом случае можно управлять поведением преобразований в класс или структуру, включая исключения, которые могут быть созданы.</span><span class="sxs-lookup"><span data-stu-id="bc680-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="bc680-126">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="bc680-126">Overloading</span></span>

<span data-ttu-id="bc680-127">Оператор `CType` также может быть перегружен в классе или структуре, определенной за пределами кода.</span><span class="sxs-lookup"><span data-stu-id="bc680-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="bc680-128">Если код преобразует в или из такого класса или структуры, убедитесь, что вы понимаете поведение его оператора `CType`.</span><span class="sxs-lookup"><span data-stu-id="bc680-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="bc680-129">Для получения дополнительной информации см. [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bc680-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="bc680-130">Преобразование динамических объектов</span><span class="sxs-lookup"><span data-stu-id="bc680-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="bc680-131">Преобразования типов динамических объектов выполняются с помощью определяемых пользователем динамических преобразований, использующих методы <xref:System.Dynamic.DynamicObject.TryConvert%2A> или <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc680-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="bc680-132">При работе с динамическими объектами используйте метод <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> для преобразования динамического объекта.</span><span class="sxs-lookup"><span data-stu-id="bc680-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="bc680-133">Пример</span><span class="sxs-lookup"><span data-stu-id="bc680-133">Example</span></span>

<span data-ttu-id="bc680-134">В следующем примере функция `CType` используется для преобразования выражения в тип данных `Single`.</span><span class="sxs-lookup"><span data-stu-id="bc680-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="bc680-135">Дополнительные примеры см. в разделе [явные и неявные преобразования](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="bc680-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc680-136">См. также</span><span class="sxs-lookup"><span data-stu-id="bc680-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="bc680-137">Функции преобразования типов</span><span class="sxs-lookup"><span data-stu-id="bc680-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="bc680-138">Функции преобразования</span><span class="sxs-lookup"><span data-stu-id="bc680-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="bc680-139">Оператор Statement</span><span class="sxs-lookup"><span data-stu-id="bc680-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- <span data-ttu-id="bc680-140">[Практическое руководство. Определение оператора преобразования @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="bc680-140">[How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)</span></span>
- [<span data-ttu-id="bc680-141">Преобразование типов в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bc680-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
