---
title: Руководство по программированию на C#. Доступ к элементу с использованием указателя
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: d0ca4a0b2189ee652ad1d9c2b63690306a651df4
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635076"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="51ad3-102">Практическое руководство. Доступ к члену с использованием указателя (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="51ad3-102">How to: access a member with a pointer (C# Programming Guide)</span></span>
<span data-ttu-id="51ad3-103">Чтобы получить доступ к члену или структуре, которые объявлены в небезопасном контексте, можно использовать оператор доступа к члену, как показано в следующем примере, где `p` — это указатель на [структуру](../../../csharp/language-reference/keywords/struct.md), содержащую член `x`.</span><span class="sxs-lookup"><span data-stu-id="51ad3-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="51ad3-104">Пример</span><span class="sxs-lookup"><span data-stu-id="51ad3-104">Example</span></span>  
 <span data-ttu-id="51ad3-105">В этом примере объявляется [структура](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, содержащая координаты `x` и `y`, а также создается ее экземпляр.</span><span class="sxs-lookup"><span data-stu-id="51ad3-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="51ad3-106">С помощью оператора доступа к члену `->` и указателя на экземпляр `home` присваиваются значения `x` и `y`.</span><span class="sxs-lookup"><span data-stu-id="51ad3-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51ad3-107">Обратите внимание, что выражение `p->x` эквивалентно выражению `(*p).x` и с помощью любого из них можно получить тот же результат.</span><span class="sxs-lookup"><span data-stu-id="51ad3-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#9)]  
  
 [!code-csharp[csProgGuidePointers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="51ad3-108">См. также</span><span class="sxs-lookup"><span data-stu-id="51ad3-108">See also</span></span>

- [<span data-ttu-id="51ad3-109">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="51ad3-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="51ad3-110">Типы указателей</span><span class="sxs-lookup"><span data-stu-id="51ad3-110">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="51ad3-111">Типы</span><span class="sxs-lookup"><span data-stu-id="51ad3-111">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="51ad3-112">unsafe</span><span class="sxs-lookup"><span data-stu-id="51ad3-112">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="51ad3-113">Оператор fixed</span><span class="sxs-lookup"><span data-stu-id="51ad3-113">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="51ad3-114">stackalloc</span><span class="sxs-lookup"><span data-stu-id="51ad3-114">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
