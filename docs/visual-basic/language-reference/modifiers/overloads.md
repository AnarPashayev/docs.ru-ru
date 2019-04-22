---
title: Overloads (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 0d68846938aba809a7a3a6f7d27f185bb90a39cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819337"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="c4653-102">Overloads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4653-102">Overloads (Visual Basic)</span></span>
<span data-ttu-id="c4653-103">Указывает, что свойство или процедура повторно определяет одно или несколько существующих свойств или процедур с таким же именем.</span><span class="sxs-lookup"><span data-stu-id="c4653-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4653-104">Примечания</span><span class="sxs-lookup"><span data-stu-id="c4653-104">Remarks</span></span>  
 <span data-ttu-id="c4653-105">*Перегрузка* — это предоставление нескольких определений для указанного имени свойства или процедуры в той же области.</span><span class="sxs-lookup"><span data-stu-id="c4653-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="c4653-106">Повторное объявление свойства или процедуры с другой сигнатурой иногда называют *скрытием за сигнатурой*.</span><span class="sxs-lookup"><span data-stu-id="c4653-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c4653-107">Правила</span><span class="sxs-lookup"><span data-stu-id="c4653-107">Rules</span></span>  
  
-   <span data-ttu-id="c4653-108">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="c4653-108">**Declaration Context.**</span></span> <span data-ttu-id="c4653-109">`Overloads` можно использовать только в операторе объявления свойства или процедуры.</span><span class="sxs-lookup"><span data-stu-id="c4653-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="c4653-110">**Комбинированные модификаторы.**</span><span class="sxs-lookup"><span data-stu-id="c4653-110">**Combined Modifiers.**</span></span> <span data-ttu-id="c4653-111">Нельзя указать `Overloads` вместе с [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) в одном объявлении процедуры.</span><span class="sxs-lookup"><span data-stu-id="c4653-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>  
  
-   <span data-ttu-id="c4653-112">**Обязательные различия.**</span><span class="sxs-lookup"><span data-stu-id="c4653-112">**Required Differences.**</span></span> <span data-ttu-id="c4653-113">*Подпись* этого объявления должна отличаться от сигнатуры каждого свойства или процедуры, которые оно переопределяет.</span><span class="sxs-lookup"><span data-stu-id="c4653-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="c4653-114">Сигнатура включает в себя имя свойства или процедуры, а также следующие элементы:</span><span class="sxs-lookup"><span data-stu-id="c4653-114">The signature comprises the property or procedure name together with the following:</span></span>  
  
    -   <span data-ttu-id="c4653-115">число параметров;</span><span class="sxs-lookup"><span data-stu-id="c4653-115">the number of parameters</span></span>  
  
    -   <span data-ttu-id="c4653-116">порядок параметров;</span><span class="sxs-lookup"><span data-stu-id="c4653-116">the order of the parameters</span></span>  
  
    -   <span data-ttu-id="c4653-117">типы данных параметров;</span><span class="sxs-lookup"><span data-stu-id="c4653-117">the data types of the parameters</span></span>  
  
    -   <span data-ttu-id="c4653-118">число параметров типа (для универсальной процедуры);</span><span class="sxs-lookup"><span data-stu-id="c4653-118">the number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="c4653-119">тип возвращаемого значения (только для процедуры оператора преобразования).</span><span class="sxs-lookup"><span data-stu-id="c4653-119">the return type (only for a conversion operator procedure)</span></span>  
  
     <span data-ttu-id="c4653-120">Все перегрузки должны иметь одно и то же имя, но каждая должна отличаться от всех остальных по одному или нескольким из предыдущих аспектов.</span><span class="sxs-lookup"><span data-stu-id="c4653-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="c4653-121">Это позволяет компилятору определить, какую именно версию следует использовать, когда код вызывает свойство или процедуру.</span><span class="sxs-lookup"><span data-stu-id="c4653-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>  
  
-   <span data-ttu-id="c4653-122">**Запрещенные различия.**</span><span class="sxs-lookup"><span data-stu-id="c4653-122">**Disallowed Differences.**</span></span> <span data-ttu-id="c4653-123">Изменение одного или нескольких из следующих аспектов не является допустимым для перегрузки свойства или процедуры, поскольку они не являются частью сигнатуры:</span><span class="sxs-lookup"><span data-stu-id="c4653-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>  
  
    -   <span data-ttu-id="c4653-124">наличие возвращаемого значения (для процедуры);</span><span class="sxs-lookup"><span data-stu-id="c4653-124">whether or not it returns a value (for a procedure)</span></span>  
  
    -   <span data-ttu-id="c4653-125">тип данных возвращаемого значения (за исключением оператора преобразования);</span><span class="sxs-lookup"><span data-stu-id="c4653-125">the data type of the return value (except for a conversion operator)</span></span>  
  
    -   <span data-ttu-id="c4653-126">имена параметров или параметров типа;</span><span class="sxs-lookup"><span data-stu-id="c4653-126">the names of the parameters or type parameters</span></span>  
  
    -   <span data-ttu-id="c4653-127">ограничения для параметров типа (для универсальной процедуры);</span><span class="sxs-lookup"><span data-stu-id="c4653-127">the constraints on the type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="c4653-128">ключевые слова модификаторов параметров (например, `ByRef` или `Optional`);</span><span class="sxs-lookup"><span data-stu-id="c4653-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>  
  
    -   <span data-ttu-id="c4653-129">ключевые слова модификаторов свойств или процедур (например, `Public` или `Shared`).</span><span class="sxs-lookup"><span data-stu-id="c4653-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>  
  
-   <span data-ttu-id="c4653-130">**Необязательный модификатор.**</span><span class="sxs-lookup"><span data-stu-id="c4653-130">**Optional Modifier.**</span></span> <span data-ttu-id="c4653-131">Модификатор `Overloads` можно не использовать при определении нескольких перегруженных свойств или процедур в одном классе.</span><span class="sxs-lookup"><span data-stu-id="c4653-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="c4653-132">Однако при использовании `Overloads` в одном из объявлений его необходимо использовать в них всех.</span><span class="sxs-lookup"><span data-stu-id="c4653-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>  
  
-   <span data-ttu-id="c4653-133">**Затенение и перегрузка.**</span><span class="sxs-lookup"><span data-stu-id="c4653-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="c4653-134">`Overloads` Можно также использовать для затенения существующего члена или набора перегруженных членов в базовом классе.</span><span class="sxs-lookup"><span data-stu-id="c4653-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="c4653-135">При таком использовании `Overloads` свойство или метод объявляются с таким же именем и таким же списком параметров, как и у члена базового класса, а ключевое слово `Shadows` не предоставляется.</span><span class="sxs-lookup"><span data-stu-id="c4653-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>  
  
 <span data-ttu-id="c4653-136">При использовании `Overrides` компилятор неявно добавляет `Overloads`, чтобы упростить работу API-интерфейсов с библиотекой C#.</span><span class="sxs-lookup"><span data-stu-id="c4653-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="c4653-137">Модификатор `Overloads` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="c4653-137">The `Overloads` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c4653-138">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="c4653-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="c4653-139">Оператор Statement</span><span class="sxs-lookup"><span data-stu-id="c4653-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="c4653-140">Оператор Property</span><span class="sxs-lookup"><span data-stu-id="c4653-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="c4653-141">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="c4653-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4653-142">См. также</span><span class="sxs-lookup"><span data-stu-id="c4653-142">See also</span></span>

- [<span data-ttu-id="c4653-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="c4653-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="c4653-144">Перегрузка процедур</span><span class="sxs-lookup"><span data-stu-id="c4653-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="c4653-145">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4653-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="c4653-146">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="c4653-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="c4653-147">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="c4653-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
