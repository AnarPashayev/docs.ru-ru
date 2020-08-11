---
title: + и += (операторы). Справочник по C#
ms.date: 04/23/2020
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: f1db0054ad2411bfe23f10b64bc2727a71ad7463
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916961"
---
# <a name="-and--operators-c-reference"></a>Операторы + и +=. Справочник по C#

Операторы `+` и `+=` поддерживаются встроенными [целыми](../builtin-types/integral-numeric-types.md) числовыми типами и числовыми типами [с плавающей запятой](../builtin-types/floating-point-numeric-types.md), а также [строковым](../builtin-types/reference-types.md#the-string-type) типом и типами[делегатов](../builtin-types/reference-types.md#the-delegate-type).

Сведения об арифметическом операторе `+` см. в разделе [Операторы унарного плюса и минуса](arithmetic-operators.md#unary-plus-and-minus-operators) и [Оператор сложения +](arithmetic-operators.md#addition-operator-) в статье [Арифметические операторы](arithmetic-operators.md).

## <a name="string-concatenation"></a>Объединение строк

Если один или оба операнда имеют тип [string](../builtin-types/reference-types.md#the-string-type), оператор `+` сцепляет строковые представления этих операндов (строковое представление `null` является пустой строкой):

[!code-csharp-interactive[string concatenation](snippets/shared/AdditionOperator.cs#AddStrings)]

В C#, начиная с версии 6, реализован более удобный способ форматирования строк, который называется [интерполяция строк](../tokens/interpolated.md):

[!code-csharp-interactive[string interpolation](snippets/shared/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Объединение делегатов

Для операндов того же типа [delegate](../builtin-types/reference-types.md#the-delegate-type) оператор `+` возвращает новый экземпляр делегата, при вызове которого вызывается сначала левый, а затем правый операнд. Если какой-либо из операндов имеет значение `null`, оператор `+` возвращает значение другого операнда (это тоже может быть `null`). Следующий пример демонстрирует объединение делегатов с помощью оператора `+`:

[!code-csharp-interactive[delegate combination](snippets/shared/AdditionOperator.cs#AddDelegates)]

Для удаления делегатов используйте [оператор `-`](subtraction-operator.md#delegate-removal).

См. дополнительные сведения о [типах делегатов](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Оператор присваивания сложения (+=)

Выражение, использующее оператор `+=`, такое как

```csharp
x += y
```

эквивалентно

```csharp
x = x + y
```

за исключением того, что `x` вычисляется только один раз.

В следующем примере иллюстрируется использование оператора `+=`.

[!code-csharp-interactive[+= examples](snippets/shared/AdditionOperator.cs#AddAndAssign)]

Можно также использовать оператор `+=`, который позволяет указать метод обработчика событий при подписке на [событие](../keywords/event.md). Дополнительные сведения см. в разделе [Практическое руководство. Подписка и отмена подписки на события](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Возможность перегрузки оператора

Определяемый пользователем тип может [перегружать](operator-overloading.md) оператор `+`. При перегрузке бинарного оператора `+` неявно перегружается и соответствующий оператор `+=`. Определяемый пользователем тип не может перегружать оператор `+=` явным образом.

## <a name="c-language-specification"></a>Спецификация языка C#

См. дополнительные сведения об [унарном операторе сложение](~/_csharplang/spec/expressions.md#unary-plus-operator) и [операторе сложения](~/_csharplang/spec/expressions.md#addition-operator) в [спецификации языка C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- [Сцепка нескольких строк](../../how-to/concatenate-multiple-strings.md)
- [События](../../programming-guide/events/index.md)
- [Арифметические операторы](arithmetic-operators.md)
- [Операторы - и -=](subtraction-operator.md)
