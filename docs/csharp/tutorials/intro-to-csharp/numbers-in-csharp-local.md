---
title: Числа в C#. Вводное руководство по C#
description: Изучите C# на примере числовых типов, их свойств и методов.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d95d5ce16abadf441158b7f8af93acc73b154e99
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661056"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="f09dc-103">Управление целыми числами и числами с плавающей запятой в C\#</span><span class="sxs-lookup"><span data-stu-id="f09dc-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="f09dc-104">Это руководство поможет в интерактивном изучении числовых типов в C#.</span><span class="sxs-lookup"><span data-stu-id="f09dc-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="f09dc-105">Вы напишете небольшие фрагменты кода, затем скомпилируете и выполните этот код.</span><span class="sxs-lookup"><span data-stu-id="f09dc-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="f09dc-106">Руководство содержит ряд уроков, в которых рассматриваются числа и математические операции в C#.</span><span class="sxs-lookup"><span data-stu-id="f09dc-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="f09dc-107">В рамках этих занятий вы ознакомитесь с основами языка C#.</span><span class="sxs-lookup"><span data-stu-id="f09dc-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="f09dc-108">Для работы с этим руководством вам потребуется компьютер, который можно использовать для разработки.</span><span class="sxs-lookup"><span data-stu-id="f09dc-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="f09dc-109">В руководстве по [началу работы с .NET за 10 минут](https://www.microsoft.com/net/core) содержатся инструкции по настройке локальной среды разработки на компьютерах Mac, Windows или Linux.</span><span class="sxs-lookup"><span data-stu-id="f09dc-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="f09dc-110">Краткий обзор команд, которые будут здесь использоваться, и ссылки на дополнительные сведения представлены в статье, посвященной [средствам разработки для .NET](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="f09dc-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="f09dc-111">Вычисления с целыми числами</span><span class="sxs-lookup"><span data-stu-id="f09dc-111">Explore integer math</span></span>

<span data-ttu-id="f09dc-112">Создайте каталог с именем **numbers-quickstart**.</span><span class="sxs-lookup"><span data-stu-id="f09dc-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="f09dc-113">Откройте этот каталог и выполните команду `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="f09dc-114">Откройте файл **Program.cs** в любом редакторе и замените строку `Console.WriteLine("Hello World!");` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="f09dc-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="f09dc-115">Чтобы выполнить этот код, введите `dotnet run` в окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="f09dc-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="f09dc-116">Вы увидели одну из основных математических операций с целыми числами.</span><span class="sxs-lookup"><span data-stu-id="f09dc-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="f09dc-117">Тип `int` представляет **целое** положительное или отрицательное число.</span><span class="sxs-lookup"><span data-stu-id="f09dc-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="f09dc-118">Для сложения используйте символ `+`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="f09dc-119">Другие стандартные математические операции с целыми числами включают:</span><span class="sxs-lookup"><span data-stu-id="f09dc-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="f09dc-120">`-` — вычитание;</span><span class="sxs-lookup"><span data-stu-id="f09dc-120">`-` for subtraction</span></span>
- <span data-ttu-id="f09dc-121">`*` — умножение;</span><span class="sxs-lookup"><span data-stu-id="f09dc-121">`*` for multiplication</span></span>
- <span data-ttu-id="f09dc-122">`/` — деление.</span><span class="sxs-lookup"><span data-stu-id="f09dc-122">`/` for division</span></span>

<span data-ttu-id="f09dc-123">Начните с ознакомления с различными операциями.</span><span class="sxs-lookup"><span data-stu-id="f09dc-123">Start by exploring those different operations.</span></span> <span data-ttu-id="f09dc-124">Добавьте следующие строки после строки, с помощью которой записывается значение `c`:</span><span class="sxs-lookup"><span data-stu-id="f09dc-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="f09dc-125">Чтобы выполнить этот код, введите `dotnet run` в окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="f09dc-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="f09dc-126">Можно также поэкспериментировать, выполнив несколько математических операций в одной строке.</span><span class="sxs-lookup"><span data-stu-id="f09dc-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="f09dc-127">Например, выполните `c = a + b - 12 * 17;`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="f09dc-128">Допускается сочетание переменных и постоянных чисел.</span><span class="sxs-lookup"><span data-stu-id="f09dc-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="f09dc-129">Вероятнее всего, при изучении C# (как и любого другого языка программирования) вы будете допускать ошибки в коде.</span><span class="sxs-lookup"><span data-stu-id="f09dc-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="f09dc-130">**Компилятор** найдет эти ошибки и сообщит вам о них.</span><span class="sxs-lookup"><span data-stu-id="f09dc-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="f09dc-131">Если результат содержит сообщения об ошибках, внимательно просмотрите пример кода и код в окне, чтобы понять, что нужно исправить.</span><span class="sxs-lookup"><span data-stu-id="f09dc-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="f09dc-132">Это упражнение поможет вам изучить структуру кода C#.</span><span class="sxs-lookup"><span data-stu-id="f09dc-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="f09dc-133">Вы завершили первый этап.</span><span class="sxs-lookup"><span data-stu-id="f09dc-133">You've finished the first step.</span></span> <span data-ttu-id="f09dc-134">Прежде чем перейти к следующему разделу, переместим текущий код в отдельный метод.</span><span class="sxs-lookup"><span data-stu-id="f09dc-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="f09dc-135">Это упростит начало работы с новым примером.</span><span class="sxs-lookup"><span data-stu-id="f09dc-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="f09dc-136">Переименуйте метод `Main` в `WorkingWithIntegers` и запишите новый метод `Main`, который вызывает `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="f09dc-137">В результате ваш код должен выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f09dc-137">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a><span data-ttu-id="f09dc-138">Изучение порядка операций</span><span class="sxs-lookup"><span data-stu-id="f09dc-138">Explore order of operations</span></span>

