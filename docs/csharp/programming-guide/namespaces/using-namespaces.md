---
title: Руководство по программированию на C#. Использование пространств имен
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: b4326be8c9e299a96477096ec21864ec69037abe
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738247"
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="ed0de-102">Использование пространств имен. (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="ed0de-102">Using namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="ed0de-103">Пространства имен часто используются в программировании на C# двумя способами.</span><span class="sxs-lookup"><span data-stu-id="ed0de-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="ed0de-104">Первый способ — платформа .NET Framework использует пространства имен для упорядочения множества ее классов.</span><span class="sxs-lookup"><span data-stu-id="ed0de-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="ed0de-105">Второй способ — объявление собственных пространств имен поможет вам контролировать область имен классов и методов в более крупных проектах.</span><span class="sxs-lookup"><span data-stu-id="ed0de-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="ed0de-106">Доступ к пространствам имен</span><span class="sxs-lookup"><span data-stu-id="ed0de-106">Accessing namespaces</span></span>

 <span data-ttu-id="ed0de-107">Большинство приложений на языке C# начинается с раздела директив `using`.</span><span class="sxs-lookup"><span data-stu-id="ed0de-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="ed0de-108">В этом разделе перечисляются пространства имен, которые будут часто использоваться приложением, благодаря чему программист может не указывать их полные названия каждый раз, когда вызывается содержащийся в них метод.</span><span class="sxs-lookup"><span data-stu-id="ed0de-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="ed0de-109">Например, включив строку</span><span class="sxs-lookup"><span data-stu-id="ed0de-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 <span data-ttu-id="ed0de-110">в начале программы, программист может использовать код</span><span class="sxs-lookup"><span data-stu-id="ed0de-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 <span data-ttu-id="ed0de-111">вместо следующего кода:</span><span class="sxs-lookup"><span data-stu-id="ed0de-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="ed0de-112">Псевдонимы пространств имен</span><span class="sxs-lookup"><span data-stu-id="ed0de-112">Namespace aliases</span></span>

 <span data-ttu-id="ed0de-113">Можно также использовать [директиву `using`](../../language-reference/keywords/using-directive.md) для создания псевдонимов пространства имен.</span><span class="sxs-lookup"><span data-stu-id="ed0de-113">You can also use the [`using` directive](../../language-reference/keywords/using-directive.md) to create an alias for a namespace.</span></span> <span data-ttu-id="ed0de-114">Используйте [квалификатор псевдонима пространства имен `::`](../../language-reference/operators/namespace-alias-qualifier.md) для доступа к членам пространства имен, обозначенного псевдонимом.</span><span class="sxs-lookup"><span data-stu-id="ed0de-114">Use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to access the members of the aliased namespace.</span></span> <span data-ttu-id="ed0de-115">В следующем примере показано, как создать и использовать псевдоним для пространства имен.</span><span class="sxs-lookup"><span data-stu-id="ed0de-115">The following example shows how to create and use a namespace alias:</span></span>
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="ed0de-116">Использование пространств имен для управления областью действия</span><span class="sxs-lookup"><span data-stu-id="ed0de-116">Using namespaces to control scope</span></span>

 <span data-ttu-id="ed0de-117">Область действия объявляется с помощью ключевого слова `namespace`.</span><span class="sxs-lookup"><span data-stu-id="ed0de-117">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="ed0de-118">Определяя области действия в проекте, вы можете упорядочивать код и создавать уникальные на глобальном уровне типы.</span><span class="sxs-lookup"><span data-stu-id="ed0de-118">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="ed0de-119">В следующем примере класс `SampleClass` определяется в двух пространствах имен, одно из которых вложено в другое.</span><span class="sxs-lookup"><span data-stu-id="ed0de-119">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="ed0de-120">Для определения конкретного вызываемого метода используется [маркер `.`](../../language-reference/operators/member-access-operators.md#member-access-expression-).</span><span class="sxs-lookup"><span data-stu-id="ed0de-120">The [`.` token](../../language-reference/operators/member-access-operators.md#member-access-expression-) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="ed0de-121">Полные имена</span><span class="sxs-lookup"><span data-stu-id="ed0de-121">Fully qualified names</span></span>

 <span data-ttu-id="ed0de-122">Пространства имен и типы имеют уникальные названия, которые описываются полными именами, определяющими их место в логической иерархии.</span><span class="sxs-lookup"><span data-stu-id="ed0de-122">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="ed0de-123">Например, инструкция `A.B` указывает, что `A` — это пространство имен или тип, а `B` — вложенный в него элемент.</span><span class="sxs-lookup"><span data-stu-id="ed0de-123">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="ed0de-124">В следующем примере показаны вложенные классы и пространства имен.</span><span class="sxs-lookup"><span data-stu-id="ed0de-124">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="ed0de-125">Полное имя каждого элемента указано в комментарии рядом с ним.</span><span class="sxs-lookup"><span data-stu-id="ed0de-125">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 <span data-ttu-id="ed0de-126">В предыдущем фрагменте кода:</span><span class="sxs-lookup"><span data-stu-id="ed0de-126">In the previous code segment:</span></span>  
  
- <span data-ttu-id="ed0de-127">Пространство имен `N1` является членом глобального пространства имен.</span><span class="sxs-lookup"><span data-stu-id="ed0de-127">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="ed0de-128">Его полное имя: `N1`.</span><span class="sxs-lookup"><span data-stu-id="ed0de-128">Its fully qualified name is `N1`.</span></span>  
  
- <span data-ttu-id="ed0de-129">Пространство имен `N2` является членом пространства имен `N1`.</span><span class="sxs-lookup"><span data-stu-id="ed0de-129">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="ed0de-130">Его полное имя: `N1.N2`.</span><span class="sxs-lookup"><span data-stu-id="ed0de-130">Its fully qualified name is `N1.N2`.</span></span>  
  
- <span data-ttu-id="ed0de-131">Класс `C1` является членом пространства имен `N1`.</span><span class="sxs-lookup"><span data-stu-id="ed0de-131">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="ed0de-132">Его полное имя: `N1.C1`.</span><span class="sxs-lookup"><span data-stu-id="ed0de-132">Its fully qualified name is `N1.C1`.</span></span>  
  
- <span data-ttu-id="ed0de-133">В этом коде имя класса `C2` используется два раза.</span><span class="sxs-lookup"><span data-stu-id="ed0de-133">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="ed0de-134">Тем не менее полные имена являются уникальными.</span><span class="sxs-lookup"><span data-stu-id="ed0de-134">However, the fully qualified names are unique.</span></span> <span data-ttu-id="ed0de-135">Первый экземпляр `C2` объявляется в классе `C1`. Соответственно, его полное имя: `N1.C1.C2`.</span><span class="sxs-lookup"><span data-stu-id="ed0de-135">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="ed0de-136">Второй экземпляр `C2` объявляется в пространстве имен `N2`. Соответственно, его полное имя: `N1.N2.C2`.</span><span class="sxs-lookup"><span data-stu-id="ed0de-136">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="ed0de-137">Используя представленный выше фрагмент кода, вы можете добавить новый элемент класса `C3` в пространство имен `N1.N2`, как показано выше:</span><span class="sxs-lookup"><span data-stu-id="ed0de-137">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 <span data-ttu-id="ed0de-138">В общем случае следует использовать [квалификатор псевдонима пространства имен `::`](../../language-reference/operators/namespace-alias-qualifier.md) для ссылки на псевдоним пространства имен или `global::` для ссылки на глобальное пространство имен, а также `.` для определения типов или элементов.</span><span class="sxs-lookup"><span data-stu-id="ed0de-138">In general, use the [namespace alias qualifier `::`](../../language-reference/operators/namespace-alias-qualifier.md) to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="ed0de-139">Использование `::` с псевдонимом, ссылающимся на тип вместо пространства имен, будет ошибкой.</span><span class="sxs-lookup"><span data-stu-id="ed0de-139">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="ed0de-140">Пример:</span><span class="sxs-lookup"><span data-stu-id="ed0de-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 <span data-ttu-id="ed0de-141">Помните, что слово `global` не является предопределенным псевдонимом и, соответственно, выражение `global.X` не имеет какого-либо конкретного значения.</span><span class="sxs-lookup"><span data-stu-id="ed0de-141">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="ed0de-142">Конкретное значение будет получено только при его использовании вместе с `::`.</span><span class="sxs-lookup"><span data-stu-id="ed0de-142">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="ed0de-143">Если определить псевдоним с именем global, возникнет предупреждение компилятора CS0440. Это связано с тем, что `global::` всегда ссылается на глобальное пространство имен, а не на псевдоним.</span><span class="sxs-lookup"><span data-stu-id="ed0de-143">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="ed0de-144">Например, предупреждение возникнет в следующем случае:</span><span class="sxs-lookup"><span data-stu-id="ed0de-144">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 <span data-ttu-id="ed0de-145">При работе с псевдонимами рекомендуется использовать `::`, поскольку это обеспечивает защиту от случайного определения дополнительных типов.</span><span class="sxs-lookup"><span data-stu-id="ed0de-145">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="ed0de-146">Рассмотрим следующий пример:</span><span class="sxs-lookup"><span data-stu-id="ed0de-146">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 <span data-ttu-id="ed0de-147">Этот код будет работать, однако если впоследствии определить тип с именем `Alias`, выражение `Alias.` будет связываться с этим типом.</span><span class="sxs-lookup"><span data-stu-id="ed0de-147">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="ed0de-148">Используя выражение `Alias::Exception`, вы гарантируете, что `Alias` будет обрабатываться как псевдоним пространства имен и не будет ошибочно связываться с типом.</span><span class="sxs-lookup"><span data-stu-id="ed0de-148">Using `Alias::Exception` ensures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  

## <a name="see-also"></a><span data-ttu-id="ed0de-149">См. также</span><span class="sxs-lookup"><span data-stu-id="ed0de-149">See also</span></span>

- [<span data-ttu-id="ed0de-150">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="ed0de-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ed0de-151">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="ed0de-151">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="ed0de-152">Выражение доступа к члену</span><span class="sxs-lookup"><span data-stu-id="ed0de-152">Member access expression</span></span>](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [<span data-ttu-id="ed0de-153">Оператор ::</span><span class="sxs-lookup"><span data-stu-id="ed0de-153">:: operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="ed0de-154">Псевдоним extern</span><span class="sxs-lookup"><span data-stu-id="ed0de-154">extern alias</span></span>](../../language-reference/keywords/extern-alias.md)
