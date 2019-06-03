---
title: '#Справочник по C#. Директива препроцессора if'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: 12ef0926665103e739ed4a8ee83ff895b439fffc
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300077"
---
# <a name="if-c-reference"></a><span data-ttu-id="af658-102">#if (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="af658-102">#if (C# Reference)</span></span>

<span data-ttu-id="af658-103">Когда компилятор C# встречает директиву `#if`, за которой следует директива [#endif](preprocessor-endif.md), код между этими директивами он компилирует, только когда определен указанный символ.</span><span class="sxs-lookup"><span data-stu-id="af658-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="af658-104">В отличие от С и С++ здесь нельзя назначить символу числовое значение.</span><span class="sxs-lookup"><span data-stu-id="af658-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="af658-105">Оператор #if в C# является логическим. Он проверяет только одно условие — определен ли указанный символ.</span><span class="sxs-lookup"><span data-stu-id="af658-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="af658-106">Например:</span><span class="sxs-lookup"><span data-stu-id="af658-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="af658-107">Операторы [==](../operators/equality-operators.md#equality-operator-) (равенство) и [! =](../operators/equality-operators.md#inequality-operator-) (неравенство) вы можете использовать только для проверки значений [true](../keywords/true-literal.md) или [false](../keywords/false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="af658-107">You can use the operators [==](../operators/equality-operators.md#equality-operator-) (equality) and [!=](../operators/equality-operators.md#inequality-operator-) (inequality) only to test for [true](../keywords/true-literal.md) or [false](../keywords/false-literal.md).</span></span> <span data-ttu-id="af658-108">Значение true означает, что символ определен.</span><span class="sxs-lookup"><span data-stu-id="af658-108">True means the symbol is defined.</span></span> <span data-ttu-id="af658-109">Инструкция `#if DEBUG` имеет то же значение, что и `#if (DEBUG == true)`.</span><span class="sxs-lookup"><span data-stu-id="af658-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="af658-110">Вы можете использовать операторы [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (логическое И), [& #124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (логическое ИЛИ) и [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="af658-110">You can use the operators [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) (and), [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) (or), and [!](../operators/boolean-logical-operators.md#logical-negation-operator-)</span></span> <span data-ttu-id="af658-111">(логическое НЕ) для проверки нескольких символов.</span><span class="sxs-lookup"><span data-stu-id="af658-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="af658-112">Можно также группировать символы и операторы при помощи скобок.</span><span class="sxs-lookup"><span data-stu-id="af658-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="af658-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="af658-113">Remarks</span></span>

<span data-ttu-id="af658-114">`#if`, как и директивы [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md) и [#undef](preprocessor-undef.md), позволяет включить или исключить код в зависимости от существования одного или нескольких символов.</span><span class="sxs-lookup"><span data-stu-id="af658-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="af658-115">Это может быть полезно при компиляции кода для отладки или для определенной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="af658-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="af658-116">Условные директивы, начинающиеся с директивы `#if`, должны явным образом завершаться директивой `#endif`.</span><span class="sxs-lookup"><span data-stu-id="af658-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="af658-117">`#define` позволяет определить символ,</span><span class="sxs-lookup"><span data-stu-id="af658-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="af658-118">чтобы директива `#if`, которой передается этот символ, возвращала значение `true`.</span><span class="sxs-lookup"><span data-stu-id="af658-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="af658-119">Также символ можно определить с помощью параметра компилятора [-define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="af658-119">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="af658-120">Для отмены определения символа служит директива [#undef](preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="af658-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="af658-121">Символ, определенный с помощью `-define` или `#define`, не конфликтует с одноименной переменной.</span><span class="sxs-lookup"><span data-stu-id="af658-121">A symbol that you define with `-define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="af658-122">Соответственно, имя переменной не должно передаваться директиве препроцессора, а символ может использоваться только в директиве препроцессора.</span><span class="sxs-lookup"><span data-stu-id="af658-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="af658-123">Символ, создаваемый с помощью `#define`, будет определен в пределах того файл, в котором он определен.</span><span class="sxs-lookup"><span data-stu-id="af658-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="af658-124">Система сборки также учитывает символы препроцессора, представляющие [целевые платформы](../../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="af658-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="af658-125">Они полезны при создании приложений, предназначенных для нескольких реализаций или версий .NET.</span><span class="sxs-lookup"><span data-stu-id="af658-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="af658-126">Другие предопределенные символы включают константы DEBUG и TRACE.</span><span class="sxs-lookup"><span data-stu-id="af658-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="af658-127">Вы можете переопределить значения для проектов с помощью `#define`.</span><span class="sxs-lookup"><span data-stu-id="af658-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="af658-128">Например, символ DEBUG автоматически устанавливается в зависимости от свойств конфигурации сборки (в режиме отладки или выпуска).</span><span class="sxs-lookup"><span data-stu-id="af658-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="af658-129">Примеры</span><span class="sxs-lookup"><span data-stu-id="af658-129">Examples</span></span>

<span data-ttu-id="af658-130">В следующем примере показано, как определить символ MYTEST в файле и затем протестировать значения символов MYTEST и DEBUG.</span><span class="sxs-lookup"><span data-stu-id="af658-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="af658-131">Выходные данные этого примера зависят от режима конфигурации, в котором создан проект (режим отладки или выпуска).</span><span class="sxs-lookup"><span data-stu-id="af658-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

```csharp
#define MYTEST
using System;
public class MyClass
{
    static void Main()
    {
#if (DEBUG && !MYTEST)
        Console.WriteLine("DEBUG is defined");
#elif (!DEBUG && MYTEST)
        Console.WriteLine("MYTEST is defined");
#elif (DEBUG && MYTEST)
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else
        Console.WriteLine("DEBUG and MYTEST are not defined");
#endif
    }
}
```

<span data-ttu-id="af658-132">В следующем примере показано, как тестировать разные целевые платформы для использования более новых интерфейсов API, когда это возможно:</span><span class="sxs-lookup"><span data-stu-id="af658-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a><span data-ttu-id="af658-133">См. также</span><span class="sxs-lookup"><span data-stu-id="af658-133">See also</span></span>

- [<span data-ttu-id="af658-134">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="af658-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="af658-135">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="af658-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="af658-136">Директивы препроцессора C#</span><span class="sxs-lookup"><span data-stu-id="af658-136">C# Preprocessor Directives</span></span>](index.md)
- <span data-ttu-id="af658-137">[Практическое руководство. Условная компиляция с использованием атрибутов Trace и Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).</span><span class="sxs-lookup"><span data-stu-id="af658-137">[How to: Compile Conditionally with Trace and Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)</span></span>
