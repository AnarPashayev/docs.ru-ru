---
title: Справочник по C#. Неуправляемые типы
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 25aa42ba8c8f0023b4f818feb2edbb325f805fb6
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374113"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="5668b-102">Справочник по C#. Неуправляемые типы</span><span class="sxs-lookup"><span data-stu-id="5668b-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="5668b-103">Тип является **неуправляемым типом**, если он принадлежит к одному из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="5668b-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="5668b-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` или `bool`;</span><span class="sxs-lookup"><span data-stu-id="5668b-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="5668b-105">любой тип [перечисления](../keywords/enum.md);</span><span class="sxs-lookup"><span data-stu-id="5668b-105">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="5668b-106">любой тип [указателя](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="5668b-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="5668b-107">Любой определенный пользователем тип [структуры](../keywords/struct.md), который содержит поля только неуправляемых типов в C# 7.3 и более ранних версиях, не является сконструированным типом (тип, который включает по крайней мере один аргумент типа)</span><span class="sxs-lookup"><span data-stu-id="5668b-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="5668b-108">Начиная с C# 7.3 можно использовать [ограничение `unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint), чтобы указать, что параметр типа является отличным от указателя неуправляемым типом.</span><span class="sxs-lookup"><span data-stu-id="5668b-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

<span data-ttu-id="5668b-109">Начиная с C# 8.0, *сконструированный* тип структуры, содержащий поля только неуправляемых типов, также является неуправляемым, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="5668b-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="5668b-110">Универсальная структура может быть источником как для неуправляемых сконструированных типов, так и для сконструированных типов, отличных от неуправляемых.</span><span class="sxs-lookup"><span data-stu-id="5668b-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="5668b-111">В предыдущем примере определяется универсальная структура `Coords<T>`, а также представлены примеры неуправляемых сконструированных типов.</span><span class="sxs-lookup"><span data-stu-id="5668b-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="5668b-112">Примером типа, отличного от неуправляемого, является `Coords<object>`.</span><span class="sxs-lookup"><span data-stu-id="5668b-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="5668b-113">Он не является неуправляемым, так как содержит поля типа `object`, которые являются отличными от неуправляемых.</span><span class="sxs-lookup"><span data-stu-id="5668b-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="5668b-114">Если необходимо, чтобы *все* сконструированные типы были неуправляемыми, используйте ограничение `unmanaged` в определении универсальной структуры:</span><span class="sxs-lookup"><span data-stu-id="5668b-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="5668b-115">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="5668b-115">C# language specification</span></span>

<span data-ttu-id="5668b-116">Дополнительные сведения см. в разделе [Типы указателей](~/_csharplang/spec/unsafe-code.md#pointer-types) в статье [Спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5668b-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5668b-117">См. также</span><span class="sxs-lookup"><span data-stu-id="5668b-117">See also</span></span>

- [<span data-ttu-id="5668b-118">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="5668b-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5668b-119">Типы указателей</span><span class="sxs-lookup"><span data-stu-id="5668b-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="5668b-120">Типы, связанные с памятью и диапазонами</span><span class="sxs-lookup"><span data-stu-id="5668b-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="5668b-121">Оператор sizeof</span><span class="sxs-lookup"><span data-stu-id="5668b-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="5668b-122">Оператор stackalloc</span><span class="sxs-lookup"><span data-stu-id="5668b-122">stackalloc operator</span></span>](../operators/stackalloc.md)