<span data-ttu-id="f09dc-139">Закомментируйте вызов `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="f09dc-140">Это поможет упорядочить выходные данные в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="f09dc-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="f09dc-141">`//` запускает **комментарий** в C#.</span><span class="sxs-lookup"><span data-stu-id="f09dc-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="f09dc-142">Комментарии — это любой текст, который должен быть сохранен в исходном коде, но не должен выполняться как код.</span><span class="sxs-lookup"><span data-stu-id="f09dc-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="f09dc-143">Компилятор не создает исполняемый код из комментариев.</span><span class="sxs-lookup"><span data-stu-id="f09dc-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="f09dc-144">Язык C# определяет приоритет математических операций в соответствии с правилами математики.</span><span class="sxs-lookup"><span data-stu-id="f09dc-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="f09dc-145">Умножение и деление имеют приоритет над сложением и вычитанием.</span><span class="sxs-lookup"><span data-stu-id="f09dc-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="f09dc-146">Чтобы удостовериться в этом, добавьте следующий код в метод `Main` и выполните команду `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="f09dc-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="f09dc-147">В выходных данных видно, что умножение выполняется раньше сложения.</span><span class="sxs-lookup"><span data-stu-id="f09dc-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="f09dc-148">Можно применить другую последовательность операций. Для этого операции, которые должны выполняться первыми, нужно заключить в скобки.</span><span class="sxs-lookup"><span data-stu-id="f09dc-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="f09dc-149">Добавьте приведенные ниже строки и выполните код еще раз.</span><span class="sxs-lookup"><span data-stu-id="f09dc-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="f09dc-150">Поэкспериментируйте, объединяя различные операции.</span><span class="sxs-lookup"><span data-stu-id="f09dc-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="f09dc-151">Добавьте в конец метода `Main` строки, подобные приведенным ниже.</span><span class="sxs-lookup"><span data-stu-id="f09dc-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="f09dc-152">Выполните `dotnet run` еще раз.</span><span class="sxs-lookup"><span data-stu-id="f09dc-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="f09dc-153">Возможно, вы заметили интересное поведение целых чисел.</span><span class="sxs-lookup"><span data-stu-id="f09dc-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="f09dc-154">Деление целых чисел всегда дает результат в виде целого числа, даже если ожидаемый результат содержит десятичную или дробную часть.</span><span class="sxs-lookup"><span data-stu-id="f09dc-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="f09dc-155">Если вы еще не видели пример такого поведения, добавьте следующий код в конец метода `Main`:</span><span class="sxs-lookup"><span data-stu-id="f09dc-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="f09dc-156">Выполните `dotnet run` еще раз, чтобы просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="f09dc-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="f09dc-157">Прежде чем продолжить, давайте поместив весь код, который вы написали в этом разделе, в новый метод.</span><span class="sxs-lookup"><span data-stu-id="f09dc-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="f09dc-158">Вызовите этот новый метод `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="f09dc-159">Результат должен выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="f09dc-159">You should end up with something like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="f09dc-160">Изучение точности и ограничений для целых чисел</span><span class="sxs-lookup"><span data-stu-id="f09dc-160">Explore integer precision and limits</span></span>

