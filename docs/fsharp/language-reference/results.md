---
title: Результаты
description: Сведения об использовании F# введите «Результат», которые помогут вам создавать ошибкам кода.
ms.date: 04/24/2017
ms.openlocfilehash: 8b419412b406018a21f2c23103c8193fec8766f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770517"
---
# <a name="results"></a><span data-ttu-id="66856-103">Результаты</span><span class="sxs-lookup"><span data-stu-id="66856-103">Results</span></span>

<span data-ttu-id="66856-104">Начиная с F# 4.1, имеется `Result<'T,'TFailure>` тип, который можно использовать для написания ошибкам код, который может быть задан.</span><span class="sxs-lookup"><span data-stu-id="66856-104">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="66856-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="66856-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="66856-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="66856-106">Remarks</span></span>

<span data-ttu-id="66856-107">Обратите внимание, что тип результата — [размеченные объединения](discriminated-unions.md#struct-discriminated-unions), который впервые появился в еще одна функция F# 4.1.</span><span class="sxs-lookup"><span data-stu-id="66856-107">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="66856-108">Здесь применяется семантика структурного равенства.</span><span class="sxs-lookup"><span data-stu-id="66856-108">Structural equality semantics apply here.</span></span>

<span data-ttu-id="66856-109">`Result` Тип обычно используется в результата вычисления обработки ошибок, который часто называется [железнодорожных ориентированное программирование](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) в F# сообщества.</span><span class="sxs-lookup"><span data-stu-id="66856-109">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="66856-110">Ниже приведен упрощенный пример этот подход.</span><span class="sxs-lookup"><span data-stu-id="66856-110">The following trivial example demonstrates this approach.</span></span>

```fsharp
// Define a simple type which has fields that can be validated
type Request = 
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult 
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() = 
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

<span data-ttu-id="66856-111">Как вы видите, это довольно просто цепочку различные функции проверки, если можно сделать так, чтобы вернуть `Result`.</span><span class="sxs-lookup"><span data-stu-id="66856-111">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="66856-112">Это позволяет разделить функциональные возможности следующим образом на мелкие части, в которых сочетаются, как их быть при необходимости.</span><span class="sxs-lookup"><span data-stu-id="66856-112">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="66856-113">Кроме того, это преимущества *применение* использование [сопоставление шаблонов](pattern-matching.md) в конце цикла проверки, который, в обеспечивает более высокую степень корректности программ.</span><span class="sxs-lookup"><span data-stu-id="66856-113">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="66856-114">См. также</span><span class="sxs-lookup"><span data-stu-id="66856-114">See also</span></span>

- [<span data-ttu-id="66856-115">Размеченные объединения</span><span class="sxs-lookup"><span data-stu-id="66856-115">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="66856-116">Соответствие шаблону</span><span class="sxs-lookup"><span data-stu-id="66856-116">Pattern Matching</span></span>](pattern-matching.md)