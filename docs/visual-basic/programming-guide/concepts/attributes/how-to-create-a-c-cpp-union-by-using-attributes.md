---
title: Инструкции. Создание объединения C-C + + с помощью атрибутов
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: ebab0ad947f776932f9379af3969e369eeec1941
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400685"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>How to: Create a C/C++ Union by Using Attributes (Visual Basic) (Практическое руководство. Создание объединения C/C++ с помощью атрибутов (Visual Basic))

С помощью атрибутов можно настраивать расположение структур в памяти. Например, можно создать так называемое объединение в C/C++ с помощью атрибутов `StructLayout(LayoutKind.Explicit)` и `FieldOffset`.

## <a name="example"></a>Пример

В этом сегменте кода все поля объединения `TestUnion` начинаются с одного адреса в памяти.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a>Пример

Ниже приведен еще один пример, в котором поля начинаются с разных явно заданных адресов.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

Два целочисленных поля `i1` и `i2` используют те же адреса памяти, что и `lg`. Такое управление расположением структуры полезно при использовании вызова неуправляемого кода.

## <a name="see-also"></a>См. также раздел

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Руководство по программированию на Visual Basic](../../index.md)
- [Атрибуты](../../../../standard/attributes/index.md)
- [Reflection (Visual Basic)](../reflection.md) (Отражение (Visual Basic))
- [Атрибуты (Visual Basic)](../../../language-reference/attributes.md)
- [Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md) (Создание настраиваемых атрибутов (Visual Basic))
- [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md) (Обращение к атрибутам с помощью отражения (Visual Basic))
