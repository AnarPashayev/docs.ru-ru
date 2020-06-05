---
title: Передача аргументов по позиции и по имени
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: 686b64977f086c8128e56298a0ed8c5aa0c51efa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364036"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="d985a-102">Передача аргументов по позиции и по имени (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d985a-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="d985a-103">При вызове `Sub` процедуры или `Function` можно передавать аргументы *по положению* , в том порядке, в котором они отображаются в определении процедуры, или передавать их *по имени*, не обращаясь к положению.</span><span class="sxs-lookup"><span data-stu-id="d985a-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="d985a-104">При передаче аргумента по имени указывается объявленное имя аргумента, за которым следует двоеточие и знак равенства ( `:=` ), за которым следует значение аргумента.</span><span class="sxs-lookup"><span data-stu-id="d985a-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="d985a-105">Именованные аргументы можно указывать в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="d985a-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="d985a-106">Например, следующая `Sub` процедура принимает три аргумента:</span><span class="sxs-lookup"><span data-stu-id="d985a-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="d985a-107">При вызове этой процедуры аргументы можно указать по положению, по имени или с помощью сочетания обоих типов.</span><span class="sxs-lookup"><span data-stu-id="d985a-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="d985a-108">Передача аргументов по положению</span><span class="sxs-lookup"><span data-stu-id="d985a-108">Passing Arguments by Position</span></span>

<span data-ttu-id="d985a-109">Метод можно вызвать `Display` с аргументами, передаваемыми по положению и разделенным запятыми, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="d985a-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="d985a-110">Если необязательный аргумент не указан в списке позиционированных аргументов, необходимо держать его место с запятой.</span><span class="sxs-lookup"><span data-stu-id="d985a-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="d985a-111">В следующем примере вызывается `Display` метод без `age` аргумента:</span><span class="sxs-lookup"><span data-stu-id="d985a-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="d985a-112">Передача аргументов по имени</span><span class="sxs-lookup"><span data-stu-id="d985a-112">Passing Arguments by Name</span></span>

<span data-ttu-id="d985a-113">Кроме того, можно вызвать `Display` с аргументами, передаваемыми по имени, также разделенными запятыми, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="d985a-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="d985a-114">Передача аргументов по имени таким способом особенно полезна при вызове процедуры, имеющей более одного необязательного аргумента.</span><span class="sxs-lookup"><span data-stu-id="d985a-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="d985a-115">Если аргументы указываются по имени, не нужно использовать последовательные запятые для обозначения пропущенных аргументов.</span><span class="sxs-lookup"><span data-stu-id="d985a-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="d985a-116">Передача аргументов по имени также упрощает отслеживание передаваемых аргументов и тех, которые вы пропускаете.</span><span class="sxs-lookup"><span data-stu-id="d985a-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="d985a-117">Смешивание аргументов по положению и по имени</span><span class="sxs-lookup"><span data-stu-id="d985a-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="d985a-118">Аргументы можно указать как по положению, так и по имени в одном вызове процедуры, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="d985a-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="d985a-119">В предыдущем примере не требуется дополнительная запятая для размещения пропущенного `age` аргумента, так как `birth` передается по имени.</span><span class="sxs-lookup"><span data-stu-id="d985a-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="d985a-120">В версиях Visual Basic до 15,5, при указании аргументов в сочетании с аргументами "расположение" и "имя" все аргументы должны быть первыми.</span><span class="sxs-lookup"><span data-stu-id="d985a-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="d985a-121">После указания аргумента по имени все остальные аргументы должны передаваться по имени.</span><span class="sxs-lookup"><span data-stu-id="d985a-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="d985a-122">Например, при следующем вызове `Display` метода отображается ошибка компилятора [BC30241: Ожидается именованный аргумент](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="d985a-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="d985a-123">Начиная с Visual Basic 15,5, позиционированные аргументы могут следовать именованным аргументам, если конечные аргументы конца находятся в правильном положении.</span><span class="sxs-lookup"><span data-stu-id="d985a-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="d985a-124">При компиляции в разделе Visual Basic 15,5 предыдущий вызов `Display` метода компилируется успешно и больше не создает ошибку компилятора [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="d985a-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="d985a-125">Возможность смешивать и сопоставлять именованные и позиционированные аргументы в любом порядке особенно полезна, если нужно использовать именованный аргумент, чтобы сделать код более удобочитаемым.</span><span class="sxs-lookup"><span data-stu-id="d985a-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="d985a-126">Например, следующий `Person` конструктор класса требует два аргумента типа `Person` , оба из которых могут иметь значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="d985a-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="d985a-127">Использование смешанных именованных и позиционированных аргументов позволяет сделать код понятным, если `father` `mother` аргументы и имеют значение `Nothing` :</span><span class="sxs-lookup"><span data-stu-id="d985a-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="d985a-128">Чтобы следовать аргументам с именованными аргументами, необходимо добавить в файл проекта Visual Basic ( \* VBPROJ) следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="d985a-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="d985a-129">Дополнительные сведения см. [в разделе Задание языковой версии Visual Basic](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="d985a-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="d985a-130">Ограничения на предоставление аргументов по имени</span><span class="sxs-lookup"><span data-stu-id="d985a-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="d985a-131">Аргументы нельзя передавать по имени, чтобы избежать ввода обязательных аргументов.</span><span class="sxs-lookup"><span data-stu-id="d985a-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="d985a-132">Можно опустить только необязательные аргументы.</span><span class="sxs-lookup"><span data-stu-id="d985a-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="d985a-133">Невозможно передать массив параметров по имени.</span><span class="sxs-lookup"><span data-stu-id="d985a-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="d985a-134">Это происходит потому, что при вызове процедуры вы предоставляете неопределенное число аргументов, разделенных запятыми, для массива параметров, и компилятор не может связать более одного аргумента с одним именем.</span><span class="sxs-lookup"><span data-stu-id="d985a-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="d985a-135">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d985a-135">See also</span></span>

- [<span data-ttu-id="d985a-136">Процедуры</span><span class="sxs-lookup"><span data-stu-id="d985a-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d985a-137">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="d985a-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d985a-138">Практическое руководство. Передача аргументов в процедуру</span><span class="sxs-lookup"><span data-stu-id="d985a-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="d985a-139">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="d985a-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="d985a-140">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="d985a-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="d985a-141">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="d985a-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="d985a-142">Необязательно</span><span class="sxs-lookup"><span data-stu-id="d985a-142">Optional</span></span>](../../../language-reference/modifiers/optional.md)
- [<span data-ttu-id="d985a-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="d985a-143">ParamArray</span></span>](../../../language-reference/modifiers/paramarray.md)
