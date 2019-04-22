---
title: Оператор Sub (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: ab94865f4881b40b38f67eb40d2f9fa2e1982af8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817231"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="386ef-102">Оператор Sub (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="386ef-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="386ef-103">Объявляет имя, параметры и код, которые определяют `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="386ef-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="386ef-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="386ef-105">Части</span><span class="sxs-lookup"><span data-stu-id="386ef-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="386ef-106">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-106">Optional.</span></span> <span data-ttu-id="386ef-107">См. в разделе [список атрибутов](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="386ef-108">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-108">Optional.</span></span> <span data-ttu-id="386ef-109">Указывает определение разделяемого метода.</span><span class="sxs-lookup"><span data-stu-id="386ef-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="386ef-110">См. в разделе [разделяемые методы](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="386ef-111">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-111">Optional.</span></span> <span data-ttu-id="386ef-112">Ниже указаны доступные значения.</span><span class="sxs-lookup"><span data-stu-id="386ef-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="386ef-113">Public</span><span class="sxs-lookup"><span data-stu-id="386ef-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="386ef-114">Protected</span><span class="sxs-lookup"><span data-stu-id="386ef-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="386ef-115">Friend</span><span class="sxs-lookup"><span data-stu-id="386ef-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="386ef-116">Закрытые</span><span class="sxs-lookup"><span data-stu-id="386ef-116">Private</span></span>](../modifiers/private.md)  
  
    - [<span data-ttu-id="386ef-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="386ef-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="386ef-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="386ef-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="386ef-119">См. раздел [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="386ef-120">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-120">Optional.</span></span> <span data-ttu-id="386ef-121">Ниже указаны доступные значения.</span><span class="sxs-lookup"><span data-stu-id="386ef-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="386ef-122">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="386ef-122">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="386ef-123">Переопределения</span><span class="sxs-lookup"><span data-stu-id="386ef-123">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="386ef-124">Переопределяемые</span><span class="sxs-lookup"><span data-stu-id="386ef-124">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="386ef-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="386ef-125">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="386ef-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="386ef-126">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="386ef-127">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-127">Optional.</span></span> <span data-ttu-id="386ef-128">См. в разделе [общих](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-128">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="386ef-129">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-129">Optional.</span></span> <span data-ttu-id="386ef-130">См. в разделе [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-130">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="386ef-131">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-131">Optional.</span></span> <span data-ttu-id="386ef-132">См. в разделе [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-132">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="386ef-133">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="386ef-133">Required.</span></span> <span data-ttu-id="386ef-134">Имя процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-134">Name of the procedure.</span></span> <span data-ttu-id="386ef-135">См. раздел [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="386ef-136">Чтобы создать процедуру конструктора для класса, задайте имя `Sub` процедура `New` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="386ef-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="386ef-137">Дополнительные сведения см. в разделе [время жизни объекта: Как создаются и удаляются объекты](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="386ef-138">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-138">Optional.</span></span> <span data-ttu-id="386ef-139">Список параметров типа для универсальной процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="386ef-140">См. в разделе [введите список](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-140">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="386ef-141">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-141">Optional.</span></span> <span data-ttu-id="386ef-142">Список имен локальных переменных, представляющих параметры этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="386ef-143">См. в разделе [список параметров](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-143">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="386ef-144">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-144">Optional.</span></span> <span data-ttu-id="386ef-145">Указывает, что эта процедура реализует один или несколько `Sub` процедуры, каждая из которых определена в интерфейс, реализуемый этой процедуры классом или структурой.</span><span class="sxs-lookup"><span data-stu-id="386ef-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="386ef-146">См. в разделе [реализует оператор](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-146">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="386ef-147">Является обязательным, если предоставлен параметр `Implements`.</span><span class="sxs-lookup"><span data-stu-id="386ef-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="386ef-148">Список реализуемых процедур `Sub`.</span><span class="sxs-lookup"><span data-stu-id="386ef-148">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="386ef-149">Каждый элемент `implementedprocedure` имеет перечисленные ниже синтаксис и компоненты.</span><span class="sxs-lookup"><span data-stu-id="386ef-149">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="386ef-150">Отделение</span><span class="sxs-lookup"><span data-stu-id="386ef-150">Part</span></span>|<span data-ttu-id="386ef-151">Описание</span><span class="sxs-lookup"><span data-stu-id="386ef-151">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="386ef-152">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="386ef-152">Required.</span></span> <span data-ttu-id="386ef-153">Имя интерфейса, реализуемого этой процедуры содержащей класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="386ef-154">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="386ef-154">Required.</span></span> <span data-ttu-id="386ef-155">Имя, под которым процедура определена в `interface`.</span><span class="sxs-lookup"><span data-stu-id="386ef-155">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="386ef-156">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-156">Optional.</span></span> <span data-ttu-id="386ef-157">Указывает, что эта процедура может обрабатывать один или несколько определенных событий.</span><span class="sxs-lookup"><span data-stu-id="386ef-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="386ef-158">См. в разделе [обрабатывает](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-158">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="386ef-159">Является обязательным, если предоставлен параметр `Handles`.</span><span class="sxs-lookup"><span data-stu-id="386ef-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="386ef-160">Список событий, которые обрабатывает эту процедуру.</span><span class="sxs-lookup"><span data-stu-id="386ef-160">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="386ef-161">Каждый элемент `eventspecifier` имеет перечисленные ниже синтаксис и компоненты.</span><span class="sxs-lookup"><span data-stu-id="386ef-161">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="386ef-162">Отделение</span><span class="sxs-lookup"><span data-stu-id="386ef-162">Part</span></span>|<span data-ttu-id="386ef-163">Описание</span><span class="sxs-lookup"><span data-stu-id="386ef-163">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="386ef-164">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="386ef-164">Required.</span></span> <span data-ttu-id="386ef-165">Объектной переменной, объявленной с типом данных класса или структуры, который вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="386ef-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="386ef-166">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="386ef-166">Required.</span></span> <span data-ttu-id="386ef-167">Имя события, которое обрабатывает эту процедуру.</span><span class="sxs-lookup"><span data-stu-id="386ef-167">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="386ef-168">Необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="386ef-168">Optional.</span></span> <span data-ttu-id="386ef-169">Блок операторов для выполнения в рамках этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-169">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="386ef-170">Завершает определение этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-170">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="386ef-171">Примечания</span><span class="sxs-lookup"><span data-stu-id="386ef-171">Remarks</span></span>  
 <span data-ttu-id="386ef-172">Весь исполняемый код должен быть внутри процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="386ef-173">Используйте `Sub` процедуре, если не требуется возвращать значение вызывающему коду.</span><span class="sxs-lookup"><span data-stu-id="386ef-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="386ef-174">Используйте `Function` процедуре, если необходимо вернуть значение.</span><span class="sxs-lookup"><span data-stu-id="386ef-174">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="386ef-175">Определение процедуры Sub</span><span class="sxs-lookup"><span data-stu-id="386ef-175">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="386ef-176">Вы можете определить `Sub` процедуры только на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="386ef-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="386ef-177">Контекст объявления для процедуры sub таким образом, должен быть класс, структура, модуль или интерфейс и не может быть исходным файлом, пространство имен, процедура или блок.</span><span class="sxs-lookup"><span data-stu-id="386ef-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="386ef-178">Дополнительные сведения см. в разделе [Контексты объявления и уровни доступа по умолчанию](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="386ef-179">`Sub` процедуры по умолчанию для общего доступа.</span><span class="sxs-lookup"><span data-stu-id="386ef-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="386ef-180">Уровни доступа можно настроить с помощью модификаторов доступа.</span><span class="sxs-lookup"><span data-stu-id="386ef-180">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="386ef-181">Если в процедуре используется `Implements` должен иметь ключевое слово, содержащим классом или структурой `Implements` оператор, который следует сразу за его `Class` или `Structure` инструкции.</span><span class="sxs-lookup"><span data-stu-id="386ef-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="386ef-182">`Implements` Инструкция должна включать каждого интерфейса, который указан в `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="386ef-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="386ef-183">Тем не менее имя, по которому определяется интерфейс `Sub` (в `definedname`) не должен совпадать с именем этой процедуры (в `name`).</span><span class="sxs-lookup"><span data-stu-id="386ef-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="386ef-184">Возвращение из процедуры Sub</span><span class="sxs-lookup"><span data-stu-id="386ef-184">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="386ef-185">Когда `Sub` процедура возвращает в вызывающий код, выполнение продолжается с оператора после оператора, который вызвал ее.</span><span class="sxs-lookup"><span data-stu-id="386ef-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="386ef-186">В следующем примере показано отклик на `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-186">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="386ef-187">`Exit Sub` И `Return` инструкции вызывают Немедленный выход из `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="386ef-188">Любое количество `Exit Sub` и `Return` инструкций может находиться в любом в процедуре, и вы можете комбинировать `Exit Sub` и `Return` инструкций.</span><span class="sxs-lookup"><span data-stu-id="386ef-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="386ef-189">Вызов процедуры Sub</span><span class="sxs-lookup"><span data-stu-id="386ef-189">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="386ef-190">Вы вызываете `Sub` процедуры с помощью имени процедуры в инструкции и затем согласно это имя с помощью списка своих аргументов в скобках.</span><span class="sxs-lookup"><span data-stu-id="386ef-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="386ef-191">Скобки могут опускаться только в том случае, если не предоставляет никакие аргументы.</span><span class="sxs-lookup"><span data-stu-id="386ef-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="386ef-192">Тем не менее код является более удобочитаемым, если всегда использовать круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="386ef-192">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="386ef-193">Объект `Sub` процедуры и `Function` процедуры могут иметь параметры и выполнять последовательность операторов.</span><span class="sxs-lookup"><span data-stu-id="386ef-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="386ef-194">Тем не менее `Function` процедура возвращает значение, а также `Sub` не процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="386ef-195">Следовательно, нельзя использовать `Sub` процедуры в выражении.</span><span class="sxs-lookup"><span data-stu-id="386ef-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="386ef-196">Можно использовать `Call` ключевое слово при вызове `Sub` процедура, но его не рекомендуется для большинства случаев.</span><span class="sxs-lookup"><span data-stu-id="386ef-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="386ef-197">Дополнительные сведения см. в разделе [инструкции Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-197">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="386ef-198">Visual Basic иногда упорядочение арифметические выражения для повышения эффективности внутренней.</span><span class="sxs-lookup"><span data-stu-id="386ef-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="386ef-199">По этой причине, если список аргументов включает выражения, которые вызывают другие процедуры, нет оснований предполагать, что эти выражения будут вызываться в определенном порядке.</span><span class="sxs-lookup"><span data-stu-id="386ef-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="386ef-200">Async Sub-процедуры</span><span class="sxs-lookup"><span data-stu-id="386ef-200">Async Sub Procedures</span></span>  
 <span data-ttu-id="386ef-201">С помощью функции Async можно вызывать асинхронные функции без использованию явных обратных вызовов или ручному разделению кода между несколькими функции или лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="386ef-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="386ef-202">Если пометить процедуры с [Async](../modifiers/async.md) модификатор, можно использовать [Await](../../../visual-basic/language-reference/operators/await-operator.md) оператор в процедуре.</span><span class="sxs-lookup"><span data-stu-id="386ef-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="386ef-203">Когда управление достигает `Await` выражение в `Async` процедуры, управление возвращается вызывающему объекту и выполнение в процедуре приостанавливается до завершения выполнения ожидающей задачи.</span><span class="sxs-lookup"><span data-stu-id="386ef-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="386ef-204">После завершения задачи можно возобновить выполнение в процедуре.</span><span class="sxs-lookup"><span data-stu-id="386ef-204">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="386ef-205">`Async` Процедура возвращает вызывающий объект при обнаружении либо первый ожидаемый объект, который еще не завершено или в конце `Async` процедуры будет достигнут, что произойдет раньше.</span><span class="sxs-lookup"><span data-stu-id="386ef-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="386ef-206">Можно также пометить [инструкции Function](function-statement.md) с `Async` модификатор.</span><span class="sxs-lookup"><span data-stu-id="386ef-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="386ef-207">`Async` Функция может иметь тип возвращаемого значения <xref:System.Threading.Tasks.Task%601> или <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="386ef-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="386ef-208">Пример далее в этом разделе показано, `Async` функции с типом возвращаемого значения <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="386ef-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="386ef-209">`Async` `Sub` процедуры в основном используются для обработчиков событий, в которой не может быть возвращено значение.</span><span class="sxs-lookup"><span data-stu-id="386ef-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="386ef-210">`Async` `Sub` Процедуру нельзя ожидать и вызывающий `Async` `Sub` процедура не может перехватывать исключения, `Sub` процедура вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="386ef-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="386ef-211">`Async` Процедура не может объявлять [ByRef](../modifiers/byref.md) параметров.</span><span class="sxs-lookup"><span data-stu-id="386ef-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="386ef-212">Дополнительные сведения о `Async` процедуры, см. в разделе [асинхронное программирование с использованием Async и Await](../../../visual-basic/programming-guide/concepts/async/index.md), [поток управления в асинхронных программах](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), и [асинхронные типы возвращаемых значений](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="386ef-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="386ef-213">Пример</span><span class="sxs-lookup"><span data-stu-id="386ef-213">Example</span></span>  
 <span data-ttu-id="386ef-214">В следующем примере используется `Sub` инструкции для определения имени, параметров и кода, образующих текст `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="386ef-215">Пример</span><span class="sxs-lookup"><span data-stu-id="386ef-215">Example</span></span>  
 <span data-ttu-id="386ef-216">В следующем примере `DelayAsync` — `Async` `Function` с типом возвращаемого значения <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="386ef-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="386ef-217">`DelayAsync` имеет инструкцию `Return` , которая возвращает целое число.</span><span class="sxs-lookup"><span data-stu-id="386ef-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="386ef-218">Таким образом, объявление функции `DelayAsync` должен иметь тип возвращаемого значения `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="386ef-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="386ef-219">Так как возвращаемый тип — `Task(Of Integer)`, вычисление `Await` выражение в `DoSomethingAsync` создает целое, как показано в следующей инструкции: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="386ef-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="386ef-220">`startButton_Click` Процедура является примером `Async Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="386ef-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="386ef-221">Так как `DoSomethingAsync` — `Async` функции, задача для вызова `DoSomethingAsync` должна быть ожидаемой, как показано в следующей инструкции: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="386ef-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="386ef-222">`startButton_Click` `Sub` Процедура должна быть определена с помощью `Async` модификатор из-за `Await` выражение.</span><span class="sxs-lookup"><span data-stu-id="386ef-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="386ef-223">См. также</span><span class="sxs-lookup"><span data-stu-id="386ef-223">See also</span></span>

- [<span data-ttu-id="386ef-224">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="386ef-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="386ef-225">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="386ef-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="386ef-226">Список параметров</span><span class="sxs-lookup"><span data-stu-id="386ef-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="386ef-227">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="386ef-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="386ef-228">Оператор Call</span><span class="sxs-lookup"><span data-stu-id="386ef-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="386ef-229">Of</span><span class="sxs-lookup"><span data-stu-id="386ef-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="386ef-230">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="386ef-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="386ef-231">Практическое руководство. Использование универсального класса</span><span class="sxs-lookup"><span data-stu-id="386ef-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="386ef-232">Рекомендации по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="386ef-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="386ef-233">Разделяемые методы</span><span class="sxs-lookup"><span data-stu-id="386ef-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
