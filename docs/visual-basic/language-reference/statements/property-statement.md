---
title: Property Statement (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 7b2d388cbcd1995178adf4102520ecaa1c9b1889
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814194"
---
# <a name="property-statement"></a><span data-ttu-id="920c4-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="920c4-102">Property Statement</span></span>
<span data-ttu-id="920c4-103">Объявляет имя свойства и процедуры свойства, используемые для хранения и извлечения значения свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="920c4-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="920c4-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="920c4-105">Части</span><span class="sxs-lookup"><span data-stu-id="920c4-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="920c4-106">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-106">Optional.</span></span> <span data-ttu-id="920c4-107">Список атрибутов, применяемых к этому свойству или `Get` или `Set` процедуры.</span><span class="sxs-lookup"><span data-stu-id="920c4-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="920c4-108">См. в разделе [список атрибутов](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="920c4-109">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-109">Optional.</span></span> <span data-ttu-id="920c4-110">Указывает, что это свойство является свойством по умолчанию для класса или структуры, в котором она определена.</span><span class="sxs-lookup"><span data-stu-id="920c4-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="920c4-111">Свойства по умолчанию, должен принимать параметры и их можно задавать и получать без указания имени свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="920c4-112">При объявлении свойства в виде `Default`, нельзя использовать `Private` в свойстве или любой из его процедур.</span><span class="sxs-lookup"><span data-stu-id="920c4-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="920c4-113">Необязательно. на `Property` инструкции и на более одного `Get` и `Set` инструкций.</span><span class="sxs-lookup"><span data-stu-id="920c4-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="920c4-114">Ниже указаны доступные значения.</span><span class="sxs-lookup"><span data-stu-id="920c4-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="920c4-115">Public</span><span class="sxs-lookup"><span data-stu-id="920c4-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="920c4-116">Protected</span><span class="sxs-lookup"><span data-stu-id="920c4-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="920c4-117">Friend</span><span class="sxs-lookup"><span data-stu-id="920c4-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="920c4-118">Закрытые</span><span class="sxs-lookup"><span data-stu-id="920c4-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="920c4-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="920c4-119">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md) 

    - [<span data-ttu-id="920c4-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="920c4-120">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="920c4-121">См. раздел [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-121">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="920c4-122">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-122">Optional.</span></span> <span data-ttu-id="920c4-123">Ниже указаны доступные значения.</span><span class="sxs-lookup"><span data-stu-id="920c4-123">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="920c4-124">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="920c4-124">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="920c4-125">Переопределения</span><span class="sxs-lookup"><span data-stu-id="920c4-125">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="920c4-126">Переопределяемые</span><span class="sxs-lookup"><span data-stu-id="920c4-126">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="920c4-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="920c4-127">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="920c4-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="920c4-128">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="920c4-129">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-129">Optional.</span></span> <span data-ttu-id="920c4-130">См. в разделе [общих](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-130">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="920c4-131">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-131">Optional.</span></span> <span data-ttu-id="920c4-132">См. в разделе [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-132">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="920c4-133">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-133">Optional.</span></span> <span data-ttu-id="920c4-134">См. в разделе [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-134">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="920c4-135">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-135">Optional.</span></span> <span data-ttu-id="920c4-136">См. в разделе [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-136">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="920c4-137">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-137">Optional.</span></span> <span data-ttu-id="920c4-138">См. в разделе [итератор](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-138">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="920c4-139">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="920c4-139">Required.</span></span> <span data-ttu-id="920c4-140">Имя свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-140">Name of the property.</span></span> <span data-ttu-id="920c4-141">См. раздел [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-141">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="920c4-142">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-142">Optional.</span></span> <span data-ttu-id="920c4-143">Список имена локальных переменных, представляющих параметры этого свойства и возможные дополнительные параметры `Set` процедуры.</span><span class="sxs-lookup"><span data-stu-id="920c4-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="920c4-144">См. в разделе [список параметров](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-144">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="920c4-145">Обязателен, если `Option Strict` является `On`.</span><span class="sxs-lookup"><span data-stu-id="920c4-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="920c4-146">Тип данных значения, возвращаемого этим свойством.</span><span class="sxs-lookup"><span data-stu-id="920c4-146">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="920c4-147">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-147">Optional.</span></span> <span data-ttu-id="920c4-148">Указывает, что это свойство реализует один или несколько свойств, каждая из которых определена в интерфейс, реализуемый этого свойства классом или структурой.</span><span class="sxs-lookup"><span data-stu-id="920c4-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="920c4-149">См. в разделе [реализует оператор](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-149">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="920c4-150">Является обязательным, если предоставлен параметр `Implements`.</span><span class="sxs-lookup"><span data-stu-id="920c4-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="920c4-151">Список реализуемых свойств.</span><span class="sxs-lookup"><span data-stu-id="920c4-151">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="920c4-152">Каждый элемент `implementedproperty` имеет перечисленные ниже синтаксис и компоненты.</span><span class="sxs-lookup"><span data-stu-id="920c4-152">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="920c4-153">Отделение</span><span class="sxs-lookup"><span data-stu-id="920c4-153">Part</span></span>|<span data-ttu-id="920c4-154">Описание</span><span class="sxs-lookup"><span data-stu-id="920c4-154">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="920c4-155">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="920c4-155">Required.</span></span> <span data-ttu-id="920c4-156">Имя интерфейса, реализуемого этим свойством, содержащей, класс или структура.</span><span class="sxs-lookup"><span data-stu-id="920c4-156">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="920c4-157">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="920c4-157">Required.</span></span> <span data-ttu-id="920c4-158">Имя, по которому это свойство определено в `interface`.</span><span class="sxs-lookup"><span data-stu-id="920c4-158">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="920c4-159">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-159">Optional.</span></span> <span data-ttu-id="920c4-160">Требуется, если свойство помечено `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="920c4-160">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="920c4-161">Запускает `Get` свойство процедуру, которая используется для возврата значения свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="920c4-162">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-162">Optional.</span></span> <span data-ttu-id="920c4-163">Блок операторов для выполнения в рамках `Get` или `Set` процедуры.</span><span class="sxs-lookup"><span data-stu-id="920c4-163">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="920c4-164">Завершает `Get` процедуры свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-164">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="920c4-165">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="920c4-165">Optional.</span></span> <span data-ttu-id="920c4-166">Требуется, если свойство помечено `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="920c4-166">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="920c4-167">Запускает `Set` свойство процедуру, которая используется для хранения значения свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-167">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="920c4-168">Завершает `Set` процедуры свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-168">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="920c4-169">Завершает определение этого свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-169">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="920c4-170">Примечания</span><span class="sxs-lookup"><span data-stu-id="920c4-170">Remarks</span></span>  
 <span data-ttu-id="920c4-171">`Property` Инструкция содержит объявление свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-171">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="920c4-172">Свойство может иметь `Get` процедура (только для чтения), `Set` процедура (только запись) или оба (чтение и запись).</span><span class="sxs-lookup"><span data-stu-id="920c4-172">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="920c4-173">Можно опустить `Get` и `Set` процедуры при использовании автоматически реализуемого свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-173">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="920c4-174">Дополнительные сведения см. в разделе [Автоматически реализуемые свойства](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-174">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="920c4-175">Можно использовать `Property` только на уровне класса.</span><span class="sxs-lookup"><span data-stu-id="920c4-175">You can use `Property` only at class level.</span></span> <span data-ttu-id="920c4-176">Это означает, что *контекст объявления* свойства должен быть класс, структура, модуль или интерфейс, и не может быть исходный файл, пространство имен, процедуры или блока.</span><span class="sxs-lookup"><span data-stu-id="920c4-176">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="920c4-177">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="920c4-177">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="920c4-178">По умолчанию свойства используют общий доступ.</span><span class="sxs-lookup"><span data-stu-id="920c4-178">By default, properties use public access.</span></span> <span data-ttu-id="920c4-179">Можно настроить уровень доступа свойства с модификатором доступа на `Property` инструкции и при необходимости можно определить один из его процедур более строгий уровень доступа.</span><span class="sxs-lookup"><span data-stu-id="920c4-179">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="920c4-180">Visual Basic передает параметр `Set` процедуры во время назначения свойств.</span><span class="sxs-lookup"><span data-stu-id="920c4-180">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="920c4-181">Если не указать параметр для `Set`, интегрированную среду разработки (IDE) использует неявный параметр с именем `value`.</span><span class="sxs-lookup"><span data-stu-id="920c4-181">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="920c4-182">Этот параметр содержит значение, присваиваемое свойству.</span><span class="sxs-lookup"><span data-stu-id="920c4-182">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="920c4-183">Обычно вы сохраните это значение в закрытую локальную переменную и вернуть его каждый раз, когда `Get` при вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="920c4-183">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="920c4-184">Правила</span><span class="sxs-lookup"><span data-stu-id="920c4-184">Rules</span></span>  
  
-   <span data-ttu-id="920c4-185">**Смешанным уровнем доступа.**</span><span class="sxs-lookup"><span data-stu-id="920c4-185">**Mixed Access Levels.**</span></span> <span data-ttu-id="920c4-186">При определении свойства чтения и записи, при необходимости можно указать другой уровень доступа для любого `Get` или `Set` процедуры, но не оба.</span><span class="sxs-lookup"><span data-stu-id="920c4-186">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="920c4-187">После этого, уровень доступа процедуры должен быть более ограничивающим, чем уровень доступа свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-187">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="920c4-188">Например, если свойство объявлено `Friend`, можно объявить `Set` процедуры `Private`, но не `Public`.</span><span class="sxs-lookup"><span data-stu-id="920c4-188">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="920c4-189">При определении `ReadOnly` или `WriteOnly` свойство, одна процедура (`Get` или `Set`, соответственно) представляет все свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-189">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="920c4-190">Нельзя объявлять другой уровень доступа для таких процедур, так как это установит два уровня доступа для свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-190">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="920c4-191">**Тип возвращаемого значения.**</span><span class="sxs-lookup"><span data-stu-id="920c4-191">**Return Type.**</span></span> <span data-ttu-id="920c4-192">`Property` Инструкции можно объявить тип данных значения, он возвращает.</span><span class="sxs-lookup"><span data-stu-id="920c4-192">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="920c4-193">Можно указать любой тип данных или имя перечисления, структуры, класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="920c4-193">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="920c4-194">Если вы не укажете `returntype`, это свойство возвращает `Object`.</span><span class="sxs-lookup"><span data-stu-id="920c4-194">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="920c4-195">**Реализация.**</span><span class="sxs-lookup"><span data-stu-id="920c4-195">**Implementation.**</span></span> <span data-ttu-id="920c4-196">Если это свойство использует `Implements` должен иметь ключевое слово, содержащим классом или структурой `Implements` оператору сразу же после его `Class` или `Structure` инструкции.</span><span class="sxs-lookup"><span data-stu-id="920c4-196">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="920c4-197">`Implements` Инструкция должна включать каждого интерфейса, указанного в `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="920c4-197">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="920c4-198">Тем не менее имя, по которому определяется интерфейс `Property` (в `definedname`) не обязательно совпадает с именем этого свойства (в `name`).</span><span class="sxs-lookup"><span data-stu-id="920c4-198">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="920c4-199">Поведение</span><span class="sxs-lookup"><span data-stu-id="920c4-199">Behavior</span></span>  
  
-   <span data-ttu-id="920c4-200">**Возвращение из процедуры свойства.**</span><span class="sxs-lookup"><span data-stu-id="920c4-200">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="920c4-201">Когда `Get` или `Set` процедура возвращает в вызывающий код, выполнение продолжается с оператора, следующего инструкции, вызвавшей его.</span><span class="sxs-lookup"><span data-stu-id="920c4-201">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="920c4-202">`Exit Property` И `Return` инструкции вызывают Немедленный выход из процедуры свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-202">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="920c4-203">Любое количество `Exit Property` и `Return` инструкций может находиться в любом в процедуре, и вы можете комбинировать `Exit Property` и `Return` инструкций.</span><span class="sxs-lookup"><span data-stu-id="920c4-203">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="920c4-204">**Возвращаемое значение.**</span><span class="sxs-lookup"><span data-stu-id="920c4-204">**Return Value.**</span></span> <span data-ttu-id="920c4-205">Для возвращения значения из `Get` процедуры, можно присвоить значение имени свойства или включить ее в `Return` инструкции.</span><span class="sxs-lookup"><span data-stu-id="920c4-205">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="920c4-206">В следующем примере присваивается значение имени свойства `quoteForTheDay` , а затем использует `Exit Property` инструкция возвращает.</span><span class="sxs-lookup"><span data-stu-id="920c4-206">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     <span data-ttu-id="920c4-207">Если вы используете `Exit Property` без присвоения значения `name`, `Get` процедура возвращает значение по умолчанию для типа данных свойства.</span><span class="sxs-lookup"><span data-stu-id="920c4-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="920c4-208">`Return` Оператор, в то же время назначает `Get` процедура возвращать значение и завершает процедуру.</span><span class="sxs-lookup"><span data-stu-id="920c4-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="920c4-209">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="920c4-209">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="920c4-210">Пример</span><span class="sxs-lookup"><span data-stu-id="920c4-210">Example</span></span>  
 <span data-ttu-id="920c4-211">В следующем примере объявляется свойство в классе.</span><span class="sxs-lookup"><span data-stu-id="920c4-211">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]  
  
## <a name="see-also"></a><span data-ttu-id="920c4-212">См. также</span><span class="sxs-lookup"><span data-stu-id="920c4-212">See also</span></span>

- [<span data-ttu-id="920c4-213">Автоматически реализуемые свойства</span><span class="sxs-lookup"><span data-stu-id="920c4-213">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="920c4-214">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="920c4-214">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="920c4-215">Оператор Get</span><span class="sxs-lookup"><span data-stu-id="920c4-215">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="920c4-216">Оператор Set</span><span class="sxs-lookup"><span data-stu-id="920c4-216">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="920c4-217">Список параметров</span><span class="sxs-lookup"><span data-stu-id="920c4-217">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="920c4-218">Default</span><span class="sxs-lookup"><span data-stu-id="920c4-218">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
