---
title: Руководство по программированию на C#. Общие сведения об универсальных шаблонах
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: 0d7ecb7f7fd0bb0985234cdc2cf8d37b53323c86
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595491"
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="0ad37-102">Введение в универсальные шаблоны. (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="0ad37-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="0ad37-103">Универсальные классы и методы сочетают такие характеристики, как возможность многократного использования, типобезопасность и эффективность, которые не обеспечивают их неуниверсальные аналоги.</span><span class="sxs-lookup"><span data-stu-id="0ad37-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="0ad37-104">Универсальные типы наиболее часто используются с коллекциями и методами, которые выполняют с ними операции.</span><span class="sxs-lookup"><span data-stu-id="0ad37-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="0ad37-105">Библиотека классов на платформе .NET Framework 2.0 предоставляет новое пространство имен <xref:System.Collections.Generic>, которое содержит несколько новых универсальных классов коллекций.</span><span class="sxs-lookup"><span data-stu-id="0ad37-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="0ad37-106">Во всех приложениях, предназначенных для .NET Framework 2.0 и более поздних версий, рекомендуем использовать новые универсальные классы коллекций вместо старых неуниверсальных аналогов, например <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="0ad37-106">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="0ad37-107">Дополнительные сведения см. в статье об [универсальных шаблонах в .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ad37-107">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="0ad37-108">Очевидно, вы можете создавать собственные универсальные типы и методы для предоставления собственных типобезопасных и эффективных обобщенных решений и шаблонов разработки.</span><span class="sxs-lookup"><span data-stu-id="0ad37-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="0ad37-109">В следующем примере кода показан простой универсальный класс связанного списка для демонстрационных целей.</span><span class="sxs-lookup"><span data-stu-id="0ad37-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="0ad37-110">(В большинстве случаев следует использовать класс <xref:System.Collections.Generic.List%601>, предоставляемый библиотекой классов .NET Framework, вместо создания собственного.) Параметр типа `T` используется в нескольких расположениях, где обычно используется конкретный тип для указания типа элемента, хранящегося в списке.</span><span class="sxs-lookup"><span data-stu-id="0ad37-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="0ad37-111">Он используется в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="0ad37-111">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="0ad37-112">в качестве типа параметра метода в методе `AddHead`;</span><span class="sxs-lookup"><span data-stu-id="0ad37-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="0ad37-113">в качестве типа возвращаемого значения свойства `Data` во вложенном классе `Node`;</span><span class="sxs-lookup"><span data-stu-id="0ad37-113">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="0ad37-114">в качестве типа закрытого члена `data` во вложенном классе.</span><span class="sxs-lookup"><span data-stu-id="0ad37-114">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="0ad37-115">Обратите внимание, что T доступен для вложенного класса `Node`.</span><span class="sxs-lookup"><span data-stu-id="0ad37-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="0ad37-116">Когда экземпляр `GenericList<T>` создается с конкретным типом, например `GenericList<int>`, каждое вхождение `T` будет заменено `int`.</span><span class="sxs-lookup"><span data-stu-id="0ad37-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="0ad37-117">В следующем примере кода показано, как клиентский код использует универсальный класс `GenericList<T>` для создания списка целых чисел.</span><span class="sxs-lookup"><span data-stu-id="0ad37-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="0ad37-118">Просто изменяя тип аргумента, следующий код можно легко изменить для создания списков строк или любого другого пользовательского типа:</span><span class="sxs-lookup"><span data-stu-id="0ad37-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0ad37-119">См. также</span><span class="sxs-lookup"><span data-stu-id="0ad37-119">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="0ad37-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="0ad37-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0ad37-121">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="0ad37-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
