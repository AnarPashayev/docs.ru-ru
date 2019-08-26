---
title: Руководство по программированию на C#. Универсальные шаблоны и массивы
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: fee66cf7bd0ab3c051ea67acc323efa02a21a017
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659793"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="18fa9-102">Универсальные методы и массивы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="18fa9-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="18fa9-103">В C# 2.0 и более поздних версиях одномерные массивы с нулевой нижней границей автоматически реализуют <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="18fa9-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="18fa9-104">Это позволяет создавать универсальные методы, которые могут использовать один и тот же код для выполнения итераций в массивах и других типах коллекций.</span><span class="sxs-lookup"><span data-stu-id="18fa9-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="18fa9-105">Этот способ используется преимущественно для чтения данных в коллекциях.</span><span class="sxs-lookup"><span data-stu-id="18fa9-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="18fa9-106">Интерфейс <xref:System.Collections.Generic.IList%601> нельзя использовать для добавления или удаления элементов массива.</span><span class="sxs-lookup"><span data-stu-id="18fa9-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="18fa9-107">При попытке вызвать метод <xref:System.Collections.Generic.IList%601>, например <xref:System.Collections.Generic.IList%601.RemoveAt%2A>, для массива в этом контексте возникнет исключение.</span><span class="sxs-lookup"><span data-stu-id="18fa9-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="18fa9-108">В следующем примере кода показано, как отдельный универсальный метод, принимающий входной параметр <xref:System.Collections.Generic.IList%601>, можно использовать для выполнения итераций в списке и массиве (в данном случае в массиве целых чисел).</span><span class="sxs-lookup"><span data-stu-id="18fa9-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="18fa9-109">См. также</span><span class="sxs-lookup"><span data-stu-id="18fa9-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="18fa9-110">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="18fa9-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="18fa9-111">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="18fa9-111">Generics</span></span>](./index.md)
- [<span data-ttu-id="18fa9-112">Массивы</span><span class="sxs-lookup"><span data-stu-id="18fa9-112">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="18fa9-113">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="18fa9-113">Generics</span></span>](../../../standard/generics/index.md)
