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
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Практическое руководство. Создание объединения C/C++ с помощью атрибутов (C#)

С помощью атрибутов можно настраивать расположение структур в памяти. Например, можно создать так называемое объединение в C/C++ с помощью атрибутов `StructLayout(LayoutKind.Explicit)` и `FieldOffset`.

## <a name="example"></a>Пример

В этом сегменте кода все поля объединения `TestUnion` начинаются с одного адреса в памяти.

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

## <a name="example"></a>Пример

Ниже приведен еще один пример, в котором поля начинаются с разных явно заданных адресов.

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

Два целочисленных поля `i1` и `i2` используют те же адреса памяти, что и `lg`. Такое управление расположением структуры полезно при использовании вызова неуправляемого кода.

## <a name="see-also"></a>См. также

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Руководство по программированию на C#](../../index.md)
- [Атрибуты](../../../../standard/attributes/index.md)
- [Отражение (C#)](../reflection.md)
- [Атрибуты (C#)](index.md)
- [Создание настраиваемых атрибутов (C#)](creating-custom-attributes.md)
- [Обращение к атрибутам с помощью отражения (C#)](accessing-attributes-by-using-reflection.md)
