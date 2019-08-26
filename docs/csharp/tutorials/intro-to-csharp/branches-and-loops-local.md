---
title: Ветви и циклы. Вводное руководство по C#
description: В рамках этого руководства, посвященного ветвям и циклам, вы создадите пример кода на C#, который демонстрирует возможности языка для организации условного ветвления и циклического выполнения операторов.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 0da446a71f5d7a7183a8323c470087c8726bc02f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587224"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="a75e4-103">Изучение условной логики с операторами ветви и цикла</span><span class="sxs-lookup"><span data-stu-id="a75e4-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="a75e4-104">В этом руководстве объясняется, как написать код, который позволяет проверить переменные и изменить путь выполнения на основе этих переменных.</span><span class="sxs-lookup"><span data-stu-id="a75e4-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="a75e4-105">Вы напишете код C# и сможете просмотреть результаты его компиляции и выполнения.</span><span class="sxs-lookup"><span data-stu-id="a75e4-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="a75e4-106">Это руководство содержит ряд уроков, в которых рассматриваются конструкции ветвления и циклов в C#.</span><span class="sxs-lookup"><span data-stu-id="a75e4-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="a75e4-107">В рамках этих занятий вы ознакомитесь с основами языка C#.</span><span class="sxs-lookup"><span data-stu-id="a75e4-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="a75e4-108">Для работы с этим руководством вам потребуется компьютер, который можно использовать для разработки.</span><span class="sxs-lookup"><span data-stu-id="a75e4-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="a75e4-109">В руководстве по [началу работы с .NET за 10 минут](https://www.microsoft.com/net/core) содержатся инструкции по настройке локальной среды разработки на компьютерах Mac, Windows или Linux.</span><span class="sxs-lookup"><span data-stu-id="a75e4-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="a75e4-110">Краткий обзор команд, которые будут здесь использоваться, и ссылки на дополнительные сведения представлены в статье, посвященной [средствам разработки для .NET](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="a75e4-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="a75e4-111">Принятие решений с помощью оператора `if`</span><span class="sxs-lookup"><span data-stu-id="a75e4-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="a75e4-112">Создайте каталог с именем **branches-tutorial**.</span><span class="sxs-lookup"><span data-stu-id="a75e4-112">Create a directory named **branches-tutorial**.</span></span> <span data-ttu-id="a75e4-113">Откройте этот каталог и выполните команду `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-113">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="a75e4-114">Эта команда создает консольное приложение .NET Core в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="a75e4-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="a75e4-115">Откройте файл **Program.cs** в любом редакторе и замените строку `Console.WriteLine("Hello World!");` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="a75e4-115">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="a75e4-116">Чтобы выполнить этот код, введите `dotnet run` в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="a75e4-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="a75e4-117">В консоли должно появиться сообщение The answer is greater than 10</span><span class="sxs-lookup"><span data-stu-id="a75e4-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="a75e4-118">(Ответ больше 10).</span><span class="sxs-lookup"><span data-stu-id="a75e4-118">printed to your console.</span></span>

<span data-ttu-id="a75e4-119">Измените объявление `b`, чтобы сумма была меньше 10:</span><span class="sxs-lookup"><span data-stu-id="a75e4-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="a75e4-120">Введите `dotnet run` еще раз.</span><span class="sxs-lookup"><span data-stu-id="a75e4-120">Type `dotnet run` again.</span></span> <span data-ttu-id="a75e4-121">Так как ответ меньше 10, никакие данные не выводятся.</span><span class="sxs-lookup"><span data-stu-id="a75e4-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="a75e4-122">Проверяемое **условие** имеет значение false.</span><span class="sxs-lookup"><span data-stu-id="a75e4-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="a75e4-123">У вас еще нет кода для выполнения, так как вы написали только одну из возможных ветвей для оператора `if` — ветвь true.</span><span class="sxs-lookup"><span data-stu-id="a75e4-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="a75e4-124">Вероятнее всего, при изучении C# (как и любого другого языка программирования) вы будете допускать ошибки в коде.</span><span class="sxs-lookup"><span data-stu-id="a75e4-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="a75e4-125">Компилятор найдет ошибки и сообщит о них.</span><span class="sxs-lookup"><span data-stu-id="a75e4-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="a75e4-126">Внимательно просмотрите выходные данные ошибки и код, вызвавший ошибку.</span><span class="sxs-lookup"><span data-stu-id="a75e4-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="a75e4-127">Как правило, сведения о причине ошибки можно найти в сообщении об ошибке компилятора.</span><span class="sxs-lookup"><span data-stu-id="a75e4-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="a75e4-128">В первом примере показаны возможности `if` и логические типы.</span><span class="sxs-lookup"><span data-stu-id="a75e4-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="a75e4-129">*Логическое значение* — это переменная, которая может иметь одно из двух значений: `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="a75e4-130">Логические переменные в C# определяются особым типом — `bool`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="a75e4-131">Оператор `if` проверяет значение `bool`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="a75e4-132">Если значение `true`, выполняется оператор, следующий после `if`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="a75e4-133">В противном случае он пропускается.</span><span class="sxs-lookup"><span data-stu-id="a75e4-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="a75e4-134">Этот процесс проверки условий и выполнения операторов на основе этих условий предоставляет широкие возможности.</span><span class="sxs-lookup"><span data-stu-id="a75e4-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="a75e4-135">Объединение операторов if и else</span><span class="sxs-lookup"><span data-stu-id="a75e4-135">Make if and else work together</span></span>