<span data-ttu-id="f09dc-161">В последнем примере вы увидели, что при делении целых чисел результат усекается.</span><span class="sxs-lookup"><span data-stu-id="f09dc-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="f09dc-162">Вы можете получить **остаток** с помощью оператора **остатка от деления**, который обозначается символом `%`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="f09dc-163">Попробуйте добавить приведенный ниже код в метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="f09dc-164">Тип целых чисел C# характеризуется еще одним отличием от математических целых: тип `int` имеет минимальные и максимальные ограничения.</span><span class="sxs-lookup"><span data-stu-id="f09dc-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="f09dc-165">Добавьте следующий код в метод `Main`, чтобы просмотреть эти ограничения:</span><span class="sxs-lookup"><span data-stu-id="f09dc-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="f09dc-166">Если при вычислении выводится значение вне этих пределов, возникает условие **потери значимости** или **переполнения**.</span><span class="sxs-lookup"><span data-stu-id="f09dc-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="f09dc-167">Ответ должен находиться в диапазоне от минимального до максимального значения.</span><span class="sxs-lookup"><span data-stu-id="f09dc-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="f09dc-168">Добавьте следующие две строки в метод `Main`, чтобы увидеть пример:</span><span class="sxs-lookup"><span data-stu-id="f09dc-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="f09dc-169">Обратите внимание, что ответ очень близок к минимальному целому числу (отрицательное значение).</span><span class="sxs-lookup"><span data-stu-id="f09dc-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="f09dc-170">Он совпадает со значением `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="f09dc-171">Оператор сложения **вызвал переполнение** допустимых значений для целых чисел.</span><span class="sxs-lookup"><span data-stu-id="f09dc-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="f09dc-172">Ответ является очень большим отрицательным числом, так как переполнение покрывает диапазон от наибольшего целого числа до наименьшего.</span><span class="sxs-lookup"><span data-stu-id="f09dc-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="f09dc-173">Существуют другие числовые типы с различными ограничениями и точностью, которые можно использовать, если тип `int` не соответствует вашим требованиям.</span><span class="sxs-lookup"><span data-stu-id="f09dc-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="f09dc-174">Рассмотрим их.</span><span class="sxs-lookup"><span data-stu-id="f09dc-174">Let's explore those next.</span></span>

<span data-ttu-id="f09dc-175">Давайте еще раз переместим код, написанный в этом разделе, в отдельный метод.</span><span class="sxs-lookup"><span data-stu-id="f09dc-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="f09dc-176">Присвойте обработчику события имя `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="f09dc-177">Работа с типом double</span><span class="sxs-lookup"><span data-stu-id="f09dc-177">Work with the double type</span></span>

<span data-ttu-id="f09dc-178">Числовой тип `double` представляет число с плавающей запятой двойной точности.</span><span class="sxs-lookup"><span data-stu-id="f09dc-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="f09dc-179">Эти термины могут быть новыми для вас.</span><span class="sxs-lookup"><span data-stu-id="f09dc-179">Those terms may be new to you.</span></span> <span data-ttu-id="f09dc-180">Число **с плавающей запятой** можно использовать для представления нецелых чисел, которые могут быть очень большими или малыми.</span><span class="sxs-lookup"><span data-stu-id="f09dc-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="f09dc-181">**Двойная точность** означает, что для хранения этих чисел используется большая точность, чем **одиночная**.</span><span class="sxs-lookup"><span data-stu-id="f09dc-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="f09dc-182">На современных компьютерах числа с двойной точностью используется чаще, чем с одиночной.</span><span class="sxs-lookup"><span data-stu-id="f09dc-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="f09dc-183">Рассмотрим их.</span><span class="sxs-lookup"><span data-stu-id="f09dc-183">Let's explore.</span></span> <span data-ttu-id="f09dc-184">Добавьте следующий код и просмотрите результат:</span><span class="sxs-lookup"><span data-stu-id="f09dc-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="f09dc-185">Обратите внимание, что ответ включает десятичную долю частного.</span><span class="sxs-lookup"><span data-stu-id="f09dc-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="f09dc-186">Попробуйте более сложное выражение с типом double:</span><span class="sxs-lookup"><span data-stu-id="f09dc-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="f09dc-187">Диапазон значений типа double гораздо больше, чем диапазон значений целых чисел.</span><span class="sxs-lookup"><span data-stu-id="f09dc-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="f09dc-188">Добавьте следующий фрагмент после написанного кода:</span><span class="sxs-lookup"><span data-stu-id="f09dc-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="f09dc-189">Значения выводятся в экспоненциальном представлении.</span><span class="sxs-lookup"><span data-stu-id="f09dc-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="f09dc-190">Число слева от символа `E` является значащим.</span><span class="sxs-lookup"><span data-stu-id="f09dc-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="f09dc-191">Число справа — это показатель степени, который равен 10.</span><span class="sxs-lookup"><span data-stu-id="f09dc-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="f09dc-192">Так же, как десятичные числа в математике, значения double в C# могут содержать ошибки округления.</span><span class="sxs-lookup"><span data-stu-id="f09dc-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="f09dc-193">Выполните этот код:</span><span class="sxs-lookup"><span data-stu-id="f09dc-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="f09dc-194">Вы знаете, что периодическая десятичная дробь `0.3` не равняется `1/3`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="f09dc-195">***Задача***</span><span class="sxs-lookup"><span data-stu-id="f09dc-195">***Challenge***</span></span>

