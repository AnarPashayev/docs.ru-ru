---
title: F#соглашения о написании кода
description: Дополнительные общие рекомендации и способы, при написании F# кода.
ms.date: 05/14/2018
ms.openlocfilehash: 1ef016184180eb8d233295e8985903e07693ad26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186749"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="8c803-103">F#соглашения о написании кода</span><span class="sxs-lookup"><span data-stu-id="8c803-103">F# coding conventions</span></span>

<span data-ttu-id="8c803-104">Из опыта работы с большими формулируются следующим соглашениям F# базы кода.</span><span class="sxs-lookup"><span data-stu-id="8c803-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="8c803-105">[Хорошее пять принципов F# кода](index.md#five-principles-of-good-f-code) являются основой каждой рекомендации.</span><span class="sxs-lookup"><span data-stu-id="8c803-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="8c803-106">Они связаны с [ F# рекомендации по проектированию компонентов](component-design-guidelines.md), но подходят для любого F# кода, не только компонентов, таких как библиотеки.</span><span class="sxs-lookup"><span data-stu-id="8c803-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="8c803-107">Упорядочение кода</span><span class="sxs-lookup"><span data-stu-id="8c803-107">Organizing code</span></span>

<span data-ttu-id="8c803-108">F#два основных способа, чтобы упорядочить код функции: модулей и пространств имен.</span><span class="sxs-lookup"><span data-stu-id="8c803-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="8c803-109">Они похожи, но имеют следующие отличия:</span><span class="sxs-lookup"><span data-stu-id="8c803-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="8c803-110">Пространства имен компилируются как пространства имен .NET.</span><span class="sxs-lookup"><span data-stu-id="8c803-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="8c803-111">Модули обычно компилируются как статических классов.</span><span class="sxs-lookup"><span data-stu-id="8c803-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="8c803-112">Пространства имен всегда являются верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="8c803-112">Namespaces are always top level.</span></span> <span data-ttu-id="8c803-113">Модули могут быть верхнего уровня и вложенные в другие модули.</span><span class="sxs-lookup"><span data-stu-id="8c803-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="8c803-114">Пространства имен могут охватывать несколько файлов.</span><span class="sxs-lookup"><span data-stu-id="8c803-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="8c803-115">Модули не могут.</span><span class="sxs-lookup"><span data-stu-id="8c803-115">Modules cannot.</span></span>
* <span data-ttu-id="8c803-116">Модули можно снабдить `[<RequireQualifiedAccess>]` и `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="8c803-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="8c803-117">Следующие рекомендации поможет вам использовать их для организации кода.</span><span class="sxs-lookup"><span data-stu-id="8c803-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="8c803-118">Предпочитать пространства имен верхнего уровня</span><span class="sxs-lookup"><span data-stu-id="8c803-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="8c803-119">Для любой доступной для использования кода пространства имен, предпочтительную модули на верхнем уровне.</span><span class="sxs-lookup"><span data-stu-id="8c803-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="8c803-120">Так как они компилируются как пространства имен .NET, они готовых к использованию с помощью C# с помощью проблем.</span><span class="sxs-lookup"><span data-stu-id="8c803-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="8c803-121">С помощью модуля верхнего уровня может не отличаться при вызове только из F#, но для C# потребителей, вызывающие объекты могут удивить необходимости квалификации `MyClass` с `MyCode` модуля.</span><span class="sxs-lookup"><span data-stu-id="8c803-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="8c803-122">Тщательно применить `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="8c803-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="8c803-123">`[<AutoOpen>]` Конструкции можно повредить области доступных вызывающим объектам, и ответ на что-то образуется «magic».</span><span class="sxs-lookup"><span data-stu-id="8c803-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="8c803-124">Обычно это не хорошо.</span><span class="sxs-lookup"><span data-stu-id="8c803-124">This is generally not a good thing.</span></span> <span data-ttu-id="8c803-125">Исключением из этого правила является F# основной библиотеки сам (хотя этот факт является также немного противоречивым).</span><span class="sxs-lookup"><span data-stu-id="8c803-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="8c803-126">Тем не менее это удобный способ, при наличии вспомогательную функциональность для открытый API, который вы хотите организовать отдельно от общедоступного интерфейса API.</span><span class="sxs-lookup"><span data-stu-id="8c803-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...

    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