<span data-ttu-id="a75e4-136">Чтобы выполнить разный код в ветвях true и false, создайте ветвь `else`, которая будет выполняться, если условие имеет значение false.</span><span class="sxs-lookup"><span data-stu-id="a75e4-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="a75e4-137">Попробуйте сделать следующее.</span><span class="sxs-lookup"><span data-stu-id="a75e4-137">Try this.</span></span> <span data-ttu-id="a75e4-138">Добавьте две последние строки из приведенного ниже кода в метод `Main` (первые четыре должны быть уже добавлены):</span><span class="sxs-lookup"><span data-stu-id="a75e4-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="a75e4-139">Оператор после ключевого слова `else` выполняется, только если проверяемое условие имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="a75e4-140">Объединив операторы `if` и `else` с логическими условиями, вы получите все необходимые возможности для обработки условий `true` и `false`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a75e4-141">Отступы под операторами `if` и `else` предназначены только для удобства чтения.</span><span class="sxs-lookup"><span data-stu-id="a75e4-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="a75e4-142">В языке C# необязательно ставить отступы или пробелы.</span><span class="sxs-lookup"><span data-stu-id="a75e4-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="a75e4-143">Операторы после ключевого слова `if` или `else` будут выполняться на основе условия.</span><span class="sxs-lookup"><span data-stu-id="a75e4-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="a75e4-144">Во всех строках в примерах кода, представленных в этом руководстве, отступы традиционно соответствуют потоку управления операторов.</span><span class="sxs-lookup"><span data-stu-id="a75e4-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="a75e4-145">Так как отступ не обязателен, используйте скобки `{` и `}`, если нужно указать несколько операторов в блоке кода, который выполняется в зависимости от условий.</span><span class="sxs-lookup"><span data-stu-id="a75e4-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="a75e4-146">Программисты C# обычно используют эти фигурные скобки во всех предложениях `if` и `else`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="a75e4-147">Следующий пример аналогичен только что созданному.</span><span class="sxs-lookup"><span data-stu-id="a75e4-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="a75e4-148">Измените код выше, чтобы он соответствовал следующему коду:</span><span class="sxs-lookup"><span data-stu-id="a75e4-148">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="a75e4-149">Все примеры кода в следующих разделах руководства содержат фигурные скобки в соответствии с принятой практикой.</span><span class="sxs-lookup"><span data-stu-id="a75e4-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="a75e4-150">Можно проверить более сложные условия.</span><span class="sxs-lookup"><span data-stu-id="a75e4-150">You can test more complicated conditions.</span></span> <span data-ttu-id="a75e4-151">Добавьте следующий код в метод `Main` после написанного кода:</span><span class="sxs-lookup"><span data-stu-id="a75e4-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

<span data-ttu-id="a75e4-152">Символ `==` позволяет проверить *равенство*.</span><span class="sxs-lookup"><span data-stu-id="a75e4-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="a75e4-153">С помощью `==` обозначается отличие проверки равенства от назначения, которое показано в `a = 5`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="a75e4-154">`&&` представляет оператор and.</span><span class="sxs-lookup"><span data-stu-id="a75e4-154">The `&&` represents "and".</span></span> <span data-ttu-id="a75e4-155">То есть для выполнения оператора в ветви true оба условия должны иметь значение true.</span><span class="sxs-lookup"><span data-stu-id="a75e4-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="a75e4-156">В этих примерах также показано, что в каждой условной ветви можно задать несколько операторов. Нужно лишь заключить их в скобки `{` и `}`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="a75e4-157">Вы также можете использовать оператор `||`, который представляет оператор or.</span><span class="sxs-lookup"><span data-stu-id="a75e4-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="a75e4-158">Добавьте следующий фрагмент после написанного кода:</span><span class="sxs-lookup"><span data-stu-id="a75e4-158">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

