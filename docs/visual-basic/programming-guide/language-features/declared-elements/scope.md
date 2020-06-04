---
title: Область
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 1bee904996257474b7457b2aefb1f17d250933cb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410738"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="8fb35-102">Область видимости в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8fb35-102">Scope in Visual Basic</span></span>

<span data-ttu-id="8fb35-103">*Областью видимости* объявленного элемента является набор всего кода, который может ссылаться на него без уточнения его имени или предоставления доступа с помощью [оператора Imports (пространство имен .NET и тип)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="8fb35-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="8fb35-104">Элемент может иметь область действия на одном из следующих уровней:</span><span class="sxs-lookup"><span data-stu-id="8fb35-104">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="8fb35-105">Level</span><span class="sxs-lookup"><span data-stu-id="8fb35-105">Level</span></span>|<span data-ttu-id="8fb35-106">Описание</span><span class="sxs-lookup"><span data-stu-id="8fb35-106">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="8fb35-107">Область действия блока</span><span class="sxs-lookup"><span data-stu-id="8fb35-107">Block scope</span></span>|<span data-ttu-id="8fb35-108">Доступно только в блоке кода, в котором он объявлен</span><span class="sxs-lookup"><span data-stu-id="8fb35-108">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="8fb35-109">Область действия процедуры</span><span class="sxs-lookup"><span data-stu-id="8fb35-109">Procedure scope</span></span>|<span data-ttu-id="8fb35-110">Доступен для всего кода в процедуре, в которой он объявлен</span><span class="sxs-lookup"><span data-stu-id="8fb35-110">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="8fb35-111">Область модуля</span><span class="sxs-lookup"><span data-stu-id="8fb35-111">Module scope</span></span>|<span data-ttu-id="8fb35-112">Доступен для всего кода в модуле, классе или структуре, в которой он объявлен</span><span class="sxs-lookup"><span data-stu-id="8fb35-112">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="8fb35-113">Область пространства имен</span><span class="sxs-lookup"><span data-stu-id="8fb35-113">Namespace scope</span></span>|<span data-ttu-id="8fb35-114">Доступен для всего кода в пространстве имен, в котором оно объявлено</span><span class="sxs-lookup"><span data-stu-id="8fb35-114">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="8fb35-115">Эти уровни области выполняются от самого узкого (блока) до самого широкого (пространства имен), где *самая узкие области* означает наименьший набор кода, который может ссылаться на элемент без квалификации.</span><span class="sxs-lookup"><span data-stu-id="8fb35-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="8fb35-116">Дополнительные сведения см. в разделе уровни области на этой странице.</span><span class="sxs-lookup"><span data-stu-id="8fb35-116">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="8fb35-117">Указание области и определение переменных</span><span class="sxs-lookup"><span data-stu-id="8fb35-117">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="8fb35-118">Вы указываете область элемента при его объявлении.</span><span class="sxs-lookup"><span data-stu-id="8fb35-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="8fb35-119">Область может зависеть от следующих факторов:</span><span class="sxs-lookup"><span data-stu-id="8fb35-119">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="8fb35-120">Область (блок, процедура, модуль, класс или структура), в которой объявляется элемент</span><span class="sxs-lookup"><span data-stu-id="8fb35-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="8fb35-121">Пространство имен, содержащее объявление элемента</span><span class="sxs-lookup"><span data-stu-id="8fb35-121">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="8fb35-122">Уровень доступа, объявленный для элемента</span><span class="sxs-lookup"><span data-stu-id="8fb35-122">The access level you declare for the element</span></span>

<span data-ttu-id="8fb35-123">Используйте осторожность при определении переменных с одинаковым именем, но с разными областями, так как это может привести к непредвиденным результатам.</span><span class="sxs-lookup"><span data-stu-id="8fb35-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="8fb35-124">Для получения дополнительной информации см. [References to Declared Elements](references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="8fb35-124">For more information, see [References to Declared Elements](references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="8fb35-125">Уровни области</span><span class="sxs-lookup"><span data-stu-id="8fb35-125">Levels of Scope</span></span>

<span data-ttu-id="8fb35-126">Программный элемент доступен по всему региону, в котором он объявлен.</span><span class="sxs-lookup"><span data-stu-id="8fb35-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="8fb35-127">Весь код в одном регионе может ссылаться на элемент без уточнения его имени.</span><span class="sxs-lookup"><span data-stu-id="8fb35-127">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="8fb35-128">Область блока</span><span class="sxs-lookup"><span data-stu-id="8fb35-128">Block Scope</span></span>

<span data-ttu-id="8fb35-129">Блок — это набор инструкций, заключенных в операторы инициирования и завершения объявления, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="8fb35-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="8fb35-130">`Do` и `Loop`</span><span class="sxs-lookup"><span data-stu-id="8fb35-130">`Do` and `Loop`</span></span>

- <span data-ttu-id="8fb35-131">`For`[ `Each` ] и`Next`</span><span class="sxs-lookup"><span data-stu-id="8fb35-131">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="8fb35-132">`If` и `End If`</span><span class="sxs-lookup"><span data-stu-id="8fb35-132">`If` and `End If`</span></span>

- <span data-ttu-id="8fb35-133">`Select` и `End Select`</span><span class="sxs-lookup"><span data-stu-id="8fb35-133">`Select` and `End Select`</span></span>

- <span data-ttu-id="8fb35-134">`SyncLock` и `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="8fb35-134">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="8fb35-135">`Try` и `End Try`</span><span class="sxs-lookup"><span data-stu-id="8fb35-135">`Try` and `End Try`</span></span>

- <span data-ttu-id="8fb35-136">`While` и `End While`</span><span class="sxs-lookup"><span data-stu-id="8fb35-136">`While` and `End While`</span></span>

- <span data-ttu-id="8fb35-137">`With` и `End With`</span><span class="sxs-lookup"><span data-stu-id="8fb35-137">`With` and `End With`</span></span>

<span data-ttu-id="8fb35-138">Если переменная объявлена в блоке, ее можно использовать только в пределах этого блока.</span><span class="sxs-lookup"><span data-stu-id="8fb35-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="8fb35-139">В следующем примере областью целочисленной переменной `cube` является блок между `If` и `End If` , и вы больше не можете ссылаться на то, `cube` когда выполнение передается из блока.</span><span class="sxs-lookup"><span data-stu-id="8fb35-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="8fb35-140">Даже если область действия переменной ограничена блоком, ее время существования все равно будет содержаться во всей процедуре.</span><span class="sxs-lookup"><span data-stu-id="8fb35-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="8fb35-141">Если вы вводите блок несколько раз во время процедуры, каждая переменная блока удерживает свое предыдущее значение.</span><span class="sxs-lookup"><span data-stu-id="8fb35-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="8fb35-142">Чтобы избежать непредвиденных результатов в таком случае, разумно инициализировать блочные переменные в начале блока.</span><span class="sxs-lookup"><span data-stu-id="8fb35-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="8fb35-143">Область действия процедуры</span><span class="sxs-lookup"><span data-stu-id="8fb35-143">Procedure Scope</span></span>

<span data-ttu-id="8fb35-144">Элемент, объявленный внутри процедуры, недоступен за пределами этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="8fb35-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="8fb35-145">Только процедура, содержащая объявление, может использовать его.</span><span class="sxs-lookup"><span data-stu-id="8fb35-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="8fb35-146">Переменные на этом уровне также называются *локальными переменными*.</span><span class="sxs-lookup"><span data-stu-id="8fb35-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="8fb35-147">Они объявляются с помощью [оператора Dim](../../../language-reference/statements/dim-statement.md)с ключевым словом [static](../../../language-reference/modifiers/static.md) или без него.</span><span class="sxs-lookup"><span data-stu-id="8fb35-147">You declare them with the [Dim Statement](../../../language-reference/statements/dim-statement.md), with or without the [Static](../../../language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="8fb35-148">Область действия процедуры и блока тесно связана.</span><span class="sxs-lookup"><span data-stu-id="8fb35-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="8fb35-149">При объявлении переменной внутри процедуры, но вне любого блока внутри этой процедуры можно считать, что переменная имеет область видимости блока, где блоком является вся процедура.</span><span class="sxs-lookup"><span data-stu-id="8fb35-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="8fb35-150">Все локальные элементы, даже если они являются `Static` переменными, являются частными для процедуры, в которой они отображаются.</span><span class="sxs-lookup"><span data-stu-id="8fb35-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="8fb35-151">Нельзя объявить какой-либо элемент с помощью ключевого слова [Public](../../../language-reference/modifiers/public.md) в процедуре.</span><span class="sxs-lookup"><span data-stu-id="8fb35-151">You cannot declare any element using the [Public](../../../language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="8fb35-152">Область модуля</span><span class="sxs-lookup"><span data-stu-id="8fb35-152">Module Scope</span></span>

<span data-ttu-id="8fb35-153">Для удобства *уровень модуля* единого термина применяется в равной степени к модулям, классам и структурам.</span><span class="sxs-lookup"><span data-stu-id="8fb35-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="8fb35-154">Вы можете объявить элементы на этом уровне, поместив оператор объявления за пределы любой процедуры или блока, но внутри модуля, класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="8fb35-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="8fb35-155">При создании объявления на уровне модуля этот уровень доступа определяет область.</span><span class="sxs-lookup"><span data-stu-id="8fb35-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="8fb35-156">Пространство имен, содержащее модуль, класс или структуру, также влияет на область.</span><span class="sxs-lookup"><span data-stu-id="8fb35-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="8fb35-157">Элементы, для которых объявлен [частный](../../../language-reference/modifiers/private.md) уровень доступа, доступны для каждой процедуры в этом модуле, но не для кода в другом модуле.</span><span class="sxs-lookup"><span data-stu-id="8fb35-157">Elements for which you declare [Private](../../../language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="8fb35-158">`Dim`Инструкция на уровне модуля по умолчанию принимает значение, `Private` если не используются ключевые слова уровня доступа.</span><span class="sxs-lookup"><span data-stu-id="8fb35-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="8fb35-159">Тем не менее можно сделать область и уровень доступа более очевидными с помощью `Private` ключевого слова в `Dim` инструкции.</span><span class="sxs-lookup"><span data-stu-id="8fb35-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="8fb35-160">В следующем примере все процедуры, определенные в модуле, могут ссылаться на строковую переменную `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="8fb35-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="8fb35-161">При вызове второй процедуры она отображает содержимое строковой переменной `strMsg` в диалоговом окне.</span><span class="sxs-lookup"><span data-stu-id="8fb35-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a><span data-ttu-id="8fb35-162">Область пространства имен</span><span class="sxs-lookup"><span data-stu-id="8fb35-162">Namespace Scope</span></span>

<span data-ttu-id="8fb35-163">Если элемент объявляется на уровне модуля с помощью ключевого слова [Friend](../../../language-reference/modifiers/friend.md) или [Public](../../../language-reference/modifiers/public.md) , он становится доступным для всех процедур в пространстве имен, в котором объявлен элемент.</span><span class="sxs-lookup"><span data-stu-id="8fb35-163">If you declare an element at module level using the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="8fb35-164">После выполнения следующей изменения в предыдущем примере строковая переменная `strMsg` может называться кодом в любом месте пространства имен его объявления.</span><span class="sxs-lookup"><span data-stu-id="8fb35-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="8fb35-165">Область пространства имен включает вложенные пространства имен.</span><span class="sxs-lookup"><span data-stu-id="8fb35-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="8fb35-166">Элемент, доступный из пространства имен, также доступен из любого пространства имен, вложенного в это пространство имен.</span><span class="sxs-lookup"><span data-stu-id="8fb35-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="8fb35-167">Если проект не содержит [операторов пространства имен](../../../language-reference/statements/namespace-statement.md), все в проекте находится в том же пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="8fb35-167">If your project does not contain any [Namespace Statement](../../../language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="8fb35-168">В этом случае область пространства имен может рассматриваться как область проекта.</span><span class="sxs-lookup"><span data-stu-id="8fb35-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="8fb35-169">`Public`элементы в модуле, классе или структуре также доступны для любого проекта, который ссылается на свой проект.</span><span class="sxs-lookup"><span data-stu-id="8fb35-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="8fb35-170">Выбора области</span><span class="sxs-lookup"><span data-stu-id="8fb35-170">Choice of Scope</span></span>

<span data-ttu-id="8fb35-171">При определении переменной следует учитывать следующие моменты при выборе ее области действия.</span><span class="sxs-lookup"><span data-stu-id="8fb35-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="8fb35-172">Преимущества локальных переменных</span><span class="sxs-lookup"><span data-stu-id="8fb35-172">Advantages of Local Variables</span></span>

<span data-ttu-id="8fb35-173">Локальные переменные являются хорошим выбором для любого временного вычисления по следующим причинам.</span><span class="sxs-lookup"><span data-stu-id="8fb35-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="8fb35-174">**Конфликт имен — избежать.**</span><span class="sxs-lookup"><span data-stu-id="8fb35-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="8fb35-175">Имена локальных переменных не подвержены конфликтам.</span><span class="sxs-lookup"><span data-stu-id="8fb35-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="8fb35-176">Например, можно создать несколько различных процедур, содержащих переменную с именем `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="8fb35-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="8fb35-177">Если каждая из них `intTemp` объявлена как локальная переменная, каждая процедура распознает только собственную версию `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="8fb35-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="8fb35-178">Любая процедура может изменить значение в локальной переменной, `intTemp` не влияя на `intTemp` переменные в других процедурах.</span><span class="sxs-lookup"><span data-stu-id="8fb35-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="8fb35-179">**Потребление памяти.**</span><span class="sxs-lookup"><span data-stu-id="8fb35-179">**Memory Consumption.**</span></span> <span data-ttu-id="8fb35-180">Локальные переменные потребляют память только во время выполнения процедуры.</span><span class="sxs-lookup"><span data-stu-id="8fb35-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="8fb35-181">Их память освобождается, когда процедура возвращается в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="8fb35-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="8fb35-182">В отличие от этого, [Общие](../../../language-reference/modifiers/shared.md) и [статические](../../../language-reference/modifiers/static.md) переменные потребляют ресурсы памяти до тех пор, пока приложение не прекратит работу, поэтому используйте их только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="8fb35-182">By contrast, [Shared](../../../language-reference/modifiers/shared.md) and [Static](../../../language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="8fb35-183">*Переменные экземпляра* потребляют память, пока их экземпляры продолжают существовать, что делает их менее эффективными, чем локальные переменные, но потенциально более эффективными, чем `Shared` `Static` переменные.</span><span class="sxs-lookup"><span data-stu-id="8fb35-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="8fb35-184">Минимизация области</span><span class="sxs-lookup"><span data-stu-id="8fb35-184">Minimizing Scope</span></span>

<span data-ttu-id="8fb35-185">Как правило, при объявлении любой переменной или константы рекомендуется сделать область как можно более узким (область блока является самой узким).</span><span class="sxs-lookup"><span data-stu-id="8fb35-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="8fb35-186">Это помогает экономить память и минимизирует вероятность того, что код ошибочно ссылался на неверную переменную.</span><span class="sxs-lookup"><span data-stu-id="8fb35-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="8fb35-187">Аналогично, следует объявить переменную как [статическую](../../../language-reference/modifiers/static.md) , только если необходимо сохранить ее значение между вызовами процедур.</span><span class="sxs-lookup"><span data-stu-id="8fb35-187">Similarly, you should declare a variable to be [Static](../../../language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fb35-188">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8fb35-188">See also</span></span>

- [<span data-ttu-id="8fb35-189">Характеристики объявленных элементов</span><span class="sxs-lookup"><span data-stu-id="8fb35-189">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="8fb35-190">Практическое руководство. Управление областью действия переменной</span><span class="sxs-lookup"><span data-stu-id="8fb35-190">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="8fb35-191">Время существования в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8fb35-191">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="8fb35-192">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8fb35-192">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="8fb35-193">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="8fb35-193">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="8fb35-194">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="8fb35-194">Variable Declaration</span></span>](../variables/variable-declaration.md)
