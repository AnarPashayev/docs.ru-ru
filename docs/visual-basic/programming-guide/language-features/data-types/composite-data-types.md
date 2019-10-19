---
title: Составные типы данных (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 768559c7a6caf064f7529786675e51ce19667d6b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581714"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="6fe9b-102">Составные типы данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fe9b-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="6fe9b-103">Помимо простейших типов данных Visual Basic предоставляет также возможность собирать элементы различных типов для создания *составных типов данных* , таких как структуры, массивы и классы.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="6fe9b-104">Составные типы данных можно создавать из простейших типов и из других составных типов.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="6fe9b-105">Например, можно определить массив элементов структуры или структуру с элементами массива.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="6fe9b-106">Типы данных</span><span class="sxs-lookup"><span data-stu-id="6fe9b-106">Data Types</span></span>  
 <span data-ttu-id="6fe9b-107">Составной тип отличается от типа данных любого из его компонентов.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="6fe9b-108">Например, массив `Integer` элементов не относится к типу данных `Integer`.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="6fe9b-109">Тип данных массива обычно представляется при необходимости с использованием типа элемента, круглых скобок и запятых.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="6fe9b-110">Например, одномерный массив `String` элементов представлен как `String()`, а двумерный массив элементов `Boolean` представляется как `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="6fe9b-111">Типы структур</span><span class="sxs-lookup"><span data-stu-id="6fe9b-111">Structure Types</span></span>  
 <span data-ttu-id="6fe9b-112">Не существует одного типа данных, включающего в себя все структуры.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="6fe9b-113">Вместо этого каждое определение структуры представляет собой уникальный тип данных, даже если две структуры определяют идентичные элементы в том же порядке.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="6fe9b-114">Однако при создании двух или более экземпляров одной и той же структуры Visual Basic рассматривает их как один и тот же тип данных.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="6fe9b-115">Кортежи</span><span class="sxs-lookup"><span data-stu-id="6fe9b-115">Tuples</span></span>

<span data-ttu-id="6fe9b-116">Кортеж — это упрощенная структура, которая содержит два или более полей, типы которых являются предопределенными.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="6fe9b-117">Кортежи поддерживаются начиная с Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="6fe9b-118">Кортежи чаще всего используются для возвращения нескольких значений из одного вызова метода без необходимости передачи аргументов по ссылке или упаковки возвращаемых полей в более тяжелом классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="6fe9b-119">Дополнительные сведения о кортежах см. в разделе [кортежи](tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="6fe9b-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="6fe9b-120">Типы массивов</span><span class="sxs-lookup"><span data-stu-id="6fe9b-120">Array Types</span></span>  
 <span data-ttu-id="6fe9b-121">Не существует одного типа данных, включающего в себя все массивы.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="6fe9b-122">Тип данных конкретного экземпляра массива определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6fe9b-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="6fe9b-123">Факт является массивом</span><span class="sxs-lookup"><span data-stu-id="6fe9b-123">The fact of being an array</span></span>  
  
- <span data-ttu-id="6fe9b-124">Ранг (число измерений) массива</span><span class="sxs-lookup"><span data-stu-id="6fe9b-124">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="6fe9b-125">Тип элемента массива</span><span class="sxs-lookup"><span data-stu-id="6fe9b-125">The element type of the array</span></span>  
  
 <span data-ttu-id="6fe9b-126">В частности, длина данного измерения не является частью типа данных экземпляра.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="6fe9b-127">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-127">The following example illustrates this.</span></span>  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="6fe9b-128">В предыдущем примере переменные массива `arrayA` и `arrayB` считаются одним и тем же типом данных — `Byte()`, несмотря на то, что они инициализируются с разной длиной.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="6fe9b-129">Переменные `arrayB` и `arrayC` относятся к разным типам, так как их типы элементов различаются.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="6fe9b-130">Переменные `arrayC` и `arrayD` имеют разные типы, так как их ранги различаются.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="6fe9b-131">Переменные `arrayD` и `arrayE` имеют одинаковый тип — `Short(,)` — так как их ранги и типы элементов одинаковы, даже если `arrayD` еще не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="6fe9b-132">Дополнительные сведения о массивах см. в разделе [массивы](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="6fe9b-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="6fe9b-133">Типы классов</span><span class="sxs-lookup"><span data-stu-id="6fe9b-133">Class Types</span></span>  
 <span data-ttu-id="6fe9b-134">Не существует одного типа данных, включающего в себя все классы.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="6fe9b-135">Хотя один класс может наследовать от другого класса, каждый из них является отдельным типом данных.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="6fe9b-136">Несколько экземпляров одного и того же класса имеют один и тот же тип данных.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="6fe9b-137">Если присвоить одну переменную экземпляра класса другой, не только те, которые имеют один и тот же тип данных, они указывают на один и тот же экземпляр класса в памяти.</span><span class="sxs-lookup"><span data-stu-id="6fe9b-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="6fe9b-138">Дополнительные сведения о классах см. в разделе [объекты и классы](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="6fe9b-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe9b-139">См. также</span><span class="sxs-lookup"><span data-stu-id="6fe9b-139">See also</span></span>

- [<span data-ttu-id="6fe9b-140">Типы данных</span><span class="sxs-lookup"><span data-stu-id="6fe9b-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="6fe9b-141">Простые типы данных</span><span class="sxs-lookup"><span data-stu-id="6fe9b-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="6fe9b-142">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6fe9b-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="6fe9b-143">Типы значений и ссылочные типы</span><span class="sxs-lookup"><span data-stu-id="6fe9b-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="6fe9b-144">Преобразования типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6fe9b-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="6fe9b-145">Структуры</span><span class="sxs-lookup"><span data-stu-id="6fe9b-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6fe9b-146">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="6fe9b-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="6fe9b-147">Практическое руководство. Хранение нескольких значений в переменной</span><span class="sxs-lookup"><span data-stu-id="6fe9b-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
