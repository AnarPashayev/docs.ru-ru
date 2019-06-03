---
title: Руководство по программированию на C#. Использование пространств имен
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: bb491ef93f0f2da89f0101d10e2cf3d158962850
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423304"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="07b46-102">Использование пространств имен (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="07b46-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="07b46-103">Пространства имен часто используются в программировании на C# двумя способами.</span><span class="sxs-lookup"><span data-stu-id="07b46-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="07b46-104">Первый способ — платформа .NET Framework использует пространства имен для упорядочения множества ее классов.</span><span class="sxs-lookup"><span data-stu-id="07b46-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="07b46-105">Второй способ — объявление собственных пространств имен поможет вам контролировать область имен классов и методов в более крупных проектах.</span><span class="sxs-lookup"><span data-stu-id="07b46-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="07b46-106">Доступ к пространствам имен</span><span class="sxs-lookup"><span data-stu-id="07b46-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="07b46-107">Большинство приложений на языке C# начинается с раздела директив `using`.</span><span class="sxs-lookup"><span data-stu-id="07b46-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="07b46-108">В этом разделе перечисляются пространства имен, которые будут часто использоваться приложением, благодаря чему программист может не указывать их полные названия каждый раз, когда вызывается содержащийся в них метод.</span><span class="sxs-lookup"><span data-stu-id="07b46-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="07b46-109">Например, включив строку</span><span class="sxs-lookup"><span data-stu-id="07b46-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="07b46-110">в начале программы, программист может использовать код</span><span class="sxs-lookup"><span data-stu-id="07b46-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="07b46-111">вместо следующего кода:</span><span class="sxs-lookup"><span data-stu-id="07b46-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="07b46-112">Псевдонимы пространств имен</span><span class="sxs-lookup"><span data-stu-id="07b46-112">Namespace Aliases</span></span>  
 <span data-ttu-id="07b46-113">С помощью [директивы using](../../../csharp/language-reference/keywords/using-directive.md) также можно создавать псевдонимы [пространств имен](../../../csharp/language-reference/keywords/namespace.md).</span><span class="sxs-lookup"><span data-stu-id="07b46-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="07b46-114">Например, при использовании ранее указанного пространства имен, содержащего вложенные пространства имен, можно объявить псевдоним для быстрого обращения к нему, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="07b46-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#7)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="07b46-115">Использование пространств имен для управления областью действия</span><span class="sxs-lookup"><span data-stu-id="07b46-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="07b46-116">Область действия объявляется с помощью ключевого слова `namespace`.</span><span class="sxs-lookup"><span data-stu-id="07b46-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="07b46-117">Определяя области действия в проекте, вы можете упорядочивать код и создавать уникальные на глобальном уровне типы.</span><span class="sxs-lookup"><span data-stu-id="07b46-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="07b46-118">В следующем примере класс `SampleClass` определяется в двух пространствах имен, одно из которых вложено в другое.</span><span class="sxs-lookup"><span data-stu-id="07b46-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="07b46-119">[Оператор доступа к членам `.`](../../language-reference/operators/member-access-operators.md#member-access-operator-) используется для отличения вызываемого метода.</span><span class="sxs-lookup"><span data-stu-id="07b46-119">The [member access `.` operator](../../language-reference/operators/member-access-operators.md#member-access-operator-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="07b46-120">полные имена</span><span class="sxs-lookup"><span data-stu-id="07b46-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="07b46-121">Пространства имен и типы имеют уникальные названия, которые описываются полными именами, определяющими их место в логической иерархии.</span><span class="sxs-lookup"><span data-stu-id="07b46-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="07b46-122">Например, инструкция `A.B` указывает, что `A` — это пространство имен или тип, а `B` — вложенный в него элемент.</span><span class="sxs-lookup"><span data-stu-id="07b46-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="07b46-123">В следующем примере показаны вложенные классы и пространства имен.</span><span class="sxs-lookup"><span data-stu-id="07b46-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="07b46-124">Полное имя каждого элемента указано в комментарии рядом с ним.</span><span class="sxs-lookup"><span data-stu-id="07b46-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="07b46-125">В предыдущем фрагменте кода:</span><span class="sxs-lookup"><span data-stu-id="07b46-125">In the previous code segment:</span></span>  
  