<span data-ttu-id="8c803-127">Это позволяет четко отдельные реализации сведения из открытого API-интерфейса функции без необходимости каждый раз, когда она вызывается полного определения вспомогательного метода.</span><span class="sxs-lookup"><span data-stu-id="8c803-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="8c803-128">Кроме того, предоставление методов расширения и построители выражений на уровне пространства имен может быть аккуратно выражен `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="8c803-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="8c803-129">Используйте `[<RequireQualifiedAccess>]` каждый раз, когда может вызвать конфликт имен, или вы считаете, что организации могут работать с удобства чтения</span><span class="sxs-lookup"><span data-stu-id="8c803-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="8c803-130">Добавление `[<RequireQualifiedAccess>]` атрибут к модулю указывает, что модуль не может быть открыт, и необходимость явной ссылки на элементы модуля полного доступа.</span><span class="sxs-lookup"><span data-stu-id="8c803-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="8c803-131">Например `Microsoft.FSharp.Collections.List` модуля с этим атрибутом.</span><span class="sxs-lookup"><span data-stu-id="8c803-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="8c803-132">Это полезно в том случае, если функции и значения в модуле имеют имена, которые могут конфликтовать с именами в других модулях.</span><span class="sxs-lookup"><span data-stu-id="8c803-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="8c803-133">Требуется метод доступа может значительно увеличивать долгосрочной поддержки и развиваемости библиотеки.</span><span class="sxs-lookup"><span data-stu-id="8c803-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="8c803-134">Сортировка `open` инструкций топологически</span><span class="sxs-lookup"><span data-stu-id="8c803-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="8c803-135">В F#, порядок имеет значение объявления, в том числе с `open` инструкций.</span><span class="sxs-lookup"><span data-stu-id="8c803-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="8c803-136">В отличие от C#, где эффект `using` и `using static` не зависит от порядка этих инструкций в файле.</span><span class="sxs-lookup"><span data-stu-id="8c803-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="8c803-137">В F#, открывается в область элементов можно скрывать другие уже присутствует.</span><span class="sxs-lookup"><span data-stu-id="8c803-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="8c803-138">Это означает, что изменение порядка `open` операторы могут привести к изменению значения кодов.</span><span class="sxs-lookup"><span data-stu-id="8c803-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="8c803-139">В результате любой произвольный сортировки всех `open` инструкций (например, буквенно-цифровом порядке) обычно не рекомендуется, иначе создать другое поведение, можно ожидать.</span><span class="sxs-lookup"><span data-stu-id="8c803-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="8c803-140">Вместо этого рекомендуется отсортировать их [топологически](https://en.wikipedia.org/wiki/Topological_sorting); то есть заказать вашей `open` операторов в порядке, в котором _слои_ определенные системы.</span><span class="sxs-lookup"><span data-stu-id="8c803-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="8c803-141">Это буквенно-цифровых, сортировки в различных уровней топологическом мощностями.</span><span class="sxs-lookup"><span data-stu-id="8c803-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="8c803-142">Например, вот топологическую сортировку для F# файл открытого API компилятора службы:</span><span class="sxs-lookup"><span data-stu-id="8c803-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

<span data-ttu-id="8c803-143">Обратите внимание на то, что разрыв строки отделяет топологическом слои с каждым слоем сортируемых буквенно-цифровом порядке позже.</span><span class="sxs-lookup"><span data-stu-id="8c803-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="8c803-144">Это четко организует кода без случайного затенение значения.</span><span class="sxs-lookup"><span data-stu-id="8c803-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="8c803-145">Используйте классы для хранения значения, которые имеют побочные эффекты</span><span class="sxs-lookup"><span data-stu-id="8c803-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="8c803-146">Существует много случаев, когда инициализация значение может иметь побочные эффекты, такие как создание экземпляра контекста базы данных или других удаленных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8c803-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="8c803-147">Соблазнительно для инициализации таких объектов, в модуль и использовать его в последующих функций:</span><span class="sxs-lookup"><span data-stu-id="8c803-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

<span data-ttu-id="8c803-148">Это часто рекомендуется по нескольким причинам:</span><span class="sxs-lookup"><span data-stu-id="8c803-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="8c803-149">Во-первых, Конфигурация приложения помещается в базе кода с `dep1` и `dep2`.</span><span class="sxs-lookup"><span data-stu-id="8c803-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="8c803-150">Этого сложно поддерживать в больших базах кода.</span><span class="sxs-lookup"><span data-stu-id="8c803-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="8c803-151">Во-вторых, статически инициализируемыми данные не должны включать значения, которые не являются потокобезопасными, если компонент будет сам будет использовать несколько потоков.</span><span class="sxs-lookup"><span data-stu-id="8c803-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="8c803-152">Очевидно, что нарушено `dep3`.</span><span class="sxs-lookup"><span data-stu-id="8c803-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="8c803-153">Наконец инициализации модуля компилирует в статический конструктор для всего блока компиляции.</span><span class="sxs-lookup"><span data-stu-id="8c803-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="8c803-154">Если возникают ошибки при инициализации значения привязки let в этом модуле, он объявляется в качестве `TypeInitializationException` , сохраняется в кэше в течение всего времени существования приложения.</span><span class="sxs-lookup"><span data-stu-id="8c803-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="8c803-155">Это может быть трудно диагностировать.</span><span class="sxs-lookup"><span data-stu-id="8c803-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="8c803-156">Обычно имеется внутреннее исключение, можно попытаться строить заключения, но если не существует, то есть не о том, что основной причиной.</span><span class="sxs-lookup"><span data-stu-id="8c803-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="8c803-157">Вместо этого используйте просто простой класс для хранения зависимости:</span><span class="sxs-lookup"><span data-stu-id="8c803-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="8c803-158">Это позволяет следующее:</span><span class="sxs-lookup"><span data-stu-id="8c803-158">This enables the following:</span></span>

