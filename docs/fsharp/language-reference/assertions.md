---
title: Утверждения
description: Узнайте, как использовать выражение "Assert" в качестве функции отладки для тестирования выражений на языке F# программирования.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630023"
---
# <a name="assertions"></a><span data-ttu-id="f698d-103">Утверждения</span><span class="sxs-lookup"><span data-stu-id="f698d-103">Assertions</span></span>

<span data-ttu-id="f698d-104">`assert` Выражение — это функция отладки, которую можно использовать для проверки выражения.</span><span class="sxs-lookup"><span data-stu-id="f698d-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="f698d-105">При сбое в режиме отладки утверждение создает диалоговое окно системной ошибки.</span><span class="sxs-lookup"><span data-stu-id="f698d-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="f698d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f698d-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="f698d-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="f698d-107">Remarks</span></span>

<span data-ttu-id="f698d-108">Выражение имеет тип `bool -> unit`. `assert`</span><span class="sxs-lookup"><span data-stu-id="f698d-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="f698d-109">В предыдущем синтаксисе *условие* представляет собой логическое выражение, которое необходимо проверить.</span><span class="sxs-lookup"><span data-stu-id="f698d-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="f698d-110">Если результат вычисления выражения равен `true`, выполнение остается неизменным.</span><span class="sxs-lookup"><span data-stu-id="f698d-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="f698d-111">Если он имеет значение `false`, то создается диалоговое окно системная ошибка.</span><span class="sxs-lookup"><span data-stu-id="f698d-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="f698d-112">В диалоговом окне "ошибка" имеется заголовок, содержащий **утверждение**строки.</span><span class="sxs-lookup"><span data-stu-id="f698d-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="f698d-113">Диалоговое окно содержит трассировку стека, которая указывает, где произошла ошибка утверждения.</span><span class="sxs-lookup"><span data-stu-id="f698d-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="f698d-114">Проверка утверждения включена только при компиляции в режиме отладки. то есть, если константа `DEBUG` определена.</span><span class="sxs-lookup"><span data-stu-id="f698d-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="f698d-115">По умолчанию `DEBUG` в системе проектов константа определена в конфигурации отладки, но не в конфигурации выпуска.</span><span class="sxs-lookup"><span data-stu-id="f698d-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="f698d-116">Ошибка при сбое утверждения не может быть перехвачена с F# помощью обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="f698d-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="f698d-117">Функция разрешается в <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>. `assert`</span><span class="sxs-lookup"><span data-stu-id="f698d-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="f698d-118">Пример</span><span class="sxs-lookup"><span data-stu-id="f698d-118">Example</span></span>

<span data-ttu-id="f698d-119">В следующем примере кода показано использование `assert` выражения.</span><span class="sxs-lookup"><span data-stu-id="f698d-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="f698d-120">См. также</span><span class="sxs-lookup"><span data-stu-id="f698d-120">See also</span></span>

- [<span data-ttu-id="f698d-121">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="f698d-121">F# Language Reference</span></span>](index.md)