- <span data-ttu-id="07b46-126">Пространство имен `N1` является членом глобального пространства имен.</span><span class="sxs-lookup"><span data-stu-id="07b46-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="07b46-127">Его полное имя: `N1`.</span><span class="sxs-lookup"><span data-stu-id="07b46-127">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="07b46-128">Пространство имен `N2` является членом пространства имен `N1`.</span><span class="sxs-lookup"><span data-stu-id="07b46-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="07b46-129">Его полное имя: `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="07b46-129">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="07b46-130">Класс `C1` является членом пространства имен `N1`.</span><span class="sxs-lookup"><span data-stu-id="07b46-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="07b46-131">Его полное имя: `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="07b46-131">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="07b46-132">В этом коде имя класса `C2` используется два раза.</span><span class="sxs-lookup"><span data-stu-id="07b46-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="07b46-133">Тем не менее полные имена являются уникальными.</span><span class="sxs-lookup"><span data-stu-id="07b46-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="07b46-134">Первый экземпляр `C2` объявляется в классе `C1`. Соответственно, его полное имя: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="07b46-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="07b46-135">Второй экземпляр `C2` объявляется в пространстве имен `N2`. Соответственно, его полное имя: `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="07b46-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="07b46-136">Используя представленный выше фрагмент кода, вы можете добавить новый элемент класса `C3` в пространство имен `N1.N2`, как показано выше:</span><span class="sxs-lookup"><span data-stu-id="07b46-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="07b46-137">В общем случае следует использовать `::` для ссылки на псевдоним пространства имен или `global::` для ссылки на глобальное пространство имен, а также `.` для определения типов или элементов.</span><span class="sxs-lookup"><span data-stu-id="07b46-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="07b46-138">Использование `::` с псевдонимом, ссылающимся на тип вместо пространства имен, будет ошибкой.</span><span class="sxs-lookup"><span data-stu-id="07b46-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="07b46-139">Например:</span><span class="sxs-lookup"><span data-stu-id="07b46-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="07b46-140">Помните, что слово `global` не является предопределенным псевдонимом и, соответственно, выражение `global.X` не имеет какого-либо конкретного значения.</span><span class="sxs-lookup"><span data-stu-id="07b46-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="07b46-141">Конкретное значение будет получено только при его использовании вместе с `::`.</span><span class="sxs-lookup"><span data-stu-id="07b46-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="07b46-142">Если определить псевдоним с именем global, возникнет предупреждение компилятора CS0440. Это связано с тем, что `global::` всегда ссылается на глобальное пространство имен, а не на псевдоним.</span><span class="sxs-lookup"><span data-stu-id="07b46-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="07b46-143">Например, предупреждение возникнет в следующем случае:</span><span class="sxs-lookup"><span data-stu-id="07b46-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="07b46-144">При работе с псевдонимами рекомендуется использовать `::`, поскольку это обеспечивает защиту от случайного определения дополнительных типов.</span><span class="sxs-lookup"><span data-stu-id="07b46-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="07b46-145">Рассмотрим следующий пример:</span><span class="sxs-lookup"><span data-stu-id="07b46-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="07b46-146">Этот код будет работать, однако если впоследствии определить тип с именем `Alias`, выражение `Alias.` будет связываться с этим типом.</span><span class="sxs-lookup"><span data-stu-id="07b46-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="07b46-147">Используя выражение `Alias::Exception`, вы гарантируете, что `Alias` будет обрабатываться как псевдоним пространства имен и не будет ошибочно связываться с типом.</span><span class="sxs-lookup"><span data-stu-id="07b46-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="07b46-148">В разделе [Использование псевдонима глобального пространства имен. Использование псевдонима глобального пространства имен](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) приводятся дополнительные сведения об использовании псевдонима `global`.</span><span class="sxs-lookup"><span data-stu-id="07b46-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b46-149">См. также</span><span class="sxs-lookup"><span data-stu-id="07b46-149">See also</span></span>

- [<span data-ttu-id="07b46-150">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="07b46-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="07b46-151">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="07b46-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="07b46-152">. Оператор</span><span class="sxs-lookup"><span data-stu-id="07b46-152">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="07b46-153">:: Оператор</span><span class="sxs-lookup"><span data-stu-id="07b46-153">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="07b46-154">extern</span><span class="sxs-lookup"><span data-stu-id="07b46-154">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