1. <span data-ttu-id="8c803-159">Помещает все зависимые состояния за пределами самого API.</span><span class="sxs-lookup"><span data-stu-id="8c803-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="8c803-160">Конфигурации теперь может выполняться за пределами API.</span><span class="sxs-lookup"><span data-stu-id="8c803-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="8c803-161">Ошибки при инициализации для зависимых значений не являются скорее всего, как `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="8c803-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="8c803-162">API удобен для тестирования.</span><span class="sxs-lookup"><span data-stu-id="8c803-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="8c803-163">Управление обработкой ошибок</span><span class="sxs-lookup"><span data-stu-id="8c803-163">Error management</span></span>

<span data-ttu-id="8c803-164">Управление обработкой ошибок в больших системах является сложной и огромным задачей, и нет не silver маркеры в обеспечении систем устойчивы к сбоям и вести себя хорошо.</span><span class="sxs-lookup"><span data-stu-id="8c803-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="8c803-165">Следующие рекомендации следует приводятся рекомендации по это сложно пространство.</span><span class="sxs-lookup"><span data-stu-id="8c803-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="8c803-166">Представляют сценарии ошибок и состояния в типах, характерными для вашего домена</span><span class="sxs-lookup"><span data-stu-id="8c803-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="8c803-167">С помощью [размеченные объединения](../language-reference/discriminated-unions.md), F# дает возможность представлять состояние неисправных программы в вашей системе типов.</span><span class="sxs-lookup"><span data-stu-id="8c803-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="8c803-168">Пример:</span><span class="sxs-lookup"><span data-stu-id="8c803-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="8c803-169">В этом случае тремя способами известных, списывая деньги с банковского счета может завершиться ошибкой.</span><span class="sxs-lookup"><span data-stu-id="8c803-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="8c803-170">Каждый вариант ошибка представить в типе и можно таким образом обработаны безопасно в программе.</span><span class="sxs-lookup"><span data-stu-id="8c803-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="8c803-171">Как правило, если можно моделировать различные способы что-то может **ошибкой** в вашем домене, то код обработки ошибок больше не рассматривается как что-то приходится работать с помимо потока программы.</span><span class="sxs-lookup"><span data-stu-id="8c803-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="8c803-172">Он является просто частью нормального выполнения программы и не считается **исключительных**.</span><span class="sxs-lookup"><span data-stu-id="8c803-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="8c803-173">Существует два основных преимущества этого:</span><span class="sxs-lookup"><span data-stu-id="8c803-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="8c803-174">Это упрощает поддержку вашего домена по мере изменения.</span><span class="sxs-lookup"><span data-stu-id="8c803-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="8c803-175">Сценарии ошибок легче модульного теста.</span><span class="sxs-lookup"><span data-stu-id="8c803-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="8c803-176">Используйте исключения, если ошибки не могут быть представлены с типами</span><span class="sxs-lookup"><span data-stu-id="8c803-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="8c803-177">Не все ошибки могут быть представлены в домене проблему.</span><span class="sxs-lookup"><span data-stu-id="8c803-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="8c803-178">Эти виды ошибок *исключительных* по своей природе, поэтому возможность вызывать и перехватывать исключения в F#.</span><span class="sxs-lookup"><span data-stu-id="8c803-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="8c803-179">Во-первых, рекомендуется ознакомиться с [правила разработки исключений](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="8c803-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="8c803-180">Это также применимо к F#.</span><span class="sxs-lookup"><span data-stu-id="8c803-180">These are also applicable to F#.</span></span>

<span data-ttu-id="8c803-181">Создает в главном F# для целей возникновения исключений следует учитывать в следующем порядке предпочтения:</span><span class="sxs-lookup"><span data-stu-id="8c803-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="8c803-182">Функция</span><span class="sxs-lookup"><span data-stu-id="8c803-182">Function</span></span> | <span data-ttu-id="8c803-183">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8c803-183">Syntax</span></span> | <span data-ttu-id="8c803-184">Цель</span><span class="sxs-lookup"><span data-stu-id="8c803-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="8c803-185">Вызывает `System.ArgumentNullException` с заданным именем аргумента.</span><span class="sxs-lookup"><span data-stu-id="8c803-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="8c803-186">Вызывает `System.ArgumentException` с заданным именем аргумента и сообщением.</span><span class="sxs-lookup"><span data-stu-id="8c803-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="8c803-187">Вызывает `System.InvalidOperationException` с заданным сообщением.</span><span class="sxs-lookup"><span data-stu-id="8c803-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="8c803-188">Универсальный механизм для создания исключений.</span><span class="sxs-lookup"><span data-stu-id="8c803-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="8c803-189">Вызывает `System.Exception` с заданным сообщением.</span><span class="sxs-lookup"><span data-stu-id="8c803-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="8c803-190">Вызывает `System.Exception` с сообщением, определить с помощью строки формата и ее входными данными.</span><span class="sxs-lookup"><span data-stu-id="8c803-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="8c803-191">Используйте `nullArg`, `invalidArg` и `invalidOp` в качестве механизма throw `ArgumentNullException`, `ArgumentException` и `InvalidOperationException` при необходимости.</span><span class="sxs-lookup"><span data-stu-id="8c803-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="8c803-192">`failwith` И `failwithf` функции обычно следует избегать, так как они вызывают базовый `Exception` тип, не определенное исключение.</span><span class="sxs-lookup"><span data-stu-id="8c803-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="8c803-193">Согласно [правила разработки исключений](../../standard/design-guidelines/exceptions.md), требуется повысить более конкретные исключения, когда это возможно.</span><span class="sxs-lookup"><span data-stu-id="8c803-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="8c803-194">Используя синтаксис обработки исключений</span><span class="sxs-lookup"><span data-stu-id="8c803-194">Using exception-handling syntax</span></span>

<span data-ttu-id="8c803-195">F#поддерживает шаблоны исключение через `try...with` синтаксис:</span><span class="sxs-lookup"><span data-stu-id="8c803-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="8c803-196">Согласование функциональные возможности для выполнения при возникновении исключения с сопоставлением шаблонов может быть немного сложнее, если вы хотите максимально оптимизировать код.</span><span class="sxs-lookup"><span data-stu-id="8c803-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="8c803-197">Один из таких способов для обработки этого является использование [активные шаблоны](../language-reference/active-patterns.md) позволяет функции группами, окружающие как случай ошибки с исключением сам.</span><span class="sxs-lookup"><span data-stu-id="8c803-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="8c803-198">Например может использовать API, который, когда он создает исключение, заключает ценную информацию в метаданные исключения.</span><span class="sxs-lookup"><span data-stu-id="8c803-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="8c803-199">Распаковывание полезное значение в теле записанного исключения внутри активный шаблон и возврат, что значение может быть полезным в некоторых ситуациях.</span><span class="sxs-lookup"><span data-stu-id="8c803-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="8c803-200">Не используйте результата вычисления обработку ошибок, чтобы заменить исключения</span><span class="sxs-lookup"><span data-stu-id="8c803-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="8c803-201">Исключения представляются отчасти запретным в функциональном программировании.</span><span class="sxs-lookup"><span data-stu-id="8c803-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="8c803-202">Действительно исключения нарушать чистоты, поэтому можно безопасно рассматривать их работы не совсем.</span><span class="sxs-lookup"><span data-stu-id="8c803-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="8c803-203">Тем не менее это не учитывает реальность, где должен быть запущен код и среды выполнения, могут возникать ошибки.</span><span class="sxs-lookup"><span data-stu-id="8c803-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="8c803-204">В общем случае следует писать код на предположении, что большинство параметров являются чисто ни общий, чтобы свести к минимуму неприятных сюрпризов.</span><span class="sxs-lookup"><span data-stu-id="8c803-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="8c803-205">Очень важно учесть следующие основные преимущества/аспекты исключений по отношению к их релевантность и адекватность в среду выполнения .NET и версий на разных языках экосистемы в целом:</span><span class="sxs-lookup"><span data-stu-id="8c803-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="8c803-206">Они содержат подробные диагностические сведения, которые очень полезно при отладке проблемы.</span><span class="sxs-lookup"><span data-stu-id="8c803-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="8c803-207">Они вполне понятной средой выполнения и других языках .NET.</span><span class="sxs-lookup"><span data-stu-id="8c803-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="8c803-208">Они могут уменьшить количество значительные стандартного по сравнению с кодом, который выходит за пределы пути *избежать* исключения путем реализации некоторого подмножества их семантику на основе ad-hoc.</span><span class="sxs-lookup"><span data-stu-id="8c803-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="8c803-209">Это третья точка важно.</span><span class="sxs-lookup"><span data-stu-id="8c803-209">This third point is critical.</span></span> <span data-ttu-id="8c803-210">Для нетривиальных сложные операции не сможет использовать исключения может привести к работе со структурами, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8c803-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="8c803-211">Может легко привести к уязвимости кода сопоставления шаблонов в «stringly типизированные» ошибки:</span><span class="sxs-lookup"><span data-stu-id="8c803-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="8c803-212">Кроме того он может показаться проглотить любое исключение в требуемом для функции «простой», возвращающий тип «лучше»:</span><span class="sxs-lookup"><span data-stu-id="8c803-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="8c803-213">К сожалению `tryReadAllText` может создавать многочисленные исключения, зависимости бесчисленного множества вещей, которые могут возникать в файловой системе, и этот код немедленно отменяет любые сведения о что могло фактически пойти в вашей среде.</span><span class="sxs-lookup"><span data-stu-id="8c803-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="8c803-214">Если необходимо заменить этот код с типом результатов, затем вы возвращаетесь назад «stringly типизированные» ошибки синтаксического анализа сообщений:</span><span class="sxs-lookup"><span data-stu-id="8c803-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

<span data-ttu-id="8c803-215">А сам объект исключения в `Error` конструктор просто заставляет должным образом работать с типом исключения во время вызова, а не в функции.</span><span class="sxs-lookup"><span data-stu-id="8c803-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="8c803-216">Это фактически создает проверяемые исключения, которые являются заведомо unfun дело как вызывающего объекта API.</span><span class="sxs-lookup"><span data-stu-id="8c803-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="8c803-217">Является хорошей альтернативой приведенных выше примерах для перехвата *конкретных* исключений и возврат осмысленное значение в контексте этого исключения.</span><span class="sxs-lookup"><span data-stu-id="8c803-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="8c803-218">При изменении `tryReadAllText` функцию следующим образом, `None` имеет большее значение:</span><span class="sxs-lookup"><span data-stu-id="8c803-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="8c803-219">Вместо того, как catch-all, эта функция будет теперь правильно обрабатывать случаи, когда файл не найден и назначить значение, возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="8c803-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="8c803-220">Это возвращаемое значение можно сопоставить в этом случае ошибка во время не отменяя все контекстные сведения или принудительное вызывающие объекты для обработки случая, которая может не относиться в этот момент в коде.</span><span class="sxs-lookup"><span data-stu-id="8c803-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="8c803-221">Типы, такие как `Result<'Success, 'Error>` наиболее подходящие для основных операций, где они не являются вложенными, и F# дополнительные типы идеальны для представляющий когда что-то удалось возвращения *что-то* или *ничего не*.</span><span class="sxs-lookup"><span data-stu-id="8c803-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="8c803-222">Они не являются заменой для исключений, хотя и не должны использоваться с целью для замены исключения.</span><span class="sxs-lookup"><span data-stu-id="8c803-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="8c803-223">Вместо этого они должны применяться осмотрительно адреса определенных аспектов исключения и ошибки политики управления целевых способами.</span><span class="sxs-lookup"><span data-stu-id="8c803-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="8c803-224">Частичное применение и программирование без использования точки</span><span class="sxs-lookup"><span data-stu-id="8c803-224">Partial application and point-free programming</span></span>

<span data-ttu-id="8c803-225">F#поддерживает частичное применение и, следовательно, различные способы программы в стиле без использования точки.</span><span class="sxs-lookup"><span data-stu-id="8c803-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="8c803-226">Это может быть использовано для повторного использования кода в модуль или что-то реализации, но обычно это не что-то для предоставления публично.</span><span class="sxs-lookup"><span data-stu-id="8c803-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="8c803-227">Как правило программирование без использования точки не тем, само по себе и можно добавить cognitive образуют серьезный барьер для тех, кто не занимается стиль.</span><span class="sxs-lookup"><span data-stu-id="8c803-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="8c803-228">Не используйте частичное применение и каррирование общедоступных интерфейсов API</span><span class="sxs-lookup"><span data-stu-id="8c803-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="8c803-229">За исключением мало использование частичное применение общедоступных интерфейсов API может запутать пользователей.</span><span class="sxs-lookup"><span data-stu-id="8c803-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="8c803-230">Как правило `let`-привязанного значения в F# код **значения**, а не **значений функций**.</span><span class="sxs-lookup"><span data-stu-id="8c803-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="8c803-231">Смешивание друг с другом, значений и значений функций может привести к сохранение небольшое количество строк кода за счет совсем немного тратить время и силы, особенно в том случае, если совместно с операторами, такие как `>>` для создания функции.</span><span class="sxs-lookup"><span data-stu-id="8c803-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="8c803-232">Следует учитывать влияние средств для программирования без использования точки</span><span class="sxs-lookup"><span data-stu-id="8c803-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="8c803-233">Каррированные функции метки не для их аргументов.</span><span class="sxs-lookup"><span data-stu-id="8c803-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="8c803-234">Это имеет последствия для средств.</span><span class="sxs-lookup"><span data-stu-id="8c803-234">This has tooling implications.</span></span> <span data-ttu-id="8c803-235">Рассмотрим следующие две функции:</span><span class="sxs-lookup"><span data-stu-id="8c803-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="8c803-236">Оба являются допустимым функции, но `funcWithApplication` Каррированная функция.</span><span class="sxs-lookup"><span data-stu-id="8c803-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="8c803-237">При наведении указателя мыши над их типы, в редакторе, вы видите это:</span><span class="sxs-lookup"><span data-stu-id="8c803-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="8c803-238">Во время вызова, всплывающие подсказки в средствах, таких как Visual Studio не даст значимую информацию о том, что `string` и `int` фактически описывают типы входных данных.</span><span class="sxs-lookup"><span data-stu-id="8c803-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="8c803-239">При возникновении кода, без точки, такие как `funcWithApplication` , доступной для использования, рекомендуется выполнить полный η-расширения, чтобы средства можно обратить ваше внимание на значимые имена для аргументов.</span><span class="sxs-lookup"><span data-stu-id="8c803-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="8c803-240">Кроме того отладка кода без точки может оказаться сложной задачей, если не невозможной.</span><span class="sxs-lookup"><span data-stu-id="8c803-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="8c803-241">Средства отладки зависит от значений, связанных с именами (например, `let` привязки) таким образом, вы можете проверить промежуточные значения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="8c803-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="8c803-242">Если код содержит значения, не проверять, нет ничего для отладки.</span><span class="sxs-lookup"><span data-stu-id="8c803-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="8c803-243">В будущем, средства отладки, могут видоизменяться синтезировать эти значения, на основании путей к предыдущим, но это не рекомендуется hedge ваша ставка на *потенциальных* функции отладки.</span><span class="sxs-lookup"><span data-stu-id="8c803-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="8c803-244">Рассмотрим частичное применение как методика, чтобы уменьшить количество внутренних стандартного</span><span class="sxs-lookup"><span data-stu-id="8c803-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="8c803-245">В отличие от предыдущей точки частичное применение – это замечательное средство для сокращения стандартный внутри приложения или более внутренних API.</span><span class="sxs-lookup"><span data-stu-id="8c803-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="8c803-246">Может быть полезным для модульного тестирования реализации более сложных интерфейсов API, в которых шаблона является неудобной, поскольку для работы с.</span><span class="sxs-lookup"><span data-stu-id="8c803-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="8c803-247">Например, в следующем коде показано, как это можно сделать какие наиболее макетирования платформы позволяют без перевода внешнюю зависимость такую платформу и необходимости изучать, связанный с ним заказному API.</span><span class="sxs-lookup"><span data-stu-id="8c803-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="8c803-248">Например рассмотрим следующие топографии решения:</span><span class="sxs-lookup"><span data-stu-id="8c803-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="8c803-249">`ImplementationLogic.fsproj` Например, может предоставлять код:</span><span class="sxs-lookup"><span data-stu-id="8c803-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="8c803-250">Модульное тестирование `Transactions.doTransaction` в `ImplementationLogic.Tests.fspoj` прост:</span><span class="sxs-lookup"><span data-stu-id="8c803-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="8c803-251">Частично применение `doTransaction` благодаря макетирования контекста объекта можно вызвать функцию во всех модульных тестов без необходимости создавать макеты контекста каждый раз:</span><span class="sxs-lookup"><span data-stu-id="8c803-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="8c803-252">Этот способ не следует применять универсально для всей базы кода, но это хороший способ уменьшить количество стандартного для сложных внутренние компоненты и модульного тестирования эти внутренние компоненты.</span><span class="sxs-lookup"><span data-stu-id="8c803-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="8c803-253">Управление доступом</span><span class="sxs-lookup"><span data-stu-id="8c803-253">Access control</span></span>

<span data-ttu-id="8c803-254">F#есть несколько вариантов для [управление доступом](../language-reference/access-control.md), унаследованное от того, что доступно в среде выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="8c803-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="8c803-255">Это не просто можно использовать для типов — их можно использовать для функций, слишком.</span><span class="sxs-lookup"><span data-stu-id="8c803-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="8c803-256">Предпочитать отличных`public` типов и членов, пока она не понадобится, чтобы быть доступной для использования.</span><span class="sxs-lookup"><span data-stu-id="8c803-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="8c803-257">Это также минимизирует какие несколько потребителей для.</span><span class="sxs-lookup"><span data-stu-id="8c803-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="8c803-258">Старайтесь, чтобы все вспомогательные функции `private`.</span><span class="sxs-lookup"><span data-stu-id="8c803-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="8c803-259">Рассмотрите возможность использования `[<AutoOpen>]` на частный модуль вспомогательные функции, если они становятся многочисленные.</span><span class="sxs-lookup"><span data-stu-id="8c803-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="8c803-260">Распознавание типов и обобщения</span><span class="sxs-lookup"><span data-stu-id="8c803-260">Type inference and generics</span></span>

<span data-ttu-id="8c803-261">Вывод типа, которые можно сохранить массу стандартного ввода.</span><span class="sxs-lookup"><span data-stu-id="8c803-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="8c803-262">И Автоматическое обобщение в F# компилятор может помочь написать более общий код с почти никаких дополнительных действий со стороны пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c803-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="8c803-263">Тем не менее эти функции не глобально.</span><span class="sxs-lookup"><span data-stu-id="8c803-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="8c803-264">Рассмотрите возможность добавления меток имена аргументов с помощью явных типов общедоступных интерфейсов API и не следует полагаться на определение типа для этого.</span><span class="sxs-lookup"><span data-stu-id="8c803-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="8c803-265">Причина в том, что **вы** должны находиться в элемент управления фигуры API, не компилятор.</span><span class="sxs-lookup"><span data-stu-id="8c803-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="8c803-266">Несмотря на то, что компилятор может сделать нормально задания на вывод типов для вас, это может быть форма изменения API, если внутренние компоненты, которые она зависит от были изменены типы.</span><span class="sxs-lookup"><span data-stu-id="8c803-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="8c803-267">Это может быть то, что нужно, но это почти наверняка приведет к критически важное изменение API, подчиненные потребители придется иметь дело с.</span><span class="sxs-lookup"><span data-stu-id="8c803-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="8c803-268">Вместо этого Если вы явным образом управления формой создаваемого общедоступного API, можно управлять эти критические изменения.</span><span class="sxs-lookup"><span data-stu-id="8c803-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="8c803-269">В терминах DDD это может рассматриваться как уровень защиты от повреждения.</span><span class="sxs-lookup"><span data-stu-id="8c803-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="8c803-270">Рекомендуется дать понятное имя для универсальных аргументов.</span><span class="sxs-lookup"><span data-stu-id="8c803-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="8c803-271">Если вы создаете по-настоящему универсальный код, который не относится к определенному домену, понятное имя может помочь другим программистам, основные сведения о домене, с которыми они работают в.</span><span class="sxs-lookup"><span data-stu-id="8c803-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="8c803-272">Например, параметр типа с именем `'Document` в контексте взаимодействия с документом базы данных дает яснее понять, что типы универсального документа может быть принят функцией или член, вы работаете.</span><span class="sxs-lookup"><span data-stu-id="8c803-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="8c803-273">Следует назвать параметров универсального типа с PascalCase.</span><span class="sxs-lookup"><span data-stu-id="8c803-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="8c803-274">Это общий способ для выполнения задач в .NET, в том случае, поэтому рекомендуется использовать PascalCase, а не snake_case или camelCase.</span><span class="sxs-lookup"><span data-stu-id="8c803-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="8c803-275">Наконец, Автоматическое обобщение не всегда отдушина для тех, кто еще не работали с F# или большой базы кода.</span><span class="sxs-lookup"><span data-stu-id="8c803-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="8c803-276">Есть время и силы в использовании компонентов, которые являются обобщенными.</span><span class="sxs-lookup"><span data-stu-id="8c803-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="8c803-277">Кроме того Если автоматически универсальной функции не используются с различными типами входных (только в том случае, если они предназначены для использования таким образом не говоря), то не имеет смысла реальных им быть универсальным в определенный момент времени.</span><span class="sxs-lookup"><span data-stu-id="8c803-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="8c803-278">Всегда учитывайте, если код, который вы пишете будет фактически преимущества, связанные с универсальным.</span><span class="sxs-lookup"><span data-stu-id="8c803-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="8c803-279">Производительность</span><span class="sxs-lookup"><span data-stu-id="8c803-279">Performance</span></span>

