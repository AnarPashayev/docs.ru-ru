---
title: Операторы пользовательского преобразования — справочник по C#
description: Узнайте, как определить пользовательские явные и неявные преобразования типа в C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: b59fc27be31f1a38e2a6c3cabd82598933b5ed53
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121401"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Операторы пользовательского преобразования (справочник по C#)

Пользовательский тип может определять неявное или явное пользовательское преобразование в другой тип или из него.

Неявные преобразования не требуют специального синтаксиса для вызова и могут происходить в различных ситуациях, например при вызовах методов и в назначениях. Предопределенные неявные преобразования на C# всегда завершаются успешно и никогда не вызывают исключение. Неявные пользовательские преобразования должны вести себя таким же образом. Если пользовательское преобразование может вызвать исключение или привести к потере данных, определите его как явное преобразование.

Пользовательские преобразования не рассматриваются операторами [is](type-testing-and-cast.md#is-operator) и [as](type-testing-and-cast.md#as-operator). Используйте [выражение приведения](type-testing-and-cast.md#cast-expression) для вызова явного пользовательского преобразования.

Используйте ключевые слова `operator` и `implicit` или `explicit` для определения неявного или явного преобразования соответственно. Тип, который определяет преобразование, должен быть типом источника или целевого объекта этого преобразования. Преобразование между двумя пользовательскими типами можно определить одним из двух типов.

Следующий пример иллюстрирует, как определить неявное и явное преобразования:

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

Можно также использовать ключевое слово `operator` для перегрузки предопределенного оператора C#. Для получения дополнительной информации см. раздел [Перегрузка операторов](operator-overloading.md).

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):

- [Операторы преобразования](~/_csharplang/spec/classes.md#conversion-operators)
- [Пользовательские преобразования](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Неявные преобразования](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Явные преобразования](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Операторы в C#](index.md)
- [Перегрузка операторов](operator-overloading.md)
- [Операторы приведения и тестирования типов](type-testing-and-cast.md)
- [Приведение и преобразование типов](../../programming-guide/types/casting-and-type-conversions.md)
- [Рекомендации по разработке. Операторы преобразования](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [Связанные пользовательские явные преобразования в C#](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
