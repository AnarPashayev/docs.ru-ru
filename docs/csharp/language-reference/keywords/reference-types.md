---
title: Ссылочные типы. Справочник по C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 4b3b1d5b27c3f6a88ce752243ab2d1389b168f0e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634058"
---
# <a name="reference-types-c-reference"></a>Ссылочные типы (справочник по C#)

В C# существуют две разновидности типов: ссылочные типы и типы значений. В переменных ссылочных типов хранятся ссылки на их данные (объекты), а переменные типа значений содержат свои данные непосредственно. Две переменные ссылочного типа могут ссылаться на один и тот же объект, поэтому операции над одной переменной могут затрагивать объект, на который ссылается другая переменная. Каждая переменная типа значения имеет собственную копию данных, и операции над одной переменной не могут затрагивать другую (за исключением переменных параметров in, ref и out; см. описание модификатора параметров [in](in-parameter-modifier.md), [ref](ref.md) и [out](out-parameter-modifier.md)).

 Для объявления ссылочных типов используются следующие ключевые слова:

- [class](class.md)

- [interface](interface.md)

- [delegate](delegate.md)

 В C# также предусмотрены следующие встроенные ссылочные типы:

- [dynamic](dynamic.md)

- [object](object.md)

- [string](string.md)

## <a name="see-also"></a>См. также

- [Справочник по C#](../../../csharp/language-reference/index.md)
- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Ключевые слова в C#](index.md)
- [Типы](types.md)
- [Типы значений](value-types.md)
