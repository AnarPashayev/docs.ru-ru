---
title: Справочник по C#. Оператор throw
ms.custom: seodec18
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4536a5caa789712227bfd637d65cfc4c22adf80
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422689"
---
# <a name="throw-c-reference"></a><span data-ttu-id="85b0c-102">throw (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="85b0c-102">throw (C# Reference)</span></span>

<span data-ttu-id="85b0c-103">Сообщает о возникновении исключения во время выполнения программы.</span><span class="sxs-lookup"><span data-stu-id="85b0c-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85b0c-104">Примечания</span><span class="sxs-lookup"><span data-stu-id="85b0c-104">Remarks</span></span>

<span data-ttu-id="85b0c-105">Синтаксис `throw` выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="85b0c-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```

<span data-ttu-id="85b0c-106">где `e` — это экземпляр класса, производного от <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="85b0c-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="85b0c-107">В следующем примере используется оператор `throw` для создания <xref:System.IndexOutOfRangeException>, если аргумент, переданный в метод с именем `GetNumber`, не соответствует допустимому индексу внутреннего массива.</span><span class="sxs-lookup"><span data-stu-id="85b0c-107">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

<span data-ttu-id="85b0c-108">Затем вызывающие объекты метода используют блок `try-catch` или `try-catch-finally` для обработки исключения.</span><span class="sxs-lookup"><span data-stu-id="85b0c-108">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="85b0c-109">В следующем примере показана обработка исключения, созданного методом `GetNumber`.</span><span class="sxs-lookup"><span data-stu-id="85b0c-109">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="85b0c-110">Повторное создание исключения</span><span class="sxs-lookup"><span data-stu-id="85b0c-110">Re-throwing an exception</span></span>

<span data-ttu-id="85b0c-111">`throw` можно также использовать в блоке `catch` для повторного создания исключения, обрабатываемого в блоке `catch`.</span><span class="sxs-lookup"><span data-stu-id="85b0c-111">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="85b0c-112">В этом случае оператор `throw` не принимает операнд исключения.</span><span class="sxs-lookup"><span data-stu-id="85b0c-112">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="85b0c-113">Это наиболее полезно, когда метод передает аргумент от вызывающего объекта в другой метод библиотеки, а метод библиотеки создает исключение, которое должно быть передано вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="85b0c-113">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="85b0c-114">Например, в следующем примере повторно создается исключение <xref:System.NullReferenceException>, возникающее при попытке получить первый символ неинициализированной строки.</span><span class="sxs-lookup"><span data-stu-id="85b0c-114">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> <span data-ttu-id="85b0c-115">Можно также использовать синтаксис `throw e` в блоке `catch`, чтобы создать исключение, которое будет передано вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="85b0c-115">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="85b0c-116">В этом случае трассировка стека исходного исключения, которое доступно из свойства <xref:System.Exception.StackTrace>, не сохраняется.</span><span class="sxs-lookup"><span data-stu-id="85b0c-116">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="85b0c-117">Выражение `throw`</span><span class="sxs-lookup"><span data-stu-id="85b0c-117">The `throw` expression</span></span>

<span data-ttu-id="85b0c-118">Начиная с C# 7.0 `throw` можно использовать в качестве выражения, а также как оператор.</span><span class="sxs-lookup"><span data-stu-id="85b0c-118">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="85b0c-119">Это позволяет вызывать исключения в контекстах, которые ранее не поддерживались.</span><span class="sxs-lookup"><span data-stu-id="85b0c-119">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="85b0c-120">Сюда входит следующее.</span><span class="sxs-lookup"><span data-stu-id="85b0c-120">These include:</span></span>

- <span data-ttu-id="85b0c-121">[Условный оператор](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="85b0c-121">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="85b0c-122">В следующем примере используется исключение `throw` для создания <xref:System.ArgumentException>, если методу передается массив пустых строк.</span><span class="sxs-lookup"><span data-stu-id="85b0c-122">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="85b0c-123">До выхода C# 7.0 эта логика должна была отображаться в операторе `if`/`else`.</span><span class="sxs-lookup"><span data-stu-id="85b0c-123">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- <span data-ttu-id="85b0c-124">[Оператор объединения с NULL](../operators/null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="85b0c-124">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="85b0c-125">В следующем примере выражение `throw` используется с оператором, принимающим значение NULL, для создания исключения, если строка, назначенная свойству `Name` является `null`.</span><span class="sxs-lookup"><span data-stu-id="85b0c-125">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- <span data-ttu-id="85b0c-126">Метод или [лямбда](../../programming-guide/statements-expressions-operators/lambda-expressions.md), воплощающие выражение.</span><span class="sxs-lookup"><span data-stu-id="85b0c-126">an expression-bodied [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="85b0c-127">В следующем примере показан метод, воплощающий выражение, который создает <xref:System.InvalidCastException>, так как преобразование в значение <xref:System.DateTime> не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="85b0c-127">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="85b0c-128">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="85b0c-128">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="85b0c-129">См. также</span><span class="sxs-lookup"><span data-stu-id="85b0c-129">See also</span></span>

- [<span data-ttu-id="85b0c-130">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="85b0c-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="85b0c-131">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="85b0c-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="85b0c-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="85b0c-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="85b0c-133">Операторы try, catch и throw в C++</span><span class="sxs-lookup"><span data-stu-id="85b0c-133">The try, catch, and throw Statements in C++</span></span>](try-catch.md)
- [<span data-ttu-id="85b0c-134">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="85b0c-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="85b0c-135">Практическое руководство. Явное создание исключений</span><span class="sxs-lookup"><span data-stu-id="85b0c-135">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
