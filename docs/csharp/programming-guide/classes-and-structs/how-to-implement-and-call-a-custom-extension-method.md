---
title: Практическое руководство. Руководство по программированию на C#. Реализация и вызов пользовательского метода расширения
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 2fe07f8e4311417980caccc9c286b4f94c7ea994
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585951"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="141a8-102">Практическое руководство. Руководство по программированию на C#. Реализация и вызов пользовательского метода расширения</span><span class="sxs-lookup"><span data-stu-id="141a8-102">How to: Implement and Call a Custom Extension Method (C# Programming Guide)</span></span>
<span data-ttu-id="141a8-103">Этот раздел описывает, как реализовать свои методы расширения для любого типа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="141a8-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="141a8-104">Клиентский код может использовать методы расширения путем добавления ссылки на содержащую их библиотеку DLL и добавления директивы [using](../../../csharp/language-reference/keywords/using-directive.md), которая указывает пространство имен, в котором определены методы расширения.</span><span class="sxs-lookup"><span data-stu-id="141a8-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../../csharp/language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="141a8-105">Определение и вызов метода расширения</span><span class="sxs-lookup"><span data-stu-id="141a8-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="141a8-106">Определите статический [класс](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md), который будет содержать метод расширения.</span><span class="sxs-lookup"><span data-stu-id="141a8-106">Define a static [class](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="141a8-107">Класс должен быть видимым для клиентского кода.</span><span class="sxs-lookup"><span data-stu-id="141a8-107">The class must be visible to client code.</span></span> <span data-ttu-id="141a8-108">Дополнительные сведения о правилах доступа см. в разделах [Модификаторы доступа](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="141a8-108">For more information about accessibility rules, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="141a8-109">Реализуйте метод расширения как статический метод как минимум с тем же уровнем видимости, что и содержащий класс.</span><span class="sxs-lookup"><span data-stu-id="141a8-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="141a8-110">Первый параметр метода указывает тип, с которым работает метод. Ему должен предшествовать модификатор [this](../../../csharp/language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="141a8-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../../csharp/language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="141a8-111">В вызывающем коде добавьте директиву `using`, чтобы задать [пространство имен](../../../csharp/language-reference/keywords/namespace.md), содержащее класс метода расширения.</span><span class="sxs-lookup"><span data-stu-id="141a8-111">In the calling code, add a `using` directive to specify the [namespace](../../../csharp/language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="141a8-112">Вызовите методы, как если бы они являлись методами экземпляра для типа.</span><span class="sxs-lookup"><span data-stu-id="141a8-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="141a8-113">Обратите внимание, что первый параметр не указан вызывающим кодом, поскольку он представляет тип, к которому применяется оператор, и компилятору уже известен тип объекта.</span><span class="sxs-lookup"><span data-stu-id="141a8-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="141a8-114">Вам необходимо предоставить аргументы только для параметров со 2 по `n`.</span><span class="sxs-lookup"><span data-stu-id="141a8-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="141a8-115">Пример</span><span class="sxs-lookup"><span data-stu-id="141a8-115">Example</span></span>  
 <span data-ttu-id="141a8-116">В приведенном ниже примере реализуется метод расширения с именем `WordCount` в классе `CustomExtensions.StringExtension`.</span><span class="sxs-lookup"><span data-stu-id="141a8-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="141a8-117">Метод работает с классом <xref:System.String> класса, который указан как первый параметр метода.</span><span class="sxs-lookup"><span data-stu-id="141a8-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="141a8-118">Пространство имен `CustomExtensions` импортируется в пространство имен приложения, и метод вызывается внутри метода `Main`.</span><span class="sxs-lookup"><span data-stu-id="141a8-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="141a8-119">Безопасность платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="141a8-119">.NET Framework Security</span></span>  
 <span data-ttu-id="141a8-120">Методы расширения не предоставляют определенных уязвимостей безопасности.</span><span class="sxs-lookup"><span data-stu-id="141a8-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="141a8-121">Они не могут использоваться для олицетворения существующих методов для типа, поскольку все конфликты имен разрешаются в пользу метода экземпляра или статического метода, определяемого самим типом.</span><span class="sxs-lookup"><span data-stu-id="141a8-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="141a8-122">Методы расширения не могут получить доступ к любым конфиденциальным данным в расширенном классе.</span><span class="sxs-lookup"><span data-stu-id="141a8-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="141a8-123">См. также</span><span class="sxs-lookup"><span data-stu-id="141a8-123">See also</span></span>

- [<span data-ttu-id="141a8-124">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="141a8-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="141a8-125">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="141a8-125">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="141a8-126">Встроенный язык запросов LINQ</span><span class="sxs-lookup"><span data-stu-id="141a8-126">LINQ (Language-Integrated Query)</span></span>](../../../csharp/linq/linq-in-csharp.md)
- [<span data-ttu-id="141a8-127">Статические классы и члены статических классов</span><span class="sxs-lookup"><span data-stu-id="141a8-127">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="141a8-128">protected</span><span class="sxs-lookup"><span data-stu-id="141a8-128">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
- [<span data-ttu-id="141a8-129">internal</span><span class="sxs-lookup"><span data-stu-id="141a8-129">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
- [<span data-ttu-id="141a8-130">public</span><span class="sxs-lookup"><span data-stu-id="141a8-130">public</span></span>](../../../csharp/language-reference/keywords/public.md)
- [<span data-ttu-id="141a8-131">this</span><span class="sxs-lookup"><span data-stu-id="141a8-131">this</span></span>](../../../csharp/language-reference/keywords/this.md)
- [<span data-ttu-id="141a8-132">namespace</span><span class="sxs-lookup"><span data-stu-id="141a8-132">namespace</span></span>](../../../csharp/language-reference/keywords/namespace.md)
