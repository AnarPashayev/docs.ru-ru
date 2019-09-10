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
# <a name="unmanaged-types-c-reference"></a>Справочник по C#. Неуправляемые типы

Тип является **неуправляемым типом**, если он принадлежит к одному из следующих типов:

- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` или `bool`;
- любой тип [перечисления](../keywords/enum.md);
- любой тип [указателя](../../programming-guide/unsafe-code-pointers/pointer-types.md).
- Любой определенный пользователем тип [структуры](../keywords/struct.md), который содержит поля только неуправляемых типов в C# 7.3 и более ранних версиях, не является сконструированным типом (тип, который включает по крайней мере один аргумент типа)

Начиная с C# 7.3 можно использовать [ограничение `unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint), чтобы указать, что параметр типа является отличным от указателя неуправляемым типом.

Начиная с C# 8.0, *сконструированный* тип структуры, содержащий поля только неуправляемых типов, также является неуправляемым, как показано в следующем примере:

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

Универсальная структура может быть источником как для неуправляемых сконструированных типов, так и для сконструированных типов, отличных от неуправляемых. В предыдущем примере определяется универсальная структура `Coords<T>`, а также представлены примеры неуправляемых сконструированных типов. Примером типа, отличного от неуправляемого, является `Coords<object>`. Он не является неуправляемым, так как содержит поля типа `object`, которые являются отличными от неуправляемых. Если необходимо, чтобы *все* сконструированные типы были неуправляемыми, используйте ограничение `unmanaged` в определении универсальной структуры:

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в разделе [Типы указателей](~/_csharplang/spec/unsafe-code.md#pointer-types) в статье [Спецификации языка C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Типы указателей](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Типы, связанные с памятью и диапазонами](../../../standard/memory-and-spans/index.md)
- [Оператор sizeof](../operators/sizeof.md)
- [Оператор stackalloc](../operators/stackalloc.md)