<span data-ttu-id="f09dc-196">Выполните другие вычисления с большими числами, малыми числами, умножением и делением с помощью типа `double`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="f09dc-197">Попробуйте выполнить более сложные вычисления.</span><span class="sxs-lookup"><span data-stu-id="f09dc-197">Try more complicated calculations.</span></span>

<span data-ttu-id="f09dc-198">После того как вы решите сложную задачу, поместите написанный код в новый метод.</span><span class="sxs-lookup"><span data-stu-id="f09dc-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="f09dc-199">Присвойте этому методу имя `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="f09dc-200">Работа с типами с фиксированной запятой</span><span class="sxs-lookup"><span data-stu-id="f09dc-200">Work with fixed point types</span></span>

<span data-ttu-id="f09dc-201">Вы уже ознакомились с базовыми числовыми типами в C# — целыми числами и числами типа double.</span><span class="sxs-lookup"><span data-stu-id="f09dc-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="f09dc-202">Осталось изучить еще один тип: `decimal`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="f09dc-203">Тип `decimal` имеет меньший диапазон, но большую точность, чем `double`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="f09dc-204">Термин **фиксированная запятая** означает, что десятичный (или двоичный) разделитель не перемещается.</span><span class="sxs-lookup"><span data-stu-id="f09dc-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="f09dc-205">Например:</span><span class="sxs-lookup"><span data-stu-id="f09dc-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="f09dc-206">Обратите внимание, что диапазон меньше, чем для типа `double`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="f09dc-207">Вы можете убедиться в повышении точности при использовании типа decimal, выполнив следующий код:</span><span class="sxs-lookup"><span data-stu-id="f09dc-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="f09dc-208">Суффикс `M` возле чисел указывает, что для константы должен использоваться тип `decimal`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="f09dc-209">Обратите внимание, что при вычислении с использованием типа decimal справа от запятой содержится больше цифр.</span><span class="sxs-lookup"><span data-stu-id="f09dc-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="f09dc-210">***Задача***</span><span class="sxs-lookup"><span data-stu-id="f09dc-210">***Challenge***</span></span>

<span data-ttu-id="f09dc-211">Теперь, когда вы ознакомились с разными числовыми типами, напишите код, который позволяет вычислить площадь круга с радиусом 2,50 см.</span><span class="sxs-lookup"><span data-stu-id="f09dc-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="f09dc-212">Помните, что площадь круга равна квадрату радиуса, умноженному на число пи.</span><span class="sxs-lookup"><span data-stu-id="f09dc-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="f09dc-213">Подсказка: в .NET есть константа пи <xref:System.Math.PI?displayProperty=nameWithType>, которую можно использовать.</span><span class="sxs-lookup"><span data-stu-id="f09dc-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="f09dc-214">Вы должны получить ответ от 19 до 20.</span><span class="sxs-lookup"><span data-stu-id="f09dc-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="f09dc-215">Ответ можно [просмотреть в готовом примере кода в GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span><span class="sxs-lookup"><span data-stu-id="f09dc-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="f09dc-216">При желании поэкспериментируйте с другими формулами.</span><span class="sxs-lookup"><span data-stu-id="f09dc-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="f09dc-217">Вы выполнили все задачи краткого руководства по числам в C#.</span><span class="sxs-lookup"><span data-stu-id="f09dc-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="f09dc-218">Теперь вы можете выполнить руководство по [ветвям и циклам](branches-and-loops-local.md) в своей среде разработки.</span><span class="sxs-lookup"><span data-stu-id="f09dc-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="f09dc-219">Дополнительные сведения о числах в C# см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="f09dc-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="f09dc-220">Целочисленные типы</span><span class="sxs-lookup"><span data-stu-id="f09dc-220">Integral types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="f09dc-221">Таблица типов с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="f09dc-221">Floating-Point Types Table</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="f09dc-222">Таблица встроенных типов</span><span class="sxs-lookup"><span data-stu-id="f09dc-222">Built-In Types Table</span></span>](../../language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="f09dc-223">Таблица неявных числовых преобразований</span><span class="sxs-lookup"><span data-stu-id="f09dc-223">Implicit Numeric Conversions Table</span></span>](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="f09dc-224">Таблица явных числовых преобразований</span><span class="sxs-lookup"><span data-stu-id="f09dc-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)
