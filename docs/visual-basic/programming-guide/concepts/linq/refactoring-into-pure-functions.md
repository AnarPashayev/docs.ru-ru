---
title: Рефакторинг в чистые функции
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 415b088661eca347330f4776901d68ee514d8dad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413483"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="8d66b-102">Рефакторинг в чистые функции (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d66b-102">Refactoring Into Pure Functions (Visual Basic)</span></span>

<span data-ttu-id="8d66b-103">Важным аспектом чисто функциональных преобразований является освоение способов оптимизации существующего кода для получения чистых функций.</span><span class="sxs-lookup"><span data-stu-id="8d66b-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

<span data-ttu-id="8d66b-104">Как отмечалось ранее в этом разделе, чистые функции имеют две полезные характеристики.</span><span class="sxs-lookup"><span data-stu-id="8d66b-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="8d66b-105">У них отсутствуют побочные эффекты.</span><span class="sxs-lookup"><span data-stu-id="8d66b-105">It has no side effects.</span></span> <span data-ttu-id="8d66b-106">Функции не изменяют значения или данные любого типа, не входящие в область их определения.</span><span class="sxs-lookup"><span data-stu-id="8d66b-106">The function does not change any variables or the data of any type outside of the function.</span></span>

- <span data-ttu-id="8d66b-107">Функции действуют единообразно.</span><span class="sxs-lookup"><span data-stu-id="8d66b-107">It is consistent.</span></span> <span data-ttu-id="8d66b-108">После получения того же набора входных данных они всегда возвращают одно и то же выходное значение.</span><span class="sxs-lookup"><span data-stu-id="8d66b-108">Given the same set of input data, it will always return the same output value.</span></span>

 <span data-ttu-id="8d66b-109">Одним из способов перехода к функциональному программированию является оптимизация существующего кода с целью устранения ненужных побочных эффектов и внешних зависимостей.</span><span class="sxs-lookup"><span data-stu-id="8d66b-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="8d66b-110">Таким образом, из существующего кода создаются чистые функции.</span><span class="sxs-lookup"><span data-stu-id="8d66b-110">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="8d66b-111">В этом разделе объясняется, что представляет собой чистая функция и чем она не является.</span><span class="sxs-lookup"><span data-stu-id="8d66b-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="8d66b-112">Руководство по [управлению содержимым в документе WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) показывает, как управлять документом WordprocessingML и содержит два примера того, как выполнить рефакторинг с помощью чистой функции.</span><span class="sxs-lookup"><span data-stu-id="8d66b-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="8d66b-113">Устранение побочных эффектов и внешних зависимостей</span><span class="sxs-lookup"><span data-stu-id="8d66b-113">Eliminating Side Effects and External Dependencies</span></span>

<span data-ttu-id="8d66b-114">В следующих примерах сравниваются обычные и чистые функции.</span><span class="sxs-lookup"><span data-stu-id="8d66b-114">The following examples contrast two non-pure functions and a pure function.</span></span>

### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="8d66b-115">Обычная функция, изменяющая член класса</span><span class="sxs-lookup"><span data-stu-id="8d66b-115">Non-Pure Function that Changes a Class Member</span></span>

<span data-ttu-id="8d66b-116">В следующем примере кода функция `HyphenatedConcat` представляет собой обычную функцию, поскольку изменяет элемент данных `aMember` в классе.</span><span class="sxs-lookup"><span data-stu-id="8d66b-116">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

<span data-ttu-id="8d66b-117">Этот код выводит следующие результаты:</span><span class="sxs-lookup"><span data-stu-id="8d66b-117">This code produces the following output:</span></span>

```console
StringOne-StringTwo
```

<span data-ttu-id="8d66b-118">Обратите внимание, что не имеет значения, имеет ли изменяемые данные `public` `private` доступ или является `shared` членом или членом экземпляра.</span><span class="sxs-lookup"><span data-stu-id="8d66b-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="8d66b-119">Чистая функция не изменяет не относящиеся к ней данные.</span><span class="sxs-lookup"><span data-stu-id="8d66b-119">A pure function does not change any data outside of the function.</span></span>

### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="8d66b-120">Обычная функция, изменяющая аргумент</span><span class="sxs-lookup"><span data-stu-id="8d66b-120">Non-Pure Function that Changes an Argument</span></span>

<span data-ttu-id="8d66b-121">Более того, следующая версия той же функции представляет собой обычную функцию, поскольку изменяет содержимое своего параметра `sb`.</span><span class="sxs-lookup"><span data-stu-id="8d66b-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

<span data-ttu-id="8d66b-122">Эта версия программы дает те же выходные данные, что и первая версия, поскольку функция `HyphenatedConcat` изменила значение (состояние) своего первого параметра, вызвав функцию-член <xref:System.Text.StringBuilder.Append%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d66b-122">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="8d66b-123">Обратите внимание, что это изменение происходит несмотря на то, что функция `HyphenatedConcat` использует передачу параметра по значению.</span><span class="sxs-lookup"><span data-stu-id="8d66b-123">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d66b-124">Передача параметров по значению для ссылочных типов приводит к созданию копии ссылки на передаваемый объект.</span><span class="sxs-lookup"><span data-stu-id="8d66b-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="8d66b-125">Эта копия все еще связана с теми же данными экземпляра, что и первоначальная ссылка (пока ссылочная переменная не будет присвоена новому объекту).</span><span class="sxs-lookup"><span data-stu-id="8d66b-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="8d66b-126">Вызов по значению необязательно требуется функции для изменения параметра.</span><span class="sxs-lookup"><span data-stu-id="8d66b-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>

### <a name="pure-function"></a><span data-ttu-id="8d66b-127">Чистая функция</span><span class="sxs-lookup"><span data-stu-id="8d66b-127">Pure Function</span></span>

<span data-ttu-id="8d66b-128">Следующая версия этой программы реализует функцию `HyphenatedConcat` в виде чистой функции.</span><span class="sxs-lookup"><span data-stu-id="8d66b-128">This next version of the program hows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

<span data-ttu-id="8d66b-129">И снова она дает ту же строку вывода: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="8d66b-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="8d66b-130">Обратите внимание, что для сохранения соединенного значения оно сохраняется в промежуточной переменной `s2`.</span><span class="sxs-lookup"><span data-stu-id="8d66b-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="8d66b-131">Одним из полезных подходов является написание функций, которые локально являются обычными (то есть в них объявляются и изменяются локальные переменные), но глобально остаются чистыми.</span><span class="sxs-lookup"><span data-stu-id="8d66b-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="8d66b-132">Такие функции имеют многие характеристики, благоприятные с точки зрения компоновки, но позволяют обойтись без использования некоторых более сложных средств функционального программирования, тех, что диктуют, например, необходимость использовать рекурсию, невзирая на возможность добиться того же результата с помощью простого цикла.</span><span class="sxs-lookup"><span data-stu-id="8d66b-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="8d66b-133">Стандартные операторы запроса</span><span class="sxs-lookup"><span data-stu-id="8d66b-133">Standard Query Operators</span></span>

<span data-ttu-id="8d66b-134">Важной характеристикой стандартных операторов запросов является то, что они реализуются как чистые функции.</span><span class="sxs-lookup"><span data-stu-id="8d66b-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>

<span data-ttu-id="8d66b-135">Дополнительные сведения см. в статье [Общие сведения о стандартных операторах запросов (Visual Basic)](standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8d66b-135">For more information, see [Standard Query Operators Overview (Visual Basic)](standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d66b-136">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8d66b-136">See also</span></span>

- [<span data-ttu-id="8d66b-137">Введение в чистые функциональные преобразования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d66b-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="8d66b-138">Сравнение функционального и императивного программирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d66b-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](functional-programming-vs-imperative-programming.md)
