---
title: Возвращаемые ссылочные значения и ссылочные локальные переменные (руководство по языку C#)
description: Сведения о том, как определять и использовать возвращаемые ссылочные значения и ссылочные локальные переменные
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: e23007deffea0f542d623be918cd1c61496d1362
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353882"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="c3a55-103">Возвращаемые ссылочные значения и ссылочные локальные переменные</span><span class="sxs-lookup"><span data-stu-id="c3a55-103">Ref returns and ref locals</span></span>

<span data-ttu-id="c3a55-104">Начиная с версии 7.0 язык C# поддерживает значения, возвращаемые по ссылке (возвращаемые ссылочные значения).</span><span class="sxs-lookup"><span data-stu-id="c3a55-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="c3a55-105">Возвращаемое ссылочное значение позволяет методу вернуть вызывающей стороне ссылку на переменную, а не фиксированное значение.</span><span class="sxs-lookup"><span data-stu-id="c3a55-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="c3a55-106">После этого вызывающий может самостоятельно решить, как обрабатывать полученную переменную: по значению или по ссылке.</span><span class="sxs-lookup"><span data-stu-id="c3a55-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="c3a55-107">Вызывающий может создать новую переменную и присвоить ей ссылку на полученное значение (локальная ссылочная переменная).</span><span class="sxs-lookup"><span data-stu-id="c3a55-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="c3a55-108">Что представляет собой возвращаемое ссылочное значение?</span><span class="sxs-lookup"><span data-stu-id="c3a55-108">What is a reference return value?</span></span>

<span data-ttu-id="c3a55-109">Большинство разработчиков прекрасно знакомы с передачей аргумента в вызываемый метод *по ссылке*.</span><span class="sxs-lookup"><span data-stu-id="c3a55-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="c3a55-110">Список аргументов вызываемого метода включает переменную, переданную по ссылке.</span><span class="sxs-lookup"><span data-stu-id="c3a55-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="c3a55-111">Вызывающий может отследить любые изменения этого значения в вызываемом методе.</span><span class="sxs-lookup"><span data-stu-id="c3a55-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="c3a55-112">*Возвращаемое ссылочное значение* означает, что метод возвращает *ссылку* на некоторую переменную (или ее псевдоним).</span><span class="sxs-lookup"><span data-stu-id="c3a55-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="c3a55-113">В область действия переменной должен входить этот метод.</span><span class="sxs-lookup"><span data-stu-id="c3a55-113">That variable's scope must include the method.</span></span> <span data-ttu-id="c3a55-114">Время существования переменной должно продолжаться после того, как метод возвращает управление.</span><span class="sxs-lookup"><span data-stu-id="c3a55-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="c3a55-115">Все изменения, которые вызывающий производит с возвращаемым значением метода, применяются к возвращенной переменной.</span><span class="sxs-lookup"><span data-stu-id="c3a55-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="c3a55-116">Если для метода объявлено *возвращаемое ссылочное значение*, значит он возвращает псевдоним переменной.</span><span class="sxs-lookup"><span data-stu-id="c3a55-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="c3a55-117">Чаще всего это нужно для того, чтобы вызывающий код получил псевдоним для доступа к этой переменной, в том числе для ее изменения.</span><span class="sxs-lookup"><span data-stu-id="c3a55-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="c3a55-118">Следовательно, методы с возвращаемыми ссылочными значениями не могут иметь тип возвращаемого значения `void`.</span><span class="sxs-lookup"><span data-stu-id="c3a55-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="c3a55-119">Есть несколько ограничений для выражений, которые можно использовать в качестве возвращаемых ссылочных значений метода.</span><span class="sxs-lookup"><span data-stu-id="c3a55-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="c3a55-120">К ним относятся указанные ниже ограничения.</span><span class="sxs-lookup"><span data-stu-id="c3a55-120">Restrictions include:</span></span>

- <span data-ttu-id="c3a55-121">Время существования возвращаемого значения должно превышать период выполнения метода.</span><span class="sxs-lookup"><span data-stu-id="c3a55-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="c3a55-122">Другими словами, нельзя возвращать ссылку на локальную переменную вызываемого метода.</span><span class="sxs-lookup"><span data-stu-id="c3a55-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="c3a55-123">Это может быть экземпляр статического поля или класса, а также переданный в метод аргумент.</span><span class="sxs-lookup"><span data-stu-id="c3a55-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="c3a55-124">При попытке возвратить локальную переменную возникает ошибка компилятора CS8168 "Невозможно вернуть по ссылке локальный "obj", так как это не локальная переменная ref".</span><span class="sxs-lookup"><span data-stu-id="c3a55-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="c3a55-125">Возвращаемое значение не может быть литералом `null`.</span><span class="sxs-lookup"><span data-stu-id="c3a55-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="c3a55-126">При возврате `null` возникает ошибка компилятора CS8156 "Выражение невозможно использовать в данном контексте, так как его невозможно вернуть по ссылке".</span><span class="sxs-lookup"><span data-stu-id="c3a55-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="c3a55-127">Метод с возвращаемым ссылочным значением может возвращать псевдоним для переменной с текущим значением NULL (которой не присвоены экземпляры) или [тип, допускающий значение NULL](../nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="c3a55-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable value type](../nullable-types/index.md) for a value type.</span></span>

- <span data-ttu-id="c3a55-128">Возвращаемое значение не может быть константой, элементом перечисления, полученным по значению, возвращаемым значением свойства, а также методом `class` или `struct`.</span><span class="sxs-lookup"><span data-stu-id="c3a55-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="c3a55-129">При нарушении этого правила возникает ошибка компилятора CS8156 "Выражение невозможно использовать в данном контексте, так как его невозможно вернуть по ссылке".</span><span class="sxs-lookup"><span data-stu-id="c3a55-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="c3a55-130">Кроме того, возвращаемые ссылочные значения недопустимы в асинхронных методах.</span><span class="sxs-lookup"><span data-stu-id="c3a55-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="c3a55-131">Асинхронный метод может вернуть управление до того, как будет завершено его выполнение и станет известно его возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="c3a55-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>

## <a name="defining-a-ref-return-value"></a><span data-ttu-id="c3a55-132">Определение возвращаемого ссылочного значения</span><span class="sxs-lookup"><span data-stu-id="c3a55-132">Defining a ref return value</span></span>

<span data-ttu-id="c3a55-133">Метод, который возвращает *возвращаемое значение ссылки*, должен удовлетворять следующим двум условиям:</span><span class="sxs-lookup"><span data-stu-id="c3a55-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="c3a55-134">Сигнатура метода включает ключевое слово [ref](../../language-reference/keywords/ref.md) перед типом возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="c3a55-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="c3a55-135">Каждый оператор [return](../../language-reference/keywords/return.md) в теле метода включает ключевое слово [ref](../../language-reference/keywords/ref.md) перед именем возвращаемого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="c3a55-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="c3a55-136">В следующем примере показан метод, который удовлетворяет указанным условиям и возвращает ссылку на объект `Person` с именем `p`:</span><span class="sxs-lookup"><span data-stu-id="c3a55-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="c3a55-137">Использование возвращаемого ссылочного значения</span><span class="sxs-lookup"><span data-stu-id="c3a55-137">Consuming a ref return value</span></span>

<span data-ttu-id="c3a55-138">Возвращаемое ссылочное значение является псевдонимом для другой переменной в области вызываемого метода.</span><span class="sxs-lookup"><span data-stu-id="c3a55-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="c3a55-139">Любое применение возвращаемого ссылочного значения можно рассматривать как применение псевдонима соответствующей переменной.</span><span class="sxs-lookup"><span data-stu-id="c3a55-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="c3a55-140">Присваивая новое значение псевдониму, вы присваиваете это значение переменной, на которую он ссылается.</span><span class="sxs-lookup"><span data-stu-id="c3a55-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="c3a55-141">Считывая значение псевдонима, вы получаете значение переменной, на которую он ссылается.</span><span class="sxs-lookup"><span data-stu-id="c3a55-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="c3a55-142">Возвращая псевдоним *по ссылке*, вы возвращаете новый псевдоним для той же переменной.</span><span class="sxs-lookup"><span data-stu-id="c3a55-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="c3a55-143">Передавая псевдоним другому методу *по ссылке*, вы передаете ссылку на переменную, на которую ссылается псевдоним.</span><span class="sxs-lookup"><span data-stu-id="c3a55-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="c3a55-144">Создавая для псевдонима [локальную ссылочную переменную](#ref-locals), вы создаете новый псевдоним для той же переменной.</span><span class="sxs-lookup"><span data-stu-id="c3a55-144">When you make a [ref local](#ref-locals) alias, you make a new alias to the same variable.</span></span>

## <a name="ref-locals"></a><span data-ttu-id="c3a55-145">Ссылочные локальные переменные</span><span class="sxs-lookup"><span data-stu-id="c3a55-145">Ref locals</span></span>

<span data-ttu-id="c3a55-146">Предположим, что для метода `GetContactInformation` объявлено возвращаемое ссылочное значение:</span><span class="sxs-lookup"><span data-stu-id="c3a55-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="c3a55-147">При назначении по значению считывается значение переменной и присваивается это значение новой переменной:</span><span class="sxs-lookup"><span data-stu-id="c3a55-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="c3a55-148">В предыдущем назначении `p` объявлена как локальная переменная.</span><span class="sxs-lookup"><span data-stu-id="c3a55-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="c3a55-149">Исходное значение копируется из значения, которое возвращает `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="c3a55-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="c3a55-150">Все последующие назначения `p` не затронут значения переменной, которую возвращает `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="c3a55-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="c3a55-151">Переменная `p` теперь не является псевдонимом для возвращаемой переменной.</span><span class="sxs-lookup"><span data-stu-id="c3a55-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="c3a55-152">Вы объявляете *локальную ссылочную переменную* и сохраняете в ней псевдоним для исходного значения.</span><span class="sxs-lookup"><span data-stu-id="c3a55-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="c3a55-153">В следующем назначении `p` является псевдонимом для переменной, возвращаемой из `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="c3a55-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="c3a55-154">При дальнейшем применении `p` действует так же, как и возвращаемая из `GetContactInformation` переменная, так как `p` является псевдонимом для этой переменной.</span><span class="sxs-lookup"><span data-stu-id="c3a55-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="c3a55-155">Любые изменения `p` затрагивают и переменную, возвращаемую из `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="c3a55-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="c3a55-156">Ключевое слово `ref` используется перед объявлением локальной переменной *и* до вызова метода.</span><span class="sxs-lookup"><span data-stu-id="c3a55-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="c3a55-157">Вы можете таким же образом обратиться к значению по ссылке.</span><span class="sxs-lookup"><span data-stu-id="c3a55-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="c3a55-158">В некоторых случаях обращение к значению по ссылке повышает производительность, поскольку позволяет избежать потенциально затратной операции копирования.</span><span class="sxs-lookup"><span data-stu-id="c3a55-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="c3a55-159">Например, в следующей инструкции показано, как можно определить локальное ссылочное значение, используемое для ссылки на значение.</span><span class="sxs-lookup"><span data-stu-id="c3a55-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="c3a55-160">Ключевое слово `ref` используется перед объявлением локальной переменной *и* перед значением во втором примере.</span><span class="sxs-lookup"><span data-stu-id="c3a55-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="c3a55-161">Если не указать ключевые слова `ref` одновременно в объявлении и присвоении переменной в обоих примерах, возникает ошибка компилятора CS8172 "Невозможно инициализировать значением переменную по ссылке".</span><span class="sxs-lookup"><span data-stu-id="c3a55-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="c3a55-162">До версии C# 7.3 ссылочные локальные переменные нельзя было переназначить после инициализации так, чтобы они ссылались на другое хранилище.</span><span class="sxs-lookup"><span data-stu-id="c3a55-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="c3a55-163">Это ограничение было снято.</span><span class="sxs-lookup"><span data-stu-id="c3a55-163">That restriction has been removed.</span></span> <span data-ttu-id="c3a55-164">В следующем примере демонстрируется переназначение:</span><span class="sxs-lookup"><span data-stu-id="c3a55-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="c3a55-165">Ссылочные локальные переменные по-прежнему необходимо инициализировать во время объявления.</span><span class="sxs-lookup"><span data-stu-id="c3a55-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="c3a55-166">Пример использования возвращаемых ссылочных значений и ссылочных локальных переменных</span><span class="sxs-lookup"><span data-stu-id="c3a55-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="c3a55-167">В следующем примере определяется класс `NumberStore`, в котором хранится массив целочисленных значений.</span><span class="sxs-lookup"><span data-stu-id="c3a55-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="c3a55-168">Метод `FindNumber` возвращает по ссылке первое число, которое не меньше переданного в аргументе значения.</span><span class="sxs-lookup"><span data-stu-id="c3a55-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="c3a55-169">Если такое число не найдено, метод возвращает число с индексом 0.</span><span class="sxs-lookup"><span data-stu-id="c3a55-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="c3a55-170">В следующем примере вызывается метод `NumberStore.FindNumber`, который извлекает первое значение не меньше 16.</span><span class="sxs-lookup"><span data-stu-id="c3a55-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="c3a55-171">После этого вызывающий объект удваивает значение, возвращаемое методом.</span><span class="sxs-lookup"><span data-stu-id="c3a55-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="c3a55-172">Как видно из выходных данных этого примера, изменение отражается в значении элементов массива в экземпляре `NumberStore`.</span><span class="sxs-lookup"><span data-stu-id="c3a55-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="c3a55-173">Без использования возвращаемых ссылочных значений такая операция выполняется путем возврата индекса элемента массива вместе с его значением.</span><span class="sxs-lookup"><span data-stu-id="c3a55-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="c3a55-174">После этого вызывающий объект использует индекс для изменения значения в отдельном вызове метода.</span><span class="sxs-lookup"><span data-stu-id="c3a55-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="c3a55-175">Тем не менее вызывающий объект также может изменить индекс для доступа к другим значениям массива и их изменения.</span><span class="sxs-lookup"><span data-stu-id="c3a55-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="c3a55-176">В следующем примере показано, как можно изменить метод `FindNumber` в версии C# 7.3 или более поздней, чтобы использовать переназначение ссылочной локальной переменной:</span><span class="sxs-lookup"><span data-stu-id="c3a55-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="c3a55-177">Вторая версия более эффективна в случаях, когда искомое число находится ближе к концу большого массива.</span><span class="sxs-lookup"><span data-stu-id="c3a55-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3a55-178">См. также</span><span class="sxs-lookup"><span data-stu-id="c3a55-178">See also</span></span>

- [<span data-ttu-id="c3a55-179">Ключевое слово ref</span><span class="sxs-lookup"><span data-stu-id="c3a55-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="c3a55-180">Написание безопасного и эффективного кода</span><span class="sxs-lookup"><span data-stu-id="c3a55-180">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