<span data-ttu-id="8c803-280">F#значения являются неизменяемыми по умолчанию, что позволяет избежать определенные классы ошибок (особенно этих включающие параллельная обработка и параллелизм).</span><span class="sxs-lookup"><span data-stu-id="8c803-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="8c803-281">Однако в некоторых случаях для достижения оптимальной (или даже разумного) эффективность времени выполнения или выделения памяти, диапазон рабочих может лучше всего реализовать с помощью встроенного мутаций состояния.</span><span class="sxs-lookup"><span data-stu-id="8c803-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="8c803-282">Это можно сделать в выраженного ими согласия с F# с `mutable` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="8c803-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="8c803-283">Однако использование `mutable` в F# может показаться соответствует функциональной чистоты.</span><span class="sxs-lookup"><span data-stu-id="8c803-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="8c803-284">Это нормально, если установить значение ожидания со чистоты для [ссылочной прозрачности](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="8c803-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="8c803-285">Ссылочной прозрачности - не чистоты — это конечная цель при написании F# функции.</span><span class="sxs-lookup"><span data-stu-id="8c803-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="8c803-286">Это позволяет писать функциональной интерфейс через реализацию на основе изменений для критического кода на производительности.</span><span class="sxs-lookup"><span data-stu-id="8c803-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="8c803-287">Поместите код с изменяемым в неизменяемом интерфейсы</span><span class="sxs-lookup"><span data-stu-id="8c803-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="8c803-288">С помощью ссылочной прозрачности как целевой показатель на крайне важно написать код, который не содержит изменяемую underbelly критически важным для производительности функций.</span><span class="sxs-lookup"><span data-stu-id="8c803-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="8c803-289">Например, в следующем коде реализуется `Array.contains` работать в F# основной библиотеки:</span><span class="sxs-lookup"><span data-stu-id="8c803-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

