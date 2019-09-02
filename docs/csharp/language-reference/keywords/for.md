---
title: Оператор for (C#)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 61315a04ca8d5a619a3dcaf43b15a309919d3c42
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167866"
---
# <a name="for-c-reference"></a><span data-ttu-id="12741-102">for (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="12741-102">for (C# reference)</span></span>

<span data-ttu-id="12741-103">Оператор `for` выполняет оператор или блок операторов, пока определенное логическое выражение равно значению `true`.</span><span class="sxs-lookup"><span data-stu-id="12741-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="12741-104">В любой момент в блоке операторов `for` вы можете прервать цикл с помощью оператора [break](break.md) или перейти к следующей итерации в цикле с помощью оператора [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="12741-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="12741-105">Также можно выйти из цикла `for` с помощью операторов [goto](goto.md), [return](return.md) или [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="12741-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="12741-106">Структура оператора `for`</span><span class="sxs-lookup"><span data-stu-id="12741-106">Structure of the `for` statement</span></span>

<span data-ttu-id="12741-107">Оператор `for` определяет разделы *инициализатора*, *условия* и *итератора*:</span><span class="sxs-lookup"><span data-stu-id="12741-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="12741-108">Все три раздела добавляются по желанию.</span><span class="sxs-lookup"><span data-stu-id="12741-108">All three sections are optional.</span></span> <span data-ttu-id="12741-109">Тело цикла является оператором или блоком операторов.</span><span class="sxs-lookup"><span data-stu-id="12741-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="12741-110">В следующем примере показан оператор `for` со всеми определенными разделами:</span><span class="sxs-lookup"><span data-stu-id="12741-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="12741-111">Раздел *инициализатора*</span><span class="sxs-lookup"><span data-stu-id="12741-111">The *initializer* section</span></span>

<span data-ttu-id="12741-112">Операторы в разделе *инициализатора* выполняются только один раз перед входом в цикл.</span><span class="sxs-lookup"><span data-stu-id="12741-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="12741-113">Раздел *инициализатора* представляет собой один из следующих объектов:</span><span class="sxs-lookup"><span data-stu-id="12741-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="12741-114">Объявление и инициализация локальной переменной цикла, к которой невозможно получить доступ вне цикла.</span><span class="sxs-lookup"><span data-stu-id="12741-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="12741-115">Ноль или более выражений операторов из следующего списка, разделенные запятыми:</span><span class="sxs-lookup"><span data-stu-id="12741-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="12741-116">оператор [присваивания](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="12741-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="12741-117">вызов метода</span><span class="sxs-lookup"><span data-stu-id="12741-117">invocation of a method</span></span>

  - <span data-ttu-id="12741-118">префиксное или постфиксное выражение [приращения](../operators/arithmetic-operators.md#increment-operator-), такое как `++i` или `i++`</span><span class="sxs-lookup"><span data-stu-id="12741-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="12741-119">префиксное или постфиксное выражение [декремента](../operators/arithmetic-operators.md#decrement-operator---), такое как `--i` или `i--`</span><span class="sxs-lookup"><span data-stu-id="12741-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="12741-120">создание объекта с помощью оператора [new](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="12741-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="12741-121">выражение [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="12741-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="12741-122">Раздел *инициализатора* в приведенном выше примере объявляет и инициализирует локальную переменную цикла `i`:</span><span class="sxs-lookup"><span data-stu-id="12741-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="12741-123">Раздел *условия*</span><span class="sxs-lookup"><span data-stu-id="12741-123">The *condition* section</span></span>

<span data-ttu-id="12741-124">Раздел *условия*, если он определен, должен быть логическим выражением.</span><span class="sxs-lookup"><span data-stu-id="12741-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="12741-125">Это выражение оценивается перед каждой итерацией цикла.</span><span class="sxs-lookup"><span data-stu-id="12741-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="12741-126">Если раздел *условия* отсутствует или логическое выражение имеет значение `true`, выполняется следующая итерация цикла. В противном случае выполняется выход из цикла.</span><span class="sxs-lookup"><span data-stu-id="12741-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="12741-127">Раздел *условия* в приведенном выше примере определяет, завершится ли цикл в зависимости от значения локальной переменной цикла:</span><span class="sxs-lookup"><span data-stu-id="12741-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="12741-128">Раздел *итератора*</span><span class="sxs-lookup"><span data-stu-id="12741-128">The *iterator* section</span></span>

<span data-ttu-id="12741-129">Раздел *итератора* определяет, что происходит после каждой итерации тела цикла.</span><span class="sxs-lookup"><span data-stu-id="12741-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="12741-130">Раздел *итератора* содержит ноль или более следующих выражений оператора, разделенных запятыми:</span><span class="sxs-lookup"><span data-stu-id="12741-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="12741-131">оператор [присваивания](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="12741-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="12741-132">вызов метода</span><span class="sxs-lookup"><span data-stu-id="12741-132">invocation of a method</span></span>

- <span data-ttu-id="12741-133">префиксное или постфиксное выражение [приращения](../operators/arithmetic-operators.md#increment-operator-), такое как `++i` или `i++`</span><span class="sxs-lookup"><span data-stu-id="12741-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="12741-134">префиксное или постфиксное выражение [декремента](../operators/arithmetic-operators.md#decrement-operator---), такое как `--i` или `i--`</span><span class="sxs-lookup"><span data-stu-id="12741-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="12741-135">создание объекта с помощью оператора [new](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="12741-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="12741-136">выражение [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="12741-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="12741-137">Раздел *итератора* в приведенном выше примере увеличивает локальную переменную цикла:</span><span class="sxs-lookup"><span data-stu-id="12741-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="12741-138">Примеры</span><span class="sxs-lookup"><span data-stu-id="12741-138">Examples</span></span>

<span data-ttu-id="12741-139">В следующем примере показано несколько менее распространенных вариантов использования разделов оператора `for`: присваивание значения внешней переменной цикла в разделе *инициализатора*, вызов метода в разделах *инициализатора* и *итератора* и изменение значения двух переменных в разделе *итератора*.</span><span class="sxs-lookup"><span data-stu-id="12741-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="12741-140">Нажмите **Запустить** для выполнения примера кода.</span><span class="sxs-lookup"><span data-stu-id="12741-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="12741-141">После этого можно изменить код и запустить его еще раз.</span><span class="sxs-lookup"><span data-stu-id="12741-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="12741-142">В следующем примере определен бесконечный цикл `for`:</span><span class="sxs-lookup"><span data-stu-id="12741-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="12741-143">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="12741-143">C# language specification</span></span>

<span data-ttu-id="12741-144">Дополнительные сведения см. в разделе [Оператор for](~/_csharplang/spec/statements.md#the-for-statement) в документации [Предварительная спецификация C# 6.0](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="12741-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="12741-145">См. также</span><span class="sxs-lookup"><span data-stu-id="12741-145">See also</span></span>

- [<span data-ttu-id="12741-146">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="12741-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="12741-147">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="12741-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="12741-148">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="12741-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="12741-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="12741-149">foreach, in</span></span>](foreach-in.md)
