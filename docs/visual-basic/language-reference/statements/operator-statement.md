---
title: Operator Statement (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: 4162f7cb5d8b89a1e5e8e7db429cf4e8dd9b700a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583593"
---
# <a name="operator-statement"></a><span data-ttu-id="2f418-102">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="2f418-102">Operator Statement</span></span>
<span data-ttu-id="2f418-103">Объявляет символ оператора, операнды и код, которые определяют процедуру оператора для класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="2f418-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f418-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2f418-104">Syntax</span></span>  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a><span data-ttu-id="2f418-105">Части</span><span class="sxs-lookup"><span data-stu-id="2f418-105">Parts</span></span>  
 `attrlist`  
 <span data-ttu-id="2f418-106">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="2f418-106">Optional.</span></span> <span data-ttu-id="2f418-107">См. в разделе [список атрибутов](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="2f418-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `Public`  
 <span data-ttu-id="2f418-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2f418-108">Required.</span></span> <span data-ttu-id="2f418-109">Указывает, что эта процедура оператора [открытый](../../../visual-basic/language-reference/modifiers/public.md) доступа.</span><span class="sxs-lookup"><span data-stu-id="2f418-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>  
  
 `Overloads`  
 <span data-ttu-id="2f418-110">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="2f418-110">Optional.</span></span> <span data-ttu-id="2f418-111">См. в разделе [перегружает](../../../visual-basic/language-reference/modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="2f418-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>  
  
 `Shared`  
 <span data-ttu-id="2f418-112">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2f418-112">Required.</span></span> <span data-ttu-id="2f418-113">Указывает, что эта процедура оператора [Shared](../../../visual-basic/language-reference/modifiers/shared.md) процедуры.</span><span class="sxs-lookup"><span data-stu-id="2f418-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>  
  
 `Shadows`  
 <span data-ttu-id="2f418-114">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="2f418-114">Optional.</span></span> <span data-ttu-id="2f418-115">См. в разделе [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="2f418-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
 `Widening`  
 <span data-ttu-id="2f418-116">Требуется для оператора преобразования, если не указать `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="2f418-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="2f418-117">Указывает, что эта процедура оператора определяет [Widening](../../../visual-basic/language-reference/modifiers/widening.md) преобразования.</span><span class="sxs-lookup"><span data-stu-id="2f418-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="2f418-118">См. в разделе «Расширяющие и сужающие преобразования» на этой странице справки.</span><span class="sxs-lookup"><span data-stu-id="2f418-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `Narrowing`  
 <span data-ttu-id="2f418-119">Требуется для оператора преобразования, если не указать `Widening`.</span><span class="sxs-lookup"><span data-stu-id="2f418-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="2f418-120">Указывает, что эта процедура оператора определяет [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) преобразования.</span><span class="sxs-lookup"><span data-stu-id="2f418-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="2f418-121">См. в разделе «Расширяющие и сужающие преобразования» на этой странице справки.</span><span class="sxs-lookup"><span data-stu-id="2f418-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `operatorsymbol`  
 <span data-ttu-id="2f418-122">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2f418-122">Required.</span></span> <span data-ttu-id="2f418-123">Символ или идентификатор оператора, который определяет Эта процедура оператора.</span><span class="sxs-lookup"><span data-stu-id="2f418-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>  
  
 `operand1`  
 <span data-ttu-id="2f418-124">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2f418-124">Required.</span></span> <span data-ttu-id="2f418-125">Имя и тип один операнд унарного оператора (включая оператор преобразования) или левого операнда бинарного оператора.</span><span class="sxs-lookup"><span data-stu-id="2f418-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>  
  
 `operand2`  
 <span data-ttu-id="2f418-126">Требуется для бинарных операторов.</span><span class="sxs-lookup"><span data-stu-id="2f418-126">Required for binary operators.</span></span> <span data-ttu-id="2f418-127">Имя и тип правого операнда бинарного оператора.</span><span class="sxs-lookup"><span data-stu-id="2f418-127">The name and type of the right operand of a binary operator.</span></span>  
  
 <span data-ttu-id="2f418-128">`operand1` и `operand2` имеет следующие синтаксис и составляющие:</span><span class="sxs-lookup"><span data-stu-id="2f418-128">`operand1` and `operand2` have the following syntax and parts:</span></span>  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|<span data-ttu-id="2f418-129">Отделение</span><span class="sxs-lookup"><span data-stu-id="2f418-129">Part</span></span>|<span data-ttu-id="2f418-130">Описание</span><span class="sxs-lookup"><span data-stu-id="2f418-130">Description</span></span>|  
|----------|-----------------|  
|`ByVal`|<span data-ttu-id="2f418-131">Необязательно, но механизм передачи должен быть [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="2f418-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|  
|`operandname`|<span data-ttu-id="2f418-132">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2f418-132">Required.</span></span> <span data-ttu-id="2f418-133">Имя переменной, представляющей этот операнд.</span><span class="sxs-lookup"><span data-stu-id="2f418-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="2f418-134">См. раздел [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="2f418-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`operandtype`|<span data-ttu-id="2f418-135">Необязательный Если `Option Strict` является `On`.</span><span class="sxs-lookup"><span data-stu-id="2f418-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="2f418-136">Тип данных этого операнда.</span><span class="sxs-lookup"><span data-stu-id="2f418-136">Data type of this operand.</span></span>|  
  
 `type`  
 <span data-ttu-id="2f418-137">Необязательный Если `Option Strict` является `On`.</span><span class="sxs-lookup"><span data-stu-id="2f418-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="2f418-138">Возвращает тип данных значения, которое процедура оператора.</span><span class="sxs-lookup"><span data-stu-id="2f418-138">Data type of the value the operator procedure returns.</span></span>  
  
 `statements`  
 <span data-ttu-id="2f418-139">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="2f418-139">Optional.</span></span> <span data-ttu-id="2f418-140">Блок операторов, процедура оператора.</span><span class="sxs-lookup"><span data-stu-id="2f418-140">Block of statements that the operator procedure runs.</span></span>  
  
 `returnvalue`  
 <span data-ttu-id="2f418-141">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2f418-141">Required.</span></span> <span data-ttu-id="2f418-142">Значение, которое процедура оператора возвращает в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="2f418-142">The value that the operator procedure returns to the calling code.</span></span>  
  
 <span data-ttu-id="2f418-143">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="2f418-143">`End` `Operator`</span></span>  
 <span data-ttu-id="2f418-144">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2f418-144">Required.</span></span> <span data-ttu-id="2f418-145">Завершает определение данной процедуры оператора.</span><span class="sxs-lookup"><span data-stu-id="2f418-145">Terminates the definition of this operator procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f418-146">Примечания</span><span class="sxs-lookup"><span data-stu-id="2f418-146">Remarks</span></span>  
 <span data-ttu-id="2f418-147">Можно использовать `Operator` только в классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="2f418-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="2f418-148">Это означает, что *контекст объявления* оператор не может быть исходный файл, пространство имен, модуля, интерфейса, процедуры или блока.</span><span class="sxs-lookup"><span data-stu-id="2f418-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="2f418-149">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2f418-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="2f418-150">Все операторы должны быть `Public Shared`.</span><span class="sxs-lookup"><span data-stu-id="2f418-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="2f418-151">Нельзя указать `ByRef`, `Optional`, или `ParamArray` для любой из операндов.</span><span class="sxs-lookup"><span data-stu-id="2f418-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>  
  
 <span data-ttu-id="2f418-152">Нельзя использовать символ оператора или идентификатор для хранения возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="2f418-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="2f418-153">Необходимо использовать `Return` инструкции и его необходимо указать значение.</span><span class="sxs-lookup"><span data-stu-id="2f418-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="2f418-154">Любое количество `Return` инструкций может находиться в любом в процедуре.</span><span class="sxs-lookup"><span data-stu-id="2f418-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>  
  
 <span data-ttu-id="2f418-155">Определение оператора таким образом называется *перегрузка операторов*, независимо от того, имеется ли вы использовать `Overloads` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="2f418-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="2f418-156">В приведенной ниже таблице перечислены операторы, которые можно определить.</span><span class="sxs-lookup"><span data-stu-id="2f418-156">The following table lists the operators you can define.</span></span>  
  
|<span data-ttu-id="2f418-157">Тип</span><span class="sxs-lookup"><span data-stu-id="2f418-157">Type</span></span>|<span data-ttu-id="2f418-158">Операторы</span><span class="sxs-lookup"><span data-stu-id="2f418-158">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="2f418-159">Унарный</span><span class="sxs-lookup"><span data-stu-id="2f418-159">Unary</span></span>|<span data-ttu-id="2f418-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="2f418-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="2f418-161">Binary</span><span class="sxs-lookup"><span data-stu-id="2f418-161">Binary</span></span>|<span data-ttu-id="2f418-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="2f418-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="2f418-163">Преобразование (унарный)</span><span class="sxs-lookup"><span data-stu-id="2f418-163">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="2f418-164">Обратите внимание, что `=` оператор в списке бинарных операторов является оператором сравнения, не оператором присваивания.</span><span class="sxs-lookup"><span data-stu-id="2f418-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="2f418-165">При определении `CType`, необходимо указать либо `Widening` или `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="2f418-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>  
  
## <a name="matched-pairs"></a><span data-ttu-id="2f418-166">Соответствующие пары</span><span class="sxs-lookup"><span data-stu-id="2f418-166">Matched Pairs</span></span>  
 <span data-ttu-id="2f418-167">Некоторые операторы необходимо определить как пары.</span><span class="sxs-lookup"><span data-stu-id="2f418-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="2f418-168">Если определен один оператор такой пары, необходимо определить другой.</span><span class="sxs-lookup"><span data-stu-id="2f418-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="2f418-169">Ниже перечислены соответствующие пары.</span><span class="sxs-lookup"><span data-stu-id="2f418-169">The matched pairs are the following:</span></span>  
  
- <span data-ttu-id="2f418-170">`=` и `<>`</span><span class="sxs-lookup"><span data-stu-id="2f418-170">`=` and `<>`</span></span>  
  
- <span data-ttu-id="2f418-171">`>` и `<`</span><span class="sxs-lookup"><span data-stu-id="2f418-171">`>` and `<`</span></span>  
  
- <span data-ttu-id="2f418-172">`>=` и `<=`</span><span class="sxs-lookup"><span data-stu-id="2f418-172">`>=` and `<=`</span></span>  
  
- <span data-ttu-id="2f418-173">`IsTrue` и `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="2f418-173">`IsTrue` and `IsFalse`</span></span>  
  
## <a name="data-type-restrictions"></a><span data-ttu-id="2f418-174">Ограничения типа данных</span><span class="sxs-lookup"><span data-stu-id="2f418-174">Data Type Restrictions</span></span>  
 <span data-ttu-id="2f418-175">Каждый оператор должен включать класса или структуры, на котором его определить.</span><span class="sxs-lookup"><span data-stu-id="2f418-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="2f418-176">Это означает, что класс или структура могут находиться только тип данных из следующих:</span><span class="sxs-lookup"><span data-stu-id="2f418-176">This means that the class or structure must appear as the data type of the following:</span></span>  
  
- <span data-ttu-id="2f418-177">Операнд унарного оператора.</span><span class="sxs-lookup"><span data-stu-id="2f418-177">The operand of a unary operator.</span></span>  
  
- <span data-ttu-id="2f418-178">По крайней мере один из операндов бинарного оператора.</span><span class="sxs-lookup"><span data-stu-id="2f418-178">At least one of the operands of a binary operator.</span></span>  
  
- <span data-ttu-id="2f418-179">Операнд или тип возвращаемого значения оператора преобразования.</span><span class="sxs-lookup"><span data-stu-id="2f418-179">Either the operand or the return type of a conversion operator.</span></span>  
  
 <span data-ttu-id="2f418-180">Некоторые операторы имеют дополнительные ограничения типа данных, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="2f418-180">Certain operators have additional data type restrictions, as follows:</span></span>  
  
- <span data-ttu-id="2f418-181">Если вы определяете `IsTrue` и `IsFalse` операторов, они должны возвращать `Boolean` типа.</span><span class="sxs-lookup"><span data-stu-id="2f418-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>  
  
- <span data-ttu-id="2f418-182">Если вы определяете `<<` и `>>` операторы, их необходимо указать `Integer` введите для `operandtype` из `operand2`.</span><span class="sxs-lookup"><span data-stu-id="2f418-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>  
  
 <span data-ttu-id="2f418-183">В соответствии с типом один из операндов имеет тип возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="2f418-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="2f418-184">Например, оператор сравнения, такие как `=` или `<>` может возвращать `Boolean` даже если оба операнда являются `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="2f418-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>  
  
## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="2f418-185">Логические и побитовые операторы</span><span class="sxs-lookup"><span data-stu-id="2f418-185">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="2f418-186">`And`, `Or`, `Not`, И `Xor` операторы могут выполнять операции либо логическая или Битовая операция в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2f418-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="2f418-187">Тем не менее если один из этих операторов определяется для класса или структуры, можно определить только его побитовую операцию.</span><span class="sxs-lookup"><span data-stu-id="2f418-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>  
  
 <span data-ttu-id="2f418-188">Не удается определить `AndAlso` оператор непосредственно с `Operator` инструкции.</span><span class="sxs-lookup"><span data-stu-id="2f418-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="2f418-189">Тем не менее, можно использовать `AndAlso` Если выполнены следующие условия:</span><span class="sxs-lookup"><span data-stu-id="2f418-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>  
  
- <span data-ttu-id="2f418-190">Вы определили `And` с теми же типами операнд, который вы хотите использовать для `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="2f418-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>  
  
- <span data-ttu-id="2f418-191">Определение `And` возвращает совпадает с типом класса или структуры, на котором оно было настроено.</span><span class="sxs-lookup"><span data-stu-id="2f418-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>  
  
- <span data-ttu-id="2f418-192">Вы определили `IsFalse` оператора для класса или структуры, на котором вы определили `And`.</span><span class="sxs-lookup"><span data-stu-id="2f418-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>  
  
 <span data-ttu-id="2f418-193">Аналогично, можно использовать `OrElse` Если вы определили `Or` на теми же операндами, определен с типом возвращаемого значения класса или структуры, и вы `IsTrue` для класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="2f418-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>  
  
## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="2f418-194">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="2f418-194">Widening and Narrowing Conversions</span></span>  
 <span data-ttu-id="2f418-195">Объект *расширяющее преобразование* всегда завершается успешно, во время выполнения, хотя *сужающее преобразование* может завершиться ошибкой во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="2f418-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="2f418-196">Для получения дополнительной информации см. [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="2f418-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="2f418-197">При объявлении процедуры преобразования `Widening`, ваш код процедуры не должны давать сбои.</span><span class="sxs-lookup"><span data-stu-id="2f418-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="2f418-198">Это означает следующее.</span><span class="sxs-lookup"><span data-stu-id="2f418-198">This means the following:</span></span>  
  
- <span data-ttu-id="2f418-199">Оно должно всегда возвращать допустимое значение типа `type`.</span><span class="sxs-lookup"><span data-stu-id="2f418-199">It must always return a valid value of type `type`.</span></span>  
  
- <span data-ttu-id="2f418-200">Он должен обрабатывать все возможные исключения и другие условия возникновения ошибок.</span><span class="sxs-lookup"><span data-stu-id="2f418-200">It must handle all possible exceptions and other error conditions.</span></span>  
  
- <span data-ttu-id="2f418-201">Он должен обрабатывать любую ошибку, возвращаемую из любой процедуры, которые она вызывает.</span><span class="sxs-lookup"><span data-stu-id="2f418-201">It must handle any error returns from any procedures it calls.</span></span>  
  
 <span data-ttu-id="2f418-202">Если есть вероятность того, что может произойти сбой процедуры преобразования, или что он может возникать необработанное исключение, необходимо объявить ее `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="2f418-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f418-203">Пример</span><span class="sxs-lookup"><span data-stu-id="2f418-203">Example</span></span>  
 <span data-ttu-id="2f418-204">В следующем примере кода используется `Operator` инструкции для определения контура структуры, которая включает в себя процедуры оператора `And`, `Or`, `IsFalse`, и `IsTrue` операторы.</span><span class="sxs-lookup"><span data-stu-id="2f418-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="2f418-205">`And` и `Or` каждого используются два операнда типа `abc` и типом возвращаемого значения `abc`.</span><span class="sxs-lookup"><span data-stu-id="2f418-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="2f418-206">`IsFalse` и `IsTrue` принимать одним операндом типа `abc` и возвращают `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="2f418-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="2f418-207">Эти определения позволяют вызывающий код для использования `And`, `AndAlso`, `Or`, и `OrElse` с операндами типа `abc`.</span><span class="sxs-lookup"><span data-stu-id="2f418-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>  
  
 [!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]  
  
## <a name="see-also"></a><span data-ttu-id="2f418-208">См. также</span><span class="sxs-lookup"><span data-stu-id="2f418-208">See also</span></span>

- [<span data-ttu-id="2f418-209">Оператор IsFalse</span><span class="sxs-lookup"><span data-stu-id="2f418-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="2f418-210">Оператор IsTrue</span><span class="sxs-lookup"><span data-stu-id="2f418-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="2f418-211">Расширение</span><span class="sxs-lookup"><span data-stu-id="2f418-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="2f418-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="2f418-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="2f418-213">Расширяющие и сужающие преобразования</span><span class="sxs-lookup"><span data-stu-id="2f418-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="2f418-214">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="2f418-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="2f418-215">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="2f418-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="2f418-216">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="2f418-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="2f418-217">Практическое руководство. Вызов процедуры оператора</span><span class="sxs-lookup"><span data-stu-id="2f418-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="2f418-218">Практическое руководство. Используйте класс, в котором определяются операторы</span><span class="sxs-lookup"><span data-stu-id="2f418-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