<span data-ttu-id="8c803-290">Вызов этой функции несколько раз не приводит к изменению базового массива, и ему не требуется возможность поддерживать любое изменяемое состояние, в использовании ее.</span><span class="sxs-lookup"><span data-stu-id="8c803-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="8c803-291">Он прозрачен со ссылочным, несмотря на то, что почти все строки кода в нем используется изменений.</span><span class="sxs-lookup"><span data-stu-id="8c803-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="8c803-292">Рассмотрите возможность инкапсуляции изменяемые данные в классах</span><span class="sxs-lookup"><span data-stu-id="8c803-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="8c803-293">В предыдущем примере использовался одной функции для инкапсуляции операций с использованием изменяемые данные.</span><span class="sxs-lookup"><span data-stu-id="8c803-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="8c803-294">Это не всегда достаточно для более сложных наборов данных.</span><span class="sxs-lookup"><span data-stu-id="8c803-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="8c803-295">Рассмотрим следующий набор функций:</span><span class="sxs-lookup"><span data-stu-id="8c803-295">Consider the following sets of functions:</span></span>

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

<span data-ttu-id="8c803-296">Этот код обеспечивает высокую производительность, но предоставляет структуру данных на основе изменений, что вызывающие объекты отвечают за обеспечение.</span><span class="sxs-lookup"><span data-stu-id="8c803-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="8c803-297">Это может быть заключен в теле класса без базовых членов, которые можно изменить:</span><span class="sxs-lookup"><span data-stu-id="8c803-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="8c803-298">`Closure1Table` Инкапсулирует базовой структуры данных на основе изменений, тем самым не выполняется принудительно вызывающих объектов для поддержания базовой структуры данных.</span><span class="sxs-lookup"><span data-stu-id="8c803-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="8c803-299">Классы являются мощным средством для инкапсуляции данных и подпрограммы, которые создаются на основе изменений без предоставления сведений для вызывающих объектов.</span><span class="sxs-lookup"><span data-stu-id="8c803-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="8c803-300">Предпочитать `let mutable` для ссылочные ячейки</span><span class="sxs-lookup"><span data-stu-id="8c803-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="8c803-301">Ссылочные ячейки — это способ ссылкой на значение, а не само значение.</span><span class="sxs-lookup"><span data-stu-id="8c803-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="8c803-302">Несмотря на то, что они могут использоваться для кода, важных для производительности, они обычно не рекомендуются.</span><span class="sxs-lookup"><span data-stu-id="8c803-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="8c803-303">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="8c803-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="8c803-304">Использовать ссылочную ячейку теперь «засоряет» все последующие кода по разыменовываем и повторно ссылаются на базовые данные.</span><span class="sxs-lookup"><span data-stu-id="8c803-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="8c803-305">Вместо этого рассмотрите возможность `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="8c803-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="8c803-306">Помимо единой точки изменений середине лямбда-выражения, все остальные кода, касается `acc` можно сделать таким образом, ничем не отличается для использования обычной `let`-привязан постоянное значение.</span><span class="sxs-lookup"><span data-stu-id="8c803-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="8c803-307">Это облегчит могут изменяться со временем.</span><span class="sxs-lookup"><span data-stu-id="8c803-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="8c803-308">Программирование на основе объекта</span><span class="sxs-lookup"><span data-stu-id="8c803-308">Object programming</span></span>

