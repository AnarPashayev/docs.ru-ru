---
title: Операторы сравнения. Справочник по C#
description: Дополнительные сведения об операторах сравнения C#, которые можно использовать для проверки очередности числовых значений.
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 9fa739d8b5461d4043f3ae51f5d14949a95c68e5
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916886"
---
# <a name="comparison-operators-c-reference"></a>Операторы сравнения (справочник по C#)

Операторы сравнения [`<` (меньше чем)](#less-than-operator-), [`>` (больше чем)](#greater-than-operator-), [`<=` (меньше или равно)](#less-than-or-equal-operator-) и [`>=` (больше или равно)](#greater-than-or-equal-operator-) (или реляционные операторы) сравнивают операнды. Эти операторы поддерживаются всеми [целочисленными](../builtin-types/integral-numeric-types.md) типами и типами с [плавающей запятой](../builtin-types/floating-point-numeric-types.md).

> [!NOTE]
> Если какой-то из операндов операторов `==`, `<`, `>`, `<=` и `>=` не является числом (<xref:System.Double.NaN?displayProperty=nameWithType> или <xref:System.Single.NaN?displayProperty=nameWithType>), результатом операции будет `false`. Это означает, что значение `NaN` не больше, не меньше и не равно любому другому значению `double` (или `float`), включая `NaN`. Дополнительные сведения и примеры см. в справочных статьях по <xref:System.Double.NaN?displayProperty=nameWithType> или <xref:System.Single.NaN?displayProperty=nameWithType>.

Тип [char](../builtin-types/char.md) также поддерживает операторы сравнения. В случае операндов `char` сравниваются соответствующие коды символов.

Типы перечисления также поддерживают операторы сравнения. Если операнды имеют одинаковый тип [enum](../builtin-types/enum.md), сравниваются соответствующие значения базового целочисленного типа.

Операторы [`==` и `!=`](equality-operators.md) проверяют равенство или неравенство своих операндов.

## <a name="less-than-operator-"></a>Оператор "меньше чем" \<

Оператор `<` возвращает `true`, если его левый операнд меньше правого. В противном случае возвращается `false`:

[!code-csharp-interactive[less than example](snippets/shared/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Оператор "больше чем" >

Оператор `>` возвращает `true`, если его левый операнд больше правого. В противном случае возвращается `false`:

[!code-csharp-interactive[greater than example](snippets/shared/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Оператор "меньше или равно" \<=

Оператор `<=` возвращает `true`, если его левый операнд меньше правого или равен ему. В противном случае возвращается `false`:

[!code-csharp-interactive[less than or equal example](snippets/shared/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Оператор "больше или равно" >=

Оператор `>=` возвращает `true`, если его левый операнд больше правого или равен ему. В противном случае возвращается `false`:

[!code-csharp-interactive[greater than or equal example](snippets/shared/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Возможность перегрузки оператора

Определяемый пользователем тип может [перегружать](operator-overloading.md) операторы `<`, `>`, `<=` и `>=`.

Если тип перегружает один из операторов `<` и `>`, он должен также перегружать операторы `<` и `>`. Если тип перегружает один из операторов `<=` и `>=`, он должен также перегружать операторы `<=` и `>=`.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в разделе [Операторы отношения и проверки типа](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) в статье по [спецификации языка C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Операторы равенства](equality-operators.md)
