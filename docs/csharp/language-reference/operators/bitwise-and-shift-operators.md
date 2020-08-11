---
title: Побитовые операторы и операторы сдвига. Справочник по C#
description: Дополнительные сведения об операторах C#, которые выполняют побитовые логические операции или операции сдвига с операндами целочисленного типа.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- <<=_CSharpKeyword
- '>>=_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 99181855fdf8e937676e44e8b347510f9405aa3d
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916905"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Побитовые операторы и операторы сдвига (справочник по C#)

Следующие операторы выполняют побитовые операции или операции сдвига с операндами [целочисленных](../builtin-types/integral-numeric-types.md) или [символьных](../builtin-types/char.md) типов:

- Унарный оператор [`~` (побитовое дополнение)](#bitwise-complement-operator-)
- Бинарные операторы сдвига [`<<` (сдвиг влево)](#left-shift-operator-) и [`>>` (сдвиг вправо)](#right-shift-operator-)
- Бинарные операторы [`&` (логическое и)](#logical-and-operator-), [`|` (логическое или)](#logical-or-operator-) и [`^` (логическое исключающее или)](#logical-exclusive-or-operator-)

Эти операторы определены для типов `int`, `uint`, `long` и `ulong`. Если оба операнда имеют другие целочисленные типы (`sbyte`, `byte`, `short`, `ushort` или `char`), их значения преобразуются в тип `int`, который также является типом результата операции. Если операнды имеют разные целочисленные типы, их значения преобразуются в ближайший содержащий целочисленный тип. Дополнительные сведения см. в разделе [Числовые повышения уровня](~/_csharplang/spec/expressions.md#numeric-promotions) в статье [Спецификации языка C#](~/_csharplang/spec/introduction.md).

Операторы `&`, `|` и `^` также определены для операндов типа `bool`. Дополнительные сведения см. в разделе [Логические операторы](boolean-logical-operators.md).

Побитовые операции и операции сдвига никогда не вызывают переполнение и дают одинаковые результаты в [проверенных и непроверенных](../keywords/checked-and-unchecked.md) контекстах.

## <a name="bitwise-complement-operator-"></a>Оператор побитового дополнения ~

Оператор `~` создает побитовое дополнение своего операнда путем инвертирования каждого бита:

[!code-csharp-interactive[bitwise NOT](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseComplement)]

Можно также использовать символ `~` для объявления методов завершения. Дополнительные сведения см. в разделе [Методы завершения](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Оператор сдвига влево \<\<

Оператор `<<` сдвигает левый операнд влево на [количество битов, определенное правым операндом](#shift-count-of-the-shift-operators).

Операция сдвига влево отбрасывает старшие биты, которые находятся за пределами диапазона типа результата, и задает позиции пустых битов низкого порядка, равные нулю, как показано в следующем примере:

[!code-csharp-interactive[left shift](snippets/shared/BitwiseAndShiftOperators.cs#LeftShift)]

Поскольку операторы сдвига определены только для типов `int`, `uint`, `long` и `ulong`, результат операции всегда содержит по крайней мере 32 бита. Если левый операнд имеет другой целочисленный тип (`sbyte`, `byte`, `short`, `ushort` или `char`), его значение преобразуется в тип `int`, как показано в следующем примере:

[!code-csharp-interactive[left shift with promotion](snippets/shared/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Сведения о том, как правый операнд оператора `<<` определяет величину сдвига, см. в разделе [Величина смещения операторов сдвига](#shift-count-of-the-shift-operators).

## <a name="right-shift-operator-"></a>Оператор сдвига вправо >>

Оператор `>>` сдвигает левый операнд вправо на [количество битов, определенное правым операндом](#shift-count-of-the-shift-operators).

Операция сдвига вправо удаляет младшие разряды, как показано в следующем примере:

[!code-csharp-interactive[right shift](snippets/shared/BitwiseAndShiftOperators.cs#RightShift)]

Позиции пустых битов высокого порядка задаются с учетом типа левого операнда следующим образом:

- Если левый операнд имеет тип `int` или `long`, оператор сдвига вправо выполняет *арифметический* сдвиг, то есть значение наиболее значимого бита (знаковый бит) левого операнда переносится в пустые битовые позиции высокого разряда. То есть для пустых битовых позиций высокого порядка задается ноль, если левый операнд неотрицательный, и единица, если он отрицательный.

  [!code-csharp-interactive[arithmetic right shift](snippets/shared/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Если левый операнд имеет тип `uint` или `ulong`, оператор сдвига вправо выполняет *логический* сдвиг, то есть пустым битовым позициям высокого порядка всегда присваивается нулевое значение.

  [!code-csharp-interactive[logical right shift](snippets/shared/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Сведения о том, как правый операнд оператора `>>` определяет величину сдвига, см. в разделе [Величина смещения операторов сдвига](#shift-count-of-the-shift-operators).

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a> Оператор логического И &amp;

Оператор `&` вычисляет побитовое логическое И своих операндов:

[!code-csharp-interactive[bitwise AND](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseAnd)]

Для операндов типа `bool` оператор `&` вычисляет [логическое И](boolean-logical-operators.md#logical-and-operator-) по своим операндам. Унарный оператор `&` является оператором [AddressOf](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Оператор логического исключения ИЛИ ^

Оператор `^` вычисляет побитовое логическое исключающее ИЛИ, также известное как побитовое логическое XOR, своих операндов:

[!code-csharp-interactive[bitwise XOR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseXor)]

Для операндов типа `bool` оператор `^` вычисляет [логическое исключающее ИЛИ](boolean-logical-operators.md#logical-exclusive-or-operator-) по своим операндам.

## <a name="logical-or-operator-"></a>Оператор логического ИЛИ |

Оператор `|` вычисляет побитовое логическое ИЛИ своих операндов:

[!code-csharp-interactive[bitwise OR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseOr)]

Для операндов типа `bool` оператор `|` вычисляет [логическое ИЛИ](boolean-logical-operators.md#logical-or-operator-) по своим операндам.

## <a name="compound-assignment"></a>Составное присваивание

Для бинарного оператора `op` выражение составного присваивания в форме

```csharp
x op= y
```

эквивалентно

```csharp
x = x op y
```

за исключением того, что `x` вычисляется только один раз.

В следующем примере показано использование составного присваивания с побитовыми операторами и операторами сдвига:

[!code-csharp-interactive[compound assignment](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignment)]

Из-за [восходящих приведений](~/_csharplang/spec/expressions.md#numeric-promotions) результат операции `op` может быть невозможно неявно преобразовать в тип `T` из `x`. В этом случае, если `op` является предопределенным оператором, и результат операции является явно преобразуемым в тип `T``x`, выражение составного присваивания формы `x op= y` эквивалентно `x = (T)(x op y)`, за исключением того, что `x` вычисляется только один раз. В следующем примере продемонстрировано такое поведение.

[!code-csharp-interactive[compound assignment with cast](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>Приоритет операторов

Следующий список упорядочивает побитовые операторы и операторы сдвига по приоритету, от высокого до низкого:

- Оператор побитового дополнения `~`
- Операторы сдвига `<<` и `>>`
- Оператор логического И `&`
- Оператор логического исключающего ИЛИ `^`
- Оператор логического ИЛИ `|`

Порядок вычисления, определяемый приоритетом операторов, можно изменить с помощью скобок (`()`).

[!code-csharp-interactive[operator precedence](snippets/shared/BitwiseAndShiftOperators.cs#Precedence)]

Полный список операторов C#, упорядоченный по уровню приоритета, можно найти в разделе [Приоритет операторов](index.md#operator-precedence) статьи [Операторы C#](index.md).

## <a name="shift-count-of-the-shift-operators"></a>Величина смещения операторов сдвига

Для операторов сдвига `<<` и `>>` тип правого операнда должен быть `int` или типом, для которого существует [предопределенное неявное числовое преобразование](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) в `int`.

Для выражений `x << count` и `x >> count` фактическая величина сдвига зависит от типа `x` следующим образом:

- Если `x` имеет тип `int` или `uint`, величина сдвига определяется младшими *пятью* битами правого операнда. То есть величина сдвига вычисляется на основе `count & 0x1F` (или `count & 0b_1_1111`).

- Если `x` имеет тип `long` или `ulong`, величина сдвига определяется младшими *шестью* битами правого операнда. То есть величина сдвига вычисляется на основе `count & 0x3F` (или `count & 0b_11_1111`).

В следующем примере продемонстрировано такое поведение.

[!code-csharp-interactive[shift count example](snippets/shared/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> Как показано в предыдущем примере, результат операции сдвига может быть ненулевым, даже если значение правого операнда больше числа битов в левом операнде.

## <a name="enumeration-logical-operators"></a>Логические операторы перечисления

Операторы `~`, `&`, `|` и `^` также поддерживаются для любого типа [перечисления](../builtin-types/enum.md). Для операндов одного типа перечисления логическая операция выполняется по соответствующим значениям базового целочисленного типа. Например, для любого `x` и `y` типа перечисления `T` с базовым типом `U` выражение `x & y` дает тот же результат, что и выражение `(T)((U)x & (U)y)`.

Побитовые логические операторы обычно используются с типом перечисления, который определяется с помощью атрибута [Flags](xref:System.FlagsAttribute). Дополнительные сведения см. в разделе [Типы перечислений как битовые флаги](../builtin-types/enum.md#enumeration-types-as-bit-flags) в статье [Типы перечислений](../builtin-types/enum.md).

## <a name="operator-overloadability"></a>Возможность перегрузки оператора

Определяемый пользователем тип может [перегружать](operator-overloading.md) операторы `~`, `<<`, `>>`, `&`, `|` и `^`. При перегрузке бинарного оператора соответствующий оператор составного присваивания также неявно перегружается. Определяемый пользователем тип не может перегружать оператор составного присваивания явным образом.

Если определяемый пользователем тип `T` перегружает оператор `<<` или `>>`, тип левого операнда должен быть `T`, а тип правого — `int`.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):

- [Оператор побитового дополнения](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Операторы сдвига](~/_csharplang/spec/expressions.md#shift-operators)
- [Логические операторы](~/_csharplang/spec/expressions.md#logical-operators)
- [Составное присваивание](~/_csharplang/spec/expressions.md#compound-assignment)
- [Восходящие приведения числовых типов](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>См. также раздел

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- [Логические операторы](boolean-logical-operators.md)