<span data-ttu-id="8c803-309">F#имеет полную поддержку для объектов и объектно ориентированные концепции (ОО).</span><span class="sxs-lookup"><span data-stu-id="8c803-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="8c803-310">Несмотря на то, что многие концепции объектно-Ориентированный являются мощным и полезным, не все из них идеально подходят для использования.</span><span class="sxs-lookup"><span data-stu-id="8c803-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="8c803-311">Перечисленные ниже приводятся рекомендации по категории: функции объектно-Ориентированный на высоком уровне.</span><span class="sxs-lookup"><span data-stu-id="8c803-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="8c803-312">**Рассмотрите возможность использования этих функций во многих ситуациях:**</span><span class="sxs-lookup"><span data-stu-id="8c803-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="8c803-313">Нотация с точками (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="8c803-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="8c803-314">Члены экземпляров</span><span class="sxs-lookup"><span data-stu-id="8c803-314">Instance members</span></span>
* <span data-ttu-id="8c803-315">Неявные конструкторы</span><span class="sxs-lookup"><span data-stu-id="8c803-315">Implicit constructors</span></span>
* <span data-ttu-id="8c803-316">Статические члены</span><span class="sxs-lookup"><span data-stu-id="8c803-316">Static members</span></span>
* <span data-ttu-id="8c803-317">Обозначения индексатора (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="8c803-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="8c803-318">Именованные и необязательные аргументы</span><span class="sxs-lookup"><span data-stu-id="8c803-318">Named and Optional arguments</span></span>
* <span data-ttu-id="8c803-319">Интерфейсы и реализации интерфейса</span><span class="sxs-lookup"><span data-stu-id="8c803-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="8c803-320">**Не достигают для этих функций сначала, но применить их их осмотрительно, когда они удобны для решения проблемы:**</span><span class="sxs-lookup"><span data-stu-id="8c803-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="8c803-321">Перегрузка методов</span><span class="sxs-lookup"><span data-stu-id="8c803-321">Method overloading</span></span>
* <span data-ttu-id="8c803-322">Инкапсулированный изменяемые данные</span><span class="sxs-lookup"><span data-stu-id="8c803-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="8c803-323">Операторы типов</span><span class="sxs-lookup"><span data-stu-id="8c803-323">Operators on types</span></span>
* <span data-ttu-id="8c803-324">Автосвойства</span><span class="sxs-lookup"><span data-stu-id="8c803-324">Auto properties</span></span>
* <span data-ttu-id="8c803-325">Реализация `IDisposable` и `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="8c803-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="8c803-326">Расширения типов</span><span class="sxs-lookup"><span data-stu-id="8c803-326">Type extensions</span></span>
* <span data-ttu-id="8c803-327">События</span><span class="sxs-lookup"><span data-stu-id="8c803-327">Events</span></span>
* <span data-ttu-id="8c803-328">Структуры</span><span class="sxs-lookup"><span data-stu-id="8c803-328">Structs</span></span>
* <span data-ttu-id="8c803-329">Делегаты</span><span class="sxs-lookup"><span data-stu-id="8c803-329">Delegates</span></span>
* <span data-ttu-id="8c803-330">перечислениям;</span><span class="sxs-lookup"><span data-stu-id="8c803-330">Enums</span></span>

<span data-ttu-id="8c803-331">**Если не требуется использовать их как правило, избегайте этих функций:**</span><span class="sxs-lookup"><span data-stu-id="8c803-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="8c803-332">Иерархии типов на основе наследования и реализации наследования</span><span class="sxs-lookup"><span data-stu-id="8c803-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="8c803-333">Значения NULL и `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="8c803-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="8c803-334">Предпочтение компоновки наследованию</span><span class="sxs-lookup"><span data-stu-id="8c803-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="8c803-335">[Композиции через наследование](https://en.wikipedia.org/wiki/Composition_over_inheritance) так просто издавна идиом F# можно придерживаться кода.</span><span class="sxs-lookup"><span data-stu-id="8c803-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="8c803-336">Фундаментальный принцип — следует предоставить базовый класс и не принудительно наследовать от этого базового класса, чтобы получить функции вызывающим объектам.</span><span class="sxs-lookup"><span data-stu-id="8c803-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="8c803-337">Выражения объекта используются для реализации интерфейсов в том случае, если класс не требуется</span><span class="sxs-lookup"><span data-stu-id="8c803-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="8c803-338">[Выражения объектов](../language-reference/object-expressions.md) позволяют реализовывать интерфейсы на ходу, привязывая реализованный интерфейс к значению без необходимости сделать это внутри класса.</span><span class="sxs-lookup"><span data-stu-id="8c803-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="8c803-339">Это удобно, особенно в том случае, если вы _только_ необходимо реализовать интерфейс и не требуются для полного класса.</span><span class="sxs-lookup"><span data-stu-id="8c803-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="8c803-340">Например, ниже приведен код, выполняемый на [Ionide](http://ionide.io/) для предоставления действие исправления кода, если вы добавили символ, у вас нет `open` инструкции для:</span><span class="sxs-lookup"><span data-stu-id="8c803-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

<span data-ttu-id="8c803-341">Так как нет необходимости для класса при взаимодействии с API кода Visual Studio, выражения объекта — идеальное средство для этого.</span><span class="sxs-lookup"><span data-stu-id="8c803-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="8c803-342">Их также можно использовать для модульного тестирования для заглушки для интерфейса с помощью процедуры тестирования ad hoc образом.</span><span class="sxs-lookup"><span data-stu-id="8c803-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="8c803-343">Сокращенные обозначения типов</span><span class="sxs-lookup"><span data-stu-id="8c803-343">Type Abbreviations</span></span>

<span data-ttu-id="8c803-344">[Аббревиатуры типов](../language-reference/type-abbreviations.md) являются удобным способом для назначения метки для другого типа, например сигнатуру функции или более сложного типа.</span><span class="sxs-lookup"><span data-stu-id="8c803-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="8c803-345">Например, следующий псевдоним присваивает метки что необходимо для определения вычислений с [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), глубокого обучения библиотеки:</span><span class="sxs-lookup"><span data-stu-id="8c803-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="8c803-346">`Computation` Имя является удобным способом для обозначения того, любая функция, которая совпадает с сигнатурой, он является присвоение псевдонимов.</span><span class="sxs-lookup"><span data-stu-id="8c803-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="8c803-347">С помощью сокращенные формы типов, как это удобно и позволяет более лаконичный код.</span><span class="sxs-lookup"><span data-stu-id="8c803-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="8c803-348">Старайтесь не использовать сокращенные формы типов для представления вашего домена</span><span class="sxs-lookup"><span data-stu-id="8c803-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="8c803-349">Несмотря на то, что сокращенные формы типов удобны для присвоения имени сигнатуры функций, они могут быть путаницу при сокращение параметра других типов.</span><span class="sxs-lookup"><span data-stu-id="8c803-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="8c803-350">Рассмотрим это сокращение.</span><span class="sxs-lookup"><span data-stu-id="8c803-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="8c803-351">Это может вызывать трудности несколькими способами:</span><span class="sxs-lookup"><span data-stu-id="8c803-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="8c803-352">`BufferSize` не представляет собой абстракцию; Это просто еще одно имя для целого числа.</span><span class="sxs-lookup"><span data-stu-id="8c803-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="8c803-353">Если `BufferSize` предоставляется в открытый API, его можно легко быть неправильно интерпретированы означает больше, чем просто `int`.</span><span class="sxs-lookup"><span data-stu-id="8c803-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="8c803-354">Как правило, типы домена имеют несколько атрибутов, чтобы их и не являются типами-примитивами, например `int`.</span><span class="sxs-lookup"><span data-stu-id="8c803-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="8c803-355">Это сокращение нарушает этого предположения.</span><span class="sxs-lookup"><span data-stu-id="8c803-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="8c803-356">Регистр `BufferSize` (PascalCase) означает, что этот тип содержит дополнительные данные.</span><span class="sxs-lookup"><span data-stu-id="8c803-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="8c803-357">Этот псевдоним не обеспечивает повышенный уровень четкости, по сравнению с обеспечением именованный аргумент в функцию.</span><span class="sxs-lookup"><span data-stu-id="8c803-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="8c803-358">Сокращение не выразится в скомпилированного промежуточного языка; Это просто целое число, и этот псевдоним — это конструкция, во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="8c803-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="8c803-359">Таким образом, ловушек с сокращенные формы типов является то, что они **не** абстракции по типам, они сокращение параметра.</span><span class="sxs-lookup"><span data-stu-id="8c803-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="8c803-360">В предыдущем примере `BufferSize` просто `int` на самом деле с нет дополнительных данных, а также все преимущества из системы типов помимо что `int` уже есть.</span><span class="sxs-lookup"><span data-stu-id="8c803-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
