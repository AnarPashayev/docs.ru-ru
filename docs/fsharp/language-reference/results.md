---
title: Результаты
description: Сведения об использовании F# введите «Результат», которые помогут вам создавать ошибкам кода.
ms.date: 04/24/2017
ms.openlocfilehash: 36f60df8a2991c1d318e4921af6c9e89a0156918
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645323"
---
# <a name="results"></a>Результаты

Начиная с F# 4.1, имеется `Result<'T,'TFailure>` тип, который можно использовать для написания ошибкам код, который может быть задан.

## <a name="syntax"></a>Синтаксис

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a>Примечания

Обратите внимание, что тип результата — [размеченные объединения](discriminated-unions.md#struct-discriminated-unions), который впервые появился в еще одна функция F# 4.1.  Здесь применяется семантика структурного равенства.

`Result` Тип обычно используется в результата вычисления обработки ошибок, который часто называется [железнодорожных ориентированное программирование](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) в F# сообщества.  Ниже приведен упрощенный пример этот подход.

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

Как вы видите, это довольно просто цепочку различные функции проверки, если можно сделать так, чтобы вернуть `Result`.  Это позволяет разделить функциональные возможности следующим образом на мелкие части, в которых сочетаются, как их быть при необходимости.  Кроме того, это преимущества *применение* использование [сопоставление шаблонов](pattern-matching.md) в конце цикла проверки, который, в обеспечивает более высокую степень корректности программ.

## <a name="see-also"></a>См. также

- [Размеченные объединения](discriminated-unions.md)
- [Соответствие шаблону](pattern-matching.md)
