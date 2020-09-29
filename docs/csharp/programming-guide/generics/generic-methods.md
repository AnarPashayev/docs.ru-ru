---
title: Руководство по программированию на C#. Универсальные методы
description: Сведения о методах, объявленных с использованием параметров типа, также называемых универсальными методами. Изучите примеры кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 195e3f11c73a17931fa6331750e2ae4ee8fd6f10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151471"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="53e01-104">Универсальные методы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="53e01-104">Generic Methods (C# Programming Guide)</span></span>

<span data-ttu-id="53e01-105">Универсальным называется метод, объявленный с использованием параметров типа, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="53e01-105">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 <span data-ttu-id="53e01-106">В следующем примере кода показан один из способов вызова метода с использованием `int` в качестве аргумента типа:</span><span class="sxs-lookup"><span data-stu-id="53e01-106">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 <span data-ttu-id="53e01-107">Если опустить аргумент типа, компилятор определит его.</span><span class="sxs-lookup"><span data-stu-id="53e01-107">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="53e01-108">Следующий вызов `Swap` эквивалентен предыдущему:</span><span class="sxs-lookup"><span data-stu-id="53e01-108">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 <span data-ttu-id="53e01-109">Для статических методов и методов экземпляра применяются одинаковые правила определения типа.</span><span class="sxs-lookup"><span data-stu-id="53e01-109">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="53e01-110">Компилятор может определить параметры типа на основе переданных ему аргументов метода. Определение параметров типа невозможно только для ограничения или возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="53e01-110">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="53e01-111">Соответственно, механизм определения типа не работает с методами, не имеющими параметров.</span><span class="sxs-lookup"><span data-stu-id="53e01-111">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="53e01-112">Определение типа происходит во время компиляции до того, как компилятор попытается разрешить сигнатуры перегруженных методов.</span><span class="sxs-lookup"><span data-stu-id="53e01-112">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="53e01-113">Компилятор применяет логику определения типа ко всем универсальным методам с одинаковым именем.</span><span class="sxs-lookup"><span data-stu-id="53e01-113">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="53e01-114">На этапе разрешения перегрузки компилятор включает только те универсальные методы, для которых был успешно определен тип.</span><span class="sxs-lookup"><span data-stu-id="53e01-114">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="53e01-115">В универсальном классе методы, не являющиеся универсальными, могут получать доступ к параметрам типа на уровне класса следующим образом:</span><span class="sxs-lookup"><span data-stu-id="53e01-115">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 <span data-ttu-id="53e01-116">Если определить универсальный метод, принимающий те же параметры типа, что и содержащий его класс, возникнет предупреждение компилятора [CS0693](../../misc/cs0693.md). Это связано с тем, что в области действия метода предоставленный для внутреннего типа `T` аргумент скрывает аргумент, предоставленный для внешнего типа `T`.</span><span class="sxs-lookup"><span data-stu-id="53e01-116">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning [CS0693](../../misc/cs0693.md) because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="53e01-117">Для большей гибкости можно вызывать метод универсального класса с использованием аргументов типа, отличающихся от предоставленных при создании экземпляра класса. В этом случае следует предоставить другой идентификатор для параметра типа метода, как показано в `GenericList2<T>` в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="53e01-117">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 <span data-ttu-id="53e01-118">С помощью ограничений можно реализовать специализированные операции в отношении параметров типа в методах.</span><span class="sxs-lookup"><span data-stu-id="53e01-118">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="53e01-119">Эта версия `Swap<T>` теперь называется `SwapIfGreater<T>` и может использоваться только с типами, реализующими <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="53e01-119">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 <span data-ttu-id="53e01-120">Универсальные методы могут быть перегружены в нескольких параметрах типа.</span><span class="sxs-lookup"><span data-stu-id="53e01-120">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="53e01-121">Например, все представленные ниже методы могут располагаться в одном классе:</span><span class="sxs-lookup"><span data-stu-id="53e01-121">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="53e01-122">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="53e01-122">C# Language Specification</span></span>  

 <span data-ttu-id="53e01-123">Дополнительные сведения см. в [спецификации языка C#](~/_csharplang/spec/classes.md#methods).</span><span class="sxs-lookup"><span data-stu-id="53e01-123">For more information, see the [C# Language Specification](~/_csharplang/spec/classes.md#methods).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e01-124">См. также</span><span class="sxs-lookup"><span data-stu-id="53e01-124">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="53e01-125">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="53e01-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="53e01-126">Введение в универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="53e01-126">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="53e01-127">Методы</span><span class="sxs-lookup"><span data-stu-id="53e01-127">Methods</span></span>](../classes-and-structs/methods.md)
