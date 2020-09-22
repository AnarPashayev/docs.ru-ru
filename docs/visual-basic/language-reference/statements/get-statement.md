---
title: Оператор Get
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 3da6c099b3f43a144484eaddf58605609eb0bbfe
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866207"
---
# <a name="get-statement"></a><span data-ttu-id="4834e-102">Оператор Get</span><span class="sxs-lookup"><span data-stu-id="4834e-102">Get Statement</span></span>

<span data-ttu-id="4834e-103">Объявляет `Get` процедуру свойства, используемую для получения значения свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4834e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4834e-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="4834e-105">Компоненты</span><span class="sxs-lookup"><span data-stu-id="4834e-105">Parts</span></span>  
  
|<span data-ttu-id="4834e-106">Термин</span><span class="sxs-lookup"><span data-stu-id="4834e-106">Term</span></span>|<span data-ttu-id="4834e-107">Определение</span><span class="sxs-lookup"><span data-stu-id="4834e-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="4834e-108">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4834e-108">Optional.</span></span> <span data-ttu-id="4834e-109">См. [список атрибутов](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="4834e-109">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="4834e-110">Необязательно для одного из `Get` `Set` операторов и в этом свойстве.</span><span class="sxs-lookup"><span data-stu-id="4834e-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="4834e-111">Может применяться один из перечисленных ниже типов.</span><span class="sxs-lookup"><span data-stu-id="4834e-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="4834e-112">-   [От](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="4834e-112">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="4834e-113">-   [Объявление](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="4834e-113">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="4834e-114">-   [Личному](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="4834e-114">-   [Private](../modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="4834e-115">См. раздел [уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4834e-115">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="4834e-116">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4834e-116">Optional.</span></span> <span data-ttu-id="4834e-117">Одна или несколько инструкций, выполняемых при `Get` вызове процедуры свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="4834e-118">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4834e-118">Required.</span></span> <span data-ttu-id="4834e-119">Завершает определение `Get` процедуры свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4834e-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="4834e-120">Remarks</span></span>  

 <span data-ttu-id="4834e-121">Каждое свойство должно иметь `Get` процедуру свойства, если только свойство не помечено как `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="4834e-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="4834e-122">`Get`Процедура используется для возврата текущего значения свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="4834e-123">Visual Basic автоматически вызывает процедуру свойства, `Get` когда выражение запрашивает значение свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="4834e-124">Текст объявления свойства может содержать только `Get` процедуры свойства и `Set` между [оператором Property](property-statement.md) и `End Property` оператором.</span><span class="sxs-lookup"><span data-stu-id="4834e-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="4834e-125">Он не может хранить ничего, Кроме этих процедур.</span><span class="sxs-lookup"><span data-stu-id="4834e-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="4834e-126">В частности, он не может хранить текущее значение свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="4834e-127">Это значение необходимо хранить за пределами свойства, так как при хранении в любой из процедур свойств другая процедура свойства не может получить к ней доступ.</span><span class="sxs-lookup"><span data-stu-id="4834e-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="4834e-128">Обычным подходом является сохранение значения в [закрытой](../modifiers/private.md) переменной, объявленной на том же уровне, что и свойство.</span><span class="sxs-lookup"><span data-stu-id="4834e-128">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="4834e-129">Необходимо определить `Get` процедуру внутри свойства, к которому она применяется.</span><span class="sxs-lookup"><span data-stu-id="4834e-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="4834e-130">`Get`Процедура по умолчанию имеет уровень доступа содержащего его свойства, если только не используется `accessmodifier` в `Get` инструкции.</span><span class="sxs-lookup"><span data-stu-id="4834e-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4834e-131">Правила</span><span class="sxs-lookup"><span data-stu-id="4834e-131">Rules</span></span>  
  
- <span data-ttu-id="4834e-132">**Уровни смешанного доступа.**</span><span class="sxs-lookup"><span data-stu-id="4834e-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="4834e-133">При определении свойства для чтения и записи можно дополнительно указать другой уровень доступа для `Get` `Set` процедуры или, но не для обоих.</span><span class="sxs-lookup"><span data-stu-id="4834e-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="4834e-134">В этом случае уровень доступа процедуры должен быть более четким, чем уровень доступа свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="4834e-135">Например, если свойство объявлено `Friend` , можно объявить `Get` процедуру `Private` , но не `Public` .</span><span class="sxs-lookup"><span data-stu-id="4834e-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="4834e-136">При определении `ReadOnly` свойства `Get` процедура представляет все свойство.</span><span class="sxs-lookup"><span data-stu-id="4834e-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="4834e-137">Нельзя объявить другой уровень доступа для `Get` , так как для свойства будет задано два уровня доступа.</span><span class="sxs-lookup"><span data-stu-id="4834e-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="4834e-138">**Тип возвращаемого значения.**</span><span class="sxs-lookup"><span data-stu-id="4834e-138">**Return Type.**</span></span> <span data-ttu-id="4834e-139">[Оператор Property](property-statement.md) может объявлять тип данных возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="4834e-139">The [Property Statement](property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="4834e-140">`Get`Процедура автоматически возвращает этот тип данных.</span><span class="sxs-lookup"><span data-stu-id="4834e-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="4834e-141">Можно указать любой тип данных или имя перечисления, структуры, класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="4834e-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="4834e-142">Если `Property` инструкция не указывает `returntype` , процедура возвращает `Object` .</span><span class="sxs-lookup"><span data-stu-id="4834e-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="4834e-143">Поведение</span><span class="sxs-lookup"><span data-stu-id="4834e-143">Behavior</span></span>  
  
- <span data-ttu-id="4834e-144">**Возврат из процедуры.**</span><span class="sxs-lookup"><span data-stu-id="4834e-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="4834e-145">Когда `Get` процедура возвращается в вызывающий код, выполнение продолжится в операторе, который запросил значение свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="4834e-146">`Get` процедуры свойств могут возвращать значение с помощью [оператора return](return-statement.md) или путем назначения возвращаемого значения имени свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-146">`Get` property procedures can return a value using either the [Return Statement](return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="4834e-147">Дополнительные сведения см. в разделе "возвращаемое значение" в [операторе Function](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4834e-147">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="4834e-148">`Exit Property`Операторы и `Return` вызывают немедленный выход из процедуры свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="4834e-149">Любое количество `Exit Property` инструкций и `Return` может использоваться в любом месте процедуры, и можно смешивать `Exit Property` `Return` операторы и.</span><span class="sxs-lookup"><span data-stu-id="4834e-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="4834e-150">**Возвращаемое значение.**</span><span class="sxs-lookup"><span data-stu-id="4834e-150">**Return Value.**</span></span> <span data-ttu-id="4834e-151">Чтобы вернуть значение из `Get` процедуры, можно либо присвоить значение имени свойства, либо включить его в [оператор return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4834e-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](return-statement.md).</span></span> <span data-ttu-id="4834e-152">`Return`Инструкция одновременно присваивает `Get` возвращаемое значение процедуры и завершает процедуру.</span><span class="sxs-lookup"><span data-stu-id="4834e-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="4834e-153">Если вы используете `Exit Property` без присвоения значения имени свойства, `Get` процедура возвращает значение по умолчанию для типа данных свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="4834e-154">Дополнительные сведения см. в разделе "возвращаемое значение" в [операторе Function](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4834e-154">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="4834e-155">В следующем примере показаны два способа, которыми свойство только для чтения `quoteForTheDay` может возвращать значение, удерживаемое в закрытой переменной `quoteValue` .</span><span class="sxs-lookup"><span data-stu-id="4834e-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="4834e-156">Пример</span><span class="sxs-lookup"><span data-stu-id="4834e-156">Example</span></span>  

 <span data-ttu-id="4834e-157">В следующем примере оператор используется `Get` для возврата значения свойства.</span><span class="sxs-lookup"><span data-stu-id="4834e-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="4834e-158">См. также</span><span class="sxs-lookup"><span data-stu-id="4834e-158">See also</span></span>

- [<span data-ttu-id="4834e-159">Инструкция SET</span><span class="sxs-lookup"><span data-stu-id="4834e-159">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="4834e-160">Property Statement</span><span class="sxs-lookup"><span data-stu-id="4834e-160">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="4834e-161">Оператор Exit</span><span class="sxs-lookup"><span data-stu-id="4834e-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="4834e-162">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="4834e-162">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="4834e-163">Пошаговое руководство. Определение классов</span><span class="sxs-lookup"><span data-stu-id="4834e-163">Walkthrough: Defining Classes</span></span>](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