<span data-ttu-id="a75e4-159">Измените значения `a`, `b` и `c`, а также переключитесь между `&&` и `||` для изучения.</span><span class="sxs-lookup"><span data-stu-id="a75e4-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="a75e4-160">Так вы лучше поймете, как работают операторы `&&` и `||`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="a75e4-161">Вы завершили первый этап.</span><span class="sxs-lookup"><span data-stu-id="a75e4-161">You've finished the first step.</span></span> <span data-ttu-id="a75e4-162">Прежде чем перейти к следующему разделу, переместим текущий код в отдельный метод.</span><span class="sxs-lookup"><span data-stu-id="a75e4-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="a75e4-163">Это упростит начало работы с новым примером.</span><span class="sxs-lookup"><span data-stu-id="a75e4-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="a75e4-164">Переименуйте метод `Main` в `ExploreIf` и запишите новый метод `Main`, который вызывает `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="a75e4-165">В результате ваш код должен выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a75e4-165">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            int c = 4;
            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

<span data-ttu-id="a75e4-166">Закомментируйте вызов `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="a75e4-167">Это поможет упорядочить выходные данные в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="a75e4-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="a75e4-168">`//` запускает **комментарий** в C#.</span><span class="sxs-lookup"><span data-stu-id="a75e4-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="a75e4-169">Комментарии — это любой текст, который должен быть сохранен в исходном коде, но не должен выполняться как код.</span><span class="sxs-lookup"><span data-stu-id="a75e4-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="a75e4-170">Компилятор не создает исполняемый код из комментариев.</span><span class="sxs-lookup"><span data-stu-id="a75e4-170">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="a75e4-171">Использование циклов для повторения операций</span><span class="sxs-lookup"><span data-stu-id="a75e4-171">Use loops to repeat operations</span></span>

<span data-ttu-id="a75e4-172">В этом разделе **циклы** используются для повторения операторов.</span><span class="sxs-lookup"><span data-stu-id="a75e4-172">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="a75e4-173">Выполните в методе `Main` следующий код:</span><span class="sxs-lookup"><span data-stu-id="a75e4-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="a75e4-174">Оператор `while` проверяет условие и выполняет инструкцию или блок инструкций, следующий после `while`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="a75e4-175">Проверка условия и выполнение этих операторов будут повторяться, пока условие не примет значение false.</span><span class="sxs-lookup"><span data-stu-id="a75e4-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="a75e4-176">В этом примере представлен еще один новый оператор.</span><span class="sxs-lookup"><span data-stu-id="a75e4-176">There's one other new operator in this example.</span></span> <span data-ttu-id="a75e4-177">Объект `++` после переменной `counter` представляет собой оператор **инкремента**.</span><span class="sxs-lookup"><span data-stu-id="a75e4-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="a75e4-178">Он добавляет 1 к значению `counter` и сохраняет это значение в переменной `counter`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a75e4-179">Напишите такой код, при выполнении которого значение условия цикла `while` изменится на false.</span><span class="sxs-lookup"><span data-stu-id="a75e4-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="a75e4-180">В противном случае будет создан **бесконечный цикл**, в котором выполнение программы никогда не закончится.</span><span class="sxs-lookup"><span data-stu-id="a75e4-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="a75e4-181">Это не показано в примере, так как нужно принудительно закрыть программу, нажав клавиши **CTRL+C**, или другим способом.</span><span class="sxs-lookup"><span data-stu-id="a75e4-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="a75e4-182">В цикле `while` условие проверяется, прежде чем выполнить код, который следует после `while`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="a75e4-183">А в цикле `do` ... `while` сначала выполняется код, а потом проверяется условие.</span><span class="sxs-lookup"><span data-stu-id="a75e4-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="a75e4-184">Действие во время цикла показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="a75e4-184">The do while loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="a75e4-185">Этот цикл `do` и цикл `while`, приведенный выше, выводят одинаковый результат.</span><span class="sxs-lookup"><span data-stu-id="a75e4-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="a75e4-186">Работа с циклом for</span><span class="sxs-lookup"><span data-stu-id="a75e4-186">Work with the for loop</span></span>

