---
title: Логические операторы. Справочник по C#
description: Узнайте об операторах C#, которые выполняют такие логические операции, как отрицание, конъюнкция (И), а также инклюзивная и эксклюзивная дизъюнкция (ИЛИ), с использованием соответствующих операндов.
ms.date: 06/29/2020
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
- '|=_CSharpKeyword'
- ^=_CSharpKeyword
- '&=_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: 00b1523029ed6562fda6947415029cd3b7a9b405
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916892"
---
# <a name="boolean-logical-operators-c-reference"></a>Логические операторы (справочник по C#)

Следующие операторы выполняют логические операции с использованием [логических](../builtin-types/bool.md) операндов:

- Унарный [`!` (логическое отрицание)](#logical-negation-operator-) оператор.
- Бинарные [`&` (логическое И)](#logical-and-operator-), [`|` (логическое ИЛИ)](#logical-or-operator-), а также [`^` (логическое исключающее ИЛИ)](#logical-exclusive-or-operator-) операторы. Эти операторы всегда обрабатывают оба операнда.
- Бинарные [`&&` (условное логическое И)](#conditional-logical-and-operator-) и [`||` (условное логическое ИЛИ)](#conditional-logical-or-operator-) операторы. Эти операторы вычисляют правый операнд, только если это необходимо.

Для операндов [целочисленных](../builtin-types/integral-numeric-types.md) типов операторы `&`, `|` и `^` выполняют побитовые логические операции. Дополнительные сведения см. в разделе [Побитовые операторы и операторы сдвига](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Оператор логического отрицания !

Унарный префиксный оператор `!` выполняет логическое отрицание операнда, возвращая `true`, если операнд имеет значение `false`, и `false`, если операнд имеет значение `true`.

[!code-csharp-interactive[logical negation](snippets/shared/BooleanLogicalOperators.cs#Negation)]

Начиная с версии C# 8.0, унарный постфиксный оператор `!`[допускает значение NULL](null-forgiving.md).

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a> Оператор логического И &amp;

Оператор `&` вычисляет логическое И для всех своих операндов. Результат операции `x & y` принимает значение `true`, если оба оператора `x` и `y` имеют значение `true`. В противном случае результат будет `false`.

Оператор `&` вычисляет оба операнда, даже если левый операнд имеет значение `false`. При этом операция должна вернуть значение `false`, независимо от значения правого операнда.

В следующем примере правый операнд оператора `&` является вызовом метода, который выполняется независимо от значения левого операнда:

[!code-csharp-interactive[logical AND](snippets/shared/BooleanLogicalOperators.cs#And)]

[Условный оператор логического И](#conditional-logical-and-operator-) `&&` также вычисляет логическое И для своих операндов, но не вычисляет правый операнд, если левый операнд имеет значение `false`.

Для операндов [целочисленных типов](../builtin-types/integral-numeric-types.md) оператор `&` вычисляет [побитовое логическое И](bitwise-and-shift-operators.md#logical-and-operator-) своих операндов. Унарный оператор `&` является оператором [AddressOf](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Оператор логического исключения ИЛИ ^

Оператор `^` вычисляет логическое исключение ИЛИ для всех своих операндов, возвращая `true` для `x ^ y`, если `x` имеет значение `true` и `y` имеет значение `false` или `x` имеет значение `false` и `y` имеет значение `true`. В противном случае результат будет `false`. То есть для операндов `bool` оператор `^` возвращает тот же результат, что и [оператор неравенства](equality-operators.md#inequality-operator-) `!=`.

[!code-csharp-interactive[logical exclusive OR](snippets/shared/BooleanLogicalOperators.cs#Xor)]

Для операндов [целочисленных типов](../builtin-types/integral-numeric-types.md) оператор `^` вычисляет [побитовое исключающее ИЛИ](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) своих операндов.

## <a name="logical-or-operator-"></a>Оператор логического ИЛИ |

Оператор `|` вычисляет логическое ИЛИ для всех своих операндов. Результат операции `x | y` принимает значение `true`, если хотя бы один из операторов `x` или `y` имеет значение `true`. В противном случае результат будет `false`.

Оператор `|` вычисляет оба операнда, даже если левый операнд имеет значение `true`. При этом операция должна вернуть значение `true`, независимо от значения правого операнда.

В следующем примере правый операнд оператора `|` является вызовом метода, который выполняется независимо от значения левого операнда:

[!code-csharp-interactive[logical OR](snippets/shared/BooleanLogicalOperators.cs#Or)]

[Условный оператор логического ИЛИ](#conditional-logical-or-operator-) `||` также вычисляет логическое ИЛИ для своих операндов, но не вычисляет правый операнд, если левый операнд имеет значение `true`.

Для операндов [целочисленных типов](../builtin-types/integral-numeric-types.md) оператор `|` вычисляет [побитовое логическое ИЛИ](bitwise-and-shift-operators.md#logical-or-operator-) своих операндов.

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a> Условный оператор логического И &amp;&amp;

Условный оператор логического И `&&` (оператор короткого замыкания) вычисляет логическое И для своих операндов. Результат операции `x && y` принимает значение `true`, если оба оператора `x` и `y` имеют значение `true`. В противном случае результат будет `false`. Если `x` имеет значение `false`, `y` не вычисляется.

В следующем примере правый операнд оператора `&&` является вызовом метода, который не выполняется, если левый операнд имеет значение `false`:

[!code-csharp-interactive[conditional logical AND](snippets/shared/BooleanLogicalOperators.cs#ConditionalAnd)]

[Оператор логического И](#logical-and-operator-) `&` также вычисляет логическое И для своих операндов, но он всегда вычисляет оба операнда.

## <a name="conditional-logical-or-operator-"></a>Условный оператор логического ИЛИ ||

Условный оператор логического ИЛИ `||` (оператор короткого замыкания) вычисляет логическое ИЛИ для своих операндов. Результат операции `x || y` принимает значение `true`, если хотя бы один из операторов `x` или `y` имеет значение `true`. В противном случае результат будет `false`. Если `x` имеет значение `true`, `y` не вычисляется.

В следующем примере правый операнд оператора `||` является вызовом метода, который не выполняется, если левый операнд имеет значение `true`:

[!code-csharp-interactive[conditional logical OR](snippets/shared/BooleanLogicalOperators.cs#ConditionalOr)]

[Оператор логического ИЛИ](#logical-or-operator-) `|` также вычисляет логическое ИЛИ для своих операндов, но всегда вычисляет оба операнда.

## <a name="nullable-boolean-logical-operators"></a>Операторы, допускающие логическое значение NULL

Для операндов `bool?` операторы [`&` (логическое И)](#logical-and-operator-) и [`|` (логическое ИЛИ)](#logical-or-operator-) поддерживают следующую логику с тремя значениями:

- Оператор `&` возвращает `true` только в том случае, если оба операнда имеют значение `true`. Если `x` или `y` имеет значение `false`, оператор `x & y` возвращает `false` (даже если другой операнд имеет значение `null`). В противном случае выражение `x & y` будет иметь значение `null`.

- Оператор `|` возвращает `false` только в том случае, если оба операнда имеют значение `false`. Если `x` или `y` имеет значение `true`, оператор `x | y` возвращает `true` (даже если другой операнд имеет значение `null`). В противном случае выражение `x | y` будет иметь значение `null`.

Эта семантика описывается в следующей таблице:

|x|y|x&y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  

Поведение этих операторов отличается от типичного поведения операторов, допускающих значение NULL. Как правило, оператор, который определяется для операндов типа значения, можно также использовать с соответствующими операндами типа, допускающего значение NULL. Такой оператор возвращает `null`, если какой-либо из операндов имеет значение `null`. При этом операторы `&` и `|` могут возвращать отличное от NULL значение, даже если один из операндов имеет значение `null`. См. подробнее о поведении операторов, допускающих значение NULL, в разделе [Операторы с нулификацией](../builtin-types/nullable-value-types.md#lifted-operators) в статье [Типы, допускающие значение NULL](../builtin-types/nullable-value-types.md).

Вы также можете также использовать операторы `!` и `^` с операндами `bool?`, как показано в следующем примере:

[!code-csharp-interactive[lifted negation and xor](snippets/shared/BooleanLogicalOperators.cs#WithNullableBoolean)]

Условные логические операторы `&&` и `||` не поддерживают операнды типа `bool?`.

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

Операторы `&`, `|` и `^` поддерживают составное присваивание, как показано в следующем примере:

[!code-csharp-interactive[compound assignment](snippets/shared/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> Условные логические операторы `&&` и `||` не поддерживают составное присваивание.

## <a name="operator-precedence"></a>Приоритет операторов

В следующем списке перечислены логические операторы в порядке убывания приоритета:

- Оператор логического отрицания `!`
- Оператор логического И `&`
- Оператор логического исключающего ИЛИ `^`
- Оператор логического ИЛИ `|`
- Условный оператор логического И `&&`
- Условный оператор логического ИЛИ `||`

Порядок вычисления, определяемый приоритетом операторов, можно изменить с помощью скобок (`()`).

[!code-csharp-interactive[operator precedence](snippets/shared/BooleanLogicalOperators.cs#Precedence)]

Полный список операторов C#, упорядоченный по уровню приоритета, можно найти в разделе [Приоритет операторов](index.md#operator-precedence) статьи [Операторы C#](index.md).

## <a name="operator-overloadability"></a>Возможность перегрузки оператора

Определяемый пользователем тип может [перегружать](operator-overloading.md) операторы `!`, `&`, `|` и `^`. При перегрузке бинарного оператора соответствующий оператор составного присваивания также неявно перегружается. Определяемый пользователем тип не может перегружать оператор составного присваивания явным образом.

Определяемый пользователем тип не может перегружать условные логические операторы `&&` и `||`. При этом, если определяемый пользователем тип каким-либо образом перегружает операторы [true и false](true-false-operators.md) и операторы `&` и `|`, операция `&&` или `||` может быть применена для операндов этого типа. Дополнительные сведения см. в разделе [Пользовательские условные логические операторы](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) в [Спецификации языка C#](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):

- [Оператор логического отрицания](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Логические операторы](~/_csharplang/spec/expressions.md#logical-operators)
- [Условные логические операторы](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Составное присваивание](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- [Побитовые операторы и операторы сдвига](bitwise-and-shift-operators.md)
