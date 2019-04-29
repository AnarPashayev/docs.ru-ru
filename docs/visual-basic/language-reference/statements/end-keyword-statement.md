---
title: Оператор End <keyword> (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 96dc8ce6b0d3b7545f5caeef43358936e426f566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638159"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="cd6a1-102">Конец \<ключевое слово > Statement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd6a1-102">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="cd6a1-103">Когда следует дополнительных ключевых слов, завершает определение блока операторов, представленного ключевым словом.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd6a1-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cd6a1-104">Syntax</span></span>

```vb
End AddHandler
End Class
End Enum
End Event
End Function
End Get
End If
End Interface
End Module
End Namespace
End Operator
End Property
End RaiseEvent  
End RemoveHandler  
End Select
End Set
End Structure
End Sub
End SyncLock
End Try
End While
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="cd6a1-105">Части</span><span class="sxs-lookup"><span data-stu-id="cd6a1-105">Parts</span></span>

|<span data-ttu-id="cd6a1-106">Отделение</span><span class="sxs-lookup"><span data-stu-id="cd6a1-106">Part</span></span>|<span data-ttu-id="cd6a1-107">Описание</span><span class="sxs-lookup"><span data-stu-id="cd6a1-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="cd6a1-108">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-108">Required.</span></span> <span data-ttu-id="cd6a1-109">Завершает определение программного элемента.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="cd6a1-110">Обязателен для завершения `AddHandler` метод доступа, начатого соответствующим `AddHandler` инструкции в настраиваемом [оператор Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="cd6a1-111">Обязателен для завершения определения класса, начатого соответствующим [оператор Class](class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="cd6a1-112">Обязателен для завершения определение перечисления начатого соответствующим [оператор Enum](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="cd6a1-113">Обязателен для завершения `Custom` определения события, начатого соответствующим [оператор Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="cd6a1-114">Обязателен для завершения `Function` определение процедуры, начатого соответствующим [инструкции Function](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="cd6a1-115">Если при выполнении обнаружена `End Function` инструкции, управление возвращается вызывающему коду.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="cd6a1-116">Обязателен для завершения `Property` определение процедуры, начатого соответствующим [оператор Get](get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="cd6a1-117">Если при выполнении обнаружена `End Get` инструкции, управление возвращается в инструкции, запрашивающего значение свойства.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="cd6a1-118">Обязателен для завершения `If`... `Then`... `Else` определением, начатого соответствующим блока `If` инструкции.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="cd6a1-119">См. в разделе [Если... Затем... Оператор Else](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="cd6a1-120">Обязателен для завершения определения интерфейса начатого соответствующим [Interface-оператор](interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="cd6a1-121">Необходимые для завершения определения события, начатого соответствующим [оператор Module](module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="cd6a1-122">Обязателен для завершения определения пространства имен, начатого соответствующим [оператор Namespace](namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="cd6a1-123">Необходимые для завершения определения оператора, начатого соответствующим [Operator Statement](operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="cd6a1-124">Необходимые для завершения определения свойства, начатого соответствующим [Property Statement](property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="cd6a1-125">Обязателен для завершения `RaiseEvent` метод доступа, начатого соответствующим `RaiseEvent` инструкции в настраиваемом [оператор Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="cd6a1-126">Обязателен для завершения `RemoveHandler` метод доступа, начатого соответствующим `RemoveHandler` инструкции в настраиваемом [оператор Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="cd6a1-127">Обязателен для завершения `Select`... `Case` определением, начатого соответствующим блока `Select` инструкции.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="cd6a1-128">См. в разделе [выберите... Оператор выбора](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="cd6a1-129">Обязателен для завершения `Property` определение процедуры, начатого соответствующим [инструкция Set](set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="cd6a1-130">Если при выполнении обнаружена `End Set` инструкции, управление возвращается оператор, который задает значение свойства.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="cd6a1-131">Обязателен для завершения определения структуры, начатого соответствующим [оператор Structure](structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="cd6a1-132">Обязателен для завершения `Sub` определение процедуры, начатого соответствующим [оператор Sub](sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="cd6a1-133">Если при выполнении обнаружена `End Sub` инструкции, управление возвращается вызывающему коду.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="cd6a1-134">Обязателен для завершения `SyncLock` определением, начатого соответствующим блока `SyncLock` инструкции.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="cd6a1-135">См. в разделе [оператор SyncLock](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="cd6a1-136">Обязателен для завершения `Try`... `Catch`... `Finally` определением, начатого соответствующим блока `Try` инструкции.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="cd6a1-137">См. в разделе [попробуйте... CATCH... Оператор Finally](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="cd6a1-138">Обязателен для завершения `While` определение, начатого соответствующим цикла for `While` инструкции.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="cd6a1-139">См. в разделе [хотя... Завершить оператор While](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="cd6a1-140">Обязателен для завершения `With` определением, начатого соответствующим блока `With` инструкции.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="cd6a1-141">См. в разделе [с... Завершить с помощью инструкции](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="cd6a1-142">Директивы</span><span class="sxs-lookup"><span data-stu-id="cd6a1-142">Directives</span></span>

<span data-ttu-id="cd6a1-143">Если предшествует знак номера (`#`), `End` ключевое слово завершает блок предварительной обработки, представленный соответствующей директивы.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="cd6a1-144">Отделение</span><span class="sxs-lookup"><span data-stu-id="cd6a1-144">Part</span></span>|<span data-ttu-id="cd6a1-145">Описание</span><span class="sxs-lookup"><span data-stu-id="cd6a1-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="cd6a1-146">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-146">Required.</span></span> <span data-ttu-id="cd6a1-147">Завершает определение блока предварительной обработки.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="cd6a1-148">Обязателен для завершения блока внешнего источника, начатого соответствующим [директива #ExternalSource](../directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="cd6a1-149">Обязателен для завершения блока условной компиляции, начатого соответствующим `#If` директива.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="cd6a1-150">См. в разделе [#If... Then... #Else директивы](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="cd6a1-151">Обязателен для завершения блока региона начатого соответствующим [директива #Region](../directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="cd6a1-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="cd6a1-152">Примечания</span><span class="sxs-lookup"><span data-stu-id="cd6a1-152">Remarks</span></span>

<span data-ttu-id="cd6a1-153">[Оператор End](end-statement.md), без дополнительных ключевых слов, немедленно прекращает выполнение.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="cd6a1-154">Примечания для разработчиков смарт-устройств</span><span class="sxs-lookup"><span data-stu-id="cd6a1-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="cd6a1-155">`End` Инструкция без дополнительных ключевых слов, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="cd6a1-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6a1-156">См. также</span><span class="sxs-lookup"><span data-stu-id="cd6a1-156">See also</span></span>

- [<span data-ttu-id="cd6a1-157">Оператор End</span><span class="sxs-lookup"><span data-stu-id="cd6a1-157">End Statement</span></span>](end-statement.md)
