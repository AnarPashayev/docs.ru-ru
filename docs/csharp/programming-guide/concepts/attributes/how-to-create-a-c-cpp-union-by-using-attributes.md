---
title: Практическое руководство. Создание объединения C/C++ с помощью атрибутов (C#)
description: Узнайте, как с помощью атрибутов можно настраивать расположение структур в памяти в C#. В этом примере реализуется эквивалент объединения из C/C++.
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 766a070105441630dfd8fecf7b9f68fa6818fe50
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925076"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="56c67-104">Практическое руководство. Создание объединения C/C++ с помощью атрибутов (C#)</span><span class="sxs-lookup"><span data-stu-id="56c67-104">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="56c67-105">С помощью атрибутов можно настраивать расположение структур в памяти.</span><span class="sxs-lookup"><span data-stu-id="56c67-105">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="56c67-106">Например, можно создать так называемое объединение в C/C++ с помощью атрибутов `StructLayout(LayoutKind.Explicit)` и `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="56c67-106">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="56c67-107">Пример</span><span class="sxs-lookup"><span data-stu-id="56c67-107">Example</span></span>

<span data-ttu-id="56c67-108">В этом сегменте кода все поля объединения `TestUnion` начинаются с одного адреса в памяти.</span><span class="sxs-lookup"><span data-stu-id="56c67-108">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestUnion
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public byte b;
}
```

## <a name="example"></a><span data-ttu-id="56c67-109">Пример</span><span class="sxs-lookup"><span data-stu-id="56c67-109">Example</span></span>

<span data-ttu-id="56c67-110">Ниже приведен еще один пример, в котором поля начинаются с разных явно заданных адресов.</span><span class="sxs-lookup"><span data-stu-id="56c67-110">The following is another example where fields start at different explicitly set locations.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestExplicit
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public long lg;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i1;

    [System.Runtime.InteropServices.FieldOffset(4)]
    public int i2;

    [System.Runtime.InteropServices.FieldOffset(8)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(12)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(14)]
    public byte b;
}
```

<span data-ttu-id="56c67-111">Два целочисленных поля `i1` и `i2` используют те же адреса памяти, что и `lg`.</span><span class="sxs-lookup"><span data-stu-id="56c67-111">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="56c67-112">Такое управление расположением структуры полезно при использовании вызова неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="56c67-112">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="56c67-113">См. также</span><span class="sxs-lookup"><span data-stu-id="56c67-113">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="56c67-114">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="56c67-114">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="56c67-115">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="56c67-115">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="56c67-116">Отражение (C#)</span><span class="sxs-lookup"><span data-stu-id="56c67-116">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="56c67-117">Атрибуты (C#)</span><span class="sxs-lookup"><span data-stu-id="56c67-117">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="56c67-118">Создание настраиваемых атрибутов (C#)</span><span class="sxs-lookup"><span data-stu-id="56c67-118">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="56c67-119">Обращение к атрибутам с помощью отражения (C#)</span><span class="sxs-lookup"><span data-stu-id="56c67-119">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
