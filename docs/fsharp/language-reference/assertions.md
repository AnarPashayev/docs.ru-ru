---
title: Утверждения
description: Узнайте, как использовать выражение «assert» как средство отладки для тестирования выражения в F# языка программирования.
ms.date: 05/16/2016
ms.openlocfilehash: c2d97386e87e9b915da490a78fff9aedb9def616
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703222"
---
# <a name="assertions"></a><span data-ttu-id="b1cd5-103">Утверждения</span><span class="sxs-lookup"><span data-stu-id="b1cd5-103">Assertions</span></span>

<span data-ttu-id="b1cd5-104">`assert` Выражение является функцией отладки, можно использовать для тестирования выражения.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="b1cd5-105">При сбое в режиме отладки утверждение создает диалоговое окно системной ошибки.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1cd5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b1cd5-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="b1cd5-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="b1cd5-107">Remarks</span></span>

<span data-ttu-id="b1cd5-108">`assert` Выражение имеет тип `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="b1cd5-109">В приведенном выше синтаксисе *условие* представляет логическое выражение, которое должен быть проверен.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="b1cd5-110">Если выражение, результатом которого является `true`, выполнение продолжается без изменений.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="b1cd5-111">Если результат вычисления равен `false`, создается диалоговое окно системной ошибки.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="b1cd5-112">Диалоговое окно ошибки имеет заголовок, содержащий строку **ложности**.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="b1cd5-113">Диалоговое окно содержит трассировку стека, который указывает, где произошел сбой утверждения.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="b1cd5-114">Проверка утверждений действует только при компиляции в режиме отладки. то есть если константа `DEBUG` определен.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="b1cd5-115">В системе проектов, по умолчанию `DEBUG` констант определена в конфигурации отладки, но не в конфигурации выпуска.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="b1cd5-116">Сбой проверочного утверждения не может быть перехвачено с помощью F# обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="b1cd5-117">`assert` Функции разрешается в <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="b1cd5-118">Пример</span><span class="sxs-lookup"><span data-stu-id="b1cd5-118">Example</span></span>

<span data-ttu-id="b1cd5-119">В следующем примере кода показано использование `assert` выражение.</span><span class="sxs-lookup"><span data-stu-id="b1cd5-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="b1cd5-120">См. также</span><span class="sxs-lookup"><span data-stu-id="b1cd5-120">See also</span></span>

- [<span data-ttu-id="b1cd5-121">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="b1cd5-121">F# Language Reference</span></span>](index.md)