<span data-ttu-id="a75e4-187">Цикл **for** широко используется в C#.</span><span class="sxs-lookup"><span data-stu-id="a75e4-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="a75e4-188">Выполните в методе Main() следующий код:</span><span class="sxs-lookup"><span data-stu-id="a75e4-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="a75e4-189">Этот цикл работает так же, как циклы `while` и `do`, использованные ранее.</span><span class="sxs-lookup"><span data-stu-id="a75e4-189">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="a75e4-190">Оператор `for` состоит из трех частей, которые отвечают за его работу.</span><span class="sxs-lookup"><span data-stu-id="a75e4-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="a75e4-191">Первая часть — **для инициализатора**: `int index = 0;` объявляет `index` переменной цикла и задает для ее начальное значение `0`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="a75e4-192">Средняя часть — **для условия**: `index < 10` объявляет, что этот цикл `for` продолжает выполняться, пока значение счетчика меньше 10.</span><span class="sxs-lookup"><span data-stu-id="a75e4-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="a75e4-193">Последняя часть — **для итератора**: `index++` определяет, как изменится переменная цикла после выполнения блока, следующего после оператора `for`.</span><span class="sxs-lookup"><span data-stu-id="a75e4-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="a75e4-194">В нашем случае определяется, что значение `index` должно увеличиваться на 1 каждый раз, когда выполняется блок.</span><span class="sxs-lookup"><span data-stu-id="a75e4-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="a75e4-195">Попробуйте сделать это самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="a75e4-195">Experiment with these yourself.</span></span> <span data-ttu-id="a75e4-196">Попытайтесь выполнить следующие задания:</span><span class="sxs-lookup"><span data-stu-id="a75e4-196">Try each of the following:</span></span>

- <span data-ttu-id="a75e4-197">Измените инициализатор, чтобы цикл начинался с другого значения.</span><span class="sxs-lookup"><span data-stu-id="a75e4-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="a75e4-198">Измените условие, чтобы цикл заканчивался другим значением.</span><span class="sxs-lookup"><span data-stu-id="a75e4-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="a75e4-199">По окончании попробуйте самостоятельно написать код, чтобы применить полученные знания.</span><span class="sxs-lookup"><span data-stu-id="a75e4-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="a75e4-200">Объединение ветвей и циклов</span><span class="sxs-lookup"><span data-stu-id="a75e4-200">Combine branches and loops</span></span>

<span data-ttu-id="a75e4-201">Теперь, когда вы ознакомились с оператором `if` и конструкциями цикла на языке C#, попытайтесь написать код C# для поиска суммы всех целых чисел от 1 до 20, которые делятся на 3.</span><span class="sxs-lookup"><span data-stu-id="a75e4-201">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="a75e4-202">Вот несколько подсказок:</span><span class="sxs-lookup"><span data-stu-id="a75e4-202">Here are a few hints:</span></span>

- <span data-ttu-id="a75e4-203">оператор `%` позволяет получить остаток от операции деления;</span><span class="sxs-lookup"><span data-stu-id="a75e4-203">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="a75e4-204">оператор `if` предоставляет условие, которое позволяет определить, будет ли число учитываться в сумме;</span><span class="sxs-lookup"><span data-stu-id="a75e4-204">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="a75e4-205">цикл `for` позволяет повторить последовательность шагов для всех чисел от 1 до 20.</span><span class="sxs-lookup"><span data-stu-id="a75e4-205">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="a75e4-206">Попробуйте самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="a75e4-206">Try it yourself.</span></span> <span data-ttu-id="a75e4-207">Затем проверьте результат.</span><span class="sxs-lookup"><span data-stu-id="a75e4-207">Then check how you did.</span></span> <span data-ttu-id="a75e4-208">Вы должны получить ответ "63".</span><span class="sxs-lookup"><span data-stu-id="a75e4-208">You should get 63 for an answer.</span></span> <span data-ttu-id="a75e4-209">Один из возможных ответов можно увидеть в [полном примере кода в GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="a75e4-209">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="a75e4-210">Вы ознакомились с руководством по ветвям и циклам.</span><span class="sxs-lookup"><span data-stu-id="a75e4-210">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="a75e4-211">Теперь вы можете перейти к ознакомлению с руководством [Массивы и коллекции](arrays-and-collections.md) в своей среде разработки.</span><span class="sxs-lookup"><span data-stu-id="a75e4-211">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="a75e4-212">Дополнительные сведения об этих понятиях см. в следующих разделах:</span><span class="sxs-lookup"><span data-stu-id="a75e4-212">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="a75e4-213">if-else (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="a75e4-213">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="a75e4-214">while (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="a75e4-214">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="a75e4-215">do (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="a75e4-215">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="a75e4-216">for (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="a75e4-216">For statement</span></span>](../../language-reference/keywords/for.md)
