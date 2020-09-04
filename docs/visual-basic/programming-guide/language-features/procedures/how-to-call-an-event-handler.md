---
title: Вызов обработчика событий
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
no-loc:
- WithEvents
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 3762c79dd3d883ae2ccfe76b335cf98ac87d4246
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2020
ms.locfileid: "89464965"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="21c67-102">Вызов обработчика событий в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21c67-102">How to call an event handler in Visual Basic</span></span>

<span data-ttu-id="21c67-103">*Событие* — это действие или ситуация (например, превышение щелчка мыши или предела кредита), которые распознаются некоторым компонентом программы и для которых можно написать код для ответа.</span><span class="sxs-lookup"><span data-stu-id="21c67-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="21c67-104">*Обработчик событий* — это код, который вы пишете для реагирования на событие.</span><span class="sxs-lookup"><span data-stu-id="21c67-104">An *event handler* is the code you write to respond to an event.</span></span>

<span data-ttu-id="21c67-105">Обработчик событий в Visual Basic является `Sub` процедурой.</span><span class="sxs-lookup"><span data-stu-id="21c67-105">An event handler in Visual Basic is a `Sub` procedure.</span></span> <span data-ttu-id="21c67-106">Однако обычно он не вызывается так же, как другие `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="21c67-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="21c67-107">Вместо этого вы определяете процедуру как обработчик для события.</span><span class="sxs-lookup"><span data-stu-id="21c67-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="21c67-108">Это можно сделать с помощью [`Handles`](../../../language-reference/statements/handles-clause.md) предложения и [`WithEvents`](../../../language-reference/modifiers/withevents.md) переменной или с помощью [оператора AddHandler](../../../language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="21c67-108">You can do this either with a [`Handles`](../../../language-reference/statements/handles-clause.md) clause and a [`WithEvents`](../../../language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="21c67-109">Использование `Handles` предложения по умолчанию является способом объявления обработчика событий в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="21c67-109">Using a `Handles` clause is the default way to declare an event handler in Visual Basic.</span></span> <span data-ttu-id="21c67-110">Это способ, которым обработчики событий пишутся конструкторами при программировании в интегрированной среде разработки (IDE).</span><span class="sxs-lookup"><span data-stu-id="21c67-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="21c67-111">`AddHandler`Оператор подходит для динамического вызова событий во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="21c67-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>

<span data-ttu-id="21c67-112">Когда происходит событие, Visual Basic автоматически вызывает процедуру обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="21c67-112">When the event occurs, Visual Basic automatically calls the event handler procedure.</span></span> <span data-ttu-id="21c67-113">Любой код, имеющий доступ к событию, может привести к его возникновению, выполнив [оператор RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="21c67-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../language-reference/statements/raiseevent-statement.md).</span></span>

<span data-ttu-id="21c67-114">Можно связать более одного обработчика событий с одним и тем же событием.</span><span class="sxs-lookup"><span data-stu-id="21c67-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="21c67-115">В некоторых случаях можно отменить связь обработчика с событием.</span><span class="sxs-lookup"><span data-stu-id="21c67-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="21c67-116">Дополнительные сведения см. в статье [Events (Visual Basic)](../events/index.md) (События в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="21c67-116">For more information, see [Events](../events/index.md).</span></span>

## <a name="call-an-event-handler-using-no-loc-texthandles-and-no-locwithevents"></a><span data-ttu-id="21c67-117">Вызовите обработчик событий с помощью :::no-loc text="Handles"::: и WithEvents</span><span class="sxs-lookup"><span data-stu-id="21c67-117">Call an event handler using :::no-loc text="Handles"::: and WithEvents</span></span>

1. <span data-ttu-id="21c67-118">Убедитесь, что событие объявлено с помощью [оператора Event](../../../language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="21c67-118">Make sure the event is declared with an [Event Statement](../../../language-reference/statements/event-statement.md).</span></span>

2. <span data-ttu-id="21c67-119">Объявите переменную объекта на уровне модуля или класса с помощью [`WithEvents`](../../../language-reference/modifiers/withevents.md) ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="21c67-119">Declare an object variable at module or class level, using the [`WithEvents`](../../../language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="21c67-120">`As`Предложение для этой переменной должно указывать класс, который вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="21c67-120">The `As` clause for this variable must specify the class that raises the event.</span></span>

3. <span data-ttu-id="21c67-121">В объявлении процедуры обработки событий `Sub` добавьте [`Handles`](../../../language-reference/statements/handles-clause.md) предложение, указывающее `WithEvents` переменную и имя события.</span><span class="sxs-lookup"><span data-stu-id="21c67-121">In the declaration of the event-handling `Sub` procedure, add a [`Handles`](../../../language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>

4. <span data-ttu-id="21c67-122">Когда происходит событие, Visual Basic автоматически вызывает `Sub` процедуру.</span><span class="sxs-lookup"><span data-stu-id="21c67-122">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="21c67-123">В коде можно использовать `RaiseEvent` инструкцию для выполнения события.</span><span class="sxs-lookup"><span data-stu-id="21c67-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="21c67-124">В следующем примере определяется событие и `WithEvents` переменная, которая ссылается на класс, который вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="21c67-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="21c67-125">Процедура обработки событий `Sub` использует `Handles` предложение для указания класса и события, которые он обрабатывает.</span><span class="sxs-lookup"><span data-stu-id="21c67-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="4":::

## <a name="call-an-event-handler-using-addhandler"></a><span data-ttu-id="21c67-126">Вызов обработчика событий с помощью AddHandler</span><span class="sxs-lookup"><span data-stu-id="21c67-126">Call an event handler using AddHandler</span></span>

1. <span data-ttu-id="21c67-127">Убедитесь, что событие объявлено с помощью `Event` оператора.</span><span class="sxs-lookup"><span data-stu-id="21c67-127">Make sure the event is declared with an `Event` statement.</span></span>

2. <span data-ttu-id="21c67-128">Выполните [оператор AddHandler](../../../language-reference/statements/addhandler-statement.md) , чтобы динамически подключить процедуру обработки событий `Sub` с событием.</span><span class="sxs-lookup"><span data-stu-id="21c67-128">Execute an [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>

3. <span data-ttu-id="21c67-129">Когда происходит событие, Visual Basic автоматически вызывает `Sub` процедуру.</span><span class="sxs-lookup"><span data-stu-id="21c67-129">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="21c67-130">В коде можно использовать `RaiseEvent` инструкцию для выполнения события.</span><span class="sxs-lookup"><span data-stu-id="21c67-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="21c67-131">В следующем примере используется [оператор AddHandler](../../../language-reference/statements/addhandler-statement.md) в конструкторе, чтобы связать `OnFormClosing` процедуру как обработчик событий для <xref:System.Windows.Forms.Form.FormClosing> .</span><span class="sxs-lookup"><span data-stu-id="21c67-131">The following example uses the [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) in the constructor to associate the `OnFormClosing` procedure as an event handler for <xref:System.Windows.Forms.Form.FormClosing>.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="5":::

    <span data-ttu-id="21c67-132">Можно отменить связь между обработчиком событий и событием, выполнив [оператор RemoveHandler](../../../language-reference/statements/removehandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="21c67-132">You can dissociate an event handler from an event by executing the [RemoveHandler statement](../../../language-reference/statements/removehandler-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21c67-133">См. также</span><span class="sxs-lookup"><span data-stu-id="21c67-133">See also</span></span>

- [<span data-ttu-id="21c67-134">Процедуры</span><span class="sxs-lookup"><span data-stu-id="21c67-134">Procedures</span></span>](index.md)
- [<span data-ttu-id="21c67-135">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="21c67-135">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="21c67-136">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="21c67-136">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="21c67-137">Оператор AddressOf</span><span class="sxs-lookup"><span data-stu-id="21c67-137">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="21c67-138">Практическое руководство. Создание процедуры</span><span class="sxs-lookup"><span data-stu-id="21c67-138">How to: Create a Procedure</span></span>](how-to-create-a-procedure.md)
- [<span data-ttu-id="21c67-139">Практическое руководство. Вызов процедуры, которая не возвращает значение</span><span class="sxs-lookup"><span data-stu-id="21c67-139">How to: Call a Procedure that Does Not Return a Value</span></span>](how-to-call-a-procedure-that-does-not-return-a-value.md)
