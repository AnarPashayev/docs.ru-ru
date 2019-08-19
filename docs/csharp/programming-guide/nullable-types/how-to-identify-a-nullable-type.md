---
title: Практическое руководство. Руководство по программированию на C#. Идентификация типа, допускающего значение NULL
ms.custom: seodec18
description: Узнайте, как определить, что тип допускает значение NULL или экземпляр принадлежит типу, допускающему значение NULL
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 43a35874b8c9f52c4b98a93e1217994980e1b223
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567377"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="a5804-103">Практическое руководство. Руководство по программированию на C#. Идентификация типа, допускающего значение NULL</span><span class="sxs-lookup"><span data-stu-id="a5804-103">How to: Identify a nullable type (C# Programming Guide)</span></span>

<span data-ttu-id="a5804-104">В следующем примере, показано, как определить, представляет ли экземпляр <xref:System.Type?displayProperty=nameWithType> закрытый универсальный тип, допускающий значение null, т. е. тип <xref:System.Nullable%601?displayProperty=nameWithType> с указанным параметром типа `T`:</span><span class="sxs-lookup"><span data-stu-id="a5804-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="a5804-105">Как показано в примере, при помощи оператора [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) можно создать объект <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a5804-105">As the example shows, you use the [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
<span data-ttu-id="a5804-106">Если вы хотите определить, принадлежит ли экземпляр к типу, допускающему значение NULL, не используйте метод <xref:System.Object.GetType%2A?displayProperty=nameWithType> для получения экземпляра <xref:System.Type> для тестирования с помощью приведенного выше кода.</span><span class="sxs-lookup"><span data-stu-id="a5804-106">If you want to determine whether an instance is of a nullable type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="a5804-107">При вызове метода <xref:System.Object.GetType%2A?displayProperty=nameWithType> в экземпляре типа, допускающего значение NULL, экземпляр [упаковывается](using-nullable-types.md#boxing-and-unboxing) в <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a5804-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="a5804-108">Поскольку упаковка экземпляра типа, допускающего значение NULL, значение которого отлично от NULL, эквивалентна упаковке значения базового типа, <xref:System.Object.GetType%2A> возвращает объект <xref:System.Type>, представляющий базовый тип типа, допускающего значение NULL:</span><span class="sxs-lookup"><span data-stu-id="a5804-108">As boxing of a non-null instance of a nullable type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="a5804-109">Не используйте оператор [is](../../language-reference/keywords/is.md), чтобы определить, принадлежит ли экземпляр к типу, допускающему значение NULL.</span><span class="sxs-lookup"><span data-stu-id="a5804-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable type.</span></span> <span data-ttu-id="a5804-110">Как показано в следующем примере, вы не можете отличить типы экземпляров типа, допускающего значение NULL, и его базового типа с помощью оператора `is`:</span><span class="sxs-lookup"><span data-stu-id="a5804-110">As the following example shows, you cannot distinguish types of instances of a nullable type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="a5804-111">Чтобы определить, принадлежит ли экземпляр типу, допускающему значение NULL, можно использовать код, представленный в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="a5804-111">You can use the code presented in the following example to determine whether an instance is of a nullable type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a><span data-ttu-id="a5804-112">См. также</span><span class="sxs-lookup"><span data-stu-id="a5804-112">See also</span></span>

- [<span data-ttu-id="a5804-113">Типы, допускающие значения NULL</span><span class="sxs-lookup"><span data-stu-id="a5804-113">Nullable types</span></span>](index.md)
- [<span data-ttu-id="a5804-114">Использование типов, допускающих значение NULL</span><span class="sxs-lookup"><span data-stu-id="a5804-114">Using nullable types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
