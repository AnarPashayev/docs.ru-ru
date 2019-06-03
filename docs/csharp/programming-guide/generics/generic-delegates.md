---
title: Руководство по программированию на C#. Универсальные методы-делегаты
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: ff19b3d71858552158a8ae5d0ab362a86dc98e65
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423505"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="4739b-102">Универсальные делегаты. (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="4739b-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="4739b-103">[Делегат](../../../csharp/language-reference/keywords/delegate.md) может определять собственные параметры типа.</span><span class="sxs-lookup"><span data-stu-id="4739b-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="4739b-104">В коде, который ссылается на универсальный делегат, можно указать аргумент типа для создания закрытого сконструированного типа. Это будет аналогично созданию экземпляра универсального класса или вызову универсального метода, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="4739b-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="4739b-105">В C# версии 2.0 представлена новая функция группового преобразования методов, которая применяется как к конкретным, так и к универсальным типам делегатов, и позволяет записать приведенную выше строку с использованием упрощенного синтаксиса:</span><span class="sxs-lookup"><span data-stu-id="4739b-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="4739b-106">Делегаты, определенные в универсальном классе, могут использовать параметры класса универсального типа таким же образом, как это делают методы класса.</span><span class="sxs-lookup"><span data-stu-id="4739b-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="4739b-107">В коде, который ссылается на делегат, необходимо указать аргумент типа содержащего класса, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="4739b-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="4739b-108">Универсальные делегаты особенно полезны при определении событий, основанных на типовых шаблонах разработки, поскольку аргумент отправителя может быть строго типизирован и больше не требует приведения к <xref:System.Object> и из него.</span><span class="sxs-lookup"><span data-stu-id="4739b-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="4739b-109">См. также</span><span class="sxs-lookup"><span data-stu-id="4739b-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="4739b-110">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="4739b-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4739b-111">Введение в универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="4739b-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="4739b-112">Универсальные методы</span><span class="sxs-lookup"><span data-stu-id="4739b-112">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)
- [<span data-ttu-id="4739b-113">Универсальные классы</span><span class="sxs-lookup"><span data-stu-id="4739b-113">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)
- [<span data-ttu-id="4739b-114">Универсальные интерфейсы</span><span class="sxs-lookup"><span data-stu-id="4739b-114">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)
- [<span data-ttu-id="4739b-115">Делегаты</span><span class="sxs-lookup"><span data-stu-id="4739b-115">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="4739b-116">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="4739b-116">Generics</span></span>](~/docs/standard/generics/index.md)
