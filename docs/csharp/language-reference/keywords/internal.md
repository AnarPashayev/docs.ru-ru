---
title: internal. Справочник по C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 9cfbea03a305dd17c07f549901bc91be0e05b792
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661167"
---
# <a name="internal-c-reference"></a><span data-ttu-id="f1df7-102">internal (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="f1df7-102">internal (C# Reference)</span></span>
<span data-ttu-id="f1df7-103">Ключевое слово `internal` является [модификатором доступа](../../../csharp/language-reference/keywords/access-modifiers.md) для типов и членов типов.</span><span class="sxs-lookup"><span data-stu-id="f1df7-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="f1df7-104">Эта страница содержит доступ `internal`.</span><span class="sxs-lookup"><span data-stu-id="f1df7-104">This page covers `internal` access.</span></span> <span data-ttu-id="f1df7-105">Ключевое слово `internal` также является частью модификатора доступа [`protected internal`](./protected-internal.md).</span><span class="sxs-lookup"><span data-stu-id="f1df7-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="f1df7-106">Внутренние типы или члены доступны только внутри файлов в той же сборке, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="f1df7-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="f1df7-107">Сравнение модификатора `internal` с другими модификаторами доступа см. в разделах [Уровни доступности](../../../csharp/language-reference/keywords/accessibility-levels.md) и [Модификаторы доступа](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="f1df7-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="f1df7-108">См. дополнительные сведения о [сборках в .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="f1df7-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="f1df7-109">Обычно доступ к внутренним компонентам используется в разработке на основе компонентов, так как он позволяет группе компонентов взаимодействовать в закрытой форме, без их предоставления остальной части кода приложения.</span><span class="sxs-lookup"><span data-stu-id="f1df7-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="f1df7-110">Например, платформа для создания графических интерфейсов пользователя может предоставлять классы `Control` и `Form`, взаимодействующие с помощью членов с внутренним доступом.</span><span class="sxs-lookup"><span data-stu-id="f1df7-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="f1df7-111">Поскольку эти члены являются внутренними, они не предоставляются коду, использующему платформу.</span><span class="sxs-lookup"><span data-stu-id="f1df7-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="f1df7-112">Будет ошибкой ссылаться на тип или член с внутренним доступом из-за пределов сборки, в которой он определен.</span><span class="sxs-lookup"><span data-stu-id="f1df7-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1df7-113">Пример</span><span class="sxs-lookup"><span data-stu-id="f1df7-113">Example</span></span>  
 <span data-ttu-id="f1df7-114">Этот пример содержит два файла, `Assembly1.cs` и `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="f1df7-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="f1df7-115">Первый файл содержит внутренний базовый класс `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="f1df7-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="f1df7-116">Во втором файле попытка создать экземпляр `BaseClass` приведет к ошибке.</span><span class="sxs-lookup"><span data-stu-id="f1df7-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="f1df7-117">Пример</span><span class="sxs-lookup"><span data-stu-id="f1df7-117">Example</span></span>  
 <span data-ttu-id="f1df7-118">В этом примере используйте те же файлы, которые использовались в примере 1, однако измените уровень доступности `BaseClass` на `public`.</span><span class="sxs-lookup"><span data-stu-id="f1df7-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="f1df7-119">Кроме того, измените уровень доступности члена `intM` на `internal`.</span><span class="sxs-lookup"><span data-stu-id="f1df7-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="f1df7-120">В этом случае можно создать экземпляр класса, но нельзя получить доступ к внутреннему члену.</span><span class="sxs-lookup"><span data-stu-id="f1df7-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="f1df7-121">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="f1df7-121">C# Language Specification</span></span>  

<span data-ttu-id="f1df7-122">Дополнительные сведения см. в разделе [Объявленная доступность](~/_csharplang/spec/basic-concepts.md#declared-accessibility) в [Спецификации языка C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f1df7-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="f1df7-123">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="f1df7-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f1df7-124">См. также</span><span class="sxs-lookup"><span data-stu-id="f1df7-124">See also</span></span>

- [<span data-ttu-id="f1df7-125">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="f1df7-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="f1df7-126">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="f1df7-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f1df7-127">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="f1df7-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="f1df7-128">Модификаторы доступа</span><span class="sxs-lookup"><span data-stu-id="f1df7-128">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="f1df7-129">Уровни доступности</span><span class="sxs-lookup"><span data-stu-id="f1df7-129">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="f1df7-130">Модификаторы</span><span class="sxs-lookup"><span data-stu-id="f1df7-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
- [<span data-ttu-id="f1df7-131">public</span><span class="sxs-lookup"><span data-stu-id="f1df7-131">public</span></span>](../../../csharp/language-reference/keywords/public.md)
- [<span data-ttu-id="f1df7-132">private</span><span class="sxs-lookup"><span data-stu-id="f1df7-132">private</span></span>](../../../csharp/language-reference/keywords/private.md)
- [<span data-ttu-id="f1df7-133">protected</span><span class="sxs-lookup"><span data-stu-id="f1df7-133">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
