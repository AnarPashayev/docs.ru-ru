---
title: Ограничение new. Справочник по C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 32fcb13e1f217707d53300c532169b1a1759fa7e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633410"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="3ac6b-102">Ограничение new (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="3ac6b-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="3ac6b-103">Ограничение `new` указывает, что аргумент любого типа в объявлении универсального класса должен иметь открытый конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="3ac6b-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="3ac6b-104">Использовать ограничение new можно только в том случае, если тип не является абстрактным.</span><span class="sxs-lookup"><span data-stu-id="3ac6b-104">To use the new constraint, the type cannot be abstract.</span></span>

## <a name="example"></a><span data-ttu-id="3ac6b-105">Пример</span><span class="sxs-lookup"><span data-stu-id="3ac6b-105">Example</span></span>

<span data-ttu-id="3ac6b-106">Примените ограничение `new` к параметру типа, когда общий класс создает новые экземпляры этого типа, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="3ac6b-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a><span data-ttu-id="3ac6b-107">Пример</span><span class="sxs-lookup"><span data-stu-id="3ac6b-107">Example</span></span>

<span data-ttu-id="3ac6b-108">При использовании ограничения `new()` с другими ограничениями его необходимо указывать последним:</span><span class="sxs-lookup"><span data-stu-id="3ac6b-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="3ac6b-109">Дополнительные сведения см. в разделе [Ограничения параметров типа](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3ac6b-109">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3ac6b-110">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="3ac6b-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3ac6b-111">См. также</span><span class="sxs-lookup"><span data-stu-id="3ac6b-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="3ac6b-112">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="3ac6b-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="3ac6b-113">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="3ac6b-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3ac6b-114">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="3ac6b-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3ac6b-115">Ключевые слова операторов</span><span class="sxs-lookup"><span data-stu-id="3ac6b-115">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="3ac6b-116">Универсальные шаблоны</span><span class="sxs-lookup"><span data-stu-id="3ac6b-116">Generics</span></span>](../../programming-guide/generics/index.md)
