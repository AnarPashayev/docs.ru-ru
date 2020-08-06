---
title: Справочник по C#. Контекстное ключевое слово when
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 2b041ca3a821f45dd63ce3f6bee7a920eb495651
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2020
ms.locfileid: "87426999"
---
# <a name="when-c-reference"></a><span data-ttu-id="f3cd6-102">when (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="f3cd6-102">when (C# Reference)</span></span>

<span data-ttu-id="f3cd6-103">Для того чтобы указать условие фильтра в следующих контекстах, можно использовать контекстно-зависимое ключевое слово `when`.</span><span class="sxs-lookup"><span data-stu-id="f3cd6-103">You can use the `when` contextual keyword to specify a filter condition in the following contexts:</span></span>

- <span data-ttu-id="f3cd6-104">В операторе `catch` блока [try/catch](try-catch.md) или [try/catch/finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="f3cd6-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="f3cd6-105">В метке `case` оператора [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="f3cd6-105">In the `case` label of a [switch](switch.md) statement.</span></span>
- <span data-ttu-id="f3cd6-106">В [выражении `switch`](../operators/switch-expression.md).</span><span class="sxs-lookup"><span data-stu-id="f3cd6-106">In the [`switch` expression](../operators/switch-expression.md).</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="f3cd6-107">`when` в операторе `catch`</span><span class="sxs-lookup"><span data-stu-id="f3cd6-107">`when` in a `catch` statement</span></span>

<span data-ttu-id="f3cd6-108">Начиная с C# версии 6, `when` можно использовать в операторе `catch`, чтобы задать условие, которое должно быть истинным для выполнения обработчика определенного исключения.</span><span class="sxs-lookup"><span data-stu-id="f3cd6-108">Starting with C# 6, `when` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="f3cd6-109">Он имеет следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="f3cd6-109">Its syntax is:</span></span>

```csharp
catch (ExceptionType [e]) when (expr)
```

<span data-ttu-id="f3cd6-110">здесь *expr* представляет собой выражение, которое оценивает значение типа Boolean.</span><span class="sxs-lookup"><span data-stu-id="f3cd6-110">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="f3cd6-111">Если он возвращает `true`, обработчик исключений выполняется, а если `false`, то нет.</span><span class="sxs-lookup"><span data-stu-id="f3cd6-111">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span>

<span data-ttu-id="f3cd6-112">В следующем примере используется ключевое слово `when`, которое позволяет условно выполнять обработчики для <xref:System.Net.Http.HttpRequestException> в зависимости от того, какой текст содержит сообщение об исключении.</span><span class="sxs-lookup"><span data-stu-id="f3cd6-112">The following example uses the `when` keyword to conditionally execute handlers for an <xref:System.Net.Http.HttpRequestException> depending on the text of the exception message.</span></span>

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a><span data-ttu-id="f3cd6-113">`when` в операторе `switch`</span><span class="sxs-lookup"><span data-stu-id="f3cd6-113">`when` in a `switch` statement</span></span>

<span data-ttu-id="f3cd6-114">Начиная с версии C# 7.0 метки `case` больше не должны быть взаимоисключающими, а порядок отображения меток `case` в операторе `switch` может определять, какие блоки switch должны быть выполнены.</span><span class="sxs-lookup"><span data-stu-id="f3cd6-114">Starting with C# 7.0, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="f3cd6-115">Ключевое слово `when` позволяет задать условие фильтра, при котором соответствующая метка case будет иметь значение true, только если условие фильтра также имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="f3cd6-115">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="f3cd6-116">Он имеет следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="f3cd6-116">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```

<span data-ttu-id="f3cd6-117">здесь *expr* является постоянным шаблоном или типом шаблона, который сравнивается с соответствующим выражением, а *условие when* представляет собой любое логическое выражение.</span><span class="sxs-lookup"><span data-stu-id="f3cd6-117">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span>

<span data-ttu-id="f3cd6-118">В следующем примере ключевое слово `when` используется для проверки объектов `Shape`, которые имеют нулевую область, а также для проверки различных объектов `Shape` с областью больше нуля.</span><span class="sxs-lookup"><span data-stu-id="f3cd6-118">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span>

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a><span data-ttu-id="f3cd6-119">См. также</span><span class="sxs-lookup"><span data-stu-id="f3cd6-119">See also</span></span>

- [<span data-ttu-id="f3cd6-120">Оператор switch</span><span class="sxs-lookup"><span data-stu-id="f3cd6-120">switch statement</span></span>](switch.md)
- [<span data-ttu-id="f3cd6-121">Оператор try-catch</span><span class="sxs-lookup"><span data-stu-id="f3cd6-121">try/catch statement</span></span>](try-catch.md)
- [<span data-ttu-id="f3cd6-122">Оператор try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="f3cd6-122">try/catch/finally statement</span></span>](try-catch-finally.md)
